---
title: Desestacionalización (I)
author: Luis Jose Zapata Bobadilla
date: '2021-04-23'
slug: introduccion-a-la-desestacionalizacion
categories: [Desestacionalizacion]
tags: [Desestacionalizacion]
subtitle: 'Introducción a la desestacionalización'
summary: 'En este post veré una introducción a los temas más básicos de la desestacionalización'
authors: ["Luis José Zapata Bobadilla"]
lastmod: '2021-04-23T15:09:40-05:00'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---

Es importante considerar el fenómeno de la estacionalidad antes de realizar una proyección a una serie de tiempo. Las series de tiempo no suelen crecer o decrecer de forma lineal, sino que suelen tener periodos de altibajos que se repiten de forma cíclica cada año, reflejando algún evento o fenómeno estacional (festividades, estaciones climáticas, etc.). De allí la relevancia de entender la estacionalidad y como podemos tomarla en cuenta.

Desestacionalizar una serie, implica restarle el ciclo estacional a una serie de tiempo. Es importante desestacionalizar para facilitar la interpretación de una serie de tiempo.

## Estacionalidad

La estacionalidad se define como la repetición de determinados fenómenos cada cierto período, normalmente igual o menor a un año. Ejemplos de estacionalidad pueden ser: las estaciones que se repiten cada año, festividades como la navidad, periodos culturales como la semana santa, las fechas límites anuales de declaración de impuestos, etc.

-   **Estacionalidad**: fluctuaciones registradas durante el  año que parecen repetirse de forma
    más o menos regular en un intervalo de 1 año. Pueden ocasionarse por variaciones del clima (estaciones), hábitos sociales/religiosos/políticos o indirectos (por ejemplo, el año nuevo chino).

-   **Efectos de calendario:** cualquier efecto económico aparentemente relacionado con el calendario (Por ejemplo, un domingo extra en un mes concreto puede afectar la producción). Los efectos de calendario incluyen: Número de **días laborables** en un período determinado, Festividades o Eventos en días laborables (Por ejemplo, una copa de football), efecto de los años bisiestos, festas móviles (Pascua, Ramadán, etc.), etc.

#### Componentes de una serie de tiempo

Una serie de tiempo es una secuencia de observaciones secuenciales en un intervalo de tiempo. Este intervalo de tiempo puede ser diario, semanal, mensual, trimestral, anual, etc. Toda serie de tiempo está divida en cuatro componentes:

-   **Ciclo/Tendencia**: la evolución de largo plazo de la serie. La tendencia vendría a ser el comportamiento a largo plazo de la serie, mientras que el ciclo, la fluctuación a largo plazo similar a la teoría de ciclos económicos.

-   **Estacional**: la fluctuación regular observada a lo largo de 1 año, la cual se repite en intervalos definidos de tiempo.

-   **Irregular:** fluctuaciones residuales o
    aleatorias, definida por fenómenos inesperados o irregulares.

La suma de estos componentes nos da como resultado la serie de tiempo inicial. Adicionalmente, hay dos formas teóricas de descomponer y sumar los componentes: **Aditiva** y **Multiplicativa**.

-   Aditiva: Se considera que los componentes se **suman** para obtener la serie final.

-   Multiplicativa: Se considera que los componentes se **multiplican** para obtener la serie final.

Para desestacionalizar la serie se **resta el componente estacional** de la serie original. De esta manera, obtendríamos la **serie desestacionalizada**.

![](imagen1.png "Componentes de desestacionalización")

No existe justificación teórica para preferir el método aditivo o el multiplicativo. Sin embargo, el método multiplicativo no puede usarse con una serie que tiene el valor 0 entre sus observaciones. Adicionalmente, el componente multiplicativo estacional a menudo es llamado **"Factor de desestacionalización"**.

Para realizar la descomposición de forma pirática, existen dos formas populares de acercamiento: los algoritmos Tramo/Seats y X13.

## Algoritmos de desestacionalización

Para desestacionalizar una serie, primera modelamos la serie a través de un modelo económico (usualmente un modelo ARIMA). A raíz de este modelo, procedemos a separar el modelo en los distintos componentes teóricos de los cuales mencionamos anteriormente. Los dos algoritmos más populares son los siguientes:

-   **Tramo Seats**: Algoritmo que modela la serie de tiempo utilizando un modelo ARIMA. Luego, extrae los componentes utilizando modelo.

-   **X13**: Algoritmo que también modela inicialmente una serie de tiempo con un modelo ARIMA. Luego, extrae los componentes a través de filtros de medias móviles.}

Ambos algoritmos utilizan variables dummies durante el modelamiento para controlar por días calendario, feriados, outliers, etc. Estos y distintos parámetros pueden modificarse para el correcto modelamiento y desestacionalización.

## Software para desestacionalizar

El software de desestacionalización más popular en Europa es JDemetra+. Este software es el método recomendado por EUROSTAT (Unión Europea), siendo desarrollado por el Banco Central de Alemania.

El INE de España realizó una guía para desestacionalizar en JDemetra+ en español: [manual_jdemetra.pdf (ine.es)](https://www.ine.es/clasifi/manual_jdemetra.pdf)

Adicionalmente, EUROSTAT ofrece varias guías de desestacionalización en internet: <https://ec.europa.eu/eurostat/cros/system/files/jdemetra_quick_start_version_2.2.pdf>
