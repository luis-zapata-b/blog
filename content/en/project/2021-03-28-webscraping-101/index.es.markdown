---
title: Webscraping 101
author: Luis José Zapata Bobadilla
date: '2021-03-28'
slug: webscraping-101
categories:
  - Webscraping
  - R
tags:
  - R
  - Webscraping
subtitle: ''
summary: ''
authors: []
lastmod: '2021-03-28T10:50:36-05:00'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---

En internet hay mucha información gratuita y de fácil acceso. Existen dos tipos de información disponible: aquella que se puede descargar fácilmente a través de un botón de "*descargar*" y la que se encuentra visible en la página web.

Para obtener ambos tipos de información, no es necesario descargar la información manualmente. Es posible automatizar la descarga de esta información a través de un código.

En este post introduciré cómo podemos descargar el primer tipo de información (aquel que solo necesitas presionar un botón de "*descarga*") de manera que se descargue automáticamente a travéz de un código. Sin embargo, para poder hacer eso hay que entender los mecanismos que permiten la descarga de información por internet. Hoy hablaremos de dos de estas: los métodos **POST** y **GET**.

## HTTP: GET y POST

El protocolo **HTTP** es el protocolo de comunicación usado por los navegadores para acceder a una página web. HTTP regula como el servidor (donde está alojada la página web) envía recursos al cliente (el navegador web). Estos recursos contienen las "*instrucciones*" que un navegador web (como Chrome) utiliza para mostrarnos la página web e interactuar con ella.

