---
title: Codificación de variables categóricas II
author: ''
date: '2019-03-10'
slug: codificacion-de-variables-categoricas-ii
categories:
  - estadística
tags:
  - estadística
  - R
description: ''
topics: []
---


Voy a comentar por encima lo que se viene llamando "codificación por impacto", la idea es codificar una variable categórica predictora usando la información del "target", evidentemente este tipo de codificación sólo sirve cuando tenemos un modelo en mente y dicen que es útil si tenemos variables categóricas con alta cardinalidad.

La idea es muy sencilla, para cada nivel de la variable categórica le asignamos su media de target, por ejemplo, (o la media(u otra medida) menos la media general) 

Básicamente sería

`cat_1_codific= E[y | x = cat_1]`

Otra codificación derivada de la relación entre las categorías de una variable y la variable a explicar es por ejemplo el WOE (Weight of Evidence). 

Y ya que estamos usando la información del target para codificar nuestras variables categóricas, ¿por qué no usamos algo como el el [*partial pooling*](https://muestrear-no-es-pecado.netlify.com/2019/02/03/partial-pooling/). 

En R tenemos el paquete `vtreat` de la gente de [WinVector](http://www.win-vector.com/site/) que implementa las codificaciones por impacto y en este [post](http://www.win-vector.com/blog/2017/09/custom-level-coding-in-vtreat/) cuentan como usar partial pooling utilizando `lme4`
