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
<iframe style="width: 55vw; height: 50vh; border: none;" src="https://query.wikidata.org/#%23defaultView%3ATable%0ASELECT%20distinct%20%3Fcreator%20%3FcreatorLabel%20%3Fdatebirth%20%3Fdatedeath%20%3FplacebirthLabel%20%28CONCAT%28STR%28%3Flat%29%2C%22%2C%20%22%2CSTR%28%3Flong%29%29%20as%20%3Flat_long%29%20%3FplacedeathLabel%20%28CONCAT%28STR%28%3Flat_2%29%2C%22%2C%20%22%2C%20STR%28%3Flong_2%29%29%20as%20%3Flat_long_2%29%0A%0AWHERE%20%7B%0A%3Fcreator%20wdt%3AP106%20wd%3AQ1028181%3B%0A%20%20%20%20%20%20%20%20%20%20p%3AP570%2Fpsv%3AP570%20%5B%0A%20%20%20%20%20%20%20%20%20%20%20%20wikibase%3AtimeValue%20%3Fdate%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20wikibase%3AtimePrecision%20%3Fprecision%0A%20%20%20%20%20%20%20%20%20%20%5D.%0A%20%20FILTER%28%221500-12-31%22%5E%5Exsd%3AdateTime%20%3C%20%3Fdate%20%26%26%20%3Fdate%20%3C%20%221600-00-00%22%5E%5Exsd%3AdateTime%29.%0A%20%20FILTER%28%3Fprecision%20%3E%3D%209%29.%0A%20%20BIND%28YEAR%28%3Fdate%29%20AS%20%3Fyear%29.%0A%3Fcreator%20wdt%3AP19%20%3Fplacebirth.%20%23%20lieu%20de%20naissance%20%0A%3Fcreator%20wdt%3AP569%20%3Fdatebirth.%0A%3Fcreator%20wdt%3AP570%20%3Fdatedeath.%20%0A%3Fplacebirth%20wdt%3AP625%20%3Fcoord.%0A%3Fplacebirth%20p%3AP625%20%3Fdeclaration.%0A%3Fdeclaration%20psv%3AP625%20%3Fcoord_geo.%0A%3Fcoord_geo%20wikibase%3AgeoLatitude%20%3Flat.%0A%3Fcoord_geo%20wikibase%3AgeoLongitude%20%3Flong.%0A%3Fcreator%20wdt%3AP20%3F%20%3Fplacedeath.%20%0A%3Fplacedeath%20wdt%3AP625%20%3Fcoord_death.%0A%3Fplacedeath%20p%3AP625%20%3Fdeclaration2.%0A%3Fdeclaration2%20psv%3AP625%20%3Fcoord_geo_2.%0A%3Fcoord_geo_2%20wikibase%3AgeoLatitude%20%3Flat_2.%0A%3Fcoord_geo_2%20wikibase%3AgeoLongitude%20%3Flong_2.%0ASERVICE%20wikibase%3Alabel%20%7B%20%0Abd%3AserviceParam%20wikibase%3Alanguage%20%22fr%2Cen%22%7D%0A%7D" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>


## Deuxième visualisation
Analyse

## Troisième visualisation
Analyse

# Conclusion
Conclusion générale

---
