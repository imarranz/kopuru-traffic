
# Predicción del tráfico a la entrada de un Polígono Industrial Vasco

![](https://repository-images.githubusercontent.com/748222615/82009552-244b-4329-b981-58fc6a5b5d07)

Este proyecto se creó en respuesta al desafío de modelización lanzado por [Kopuru](https://kopuru.com/), con el objetivo de predecir el tráfico en la entrada de un polígono industrial. [Kopuru](https://kopuru.com/) planteó este [reto](https://kopuru.com/challenge/prediccion-del-trafico-a-la-entrada-del-poligono-industrial-pais-vasco/) para abordar cuestiones relacionadas con la gestión del tráfico y mejorar la eficiencia en un entorno industrial. El propósito de este repositorio es desarrollar modelos de predicción robustos y compartir soluciones relacionadas con el desafío propuesto por [Kopuru](https://kopuru.com/).

¡Gracias a [Kopuru](https://kopuru.com/) por lanzar este emocionante desafío!

**Versión y Actividad**

<p align="left">
  <a href="https://github.com/imarranz/kopuru-traffic/pulls">
    <img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg?longCache=true" alt="Pull Requests">
  </a>
  <a href="LICENSE.md">
    <img src="https://img.shields.io/badge/License-MIT-red.svg?longCache=true" alt="MIT License">
  </a>
   <a href="https://github.com/imarranz/kopuru-traffic"><img src="https://img.shields.io/github/stars/imarranz/kopuru-traffic" alt="Stars"/></a>
  </a>
</p>


![GitHub release (latest by date)](https://img.shields.io/github/v/release/imarranz/kopuru-traffic)
![GitHub Release Date](https://img.shields.io/github/release-date/imarranz/kopuru-traffic)

![GitHub last commit](https://img.shields.io/github/last-commit/imarranz/kopuru-traffic)
![GitHub all releases](https://img.shields.io/github/downloads/imarranz/kopuru-traffic/total)<br>

**Análisis**

![GitHub top language](https://img.shields.io/github/languages/top/imarranz/kopuru-traffic)
![GitHub language count](https://img.shields.io/github/languages/count/imarranz/kopuru-traffic)<br>

**Redes Sociales**

<p align="left">
  <a href="https://twitter.com/imarranz" target="_blank">
    <img src="https://img.shields.io/twitter/follow/imarranz.svg?logo=twitter">
  </a>
</p>

La congestión del tráfico y los problemas relacionados son una preocupación común en las zonas de acceso a Polígonos Industriales, a los que miles de trabajadores acceden a diario. Comprender los patrones de tráfico y analizar sus datos puede proporcionar información valiosa para la planificación del transporte, el desarrollo de infraestructura y la gestión de estos atascos, que suponen un contratiempo para quienes se desplazan.

## Descripción

La entrada al Polígono Industrial de este [reto](https://kopuru.com/challenge/prediccion-del-trafico-a-la-entrada-del-poligono-industrial-pais-vasco/) tiene un tráfico elevado. Miles de vehículos se desplazan a diario a esa zona de la ciudad para realizar su trabajo. Esto se agrava a determinadas horas del día, donde el flujo de vehículos es más alto. Si a esto le sumamos que se trata de un entorno industrial, donde se mueven grandes cantidades de camiones de transporte, y que debido a la turnicidad, la afluencia de vehículos es elevada en muchos momentos del día, el estudio de estos momentos pico del día, resulta complejo.

La ciudad quiere establecer medidas que permitan favorecer el tráfico, evitar los accidentes y los atascos, además de reducir la contaminación. Para ello, se ha instalado a la entrada del polígono un sistema de visión que ha capturado durante un mes (31 días exactamente) la tipología de vehículos que han accedido al polígono. Estos datos se tomaron en franjas de 15 minutos. Con esta información capturada, la ciudad ha estudiado si la afluencia de vehículos es muy elevada, y han clasificado el tráfico como muy alto, alto, normal o bajo.

Pero este estudio no termina aquí: con esta información la ciudad quiere establecer un modelo predictivo a través del cual, puedan predecir para determinados momentos del día y la semana, si el tráfico en el polígono será elevado, y establecer políticas que mejoren los accesos y el tránsito en estas zonas. Y es aquí donde comienza tu labor: mediante los datos de train que encontrarás en el apartado de “Datos”, deberás:

  1. Analizar la información facilitada en el apartado de “Datos” y estudiar la calidad de la información recopilada por el sistema de visión a la entrada del polígono.

  2. A través de los datos de entrenamiento (train) desarrollar un modelo de clasificación que, en función de las variables de estudio que consideres más importantes, determine si el tráfico es muy denso, alto, normal o bajo (de acuerdo a la clasificación que encontrarás en el apartado “Datos”)

  3. Una vez tengas el modelo entrenado, con los datos de test, podrás aplicar en ellos la lógica de tu modelo, y obtener la clasificación para esos datos no etiquetados. Ese resultado será el que deberás subir a Kopuru, para que podamos evaluar tu porcentaje de acierto.

  4. ¿Quieres deslumbrar? Si además crees que de tu análisis puede obtenerse más información, adjunta un PDF donde nos cuentes: por qué tu solución es la mejor, y que ideas se te ocurren para aplicar soluciones que mejoren el tráfico, basado en las conclusiones que has obtenido al entrenar tu modelo. Nos encantará ver soluciones que además, aporten un valor a problemas reales.

## Explicación de Datos

En este reto se pide estudiar las condiciones del tráfico, con información recopilada gracias a un sistema de visión. El sistema detecta cuatro clases de vehículos a la entrada de un polígono industrial al que acceden trabajadores a diario:

  * Automóviles (vehículos utilitarios)
  * Bicicletas
  * Autobuses
  * Camiones

El conjunto de datos se almacena en un archivo CSV e incluye columnas que dan información adicional, y que puede ser necesaria para el modelo que desarrolles:

  * Horas (con información actualizada en bloques de 15 minutos)

  * Fecha (el número del día del mes, ya que el estudio está hecho en un mes completo de 31 días)

  * Días de la semana (de lunes a domingo)

  * Recuentos para cada tipo de vehículo (`CarCount`, `BikeCount`, `BusCount`, `TruckCount`).

  * La columna `Total` representa el recuento total de todos los tipos de vehículos detectados en un período de 15 minutos.

El conjunto de datos se actualiza cada 15 minutos, lo que proporciona una visión completa de los patrones de tráfico a lo largo de un mes completo (31 días). Además, el conjunto de datos incluye una columna que indica la situación del tráfico categorizada en cuatro clases:

  * 1-Heavy: tráfico denso y con propensión a atascos

  * 2-High: alto, con altas probabilidades de atascos

  * 3-Normal: tráfico normal, sin incidencias reseñables

  * 4-Low: bajo, con muy baja probabilidad de incidencias.

Esta información te debe ayudar a evaluar la gravedad de la congestión y a monitorizar las condiciones del tráfico en diferentes momentos y días de la semana.

Contarás con dos bases de datos para elaborar un modelo de clasificación basado en datos etiquetados:

**train_datos trafico.csv**: Esta base de datos completa y clasificada, con 2380 registros, te permitirá entrenar tu modelo. Comienza realizando un análisis descriptivo de la información, identifica las variables que son realmente significativas en tu análisis y entrena tu modelo.

[train_datos trafico](https://kopuru.com/wp-content/uploads/2023/11/train_datos-trafico.csv)

**test_datos trafico.csv**: Te proporcionamos además la base de datos de test, la cual, una vez tengas tu algoritmo listo, deberás utilizar para obtener los resultados de 596 registros, a los que tu modelo asignará la clasificación de la tipología de tráfico para cada registro.

[test_datos trafico](https://kopuru.com/wp-content/uploads/2023/11/test_datos-trafico.csv)

## Objetivos

Mediante los datos de train que encontrarás en el apartado de “Datos”, deberás:

  1. Analizar la información facilitada en el apartado de “Datos” y estudiar la calidad de la información recopilada por el sistema de visión a la entrada del polígono.

  2. A través de los datos de entrenamiento (train) desarrollar un modelo predictivo de clasificación que, en función de las variables de estudio que consideres más importantes, determine si el tráfico es muy denso, alto, normal o bajo (de acuerdo a la clasificación que encontrarás en el apartado “Datos”)

  3. Una vez tengas el modelo entrenado, con los datos de test, podrás aplicar en ellos la lógica de tu modelo, y obtener la clasificación para esos datos no etiquetados. Ese resultado será el que deberás subir a Kopuru, para que podamos evaluar tu porcentaje de acierto, junto con el código de tu solución.

  4. ¿Quieres deslumbrar? Si además crees que de tu análisis puede obtenerse más información, adjunta un PDF donde nos cuentes: por qué tu solución es la mejor, y que ideas se te ocurren para aplicar soluciones que mejoren el tráfico, basado en las conclusiones que has obtenido al entrenar tu modelo. Nos encantará ver soluciones que además, aporten un valor a problemas reales.

## Resultados

Estos son los resultados del reto sobre predicción del tráfico. El código de este repositorio me permitió obtener ¡una exactitud del **99,16%**!

![](https://kopuru.com/wp-content/uploads/2023/11/Captura-de-pantalla-2024-01-24-132121.png)
