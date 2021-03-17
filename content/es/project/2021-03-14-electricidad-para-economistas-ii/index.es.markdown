---
title: Electricidad para Economistas II
author: Luis José Zapata Bobadilla
date: '2021-03-14'
slug: 'electricidad-para-economistas-2'
categories:
  - Electricidad
tags: [Electricidad]
subtitle: 'Fuentes de información de electricidad en el Perú'
summary: 'Segunda introducción a conceptos básicos del sector eléctrico en el Perú. Ahora hablaremos de la información disponible al público del sector eléctrico en Perú.'
authors: []
lastmod: '2021-03-14T18:41:56-05:00'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---



# Fuentes de Información en el Perú

# COES

El COES administra el aspecto técnico del tráfico eléctrico (oferta y demanda) en el Sistema Eléctrico Interconectado Nacional o [SEIN](https://es.wikipedia.org/wiki/Sistema_El%C3%A9ctrico_Interconectado_Nacional). Si desea repasar los aspectos técnicos de la electricidad, puedes revisarlos [aquí](https://rpubs.com/luisjo819/electricidad).

Debido a lo mencionado anteriormente, **el COES administra información de la generación, transmisión y demanda de electricidad** en tiempo real, de manera que el sistema eléctrico se mantenga en equilibrio (Oferta = Demanda).

El COES asimismo **publica esta información en su página web <https://www.coes.org.pe/portal/>**.

Existe diversa información disponible en la página web del COES, la cual iremos describiendo a continuación, priorizando aquello que nos hes más relevante en nuestro trabajo:

## **Indicadores del Sector Energético Peruano**

Es la información de más fácil acceso en la página web del COES. Existe un enlace apenas ingresamos a la página web principal del COES:

<div class="figure" style="text-align: center">
<img src="images/COESII.png" alt="Indicador de generación total" width="700px" />
<p class="caption">Figure 1: Indicador de generación total</p>
</div>

Dentro, podemos acceder a diversa información proporcionada por los agentes involucrados en el sector eléctrico como por ejemplo:

-   **La generación de electricidad de todas las empresas generadoras peruanas dentro del SEIN.**
-   Una estimación de la demanda de electricidad.
-   Anuncios de Fallas y reparaciones en el SEIN.
-   Información de volumen y capacidad de represas de empresas hidroeléctricas.

La información más relevante para el análisis de la economía, en el día a día, es la **generación de electricidad**. Es posible seleccionar el rango de fecha y consultar en la página web, así como descargar los datos en un excel. La página web tiene el ejecutado medido cada 30 minutos, así como la proyección del resto de horas del día actual. Si seleccionamos una fecha anterior a el día actual, solo encontraremos datos ejecutados.

<div class="figure" style="text-align: center">
<img src="images/COESIII.png" alt="Consultar generacion" width="700px" />
<p class="caption">Figure 2: Consultar generacion</p>
</div>

La información está separada según empresa generadora, así como insumo (hidroeléctrica, gas, etc.).

## **Operación**

Dentro de las opciones disponibles en el menú superior de la página web, encontramos diversas opciones, entre entre ellas las opciones de la operación del COES.

![](images/coesIV-01.png "Operación del COES")

Dentro de este apartado, podemos acceder a diversa información de las operaciones del COES, de las cuales hablaremos solo de las más importantes:

### Base de datos

Dentro de Base de datos, se puede acceder a diversa información de forma automatizada, antes de que sea transcrita en comunicados. De ellas, la opción más relevante para nosotros es los **Medidores de Generación**.

-   Medidores de Generación: Contiene la información de la **generación eléctrica mensual** en el país según el rango de fecha que seleccionemos. Lo más relevante es el **Total de Energía (MWh)**. La información del mes anterior es colgada **el tercer día del mes**.

> En este apartado podemos saber la información de energía generada el mes anterior **oficial**, de primera mano y antes de que aparezca en otros medios.

### Programa de operación

El apartado de programa de operación contiene la proyección de la demanda de energía futura (y por consiguiente la planificación futura de la generación de electricidad). La proyección es más fiable según menos distante sea el futuro de la fecha. Por ejemplo, la **proyección diaria** es bastante confiable. Sin embargo, la **proyección semanal** y la de **mediano plazo** lo son menos.

> Esta información no es muy relevante en nuestro trabajo del día a día, y no es necesario dominarla, sin embargo, puede ser útil conocerla para algunos pedidos especiales.

La demanda de electricidad se puede separar matemáticamente en dos partes: una tendencia casi invariable, y una parte variable que fluctúa según el ciclo económico. Se suele considerar que el consumo de clientes libres (Industrias, minas, etc) es la parte variable, y que el consumo de clientes regulados (hogares) es la tendencia invariable. Para el cálculo de la proyección de **mediano plazo** se calcula la demanda de clientes libres así como regulados. La **Demanda Vegetativa** es el nombre al que se le suele dar a la parte tendencial de la demanda eléctrica.

Para la proyección de la demanda, el COES obtiene la demanda vegetativa utilizando un modelo **ARIMA**, y obtiene la parte variable haciendo una encuesta a todos los usuarios libres. Con esto logra hacer la proyección de mediano plazo.

Para visualizar esa proyección, hacemos click en el **Programa Mediano Plazo Operación**, podemos elegir la fecha, y dentro del apartado **2_InformeS**, descargar el archivo PMPO\_"Fecha".zip. Dentro del zip, solo abría que descomprimir el otro zip **Demanda\_"Fecha".zip**, y en el, abrir el excel **Proyección Demanda MP_Arima "Fecha".xlsx**. Dentro podremos ver la proyección. Sin embargo, hay que considerar que la parte de clientes libres solo es obtenida con una encuesta, la cual se hace anualmente, por ende, la proyección no es muy fiable, pero es útil para organizar las inversiones dentro del sector eléctrico.

### Intercambios Internacionales

El apartado de intercambios internacionales contiene información de la importación y exportación de electricidad. El apartado más relevante dentro de las opciones es el de **Registro de contadores de energía**. La información relevante es la importación/exportación de MWh.

La electricidad se traslada en cargas, y las cargas pueden ser positivas o negativas según la dirección, es decir, según la demanda provenga de un lado o del otro. De esta manera, se puede medir el signo de la carga en las sub-estaciones localizada en la frontera.

> El intercambio internacional de electricidad más relevante que tiene el Perú es con el vecino país de Ecuador, y corresponde con las condiciones energéticas del norte del país (demanda o exceso de energía), usualmente relacionadas a su actividad económica.

### Diagrama Unifilar

Finalmente, lo último más relevante dentro del apartado de operaciones es el *diagrama unifilar*. El diagrama unifilar es un mapa (en PDF) que contiene el nombre y ubicación de cada punto de medición de electricidad dentro del SEIN.

El mapa nos permite observar que hay lineas de transmisión de electricidad, que se subdividen en otras lineas que alimentan a sectores más pequeños. De esta forma, si poseemos información más desmembrada de una demanda focalizada regionalmente (**Post Operación - Demanda de los Agentes - Distribuidoras**), podremos saber con certeza si un punto de medición incorpora la medición de otro punto (es decir, si es la madre de otra linea) evitando sobrestimar la demanda al agrupar toda la información.

## **Post-Operación**

Dentro de las opciones disponibles en el menú superior de la página web, encontramos diversas opciones, entre entre ellas las opciones de la post-operación del COES. Es aquella información procesada después tras pasar por el área de **Operación**. Nos permite acceder a información más desmembrada y procesada de la demanda nacional de electricidad.

<div class="figure" style="text-align: center">
<img src="images/COESV.png" alt="Post Operacion" width="700px" />
<p class="caption">Figure 3: Post Operacion</p>
</div>

### **IEOD**

La información más importante con la que trabajamos, es la que viene en el **Informe de Evaluación de la Operación Diaria** (IEOD). Este informe contiene toda la información desmembrada de la operación del COES realizada en un día en particular.

Al acceder al apartado, podemos elegir el día de interés, y descargar el excel más relevante para nosotros: **Anexo1_Resumen\_*"Fecha"*.xlsx**.

Parte de la información separa regionalmente el país en Norte, Centro y sur, según al siguiente mapa:

<div class="figure" style="text-align: center">
<img src="images/region.jpeg" alt="Diagrama unifilar" width="700px" />
<p class="caption">Figure 4: Diagrama unifilar</p>
</div>

En donde el centro, es la región obtenida exceptuando el norte y sur. Iquitos no forma parte del SEIN, y se le considera un sistema independiente.

Dentro de el excel IEOD encontramos información bastante útil en sus distintas hojas, de las cuales solo hablaré de las más relevantes:

-   **Demanda_UL**: Muestra la demanda en potencia de Grandes Usuarios Libres (a diferencia de los usuarios libres \[\>2'500KW\], los grandes usuarios libres son aquellos que demanda aún más electricidad \[\>10'000KW\]). Las empresas están separadas según ubicación en el norte, centro o sur. Como la información está en potencia, y suministrada cada 30 minutos, para obtener la demanda del día en GWh, la información se debe sumar, multiplicar por 1000, y dividirse entre 2 (para que la unidad sea 1 hora).

> Es con esta información que podemos encontrar la demanda inferida de los sectores **mineros y manufactureros**. Las empresas no están obligadas penalmente a ingresar información (aunque si hay penalidades monetarias), por lo que la información puede tener vacíos en forma de una demanda de 0. El investigador debe decidir a su criterio como imputar la información faltante.

-   **Demanda_Areas**: Muestra la demanda total, en potencia, en el país. Se muestra separada en Áreas y en Sub-Áreas, en donde la información por Áreas (Norte, Centro y Sur) es la más confiable. Para obtener la información del día, se suman los datos contados cada 30 minutos, y luego se divide en 2. El total corresponde a la información de la energía observada por empresas pertenecientes al COES, por lo que es menor a el total que se mediría en el SEIN (Indicadores del sector energético peruano).

Estas dos hojas son las más relevantes, sin embargo, el excel también muestra información de la generación por recurso (Hidroeléctrica, gas natural, etc.) que puede ser útil según la discreción del investigador.

### Informes - Evaluación

Muestra los informes redactados por el COES para el público. El más relevante es el **Informe Mensual** el cual muestra el dato oficial de la generación y variación porcentual de determinado mes. *El dato mensual no es igual a la suma de la información recopilada diariamente, debido a errores de medición*.

Se publica el 15 de cada mes, sin embargo, la información oficial de la generación mensual se puede observar desde la sección Operación -\> Base de datos, con anterioridad.

### Demanda de Agentes

Muestra la demanda de dos agentes del COES: Usuarios Libres y empresa distribuidoras:

-   **Usuarios Libres**: Demanda de algunos de los usuarios libres pertenecientes al COES. Cada mes algunos usuarios libres incorporan voluntariamente la información su demanda diaria al COES, y a la vez algunos declinan de hacerlo, por lo que **esta información es variable**. El beneficio en comparación al IEOD, es que muestra información de más empresas, y sub-dividido según cada punto de medición de la empresa (cada fábrica).

-   **Distribuidoras**: Muestra la demanda eléctrica en la región asignada a cada empresa distribuidora. Un punto de medición puede incorporar la medición de otro punto de medición, por eso es importante revisar el *Diagrama Unifilar* para poder estar seguro de que la información es coherente. La información más relevante en este apartado, es de aquellos puntos de medición que se encuentren en puntos superiores (por ejemplo, en subestaciones en la capital de la región, entre otras). Para hallarlos también es conveniente revisar el diagrama unifilar. Es información algo delicada de procesar y relativamente reciente, por lo que hice un análisis [aquí](https://rpubs.com/luisjo819/Distribuidores).

> Las empresas distribuidoras suelen ser empresas estatales y poco eficientes, por lo que **la información es variable y poco confiable**. Esta información aún se está implementando y no está disponible en todos los distritos, sin embargo, el COES trabaja para que en el futuro cada empresa distribuidora reporte automáticamente la información de su demanda.

## Integrantes

Finalmente, otra de las opciones en el menú superior es el de Integrantes. Al hacer click en **"Listado de Integrantes"** podemos ver los miembros del COES, ya sean Generadoras, Distribuidoras y Usuarios Libres.

#### Finalmente, el COES responde cualquier consulta que tengamos. Esto es útil por ejemplo, cuando sospechamos que algún dato es erróneo. Solo hay que hacer click en el botón azul ubicado en la parte superior, el cual dice "Contáctenos" al pasar el muse encima.

# OSINERMING

OSINERMING es la entidad encargada de fiscalizar a los integrantes del COES. Una aplicación interesante es el mapa del SEIN, el cual contiene la ubicación geográfica de los componentes del SEIN: <https://www.osinergmin.gob.pe/newweb/uploads/Publico/MapaSEIN/>.

Adicionalmente, también se puede acceder a la información de **la demanda de todos los usuarios libres en el país** en el siguiente enlace, dentro de Publicaciones -\> Informes Mensuales -\> Mercado libre de electricidad:

<https://www.osinergmin.gob.pe/seccion/institucional/regulacion-tarifaria/publicaciones/regulacion-tarifaria>

La información sin embargo, está disponible con un retraso de 2 meses, por lo que llega algo tarde si deseamos información reciente.

# MINISTERIO DE ENERGÍA Y MINAS

Finalmente, el ministerio de energía y minas también hace una revisión anual de la electricidad. Sus reportes tienen un retraso de 1 o 2 años, sin embargo, contienen mucha información histórica, como por ejemplo, **la demanda total en el país por actividad industrial**.

La información se puede descargar de: <http://www.minem.gob.pe/_estadisticaSector.php?idSector=6>
