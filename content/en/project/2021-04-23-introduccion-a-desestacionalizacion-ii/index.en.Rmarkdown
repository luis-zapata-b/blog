---
title: Desestacionalización (II)
author: Luis Jose Zapata Bobadilla
date: '2021-04-23'
slug: introduccion-a-desestacionalizacion-ii
categories:
  - Desestacionalizacion
tags:
  - Desestacionalizacion
subtitle: 'Guía práctica para desestacionalizar'
summary: 'En esta segunda parte de desestacionalización, doy indicaciones prácticas para realizar una desestacionalización'
authors: ["Luis Jose Zapata"]
lastmod: '2021-04-23T19:59:57-05:00'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---

En esta publicación veremos como podemos desestacionalizar de forma práctica. Para esto, utilizaremos el software libre JDemetra+ que puede ser descargado [aquí](https://github.com/jdemetra/jdemetra-app/releases/tag/v2.2.3). El software necesita que tengas instalado Java en tu computadora, el cual puedes descargar de [aquí](https://www.java.com/es/download/ie_manual.jsp).

## Comenzando con JDemetra+

Primero hay que instalar JDemetra+ y Java. Luego de instalarlo, necesitamos preparar la información a procesar. JDemetra+ lee la información en distintos formatos, siendo excel el más popular. En orden de que JDemetra+ pueda leer tus datos, *la primera columna tiene que definir la fecha, y las siguientes las variables a analizar.*

Ahora, abrimos JDemetra+ (el ícono que dice NbDemetra) y ubicamos la pestama "**Providers**" en donde se ubican las fuentes de datos para el software.

![](imagen1.PNG "Providers")

Si tenemos un excel como base de datos, hacemos click derecho en "**Spreadsheets**" y luego abrimos el excel que deseamos analizar. Tras hacerlo, debajo de Spreadsheets se abrirá el excel y las hojas con nuestros datos. Si hacemos doble click en uno de los datos, podremos observar la serie y verificar que es la correcta.

![](imagen2.png "Verificando datos")

## Desestacionalizando con JDemetra+

En orden de iniciar un proceso de desestacionalizción, hacemos click en la opción de "**Statistical Methods**", luego en "**Seasonal Adjustmen**" y posteriormente "**Multi Procesing**".

![](imagen3.png "New Process")

Luego de hacerlo, podremos arrastrar la variable a analizar al espacio creado. Luego, podemos especificar si queremos usar el algoritmo Tramo Seats o X13. Finalmente, en las opciones de especificación podremos delimitar que intervalo de tiempo considerar (también podríamos definirlo en el excel antes de subirlo al software).

![](imagen4.png "Desestacionalizando")

Algo importante es que, si deseas que la especificación sea Multiplicativa (es decir, obtener **factores** de desestacionalización, los cuales se dividen a la serie original) hay que cambiar la especificación. En especificación, eligiriamos dentro de **Transformation**, la opción **Function** y eligimos **Log.**

Con esto definido, procedemos a hacer click en el botón de flecha verde y ya habremos desestacionalizado nuestra serie. Voila!

![](imagen5.png "Desestacionalización")

Si deseamos obtener los factores de desestacionalización (previo haber elegido Log en la especificación), debemos ir a la pestaña **Main Results** de nuestros resultados, y hacer click en **Table**. Luego elegir la columna **Seasonal**, la cual contiene los **factores de desestacionalización**.

Con los factores de desestacionalización, uno puede desestacionalizar una serie de tiempo al dividirla entre los factores.

En orden de especificar aún más el modelo, no te olvides de revisar las guías de JDemetra+:

[manual_jdemetra.pdf (ine.es)](https://www.ine.es/clasifi/manual_jdemetra.pdf)

<https://ec.europa.eu/eurostat/cros/system/files/jdemetra_quick_start_version_2.2.pdf>
