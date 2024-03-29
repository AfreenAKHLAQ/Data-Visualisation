# Musées ou pas musées, telle est la question.

# Sommaire : 
1. [Pourquoi ce sujet ?](#1)
2. [Comment répondre à ces questions ? Avec l’Open Data !](#2)
3. [Commençons par l’Île-de-France…](#3)
4. [Zoom sur Paris](#4)
5. [Quels sont les musées que préfèrent les gens ?](#5)
6. [Je veux des photos !](#6)
7. [Data Wrangling](#7)

# 1. Pourquoi ce sujet ? <a name="1"></a>

Parce je suis sur le point d’avoir 26 ans et je vais donc devoir payer mon entrée au musée. Mes derniers jours de jeunesse me poussent à sortir et profiter de la gratuité des musées... avant la fin.

C'est dans cette perspective d’organisation de Sorties Musées que je me pose quelques questions : 
* Combien est-ce qu'il y a de musées en Île-de-France ?
* Lesquels sont-ils ?
* Par quels musées devrais-je commencer mes Sorties Musées ? Les plus fréquentés peut-être ?
* (Est-ce que l’envie d’aller au musée à un rapport avec le revenu ?)

# 2. Comment répondre à ces questions ? Avec l’Open Data ! <a name="2"></a>

La plateforme open data de la Région Île-de-France m’a fourni mon jeu de données initial (Fichier 1) : [La liste des Musées de France](https://data.iledefrance.fr/explore/dataset/liste_des_musees_franciliens/information/?disjunctive.region_administrative&disjunctive.departement). Il s’agit d’un fichier de 133 lignes recensant toutes les « institutions dotées de l'appellation "Musée de France" au sens du Code du patrimoine. » Je note donc qu’il ne s’agit pas de tous les musées d’Île-de-France.

J’ai tiré mes deux autres jeux de données de la plateforme de données ouvertes du ministère de la Culture : [Fréquentation des Musées de France](https://data.culture.gouv.fr/explore/dataset/frequentation-des-musees-de-france/export/?disjunctive.nomdep). On trouve dans les deux jeux de données, la fréquentation totale, payante et gratuite dans les Musées de France, de 2001 à 2021 pour l'un (Fichier 2) et de 2001 à 2016 pour l'autre (Fichier 3).

* *Fichier 1 après modifications : [1_liste-des-musees-franciliens.csv](https://github.com/AfreenAKHLAQ/Data-Visualisation/blob/main/Fichiers_utilis%C3%A9s/1_liste-des-musees-franciliens-avec-images.csv)*
* *Fichier 2 après modifications : [2_frequentation-des-musees-de-France-V2.csv](https://github.com/AfreenAKHLAQ/Data-Visualisation/blob/main/Fichiers_utilis%C3%A9s/2_frequentation-des-musees-de-france.csv)*
* *Fichier 3 après modifications : [3_frequentation-totale-mdf-2001-a-2016-V2.csv](https://github.com/AfreenAKHLAQ/Data-Visualisation/blob/main/Fichiers_utilis%C3%A9s/3_frequentation-totale-mdf-2001-a-2016.csv)*


Un Srpint Qualité allégé m’a permis de vérifier que chaque jeu de données était : 
* facilement accessible, 
* sous licence ouverte, 
* disponible au téléchargement sous différents formats (CSV, JSON, Excel, etc.),
* très bien documenté,
* sans de gros problèmes de syntaxe, de valeurs suspectes, de valeurs manquantes ou de doublons (bien que je me suis rendu compte au fur et à mesure de mon exploration qu’il y avait bien quelques corrections à faire),
* sans données ou contenu problématique, que cela soit au niveau réglementaire ou autre.

Ces jeux de données couplés aux outils comme OpenRefine, Datwrapper, Flourish et uMap m’ont permis de traiter et visualiser les données afin de pouvoir organiser au mieux mes Sorties Musées.

Vus trouverez la description détaillée du traitement des jeux de données ici.

# 3. Commençons par l’Île-de-France… <a name="3"></a>

Je commence mon exploration en visualisant tout ce qui s’offre à moi, sans aller trop loin. Pour cela, je vais utiliser mon premier fichier, le nettoyer sur OpenRefine et créer une carte affichant tous les « Musées de France » en Île-de-France.

<iframe title="Les &quot;Musées de France&quot; en Île-de-France" aria-label="Carte" id="datawrapper-chart-2JZHu" src="https://datawrapper.dwcdn.net/2JZHu/9/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="808" data-external="1"></iframe><script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(a){if(void 0!==a.data["datawrapper-height"]){var e=document.querySelectorAll("iframe");for(var t in a.data["datawrapper-height"])for(var r=0;r<e.length;r++)if(e[r].contentWindow===a.source){var i=a.data["datawrapper-height"][t]+"px";e[r].style.height=i}}}))}();
</script>

> *[Jeu de données utilisé : Fichier 1](https://github.com/AfreenAKHLAQ/Data-Visualisation/blob/main/Historiques_OpenRefine/history_1_liste-des-musees-franciliens-avec-images.json)*

Il semblerait, à priori, que la région parisienne détient le plus grand nombre de Musées de France.

Je veux vérifier cela et par la même occasion voir la répartition du nombre de « Musées de France » en Île-de-France par département et par commune. Je réalise donc un Treemap, ou une carte proportionnelle :

<div class="flourish-embed flourish-hierarchy" data-src="visualisation/16629623"><script src="https://public.flourish.studio/resources/embed.js"></script></div>

> *[Jeu de données utilisé : Fichier 1](https://github.com/AfreenAKHLAQ/Data-Visualisation/blob/main/Historiques_OpenRefine/history_1_liste-des-musees-franciliens-avec-images.json)*

Donc mon premier constat visuel était bien correcte : les « Musées de France en Île-de-France » se retrouvent surtout autour de Paris.

Il peut y avoir plusieurs raisons pour cela :

*	Paris est une ville qui a une longue histoire culturelle et artistique. En effet, elle a été le centre de beaucoup de mouvement antistatique (Renaissance, Lumières, etc.) et a donc accumulé, au fil des années, un patrimoine important.
*	Paris a une densité de population de 20 238 habitants par km2. Cette densité urbaine élevée favorise la création et la fréquentation de musées.
*	Paris est la capitale de la France et donc un pôle culturel et touristique majeur. Donc plus de visiteurs et plus de ressources pour maintenir le patrimoine.
*	Les acteurs majeurs responsables de  l’attribution du label « Musée de France », le Ministère de la Culture et le Service des musées de France, sont basés à Paris. J’image que cela influence  aussi le nombre de musées labellisés dans la région.

> *[Merci Wikipedia]( https://fr.wikipedia.org/wiki/Paris) et [Merci Ministère de la Culture](https://www.culture.gouv.fr/Thematiques/Musees/Les-musees-en-France/Les-musees-de-France/Le-reseau-des-musees-de-France)*

Cela tombe bien, car je suis fauchée et je n’ai pas le permis. Plus encore, en 6 jours (avant mon anniversaire) je n’ai pas le temps d’aller visiter les « Musées de France » de toute l’Île-de-France.

# 4. Zoom sur Paris <a name="4"></a>

Je veux voir la liste de tous les « Musées de France » situé à Paris. Je réalise donc un tableau :

<iframe title="Musées situés à Paris labélisés &quot;Musées de France&quot;" aria-label="Tableau" id="datawrapper-chart-mbgXq" src="https://datawrapper.dwcdn.net/mbgXq/2/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="938" data-external="1"></iframe><script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(a){if(void 0!==a.data["datawrapper-height"]){var e=document.querySelectorAll("iframe");for(var t in a.data["datawrapper-height"])for(var r=0;r<e.length;r++)if(e[r].contentWindow===a.source){var i=a.data["datawrapper-height"][t]+"px";e[r].style.height=i}}}))}();
</script>

> *[Jeu de données utilisé : Fichier 1](https://github.com/AfreenAKHLAQ/Data-Visualisation/blob/main/Historiques_OpenRefine/history_1_liste-des-musees-franciliens-avec-images.json)*

Je veux maintenant savoir quel est leur âge. Ou plutôt, quel est leur date de création. Il suffit d'une réconciliation sur OpenRefine pour exaucer mon vœux. Je créer ainsi une frise chronologique des date d’ouverture officielle des musées parisiens ayant le label « Musées de France » en les répartissant par arrondissement :

<div class="flourish-embed flourish-scatter" data-src="visualisation/16648982"><script src="https://public.flourish.studio/resources/embed.js"></script></div>> 

*[Jeu de données utilisé : Fichier 1](https://github.com/AfreenAKHLAQ/Data-Visualisation/blob/main/Historiques_OpenRefine/history_1_liste-des-musees-franciliens-avec-images.json)*

Voilà ! Maintenant je sais qu'il n'y a pas de « Musées de France » dans 2ème et le 20ème arrondissment mais qu'il y en a 7 dans 16ème. Pourquoi ne pas commencer mes Sorties Musées par le 16ème arrondissement donc ?

J’ai donc le choix de 48 jolis « Musées de France » avec le plus ancient datant de 1793 (Le Muséum National d'Histoire Naturelle) et le plus récent, de 2017 (Le Musée Yves Saint-Laurent Paris). C'est déjà pas mal. Mais par curiosité, je me demande combien il y a vraiment de musées dans la ville de Paris.

Pour répondre à cette question, ma première recherche m’a amené sur la page Wikipédia de la [Catégorie:Musée à Paris]( https://fr.wikipedia.org/wiki/Cat%C3%A9gorie:Mus%C3%A9e_%C3%A0_Paris). Cette page présente 96 liens vers des pages qui ne sont pas toutes celles de musées.

Que faire ? Consulter les 96 liens et vérifier, pour chacun, s’il s’agit bien de la page d'un musée ? Ou alors, faire une requête SPARQL sur Wikidata Query Service permettant de recenser les musées situés à Paris ? 

Go sur Wikidata !

```sparql
# Listes des musées situés à Paris et leur coordonnées géographiques (latitude, longitude) 
SELECT DISTINCT ?musee ?museeLabel ?lat ?long (CONCAT(STR(?lat),", ",STR(?long)) as ?lat_long)
WHERE {
  ?musee wdt:P31 wd:Q33506. # Instance de musée (Q33506) ou ses sous-classes (P31/wdt:P279*)
  ?musee wdt:P131 wd:Q90. # Situé à (P131) Paris (Q90)

  OPTIONAL { 
    ?musee wdt:P625 ?coordonees. # P625: Coordonnées géographiques
    ?musee p:P625 ?declaration.
    ?declaration psv:P625 ?coord_geo.
    ?coord_geo wikibase:geoLatitude ?lat.
    ?coord_geo wikibase:geoLongitude ?long.    
  }
  
  SERVICE wikibase:label { bd:serviceParam wikibase:language "fr,en". }
}
ORDER BY ?museeLabel
```
Cette requête m'a permis de récupérées des données (Fichier 4) puis de les modifiés dans OpenRefine pour obtenir ceci :

<iframe title="Liste des musées situés à Paris" aria-label="Tableau" id="datawrapper-chart-pJ8Cw" src="https://datawrapper.dwcdn.net/pJ8Cw/2/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="866" data-external="1"></iframe><script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(a){if(void 0!==a.data["datawrapper-height"]){var e=document.querySelectorAll("iframe");for(var t in a.data["datawrapper-height"])for(var r=0;r<e.length;r++)if(e[r].contentWindow===a.source){var i=a.data["datawrapper-height"][t]+"px";e[r].style.height=i}}}))}();
</script>

> *[Jeu de données utilisé : Fichier 4](https://github.com/AfreenAKHLAQ/Data-Visualisation/blob/main/Fichiers_utilis%C3%A9s/4_query-wikidata-liste-des-musees-parisiens.csv)*

Après avoir comblé les données manquantes, je croisent ce jeu de données avec la liste des « Musées de France » à Paris et je vérifie qu’il n’y a pas de doublons dans un fichier Excel. Je crée ensuite une carte montrant les musées parisiens avec et sans le label « Musées de France ».

<iframe width="100%" height="800px" frameborder="0" allowfullscreen allow="geolocation" src="//umap.openstreetmap.fr/fr/map/les-musees-parisiens_1015509?scaleControl=true&miniMap=true&scrollWheelZoom=true&zoomControl=true&editMode=disabled&moreControl=true&searchControl=true&tilelayersControl=null&embedControl=null&datalayersControl=true&onLoadPanel=caption&captionBar=true&captionMenus=true&fullscreenControl=true&locateControl=false&editinosmControl=false&starControl=false"></iframe><p><a href="//umap.openstreetmap.fr/fr/map/les-musees-parisiens_1015509?scaleControl=true&miniMap=true&scrollWheelZoom=true&zoomControl=true&editMode=disabled&moreControl=true&searchControl=true&tilelayersControl=null&embedControl=null&datalayersControl=true&onLoadPanel=caption&captionBar=true&captionMenus=true&fullscreenControl=true&locateControl=false&editinosmControl=false&starControl=false">Voir en plein écran</a></p>

> *[Jeu de données utilisé : Fichier 5](https://github.com/AfreenAKHLAQ/Data-Visualisation/blob/main/Fichiers_utilis%C3%A9s/5_query-wikidata-liste-des-musees-parisiens.GEOJSON)*

> *[Jeu de données utilisé : Fichier 6](https://github.com/AfreenAKHLAQ/Data-Visualisation/blob/main/Fichiers_utilis%C3%A9s/6_liste-des-musees-franciliens.geojson)*

Je vois qu'il y a à peu près autant de musées parisiens avec le label « Musées de France » que sans. Toutefois, et c'est un choix personnel, je préfère les musées labbilisés. Je préfère aussi suivre le mouvement des gens, tel un mouton. C'est pour cela que je cherche maintenant à savoir quels musées sont les plus visités.

# 5. Quels sont les musées que préfèrent les gens <a name="5"></a>

J'utilise maintenant mon second fichier pour visualiser les 10 musées les plus visités chaque années pour les 10 dernières années. Mais les données ne sont valables que jusqu'à 2021, donc je me contente des Top 10 de de 2011 à 2021 :

<div class="flourish-embed flourish-chart" data-src="visualisation/16601101"><script src="https://public.flourish.studio/resources/embed.js"></script></div>

> *[Jeu de données utilisé : Fichier 2](https://github.com/AfreenAKHLAQ/Data-Visualisation/blob/main/Fichiers_utilis%C3%A9s/2_frequentation-des-musees-de-france.csv)*

Je vois que trois musées restent constamment les premiers, en commençant par le Musée du Louvre, puis le Musée d’Orsay et le Musée National d'Art Moderne (MNAM) qui est situé à Paris dans le centre Georges-Pompidou.

Cette constance peut s’explique par la notoriété de ces trois musées, mais aussi par le fais que créer ce Top 10, j’ai due retirée tous les musées ayant ne seraient-ce qu’une seule donnée manquante (pour des questions de lisibilité de la visualisation). On pourrait se demander si ces Top 10 seraient différents avec toutes les données.

Ce que je trouve surprennant, c'est que les entrées majoritairent, sont les entrées payantes. Ce n'est que pour le Musées du Louvre que l'ont voit la tendance s'inversée légèrement après l'année du Covid.

Je suis une personne curieuse, mais aussi paresseuse. Je me demande à quoi ressemble l'évolution de la fréquentation des 10 dernières dernières années. C'est-à-dire de 2001 à 2011. Pour cela, je choisi sur le site du Minitère de la Culture, un fichier tout prêt (Fichier 3) que je mofifie légèrement pour obtenir la visualisation que je souhaite : 

<div class="flourish-embed flourish-bar-chart-race" data-src="visualisation/16635811"><script src="https://public.flourish.studio/resources/embed.js"></script></div>

> *[Jeu de données utilisé : Fichier 3](https://github.com/AfreenAKHLAQ/Data-Visualisation/blob/main/Fichiers_utilis%C3%A9s/3_frequentation-totale-mdf-2001-a-2016.csv)*

Ici aussi, la tendence des musées les plus fréquentés est la même mais parmis les musées les moins fréquentés se trouve le Musée de Montmartre. Cela me semble douteux pusqu'il s'agit d'un site touristique assez connu.

# 6. Je veux des photos ! <a name="6"></a>

Mainbtenant que j'ai une idées globale des musées qui me sont disponibles, je veux aussi pouvoir voir à quoi ils ressemblent. Quoi de mieu qu'une requête Wikidata pour cela ?

```sparql
#defaultView:ImageGrid
SELECT ?item ?itemLabel ?imageLink
WHERE {
  VALUES (?item ?order) {
  (wd:Q3330124 1)(wd:Q3329303 2)(wd:Q3330300 3)(wd:Q3075375 4)(wd:Q15731380 5)(wd:Q2391572 6)(wd:Q88645654 7)(wd:Q2714932 8)(wd:Q1889428 9)(wd:Q1632912 10)(wd:Q1319378 11)(wd:Q19675 12)(wd:Q977732 13)(wd:Q3329933 14)(wd:Q23402 15)(wd:Q23600018 16)(wd:Q2415229 17)(wd:Q105988788 18)(wd:Q30538871 19)(wd:Q2860590 20)(wd:Q23639828 21)(wd:Q1631711 22)(wd:Q3329734 23)(wd:Q3329594 24)(wd:Q3330694 25)(wd:Q23600382 26)(wd:Q23600219 27)(wd:Q2588025 28)(wd:Q2342844 29)(wd:Q3329245 30)(wd:Q3330653 31)(wd:Q3330509 32)(wd:Q3329026 33)(wd:Q3329618 34)(wd:Q64549730 35)(wd:Q547789 36)(wd:Q1585909 37)(wd:Q2915606 38)(wd:Q1094332 39)(wd:Q2613771 40)(wd:Q106448129 41)(wd:Q1955698 42)(wd:Q1998638 43)(wd:Q1124095 44)(wd:Q838691 45)(wd:Q650519 46)(wd:Q30303348 47)(wd:Q23599965 48)(wd:Q23600488 49)(wd:Q3330528 50)(wd:Q1189955 51)(wd:Q3329627 52)(wd:Q3330076 53)(wd:Q23600423 54)(wd:Q3418414 55)(wd:Q3330506 56)(wd:Q3075615 57)(wd:Q3330577 58)(wd:Q3329327 59)(wd:Q3329330 60)(wd:Q3329678 61)(wd:Q28033642 62)(wd:Q1667022 63)(wd:Q1572452 64)(wd:Q88640485 65)(wd:Q860166 66)(wd:Q3330482 67)(wd:Q2445818 68)(wd:Q2919066 69)(wd:Q726781 70)(wd:Q1538826 71)(wd:Q1895953 72)(wd:Q1782606 73)(wd:Q2597719 74)(wd:Q3330663 75)(wd:Q3329170 76)(wd:Q2970121 77)(wd:Q23600664 78)(wd:Q3330504 79)(wd:Q3329788 80)(wd:Q23640566 81)(wd:Q1955692 82)(wd:Q23599751 83)(wd:Q3329963 84)(wd:Q23639850 85)(wd:Q3329993 86)(wd:Q107269421 87)(wd:Q3330439 88)(wd:Q23599717 89)(wd:Q36362855 90)(wd:Q23599912 91)(wd:Q31203332 92)(wd:Q3329858 93)(wd:Q2715373 94)(wd:Q857276 95)(wd:Q167863 96)(wd:Q1579504 97)(wd:Q1094302 98)(wd:Q1128657 99)(wd:Q743206 100)(wd:Q1996069 101)(wd:Q1954498 102)(wd:Q2296362 103)(wd:Q23057803 104)(wd:Q3578591 105)(wd:Q3330084 107)(wd:Q1530976 108)(wd:Q3330182 109)(wd:Q1587628 110)(wd:Q2599177 111)(wd:Q640447 112)(wd:Q43688220 113)(wd:Q59546080 114)(wd:Q860994 115)(wd:Q3329915 116)(wd:Q3330523 117)(wd:Q23599848 118)(wd:Q17560765 119)(wd:Q82748 120)(wd:Q611062 121)(wd:Q23600534 122)(wd:Q3330518 123)(wd:Q3329532 124)(wd:Q2420675 125)(wd:Q23639858 126)(wd:Q3329216 127)(wd:Q3329361 128)(wd:Q23641285 129)(wd:Q1230290 130)(wd:Q3330662 131)(wd:Q2946 132) 
  }

  OPTIONAL { ?item wdt:P18 ?imageLink. }
  SERVICE wikibase:label { bd:serviceParam wikibase:language "fr,en". }
}
ORDER BY ?order
```

<iframe style="width: 80vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3AImageGrid%0ASELECT%20%3Fitem%20%3FitemLabel%20%3FimageLink%0AWHERE%20%7B%0A%20%20VALUES%20(%3Fitem%20%3Forder)%20%7B%0A%20%20(wd%3AQ3330124%201)(wd%3AQ3329303%202)(wd%3AQ3330300%203)(wd%3AQ3075375%204)(wd%3AQ15731380%205)(wd%3AQ2391572%206)(wd%3AQ88645654%207)(wd%3AQ2714932%208)(wd%3AQ1889428%209)(wd%3AQ1632912%2010)(wd%3AQ1319378%2011)(wd%3AQ19675%2012)(wd%3AQ977732%2013)(wd%3AQ3329933%2014)(wd%3AQ23402%2015)(wd%3AQ23600018%2016)(wd%3AQ2415229%2017)(wd%3AQ105988788%2018)(wd%3AQ30538871%2019)(wd%3AQ2860590%2020)(wd%3AQ23639828%2021)(wd%3AQ1631711%2022)(wd%3AQ3329734%2023)(wd%3AQ3329594%2024)(wd%3AQ3330694%2025)(wd%3AQ23600382%2026)(wd%3AQ23600219%2027)(wd%3AQ2588025%2028)(wd%3AQ2342844%2029)(wd%3AQ3329245%2030)(wd%3AQ3330653%2031)(wd%3AQ3330509%2032)(wd%3AQ3329026%2033)(wd%3AQ3329618%2034)(wd%3AQ64549730%2035)(wd%3AQ547789%2036)(wd%3AQ1585909%2037)(wd%3AQ2915606%2038)(wd%3AQ1094332%2039)(wd%3AQ2613771%2040)(wd%3AQ106448129%2041)(wd%3AQ1955698%2042)(wd%3AQ1998638%2043)(wd%3AQ1124095%2044)(wd%3AQ838691%2045)(wd%3AQ650519%2046)(wd%3AQ30303348%2047)(wd%3AQ23599965%2048)(wd%3AQ23600488%2049)(wd%3AQ3330528%2050)(wd%3AQ1189955%2051)(wd%3AQ3329627%2052)(wd%3AQ3330076%2053)(wd%3AQ23600423%2054)(wd%3AQ3418414%2055)(wd%3AQ3330506%2056)(wd%3AQ3075615%2057)(wd%3AQ3330577%2058)(wd%3AQ3329327%2059)(wd%3AQ3329330%2060)(wd%3AQ3329678%2061)(wd%3AQ28033642%2062)(wd%3AQ1667022%2063)(wd%3AQ1572452%2064)(wd%3AQ88640485%2065)(wd%3AQ860166%2066)(wd%3AQ3330482%2067)(wd%3AQ2445818%2068)(wd%3AQ2919066%2069)(wd%3AQ726781%2070)(wd%3AQ1538826%2071)(wd%3AQ1895953%2072)(wd%3AQ1782606%2073)(wd%3AQ2597719%2074)(wd%3AQ3330663%2075)(wd%3AQ3329170%2076)(wd%3AQ2970121%2077)(wd%3AQ23600664%2078)(wd%3AQ3330504%2079)(wd%3AQ3329788%2080)(wd%3AQ23640566%2081)(wd%3AQ1955692%2082)(wd%3AQ23599751%2083)(wd%3AQ3329963%2084)(wd%3AQ23639850%2085)(wd%3AQ3329993%2086)(wd%3AQ107269421%2087)(wd%3AQ3330439%2088)(wd%3AQ23599717%2089)(wd%3AQ36362855%2090)(wd%3AQ23599912%2091)(wd%3AQ31203332%2092)(wd%3AQ3329858%2093)(wd%3AQ2715373%2094)(wd%3AQ857276%2095)(wd%3AQ167863%2096)(wd%3AQ1579504%2097)(wd%3AQ1094302%2098)(wd%3AQ1128657%2099)(wd%3AQ743206%20100)(wd%3AQ1996069%20101)(wd%3AQ1954498%20102)(wd%3AQ2296362%20103)(wd%3AQ23057803%20104)(wd%3AQ3578591%20105)(wd%3AQ3330084%20107)(wd%3AQ1530976%20108)(wd%3AQ3330182%20109)(wd%3AQ1587628%20110)(wd%3AQ2599177%20111)(wd%3AQ640447%20112)(wd%3AQ43688220%20113)(wd%3AQ59546080%20114)(wd%3AQ860994%20115)(wd%3AQ3329915%20116)(wd%3AQ3330523%20117)(wd%3AQ23599848%20118)(wd%3AQ17560765%20119)(wd%3AQ82748%20120)(wd%3AQ611062%20121)(wd%3AQ23600534%20122)(wd%3AQ3330518%20123)(wd%3AQ3329532%20124)(wd%3AQ2420675%20125)(wd%3AQ23639858%20126)(wd%3AQ3329216%20127)(wd%3AQ3329361%20128)(wd%3AQ23641285%20129)(wd%3AQ1230290%20130)(wd%3AQ3330662%20131)(wd%3AQ2946%20132)%20%0A%20%20%7D%0A%0A%20%20OPTIONAL%20%7B%20%3Fitem%20wdt%3AP18%20%3FimageLink.%20%7D%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22fr%2Cen%22.%20%7D%0A%7D%0AORDER%20BY%20%3Forder%0A" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups"></iframe>

Bon... C'est bien joli tout ça mais, j'ai pas le temps d'aller au musée... 

# 7. Data Wrangling <a name="7"></a>

* Retrouvez la descriptions des modifcations principales effectuées sur les jeux de données dans le fichier [Data Wrangling.pdf](https://github.com/AfreenAKHLAQ/Data-Visualisation/blob/main/Historiques_OpenRefine/Data%20Wrangling.pdf)
* Retrouvez l'historique OpenRefine des fichiers :
*   [Fichier 1 : 1_liste-des-musees-franciliens-avec-images.csv](https://github.com/AfreenAKHLAQ/Data-Visualisation/blob/main/Historiques_OpenRefine/history_1_liste-des-musees-franciliens-avec-images.json)
*   [Fichier 2 : 2_frequentation-des-musees-de-france.csv](https://github.com/AfreenAKHLAQ/Data-Visualisation/blob/main/Historiques_OpenRefine/history_2_frequentation-des-musees-de-france.json)
*   [Fichier 3 : 3_frequentation-totale-mdf-2001-a-2016.csv](https://github.com/AfreenAKHLAQ/Data-Visualisation/blob/main/Historiques_OpenRefine/history_3_frequentation-totale-mdf-2001-a-2016.json)
*   [Fichier 4 : 4_query-wikidata-liste-des-musees-parisiens.csv](https://github.com/AfreenAKHLAQ/Data-Visualisation/blob/main/Historiques_OpenRefine/history_4_query-wikidata-liste-des-musees-parisiens.json)

