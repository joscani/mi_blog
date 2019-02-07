---
title: Cosas que quiero probar
author: jlcr
date: '2019-02-07'
slug: cosas-que-quiero-probar
categories:
  - ciencia de datos
  - spark
  - machine learning
tags:
  - producción
  - R
  - spark
  - pyspark
description: ''
topics: []
---


Iba a escribir una cosa chula que hiciera honor al nombre del blog, algo sobre muestreo, postestratificación  y demás, pero he llegado a casa tarde y no tengo ni tiempo ni ganas. 

Así que voy a poner una serie de librerías que tengo pendiente de probar y que creo reducirían la brecha idiomática entre los científicos de datos, los ingenieros y los arquitectos de datos y big data (si es que en tu organización tienes la suerte de que exista este perfil)


* [MLEAP](http://mleap-docs.combust.ml/) Promete poner en producción de manera fácil modelos de spark, sklearn y tensor flow. Parece que funciona bien, habrá que probar.

* [MLflow](https://mlflow.org/) Estos prometen gestionar todo el ciclo de vida del "machine learning", tiene muy buena pinta, y lo han hecho los de databrick, que parecen gente seria y con equipo de desarrolladores bueno.

* [Photon-ml](https://github.com/linkedin/photon-ml#game---generalized-additive-mixed-models) Librería en spark de la gente de Linkedin que permite ajustar modelos mixtos generalizados en spark. Esta hay que probarla si o sí. 

* [Dask-ml](https://dask-ml.readthedocs.io/en/latest/) Computación distribuida con librería Dask de python, tiene muy buena pinta. 

* [Drake](https://ropenscilabs.github.io/drake-manual/hpc.html) High performance computing con R, también tiene muy buena pinta usando las librerías de R [`future`](https://github.com/HenrikBengtsson/future) y [`future.batchtool`](https://github.com/HenrikBengtsson/future.batchtools) que permiten una interfaz unificada para computación distribuida en R. 

Y nada más, si alguno de mis lectores ha probado alguna de estas librerías u otras similares sientáse libre de compartir sus impresiones. 

