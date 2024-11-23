---
title: Electricity for Economists I
author: Luis Jose Zapata Bobadilla
date: '2021-03-14'
slug: 'electricidad-para-economistas-1'
categories:
  - Electricity
tags: [Electricity]
subtitle: 'Basic concepts of electricity'
summary: 'An introduction to the basic concepts of the electricity sector in Peru'
authors: []
lastmod: '2021-03-14T14:20:40-05:00'
featured: yes
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---



Electricity demand is an excellent predictor of GDP. This information has a lag of only one day, which can help us quickly predict whether current GDP is growing or declining. However, it is essential to understand some basic concepts before using it.

## Technical Aspects

Electric energy is defined as the movement of electrons through a conductor over a given period. The physical force or pressure that induces this movement is called voltage, measured in volts (V). The rate at which the electrons flow is called current intensity, measured in amperes (I).

Electric current (I) is produced by the movement of electrons caused by a voltage difference (V).

The **electric power**, measured in watts (W), quantifies the amount of energy consumed, produced, or transferred per unit of time. **Electric energy**, on the other hand, represents the total amount of energy consumed, produced, or transferred during a specific period and is measured in watt-hours (Wh).

For example, if the power of a lightbulb is 100 W and it remains on for two hours, the electric energy consumed would be 200 Wh.



<div class="figure" style="text-align: center">
<img src="images/electricidad.png" alt="Electricity" width="700px" />
<p class="caption"><span id="fig:unnamed-chunk-1"></span>Figure 1: Electricity</p>
</div>


<div class="figure" style="text-align: center">
<img src="images/watt.png" alt="Energy vs Power" width="630px" />
<p class="caption"><span id="fig:unnamed-chunk-2"></span>Figure 2: Energy vs Power</p>
</div>


It’s common to find these units with the following prefixes. We will frequently use the *giga* unit when conducting analyses:

| Prefix  | Symbol | `\(10^n\)` | Equivalent    |
|---------|--------|--------|---------------|
| kilo    | K      | `\(10^3\)` | 1,000         |
| mega    | M      | `\(10^6\)` | 1,000,000     |
| giga    | G      | `\(10^9\)` | 1,000,000,000 |

### Demand

Electricity's utility doesn’t derive from its direct consumption but from its ability to power equipment, making it a derived demand from other economic agents' needs (industries, households, and governments).

In Peru, there are two types of users in the national electricity system:

![Clientes COES](images/Demanda.png)
- **Regulated Users:** These are agents with a demand of less than 200 KW, typically residential users and small businesses. Their prices are regulated by the government entity OSINERGMIN.

- **Free Users:** These are agents with a demand of over 200 KW, usually large factories and mines that can negotiate electricity prices. Users with a demand between 200 KW and 2500 KW can choose to be either regulated or free.

### Generation, Transmission, and Distribution

Electricity cannot be stored on a large scale at viable costs, necessitating its simultaneous production and consumption. This requires an infrastructure capable of **generation**, **transportation**, and **distribution** in real time.

<div class="figure">
<img src="images/gtd.png" alt="Generation and Distribution" width="680px" />
<p class="caption"><span id="fig:unnamed-chunk-3"></span>Figure 3: Generation and Distribution</p>
</div>

### Generation

This first step transforms other energy forms (coal, gas, water flow) into electric energy. Generation relies on diverse technologies such as hydroelectric, thermal, solar, and wind plants, depending on the market size and energy resource availability.

In Peru, hydroelectric energy has historically dominated, but the development of the **Camisea** natural gas field has expanded gas-based electricity generation. <center>

<div class="figure">
<img src="images/generacion.png" alt="Generacion" width="650px" />
<p class="caption"><span id="fig:unnamed-chunk-4"></span>Figure 4: Generacion</p>
</div>

</center>


### Transmission

This step transports electricity from generation centers to consumption areas via high-capacity transmission lines. Due to economies of scale, this segment exhibits natural monopoly characteristics.


<center>

<div class="figure">
<img src="images/cable.png" alt="Cables de Transmision" width="370px" />
<p class="caption"><span id="fig:unnamed-chunk-5"></span>Figure 5: Cables de Transmision</p>
</div>

</center>

In Peru, most transmission lines are 138 kV, 220 kV, and 500 kV. Higher capacity lines allow for greater energy transport, which is crucial for supporting industrial growth.

### Distribution

Distribution involves delivering electricity to end-users through medium- and low-voltage networks. In Peru, this segment is often managed by state companies, except in large cities like Lima, where private companies like Luz del Sur operate.


### Key Institutions

- **Ministry of Energy and Mines:** Responsible for legislating energy-related matters.
- **OSINERGMIN:** Supervises compliance and sets regulated user prices.
- **COES (Committee for Economic Operation of the System):** Coordinates the electricity system, manages the short-term market, and plans long-term energy needs.


<div class="figure">
<img src="images/coes.png" alt="Modelo del Mercado Peruano" width="600px" />
<p class="caption"><span id="fig:unnamed-chunk-6"></span>Figure 6: Modelo del Mercado Peruano</p>
</div>

</center>

The COES exists to maintain the proper balance between energy demand and supply, managing the agents involved (Generators-Distributors) through the electricity market.

The decisions of the COES are mandatory for its members (generation, transmission, and distribution companies). Electricity generation is dispatched in order of the marginal cost of production. As a result, the first energy to be dispatched comes from the most efficient technologies (solar, wind, etc.).

<center>

<div class="figure">
<img src="images/coes2.png" alt="COES Despacho" width="300px" />
<p class="caption"><span id="fig:unnamed-chunk-7"></span>Figure 7: COES Despacho</p>
</div>

</center>

