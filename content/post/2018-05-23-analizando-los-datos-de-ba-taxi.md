---
title: Explorando los datos de BA Taxi con Tableau
author: Martin Olmos
date: '2018-05-23'
slug: analizando-los-datos-de-ba-taxi
categories: []
tags: []
---

Algunas preguntas exploratorias para hacerle a los [datos de BA Taxi][1].

El dataset cuenta con 19.148 viajes que van desde el 1ro de mayo al 1ro de septiembre de 2017

Veamos primero cuántos viajes se realizaron en cada mes:

<iframe align = "center" width = "400" height = "600" src="https://public.tableau.com/views/ViajesdeBATaxipormes/Sheet3?:embed=true&:showVizHome=no&:display_count=yes">
</iframe>
  
  
Y cómo se distribuyen los viajes según día y horario:

<iframe align = "center" width = "690" height = "650" src="https://public.tableau.com/views/ViajesdeBATaxipormes/Sheet4?:embed=true&:showVizHome=no&:display_count=yes">
</iframe>  
  
En el gráfico se ven claramente gran cantidad de viajes los viernes a la noche (madrugada del sábado) y sábado a la noche (madrugada del domingo) y los días de semana en las horas pico de la mañana (7, 8 y 9am). 


Veamos ahora cómo se distribuyen los viajes según la cantidad de pasajeros:

<iframe align = "center" width = "400" height = "600"
https://public.tableau.com/views/ViajesdeBATaxipormes/Sheet5?:embed=true&:showVizHome=no&:display_count=yes&publish=yes>
</iframe>


Barrios de origen y destino:

<iframe align = "center" width = "650" height = "650"
https://public.tableau.com/views/ViajesdeBATaxipormes/Sheet10?:embed=true&:showVizHome=no&:display_count=yes>
</iframe>

Relación entre distancia y duración del viaje:

<iframe align = "center" width = "650" height = "650"
https://public.tableau.com/views/ViajesdeBATaxipormes/Sheet9?:embed=true&:showVizHome=no&:display_count=yes>
</iframe>

Origen de los viajes:

<iframe align = "center" width = "650" height = "650"
https://public.tableau.com/views/ViajesdeBATaxipormes/Sheet7?:embed=y&:display_count=yes>
</iframe>

Destino de los viajes:

<iframe align = "center" width = "650" height = "650"
https://public.tableau.com/views/ViajesdeBATaxipormes/Sheet8?:embed=y&:display_count=yes>
</iframe>

Finalmente, recomiendo [este][2] interesantísimo análisis que hizo [@vazquezbrust](https://twitter.com/vazquezbrust) con estos datos sobre la mafia de los taxis.


[1]:https://data.world/vazquez-brust/viajes-solicitados-por-ba-taxi
[2]:https://bitsandbricks.github.io/post/taxis-en-buenos-aires-mapas-claros-y-negocios-turbios/