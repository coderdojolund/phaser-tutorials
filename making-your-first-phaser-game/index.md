# Del 1 &ndash; Inledning

[Engelskt original](http://phaser.io/tutorials/making-your-first-phaser-game/index):
_By [Alvin Ourrad and Richard Davey](https://twitter.com/photonstorm)_ on 7th December 2013   [@photonstorm](https://twitter.com/photonstorm) 

![image](http://phaser.io/content/tutorials/making-your-first-phaser-game/tutorial_header.png)

Välkommen till vår första handledning om att göra ett spel med Phaser.
Här kommer vi att lära oss hur man bygger ett litet spel med en spelare som hoppar och springer omkring på plattformar och samlar stjärnor.
Medan vi går igenom stegen kommer vi att förklara några av kärnfunktionerna i ramverket.

### Vad är Phaser?

Phaser är ett ramverk för spel i HTML5 med målet att hjälpa utvecklare att riktigt snabbt göra kraftfulla HTML5-spel som fungerar i alla webbläsare och som, till skillnad från en del andra ramverk, är byggt speciellt för att fungera med mobila webbläsare.
Det enda kravet på webbläsaren är att den stödjer *canvas*-taggen.
Ramverket lånar också en hel del från Flixel.

## Krav

[Ladda ner källkodsfilerna](https://github.com/coderdojolund/phaser-tutorials/archive/master.zip)
och resurserna som hör till den här handledningen. Packa upp ZIP-filen på din hårddisk.

Du behöver ha lite, lite grundläggande kunskap i JavaScript.

Installera editorn Brackets. [Se beskrivningen här.](https://github.com/coderdojolund/flappy-bird-phaser-lessmilk.com/blob/master/docs/flappy-bird-phaser-0.md)

Starta Brackets och öppna mappen *phaser_tutorial_02*.

Öppna sidan `part1.html` i Brackets så tar vi en närmare titt på koden. Filen innehåller lite vanlig HTML som läser in Phaser och vår kod i `part1.js`. 

```html
<!doctype html> 
<html lang="en"> 
<head> 
	<meta charset="UTF-8" />
	<title>Phaser - Making your first game, part 1</title>
	<script src="//cdn.jsdelivr.net/phaser/2.5.0/phaser.min.js"></script>
    <style type="text/css">
        body {
            margin: 0;
        }
    </style>
</head>
<body>
<script src="part1.js"/>
</body>
</html>
```

Öppna nu `part1.js` i Brackets. Kodstrukturen ser ut så här:
```javascript
var game;

function preload() {
}

function create() {
}

function update() {
}

game = new Phaser.Game(800, 600, Phaser.AUTO, '', { preload: preload, create: create, update: update });
```
Den sista raden blåser liv i Phaser genom att skapa en instans av objektet *Phaser.Game* och sparar den i en lokal variabel som heter 
*game*.
Att kalla variabeln *game* är vanligast, men inget krav, och du kommer att se den i Phaser-exemplen.

## Första två parametrarna: `800, 600`
De första två parametrarna är bredden och höjden på *canvas*-elementet som Phaser skapar. I det här fallet 800 x 600 pixlar.
Din spelvärld kan ha vilken storlek som helst, men detta är upplösningen som spelet kommer att visas i. 

## Tredje parametern: `Phaser.AUTO`
Den tredje parametern kan vara antingen `Phaser.CANVAS`, `Phaser.WEBGL` eller `Phaser.AUTO`.
Detta är den s.k. rit-kontexten som du vill använda. Den parameter som rekommenderas är `Phaser.AUTO`, som automatiskt försöker använda WebGL, men om webbläsaren eller enheten inte stödjer det så faller Phaser tillbaks på Canvas.

## Fjärde parametern: `''`
Den fjäde parametern är en tom sträng, som är id på det DOM-element där du vill lägga in *canvas*-elementet som Phaser skapar. Eftersom vi lämnat den tom kommer *canvas*-elementet helt enkelt att läggas till i *body*. 

## Sista parametern: `{ preload: preload, create: create, update: update }`
Den sista parametern är ett objekt med tre referenser till Phasers viktigaste funktioner. Hur de används förklaras noggrant här. Lägg märke till att objektet inte är obligatoriskt &ndash; Phaser stödjer ett fullständigt system med tillstånd som låter dig dela upp din kod i mycket renare enstaka objekt. Men för en enkel kom igång-handledning som denna gör vi så här eftersom det här sättet låter oss prototypa snabbare.

Försöker du köra koden så här långt kommer du att märka att inget händer. I del 2 ska vi ändra på det. 

# `jslint` hjälper oss undvika dumma fel i koden

Om du försöker spara koden i Brackets, så märker du att det kommer ett fönster med varningar längst ner. Koden går att köra men vi kan få bort varningarna genom att lägga till det här högst upp i `part1.js`, vår kodfil.

```javascript
/*global Phaser */
/*jslint node: true */
'use strict';
```

Spara `part1.js` igen och varningarna bör vara borta.

# [Fortsätt till del 2](/del2.md)

## Att läsa på
[Mer om `Phaser.Game` hittar du här](http://phaser.io/docs/2.5.0/Phaser.Game.html)

## Ordlista
* **DOM-element** DOM är det sätt som JavaScript ser innehållet på en webbsida. DOM:en är ett objekt som innehåller formatteringen för HTML/XHTML/XML-koden och webbläsarens tillstånd. Exempel på DOM-element är `<div>`, `<html>`, `<head>` och `<body>`. Man styr utseendet på DOM-elementen med språket CSS och påverkar deras beteende med språket JavaScript.
* **rit-kontext** En grafisk rityta på en webbsida, t.ex. `<canvas>`

## Referenser
[Källkodsfiler i original](https://github.com/photonstorm/phaser/raw/master/resources/tutorials/02%20Making%20your%20first%20game/phaser_tutorial_02.zip)

[Skriv ut sidan](https://gitprint.com/coderdojolund/phaser-tutorials/blob/master/making-your-first-phaser-game/index.md)
