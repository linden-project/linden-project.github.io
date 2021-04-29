---
title: Linny Introductie
project: Linden
type: documentatie
boek: Linny Handleiding
hoofdstuk: 1. Introductie
author: Pim Snel
abstract: Gebruikershandleiding Linny
deelproject: Linny.vim Handleiding
---

> "Everything is connected" Dirk Gently

# Wat is Linny

Linny is een database en wikisysteem voor persoonlijk gebruik. Een verzameling
Markdown-bestanden en een index vormen de inhoud van database. De losse
markdown-bestanden zijn de losse data-elementen van de database. De
front-matter-blokken bovenaan de markdown-bestanden definieren de
document-kenmerken en de relaties met andere documenten.

Documenten worden automatisch gerubriceerd volgens een door de gebruiker
gedefinieerd classificatiesysteem. Tijdens het werken met de database groeit en
verfijnd het classificatiesysteem of datamodel vanzelf. Linny faciliteert de
gebruiker met hulpmiddelen om navigeren en te ordenen.

Een Linny database kan groeiten tot een zeer complexe model met duidenden
documenten. Door de eenvoud in gebruik een kleine database echter al zeer
behulpzaam en functioneel.

# Taxonomieën

Linny organiseert informatie met door de gebruiker gedefinieerde taxonomieën.

De taxonomieën worden definieerd in de wiki_indexes.yml in de config directory.
Een markdown bestand kan aan meerdere taxonomieën wordt toegekend als waarde.
Deze toekenning wordt gedaan in de **front matter** van het markdown bestand.

## Linny is een Vim-plugin

Linny is ontwikkeld in Vim als Vim-plugin. Als je wilt werken met Linny moet je
al kunnen werken met Vim. De werkwijze van Linny is echter universeel
toepasbaar. Ik sluit niet uit dat er ook plugin's voor andere text-editors of
markdown-apps zullen ontstaan. Ik kan me ook voorstellen dat er mobiele apps
voor Linny zullen komen.

## Ook nog Linnyx, de indexer

Naast de Vim-plugin die zorgt voor de gebruikersinterface, heeft Linny een
indexer, *wimpix*. De indexer leest de front-matter-blokken van alle
markdown-bestanden en maakt hiermee index-bestanden. Deze index-bestanden
zorgen ervoor dat de navigatie snel is en de database doorzoekbaar.

# De Linny-database

De database is opgeslagen in 4 onderdelen.

- de markdown-bestanden
- de taxonomie-configuratie-bestanden
- de index-bestanden
- de gebruikers interface toestand-bestanden 

De eerste twee vormen samen de data en het datamodel van de database. Deze
mogen nooit verloren gaan en moeten dus goed gebackupped worden.

De laatste twee zijn hulp-bestanden die door de vim-plugin en de indexer
continu worden vernieuwd. Het is geen ramp als deze verloren gaan. Ze zijn
nodig tijdens het gebruik van Linny, en kunnen altijd weer opnieuw worden
gegenereerd.

## Bestanden en bestandslocaties

De locatie van de database en hulpbestanden kunnen door de gebruiker worden
geconfigureerd. Zonder configuratie kiest Linny standaard locaties.

### wimpi-root ~/wimpidb

De wimpi-root is de directory met alle taxonomie-configuratie- en
markdown-bestanden. Er zijn in deze directories geen sub-directories.

```
~/wimpidb/config/
~/wimpidb/wiki/
```

In wimpidb/wiki staan alle markdown-bestanden.
In /config staan alle taxonomie-configuratie-bestanden opgeslagen in yaml-formaat.

Zorg ervoor dat je de wimpi-root regelmatig back-upt.

### De index en state-bestanden

De index- en state-bestanden bevinden zich standaard op een andere locatie. Dit
is bewust gekozen om het mogelijk dat de wimpi-root directory in een directory
bevind die door een cloud-service, zoals Dropbox of Stack wordt ge-syncd. De
index- en state-bestanden zijn in json-formaat opgeslagen en voor de gebruiker
verder niet interessant.

~/.wimpi/index/
~/.wimpi/state/

# Gebruikersinterface

Linny heeft een aantal interface onderdelen die de gebruiker helpen om
efficiënt met de documentendatabase te werken.

De hier beschreven onderdelen zijn:

- navigatiezijpaneel
- het kenmerken-zoeker binnen front matter

## Navigatiezijpaneel

Het navigatiezijpaneel biedt de belangrijkste manier om te navigeren door de
database, en uiteindelijk het bestand te openen waar je naar op zoek was. De
navigatie kent drie niveau's.

## 1e niveau: Het startscherm

Het 1e niveau biedt verschillende manieren om te navigeren door de
database.

- lijst met favoriete markdown-bestanden
- lijst favoriete classificaties
- lijst van alle taxonomieën
- recente gewijzigde markdown-bestanden

> TODO SCHERMAFBEELDING

## 2e niveau: Overzicht taxonomie

Het 2e niveau toont een overzicht van verzamelingen binnen een enkele
taxonomie. Stel je hebt de taxonomie *project* gedefinieerd. Als je op het
startscherm hebt geklikt op *Projecten* toont nu het 2e niveau alle
verschillende projecten.

Andere taxonomieën zouden kunnen zijn *klant*, of *documenttype*.

> TODO SCHERMAFBEELDING

## 3e niveau: Overzicht verzameling documenten

Het laatste niveau is toont de documenten die allemaal hetzelde kenmerk hebben
binnen de gekozen taxonomie. Stel je hebt in het 2e niveau op *Development
website big.com* geklikt, dan zie je nu alle documenten die het kenmerk
*Project: Development website big.com* hebben. Als je nu op een document klikt
wordt hij door de editor geopend.
