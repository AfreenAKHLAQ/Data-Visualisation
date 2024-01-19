# Devoir de M2 DEFI - Data Visualisation
M2 DEFI - Data Visualisation

# Présentation du sujet
Le sujet : ...

# Jeu de données
Les jeux de données utilisés : ...

# OpenRefine & WikiData
Utilisation d'OpenRefine et WikiData

# Les Visualisations

## Première visualisation
Analyse

```sparql
SELECT distinct ?creator ?creatorLabel ?datebirth ?datedeath ?placebirthLabel (CONCAT(STR(?lat),", ",STR(?long)) as ?lat_long) ?placedeathLabel (CONCAT(STR(?lat_2),", ", STR(?long_2)) as ?lat_long_2)

WHERE {
?creator wdt:P106 wd:Q1028181;
          p:P570/psv:P570 [
            wikibase:timeValue ?date;
            wikibase:timePrecision ?precision
          ].
  FILTER("1500-12-31"^^xsd:dateTime < ?date && ?date < "1600-00-00"^^xsd:dateTime).
  FILTER(?precision >= 9).
  BIND(YEAR(?date) AS ?year).
?creator wdt:P19 ?placebirth. # lieu de naissance 
?creator wdt:P569 ?datebirth.
?creator wdt:P570 ?datedeath. 
?placebirth wdt:P625 ?coord.
?placebirth p:P625 ?declaration.
?declaration psv:P625 ?coord_geo.
?coord_geo wikibase:geoLatitude ?lat.
?coord_geo wikibase:geoLongitude ?long.
?creator wdt:P20? ?placedeath. 
?placedeath wdt:P625 ?coord_death.
?placedeath p:P625 ?declaration2.
?declaration2 psv:P625 ?coord_geo_2.
?coord_geo_2 wikibase:geoLatitude ?lat_2.
?coord_geo_2 wikibase:geoLongitude ?long_2.
SERVICE wikibase:label { 
bd:serviceParam wikibase:language "fr,en"}
}
```

## Deuxième visualisation
Analyse

## Troisième visualisation
Analyse

# Conclusion
Conclusion générale

---