Una **URL** es una *dirección* en la web, que define cómo se localiza un recurso en internet (Ejem: <https://www.google.com>). Al teclear esta dirección en un navegador, este envía una petición HTTP al servidor solicitando el recurso web (utilizando un método **GET** o **POST**). El servidor recibe la solicitud, busca el archivo en cuestión (una página web html, o un excel) y envía un **header** al navegador. El **header** es básicamente un mensaje sobre si la búsqueda tuve éxito o no (si el archivo existe). Si la busqueda tuvo éxito, el servidor envía adicionalmente el archivo.

Para la descarga de datos, usualmente se utilizan dos formas de envíos de datos en HTTP: **GET** y **POST**. El método **GET** se utiliza para "*sacar*" recursos del servidor, a través de una petición. El método **POST** permite "*sacar*" y "*guardar*" recursos en el servidor, a través de una petición la cual puede incluir información a *guardar*.

-   **GET**: Método del protocolo HTTP, para *obtener información*¨de un servidor. Transmite una solicitud (request) para obtener una respuesta (response, que puede ser un excel o datos que queramos descargar) al cliente (página web). Una característica del método GET es que permite llevar los datos de forma "visible" al navegador web a través del URL. Es decir, permite el uso de **querys**. Un Query es un mensaje añadido al **URL** en donde se especifica qué información se requiere. Por ejemplo, imaginemos que queremos solicitar una información a la imaginaria página web www.luis.com y los datos solicitados las visitas del mes de noviembre: variable = visitas y mes = noviembre. El *query* sería algo como: www.luis.com/**download?=variable=visitas&mes=noviembre** en donde lo que está en negritas es el llamado **query**. De esta forma, ingresaríamos un pedido al servidor y obtendríamos una respuesta a cambio (la cual podría ser un excel, por dar un ejemplo). Cada página web tiene su propia sintaxis de como solicitar un pedido.

-   **POST**: Otro método del protocolo HTTP, que a diferencia del GET, *envía información* la cual es procesada en el servidor, el cual es actualizado. Con el método POST podemos enviar información para ser guardada en el servidor. Adicionalmente, se puede utilizar para descargar información. La peculariedad del método POST para descargar información, es que se utilizan dos URL's para la descarga. Esto es útil para el servidor dado que mejora su seguridad. Para descargar un archivo con el método POST, primero se envía un **query** de forma similar al método GET. Sin embargo, el servidor no nos enviará una respuesta inmediatamente, más bien, abriría una *puerta temporal* desde otra URL para descargar el archivo.

### Ejemplo de descarga con GET y POST

Para entender mejor los protocolos GET y POST, utilizaremos ambos métodos para descargar información disponible en la página web del [COES](https://www.coes.org.pe/portal/). En la página web hay información que se puede descargar utilizando ambos métodos.

#### Ejemplo: Método POST

El Portal de Indicadores del COES permite descargar información de la producción diaria de electricidad hasta el día de ayer.

Para acceder a esta parte, ingresamos al **Portal de Indicadores** en la página web del COES. Si hacemos clic en exportar, estaríamos enviandoun **query** el cual contendría el intervalo de fechas seleccionados dentro del **request**, recibiendo a cambio una respuesta, conteniendo un excel con los datos. *Como podemos saber si el método es POST o QUERY?* Es fácil, si alguna herramienta de análisis web como las **herramientas de desarrollador de Chrome**.

<div class="figure" style="text-align: center">
<img src="images/HTMLI.png" alt="Herramientas de desarrollador de Chrome" width="600px" />
<p class="caption">Figure 1: Herramientas de desarrollador de Chrome</p>
</div>

Al hacer clic en ella, nos mostrará diversas herramientas, dentro de la cual la más relevante ahora para nosotros es **Network**. Al hacer clic en ella, nos muestra la interacción que hace nuestro cliente (página web) con el servidor del COES. Lo primero que hacemos para tener mas limpio el espacio es hacer clic en *Clear*, lo cual limpiará la ventana y nos permitirá concentrarnos en las interacciones futuras. A continuación, hacemos clic en el botón de la página web del COES **Exportar** (después de elegir el intervalo de fecha) para descargar el excel. Vemos que en la área de *Network* han aparecido dos interacciones: como son dos, nos da una pista de que posiblemente sea un método POST (una URL de envío y otra de descarga).

<div class="figure" style="text-align: center">
<img src="images/HTMLII.png" alt="Network" width="700px" />
<p class="caption">Figure 2: Network</p>
</div>

Hacemos clic en la primera interacción (**exportargeneracion**) para obtener más información. Al ser la primera, esta debería contener la información del pedido (**request**) hecho al servidor.

<div class="figure" style="text-align: center">
<img src="images/request.png" alt="Headers - POST" width="600px" />
<p class="caption">Figure 3: Headers - POST</p>
</div>

Podemos ver que el **Request Method** es, de hecho, un **POST**. Adicionalmente, se ve que el URL de envió del request es *"<https://www.coes.org.pe/Portal/portalinformacion/exportargeneracion>"*. Finalmente, podemos ver que la información enviada en el pedido son 3 datos: La fecha inicial (fechaInicial), la fecha final (fechaFinal) y un indicador (indicador).

Hay que fijarse también en el formato de la fecha: *día/mes/año*, en donde el día y el mes siempre contiene dos dígitos. Esto es importante a la hora de enviar el request.

Un **header** es como un meta-datado (información descriptiva adicional, aunque no intrínseca a nuestro pedido) que va en la petición (request) y en la recepción (response). Nótese que en la imagen hay 15 **request headers**. Como no es obligatorio usarlos, no los veremos, pero pueden ser de ayuda como veremos más adelante.

Finalmente, el **Status Code = 200** nos indica que la interacción fue exitosa.

Por lo tanto, podemos concluir, que el método para obtener esta información fue **POST**, incluyendo dentro del pedido el intervalo de fecha de los datos solicitados.

> Sin embargo, al ser un método POST el request no nos dará una respuesta automáticamente. Tenemos que revisar la segunda interacción para saber desde que dirección URL descargar los datos.

Por lo tanto, si hacemos clic en la segunda interacción (**descargargeneracion**) accederemos a la siguiente información:.

<div class="figure" style="text-align: center">
<img src="images/response.png" alt="Headers - GET" width="700px" />
<p class="caption">Figure 4: Headers - GET</p>
</div>

En donde podemos ver que se abrió una "*puerta de acceso*" a los datos desde la dirección URL: "[*https://www.coes.org.pe/Portal/portalinformacion/descargargeneracion*](https://www.coes.org.pe/Portal/portalinformacion/descargargeneracion)". Podemos ver que es un método GET, es decir, al ingresar la URL el servidor nos otorgará los datos automáticamente. Como ya ingresamos los datos del request en la anterior interacción, no es necesario añadir nuevos datos como un **query**.

#### Ejemplo: Método GET

En este ejemplo, descargaremos la información del Informe de Evaluación de la Operación Diaria. Este informe nos permite obtener información más desagregada del consumo de electricidad diario: la demanda por zonas geográficas, de grandes empresas, por recursos, etc. Para acceder a esta información primero debemos acceder a la plataforma de IEOD y revisar si la función de descarga es **POST** o **GET**.

<div class="figure" style="text-align: center">
<img src="images/IEOD_GET.png" alt="IEOD" width="500px" />
<p class="caption">Figure 5: IEOD</p>
</div>

Al acceder a la plataforma del IEOD, elegir un día, y seleccionar el excel de interés ("**Anexo1_Resumen_0709.xlsx**"). Al hacer **click derecho en el enlace**, podemos copiar la dirección URL. En este caso, la dirección copiada es: "<https://www.coes.org.pe/portal/browser/>**download?url=Post%20Operaci%C3%B3n%2FReportes%2FIEOD%2F2020%2F09%20Setiembre%2F07%2FAnexo1_Resumen_0709.xlsx**". Se puede ver por la parte en negritas que es un método **GET** de descarga (los datos añadidos al **request** se encuentran en la URL, algo que no pasa en POST). Sin embargo, que datos cambian en el request, y qué significan los caracteres extraños como **%2F**, **%20** o **%C3%B3**?

Revisando el **Network** de las **Herramientas del desarrollador de Chrome** podemos ver que el **Query** parte después de *download?url=*.

<div class="figure" style="text-align: center">
<img src="images/query1.png" alt="Headers - GET" width="500px" />
<p class="caption">Figure 6: Headers - GET</p>
</div>

Con lo visto anteriormente, podemos inferir que la parte del **GET** que lleva los datos, es decir, el **query**, es: "Post Operación/Reportes/IEOD/**2020**/**09 Setiembre**/**07**/Anexo1_Resumen\_**0709**.xlsx". En donde las primeras letras en negritas son el **año**, las segunda el **mes en número y letras**, la tercera el **número del día**, y la última el **número del día y del mes**.

Si hacemos clic en *view URL encoded* veremos que la parte codificada del URL (*Post%20Operaci%C3%B3n%2FReportes%2FIEOD%2F2020%2F09%20Setiembre%2F07%2FAnexo1_Resumen_0709.xlsx*) es:

-   **%20** = espacio vacío
-   **%C3%B3** = "ó" (letra con acento)
-   **%2F** = "/" (dash)

En conclusión, podemos decir que la descarga del IEOD se hace usando el método **GET** enviando los datos de la fecha en el **request**, incrustado en el URL en un **query**.

## Conclusiones

Ambos métodos son muy útiles para automatizar la descarga de información disponible para su descarga en internet. El siguiente paso es automatizar la descarga utilizando un software como R o Python.
