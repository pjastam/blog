---
title: 'Personal Health Train: An application to risk equalization (in Dutch)'
subtitle: A Dockerized version of the Shiny app for talent scouting & development of junior speed skaters

# Summary for listings and search engines
summary: A Dockerized version of the Shiny app for talent scouting & development of junior speed skaters

# Link this post with a project
projects: []

# Date published
date: "2019-02-19T00:00:00Z"

# Date updated
lastmod: "2019-02-19T00:00:00Z"

# Is this an unpublished draft?
draft: false

# Show this page in the Featured widget?
featured: false

# Featured image
# Place an image named `featured.jpg/png` in this page's folder and customize its options here.
image:
  caption: 'Image credit: [**Kim Stellingwerf/RTV Drenthe**](https://www.rtvdrenthe.nl/nieuws/136382/met-de-trein-via-zwolle-houd-rekening-met-vertraging)'
  focal_point: ""
  placement: 2
  preview_only: false

authors:
- admin

tags:
- PHT
- Personal Health Train

categories:
- Risk equalization
- Digital strategy
---

> Deze blog van mijn hand heb ik op bovenstaande datum op [LinkedIn](https://www.linkedin.com/pulse/personal-health-train-casus-risicoverevening-piet-stam/) gepubliceerd en is hier integraal overgenomen om de openbare beschikbaarheid te garanderen.

Voor [onderzoek](https://www.rijksoverheid.nl/documenten/brochures/2016/03/01/beschrijving-van-het-risicovereveningssysteem-van-de-zorgverzekeringswet) & [uitvoering](https://www.zorginstituutnederland.nl/financiering/risicoverevening-zvw/wat-is-risicoverevening) van de risicoverevening tussen zorgverzekeraars wordt het zorggebruik van alle 17 miljoen individuele (!) Nederlanders centraal verzameld in een landelijk databestand. Kan dat ook decentraal? Misschien met de [Personal Health Train](http://www.personalhealthtrain.nl/) (PHT), het concept dat Minister Bruins [propageert](https://www.rijksoverheid.nl/documenten/kamerstukken/2018/11/15/kamerbrief-over-data-laten-werken-voor-gezondheid) en is ontwikkeld door [DTL](https://www.dtls.nl/fair-data/personal-health-train/), [MAASTRO](https://www.linkedin.com/in/alajdekker/) en [LUMC](https://www.linkedin.com/in/peter-bram-t-hoen-1b6b9a18/)? Mijn voorlopige conclusie is: helaas (nog?) niet.

De bedoeling is dat de PHT gaat rijden voor zgn. [horizontaal èn verticaal gepartitioneerde databestanden](https://en.wikipedia.org/wiki/Partition_(database)#Partitioning_methods). Het landelijke databestand van de risicoverevening is een voorbeeld van een verticaal gepartitioneerd databestand. Dat betekent zoveel als dat de informatie in de verschillende kolommen uit verschillende databronnen (lees: locaties) komt. Bijv. de inkomensinformatie voor het kenmerk Sociaal-Economische Status (SES) wordt van de Belastingdienst betrokken, terwijl de informatie over de leeftijd van een individu door zijn/haar zorgverzekeraar wordt aangeleverd. Zo kom je tot een centraal databestand met 17 miljoen horizontale records en (o.a.) SES en leeftijd in de kolommen.

De bedoeling van de PHT is het tegenovergestelde van de gebruikelijke werkwijze, waarbij data eerst in een centraal databestand vanuit verschillende bronnen bij elkaar gebracht worden, voordat onderzoekers en algoritmen hun werk kunnen doen. De PHT beoogt juist de data op de bronlocatie te laten staan en de onderzoeker en de algoritmen daar naartoe te brengen. Voor de techneuten onder ons: je kunt een algoritme in een Docker container programmeren en deze op de data op de bronlocatie laten uitvoeren. Voor de niet-techneuten onder ons: stel je een treintje voor (met daarop een algoritme) dat langs de verschillende stations (i.e. bronlocaties) rijdt. Dit is fraai gevisualiseerd in een [korte video](https://vimeo.com/143245835).

Alleen al om privacyredenen zou het prachtig zijn als de PHT faciliteert dat horizontaal èn verticaal gepartitioneerde databestanden op de bronlocatie kunnen blijven staan. Ten aanzien van horizontaal gepartitioneerde databestanden zijn inmiddels prototypes van de PHT [beschikbaar](https://www.thegreenjournal.com/article/S0167-8140(16)34336-5/fulltext), maar ten aanzien van verticaal gepartitioneerde databestanden zit de PHT vooralsnog in [de experimentele fase](http://www.medra.org/servlet/aliasResolver?alias=iospressISBN&isbn=978-1-61499-851-8&spage=581&doi=10.3233/978-1-61499-852-5-581). Het algoritme wordt weliswaar naar de bronlocaties gebracht, maar als de data van verschillende bronlocaties met elkaar gecombineerd moeten worden, dan moeten de data toch even deze bronlocaties (tegelijkertijd) verlaten voordat het algoritme haar werk kan doen. En juist op dat ene moment is er toch weer (even) sprake van een centraal databestand waarop de berekening wordt uitgevoerd. En dat willen we met de PHT idealiter voorkomen.

Een oplossing hiervoor is er nog niet. Er wordt momenteel gedacht over het invoegen van een derde partij, die de data uit de locaties ophaalt en centraal koppelt zonder zelf inzage te krijgen in de data. Maar dat is niet nieuw: dat doet [ZorgTTP](https://www.zorgttp.nl/) al langer ten behoeve van het onderzoek en de uitvoering van de risicoverevening middels [pseudonimisatie](https://www.zorgttp.nl/pseudonimisatie/). Ook deze oplossingsrichting laat echter onverlet dat data de bronlocaties (tijdelijk) moeten verlaten voordat we onderzoekers en algoritmen hun werk kunnen laten doen. De werkwijze van ZorgTTP speelt weliswaar al goed in op de aspiratie van de PHT om de data zo dicht mogelijk bij de bronlocaties te verwerken, maar idealiter gebeurt dat op de bronlocaties zelf. Net zoals dat met de prototypes van de PHT bij horizontaal gepartitioneerde databestanden lukt.

De hamvraag is: hoe krijgen we de PHT op volle snelheid aan het rijden voor datavraagstukken zoals de risicoverevening? Als dat lukt, dan zou dit een enorme verbetering en vereenvoudiging betekenen voor de jaarlijkse verwerking van de individuele zorggebruikdata van ons allemaal. Op dinsdag 19 maart leggen [Hans van Vlaanderen](https://www.linkedin.com/in/hans-van-vlaanderen-b2541b3/) ([ZorgTTP](http://www.zorgttp.nl/)) en ik deze vraag voor in de “Making data work for health” sessie van [COMMIT/](https://www.commit-nl.nl/) en [DTL](https://www.dtls.nl/) op de [ICT.OPEN2019](https://ict-research.nl/ict-open/) conferentie. Samen met aanwezigen gaan we op zoek naar nieuwe oplossingsrichtingen. Want hoe mooi zou het zijn om de PHT ook voor data van de risicoverevening op volle snelheid aan het rijden te krijgen?
