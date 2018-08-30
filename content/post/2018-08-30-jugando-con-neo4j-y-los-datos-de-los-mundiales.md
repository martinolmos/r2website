---
title: Jugando con neo4j y los datos de los mundiales
author: Martin Olmos
date: '2018-08-30'
slug: jugando-con-neo4j-y-los-datos-de-los-mundiales
categories:
  - neo4j
tags: []
---

Como parte de la [Especialización en Ciencia de Datos del ITBA][1] participé de un seminario sobre [bases de datos de grafos][2] donde jugamos con [Neo4j][3] y datos históricos de los mundiales de fútbol.

A continuación algunas de las queries más interesantes.

### 1.¿Quiénes son los países que ganaron la Copa del Mundo siendo anfitriones?

```
MATCH (match:Match {round: "Final"})<-[hostPlayed:PLAYED_IN]-(host:Country),
      (host)<-[:HOSTED_BY]-(worldCup),
      (worldCup)-[:CONTAINS_MATCH]->(match),
      (match)<-[oppositionPlayed:PLAYED_IN]-(opposition)
WHERE (hostPlayed.score > oppositionPlayed.score) OR (hostPlayed.penalties > oppositionPlayed.score)
RETURN host, worldCup
ORDER BY worldCup.year
```
### Grafo 1

![Anfitriones ganadores de la Copa](/post/2018-08-30-jugando-con-neo4j-y-los-datos-de-los-mundiales/Anfitriones ganadores.png)

### 2.¿Qué países nunca ganaron un partido en un mundial?

```
MATCH (loser:Country)-[loserPlayed:PLAYED_IN]->(match:Match)<-[winnerPlayed:PLAYED_IN]-(winner:Country)
WHERE (winnerPlayed.score > loserPlayed.score)
WITH collect(distinct winner) as winners
MATCH (losers:Country)
WHERE NOT losers IN winners
RETURN losers.name        
```
### Respuesta 2
"Egypt"
"Iceland"
"Panama"
"Honduras"
"New Zealand"
"Angola"
"Togo"
"Serbia and Montenegro"
"Trinidad and Tobago"
"China PR"
"Bolivia"
"United Arab Emirates"
"Iraq"
"Canada"
"Kuwait"
"El Salvador"
"Zaire"
"Haiti"
"Israel"
"Dutch East Indies"
### 3.¿Cuál es el máximo número de goles en un partido de Mundial (sumando los dos equipos)?

```
MATCH(match:Match)
RETURN max(match.h_score + match.a_score) as max_goals
```

### Respuesta 3
12 goles 

### 4.¿Cuál es el estadio en el que se jugaron más partidos de Mundial?

```
MATCH (stad:Stadium)<-[:PLAYED_IN_STADIUM]-(match:Match)
RETURN stad.name, count(match) as cant
ORDER BY cant DESC
LIMIT 1
```

### Respuesta 4
Estadio Azteca, 19 partidos

### 5.¿Qué pais hizo la mayor cantidad de goles a lo largo de todos los mundiales?

```
MATCH(c1:Country)-[r:PLAYED_IN]->(match:Match)
RETURN c1.name, sum(r.score) as sum_goals
ORDER BY sum_goals DESC
LIMIT 1
```

### Respuesta 5
Brasil, 229 goles

### 6.¿Qué país participó de la mayor cantidad de mundiales?

```
MATCH(c1:Country)-[r:NAMED_SQUAD]->(squad:Squad)-[:FOR_WORLD_CUP]->(wc:WorldCup)
RETURN c1.name, count(c1) as cant
ORDER BY cant DESC
LIMIT 1
```

### Respuesta 6
Brasil, 21 mundiales


[1]:https://www.itba.edu.ar/postgrado/maestrias-y-especializaciones/especializacion-en-ciencia-de-datos/
[2]:https://es.wikipedia.org/wiki/Base_de_datos_orientada_a_grafos
[3]:https://neo4j.com/