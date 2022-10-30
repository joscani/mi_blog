---
title: Api y docker con R. parte 2
author: ''
date: '2022-10-12'
categories:
  - docker
  - R
tags:
  - api
  - docker
  - R
slug: api-y-docker-con-r-parte-2
---

En la entrada de [api y docker con R parte I](https://muestrear-no-es-pecado.netlify.app/2022/10/12/api-y-docker-con-r-parte-1/) veíamos que es muy fácil construir una api y dockerizarla para tener un modelo bayesiano en producción. Pero hay un pequeño incoveniente, el docker que hemos creado se base en [rocker/verse](https://rocker-project.org/images/) que se basan en ubuntu. Y ubuntu ocupa mucho. Pero gracias a gente como Gabor Csardi (autor entre otras librerías de `igraph`), tenemos [r-hub/minimal](https://github.com/r-hub/r-minimal), que permiten tener una imagen de docker con R basadas en alpine, de hecho una imagen de docker con R y dplyr son unos 50 mb. 


Lo primero de todo es ver cuánto ocupa el docker creado en el primer post. 

```bash
╰─ $ ▶ docker image ls mi_modelo_brms
REPOSITORY       TAG       IMAGE ID       CREATED       SIZE
mi_modelo_brms   latest    9e641ec2c150   3 weeks ago   3.42GB


``` 

Pues son unos cuántos gigas, mayoritariamente al estar basado en ubuntu y al que los docker de rocker/verse instalan todo el software de R recomendado, los ficheros de ayuda, las capacidades gráficas, etc.. 

Pero con r-hub/minimal podemos dejar bastante limpio el tema. Leyendo el Readme del repo vemos que han configurado una utilidad a la que llaman `installr` que permite instalar librerías del sistema o de R, instalando los compiladores de C, fortran etc que haga falta y eliminarlos una vez están compiladas la librerías. 

Sin más, cambiamos el Dockerfile del otro día por este otro . 


```bash

# Docker file para modelo brms

FROM rhub/r-minimal:4.2.1


RUN installr -d -a linux-headers ps

RUN installr -d -a "curl-dev linux-headers gfortran libcurl libxml2 libsodium-dev libsodium automake autoconf"

RUN installr -d Matrix MASS mgcv future codetools brms plumber tidybayes

## Copio el modelo y el fichero de la api
COPY brms_model.rds /opt/ml/brms_model.rds
COPY plumber.R /opt/ml/plumber.R

# exponemos el puerto
EXPOSE 8081
ENTRYPOINT ["R", "-e", "pr <- plumber::plumb('/opt/ml/plumber.R'); pr$run(host = '0.0.0.0', port = 8081)"]

```


Y haciendo `docker build -t mi_modelo_brms_rminimal .` pasado un rato puesto que ha de compilar las librerías tenemos nuestra api dockerizada con la misma funcionalidad que el otro día. 

Y con un tamaño mucho más contenido 


```bash
  ╰─ $ ▶ docker image ls
REPOSITORY                    TAG                    IMAGE ID       CREATED         SIZE
mi_modelo_brms_rminimal       latest                 8d791d2ebc74   2 hours ago     665MB

```
que se va a unos 655 mb, de los cuales unos 300 MB se deben a `stan` y `rstan`. Pero vamos, no está mal, pasar de 3.4 Gb a 665MB. 
