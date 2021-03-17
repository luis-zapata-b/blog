---
title: Electricidad para Economistas I
author: Luis José Zapata Bobadilla
date: '2021-03-14'
slug: 'electricidad-para-economistas-1'
categories:
  - Electricidad
tags: [Electricidad]
subtitle: 'Conceptos básicos de la electricidad'
summary: 'Una introducción a los conceptos básicos del sector eléctrico en el Perú'
authors: []
lastmod: '2021-03-14T14:20:40-05:00'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---



La demanda de electricidad es un excelente predictor de el PBI. Esta información tiene un rezago de solo 1 día, y puede ayudarnos a predecir rápidamente si el PBI actual está creciendo o disminuyendo. Sin embargo, es importante entender algunos conceptos básicos antes de usarlo.

## Aspectos Técnicos

La energía eléctrica está definida como el movimiento de electrones que se trasladan por un conductor eléctrico durante un determinado periodo. La fuerza física o presión que induce este movimiento se denomina voltaje y su unidad de medida es el voltio (V), mientras que la tasa a la cual fluyen los electrones se llama intensidad de corriente, cuya unidad de medida es el amperio (I).

La corriente eléctrica (I) se produce por el movimiento de electrones causado por una diferencia de tensión (V).

<div class="figure" style="text-align: center">
<img src="images/electricidad.png" alt="Electricidad" width="700px" />
<p class="caption">Figure 1: Electricidad</p>
</div>

La **potencia eléctrica**, cuya unidad de medida es el watt (W) , cuantifica la cantidad de energía que se consume, produce o traslada en cada unidad de tiempo; mientras que la **energía eléctrica** representa la cantidad total de energía que se consumió, produjo o trasladó durante un determinado periodo, por lo que su unidad de medida suele ser el watt-hora (Wh).

Por ejemplo, si la potencia de una lámpara eléctrica es 100 W y esta permanece encendida por dos horas, entonces, la energía eléctrica consumida sería 200 Wh.

<div class="figure" style="text-align: center">
<img src="images/watt.png" alt="Energia vs Potencia" width="630px" />
<p class="caption">Figure 2: Energia vs Potencia</p>
</div>

Es normal encontrar las unidades con los siguientes prefijos, de los cuales emplearemos con frecuencia las unidades en *giga* cuando realicemos análisis:

| Prefijo | Simbolo | `\(10^n\)` | Equivalencia  |
|:--------|:--------|:-------|:--------------|
| kilo    | K       | `\(10^3\)` | 1 000         |
| mega    | M       | `\(10^6\)` | 1 000 000     |
| giga    | G       | `\(10^9\)` | 1 000 000 000 |

### Demanda

Una característica de la electricidad es que su utilidad no se deriva de su consumo directo, sino que proporciona una fuente de energía que permite la funcionalidad de equipos eléctricos, convirtiéndose en una demanda derivada de otras necesidades provenientes de los agentes económicos (industrias, hogares y gobierno).

Según la legislación peruana, existen dos tipos de usuarios del sistema eléctrico nacional: Los usuarios regulados y los usuarios libres.

![Clientes COES](images/Demanda.png)

-   **Usuarios Regulados**: Son aquellos agentes cuya demanda es inferior a 200KW. Usualmente constituido por residenciales, así como pequeños negocios y fábricas. El precio que pagan viene determinado por la entidad reguladora del estado (OSINERMING).

-   **Usuarios Libres**: Son aquellos agentes cuya demanda es superior a 200KW. Usualmente constituido por grandes fábricas y minas que demandan una grán cantidad de energía en sus operaciones. Pueden negociar el precio que pagan por la electricidad. Aquellos cuya demanda oscila entre los 200KW y los 2500 KW pueden elegir si ser usuarios libres o regulados.

Fijese que hablamos de KW y no KWH, es decir potencia y no energía, debido a que la condición se refiere la demanda instantanea (en una unidad de tiempo).

### Generación, Transmisión y Distribución

Otra de las particularidades de la energía eléctrica está vinculada a la imposibilidad de almacenarla en gran escala a costos viables. Esto genera que su consumo deba ser producido de forma simultánea, con lo cual se requerirá de una infraestructura capáz de **generarla**, **transportarla** y **distribuirla** en tiempo real.

<div class="figure">
<img src="images/gtd.png" alt="Generacion y Distribucion" width="680px" />
<p class="caption">Figure 3: Generacion y Distribucion</p>
</div>

### Generación

Es la primera actividad en la cadena. Su función es transformar otro tipo de energía (carbón, gas, caida de agua, etc) en energía eléctrica.

Una particularidad en este segmento es que el grán tamaño de la demanda agregada de electricidad (una ciudad o región) genera que las economías de escala se agoten rápidamente, promoviendo la la competencia.

Una industria diversificada suele operar con distintas escalas y tipos de tecnologías de producción: centrales hidroeléctricas, térmicas, solares, eólicas y nucleares, entre otras. La diversificación dependerá del tamaño del mercado, así como de la disponibilidad de las fuentes de energía.<center>

<div class="figure">
<img src="images/generacion.png" alt="Generacion" width="650px" />
<p class="caption">Figure 4: Generacion</p>
</div>

</center>

Debido a la necesidad de mantener un equilibrio constante entre la oferta y la demanda de electricidad en tiempo real, es necesario contar con una flexibilidad de las centrales eléctricas en su generación. Las distintas tecnologías tienen varias características para ajustarse a cambios en la demanda.

