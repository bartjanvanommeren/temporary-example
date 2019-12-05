# Minor Multi Philadelphia Software Guidebook  
Deze README is een korte samenvatting van de Sportestic app. De README bevat een uitleg over hoe de applicatie opgestart moet worden en welke vereisten hiervoor zijn. Ook kunt u requirements, een mappenstructuur en de gebruikte libraries terug vinden. Dit document is een toevoeging bij het Functioneel Ontwerp geleverd tijdens overdracht aan de opdrachtgever.

### Versie
0.3.2

## Mappen structuur
```
root
│   README.md
│   package.json   
|
└───node_modules
│
└───public
│    │   index.html
│    │   manifest.json
|    └───assets
|    |    |   example.svg
|    └───audio
|    |    |   example.mp3   
|    
│   
└───server
|    │   index.js
|
└───src
|    |   index.js
|    |   index.scss
|    |   rooms.js
|    |   sportsInformation.js
|    |
|    └───components
|    |    └───component1
|    |    |    |   index.js
|    |    |    |   index.scss
|    |    |
|    |    └───component2
|    |    |    |   index.js
|    |    |    |   index.scss
|    |    |
```
### Opmerkingen
Hieronder een uitleg van een aantal bestanden uit de mappen structuur die hierboven is weergegeven.
* rooms.js: In dit bestand staat een JSON structuur met alle data waarmee de applicatie is opgebouwd.
Hier kunnen assets, pagina volgorde en teksten worden toegevoegd en aangepast.  
* sportsInformation.js: In dit bestand staat een JSON structuur met alle informatie over de verschillende sporten.
Hier kunnen de video's en teksten worden aangepast die bij een sport worden weergegeven.  

## Installatie en demo versie
```
git clone https://github.com/example
npm install
npm run start-local
```

Een demo Sportestic applicatie draait op een Heroku server. Deze is bereikbaar via http://example.com/.

## Routes
``/`` <br>
Startpagina waarop de gebruiker een foto maakt.

``/room/#`` <br>
Ruimtes waar de gebruiker keuzes maakt in verschillende categorieën.

``/room/#/#`` <br>
Ruimte waar de gebruiker keuzes maakt tussen drie verschillende sporten.

``/information/example`` <br>
Informatiepagina met een video over de geselecteerde sport.

## Gebruikte libraries
Libary naam | Versie
--- | ---
[NodeJS](https://nodejs.org/en/) | 6.10.0
[React](https://facebook.github.io/react/) | 15.5.4
[Express](https://expressjs.com/) | 4.15.3
[React-Router](https://github.com/ReactTraining/react-router) | 2.8.1
[React-Youtube](https://github.com/ReactTraining/react-router) | 7.4.0