Las tecnologías tradicionales (térmica e hidroeléctrica) pueden variar su producción según sus reservas (un embalse de un rio, o un tanque de gas o petroleo). En el caso de las generadoras renovables (solar, eólica, entre otras), la máxima producción eléctrica está sujeta a las condiciones climatológicas.

En el caso de Perú, históricamente el país siempre tenía como principal fuente generadora de electricidad la energía hidráulica. Sin embargo, el desarrollo de **Camisea** ha permitido un crecimiento importante de la generación basada en gas natural.

### Transmisión

La transmisión permite transportar la electricidad desde los centros de generación hacia las zonas de consumo final. Está compuesto por líneas de transmisión, subestaciones de transformación, torres de transmisión, entre otras instalaciones.

Este segmento presenta características de monopolio natural debido a importantes economías de escala (por ejemplo, una linea de transmisión puede trasladar por si sola energía a una ciudad). Los costos de transportar energía disminuyen a medida que incremente la capacidad de carga de la red.

La capacidad de carga está en función del grosor y calidad del cable de transmisión. En el Perú se suelen utilizar cables de 138 kV, 220 Kv y 500 Kv. A mayor capacidad, mayor es el precio del cable por metro.

<center>

<div class="figure">
<img src="images/cable.png" alt="Cables de Transmision" width="370px" />
<p class="caption">Figure 5: Cables de Transmision</p>
</div>

</center>

La capacidad de carga de una red se puede interpretar como el ancho de una autopista. Mientras más ancha sea la autopista, más carros podrán llegar a su destino. Del mismo modo, mientras mayor sea la capacidad de carga, mayor es la cantidad de energía que se podrá transportar a su punto de destino. Así, si existe capacidad no utilizada, resultará más eficiente incrementar la carga sobre el sistema de transmisión existente antes que construir uno nuevo.

Si la capacidad de carga de las lineas de transmisión son bajas (por ejemplo, la mayoría sean de 138Kv) las ciudades o regiones tendrán un tope de demanda energética (independientemente de la cantidad de centrales generadoras en el país) lo cual puede afectar seriamente la capacidad de inversión o crecimiento de producción de fábricas y minas.

En el Perú, en los últimos años, se ha incrementado la cantidad de lineas de transmisión de 500KV, lo cual permitirá una mayor crecimiento futuro de la minería e industrias.

Finalmente, es importante notar que en el proceso de transmisión se pierde aproximadamente un 8% de la energía transmitida, debido a emisión de calor, defectos en las subestaciones, etc. Es por esto, que la cantidad de energía generada es igual a la energía demandada más las pérdidas de energía.

### Distribución

En el segmento de transmisión se transporta energía eléctrica a altos niveles de tensión y a largas distancias, mientras que en el segmento de distribución se traslada electricidad hacia los consumidores finales mediante redes eléctricas de mediana y baja tensión.

Las empresas distribuidoras también se encargan de la comercialización de la electricidad. Es un monopolio natural, y por lo tanto suelen tener jurisdicción sobre ciudades o regiones extensas.

Usualmente son empresas estatales a excepción de aquellas que se encuentran en grandes ciudades (como Lima, Perú, cuyas empresas distribuidoras son las empresas privadas Luz del Sur y Enel Distribución).

Ofrecen los contratos de clientes libres, bajo el cual el precio esta fijado por la entidad reguladora OSINERMING.

También pueden ofrecer contratos de usuario libre en las ciudades, intercediendo ante las empresas generadoras.

## Agentes Involucrados

#### **Ministerio de Energía y Minas**

Institución encargada de legislar sobre temas relacionados a la energía y minas del páis. No tiene atributos de ejecución o aplicación directa, los cuales recaen más sobre OSINERMING y COES. No interviene en el desempeño diario de los mercados, excepto cuando publica una ley.

#### **OSINERMING**

Institución encargada de supervizar y fiscalizar el cumplimiento de leyes relacionadas al sector de energía. Adicionalmente, se encarga de fijar el precio que se cobra a los usuarios regulados por el consumo eléctrico.

### **COES**

Es una entidad privada, sin fines de lucro, cuyas funciones son las de:

-   Coordinar la operación del sistema eléctrico interconectado nacional.
-   Administrar el mercado de corto plazo.
-   Planificar el desarrollo de la transmisión del SEIN.

El COES tiene por finalidad coordinar la operación de corto, mediano y largo plazo del Sistema Electrico Interconectado Nacional (SEIN) al mínimo costo, preservando la seguridad del sistema y el aprovechamiento de recursos energéticos.<center>

<div class="figure">
<img src="images/coes.png" alt="Modelo del Mercado Peruano" width="600px" />
<p class="caption">Figure 6: Modelo del Mercado Peruano</p>
</div>

</center>

El COES existe por el adecuado equilibrio entre la demanda y la oferta energética, administrando a los agentes involucrados (Generadoras-Distribuidoras) a travéz del mercado de electricidad.

Las decisiones del COES son de caracter obligatorio para sus integrantes (empresas generadoras, transmisoras y distribuidoras). La generación de electricidad es despachada en orden según el costo marginal de producir la energía. Debido a esto, la primera energía en ser despachada es de aquellas tecnologías más eficientes (solar, eólica, etc.)

<center>

<div class="figure">
<img src="images/coes2.png" alt="COES Despacho" width="300px" />
<p class="caption">Figure 7: COES Despacho</p>
</div>

</center>

En resumen, el COES tiene a cargo la parte aplicativa y técnica del mercado eléctrico, por lo que siempre tienen datos actuales del mismo en su página [web](https://www.coes.org.pe/portal/).
