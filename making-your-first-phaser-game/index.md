# Del 1 &ndash; Inledning

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

[Ladda ner källkodsfilerna](https://github.com/photonstorm/phaser/raw/master/resources/tutorials/02%20Making%20your%20first%20game/phaser_tutorial_02.zip) och resurserna som hör till den här handledningen. Om du redan har hämtat ner Phaser-repot så har du redan de här filerna. Titta bara i mappen *resources/tutorials*.

Du behöver ha lite, lite grundläggande kunskap i JavaScript.

Tänk också på at gå igenom [Getting Started Guide](/tutorials/getting-started);
den visar hur du laddar ner ramverket, sätter upp en lokal utvecklingsmiljö och ger dig en vink om strukturen på ett Phaser-projekt och kärnfunktionerna.

Om du har gått igenom startguiden har du redan laddar ner Phaser och har allt installerat och klart för att koda. Ladda ner resurserna för den här handledningen och packa upp dem i rotmappen på din webbserver.

Öppna sidan `part1.html` i din editor så tar vi en närmare titt på koden. Nedanför lite standard-HTML som läser in Phaser, ser kodstrukturen ut så här:

```javascript
var game = new Phaser.Game(800, 600, Phaser.AUTO, '', { preload: preload, create: create, update: update });

function preload() {
}

function create() {
}

function update() {
}
```
Rad 1 är blåser liv i Phaser genom att skapa en instans av objektet *Phaser.Game* och sparar den i en lokal variabel som heter 
'game'.
Att kalla variabeln 'game' är brukligt, men inget krav, och du kommer att se den i Phaser-exemplen.

De första två parametrarna är bredden och höjden på *canvas*-elementet som Phaser skapar. I det här fallet 800 x 600 pixlar.
Din spelvärld kan ha godtycklig storlek, men detta är upplösningen som spelet kommer att visas i. Den tredje parametern kan vara antingen *Phaser.CANVAS*, *Phaser.WEBGL* eller *Phaser.AUTO*.
Detta är den s.k. ritkontexten som du vill använda. Den parameter som rekommenderas är *Phaser.AUTO*, som automatiskt försöker använda WebGL, men om webbläsaren eller enheten inte stödjer det så faller Phaser tillbaks på Canvas.

Den fjäde parametern är en tom sträng, som är id på det DOM-element där du vill lägga in *canvas*-elementet som Phaser skapar. Eftersom vi lämnat den tom kommer *canvas*-elementet helt enkelt att läggas till i *body*. Den sista parametern är ett objekt med fyra referenser till Phasers viktigaste funktioner. Hur de användas förklaras noggrant här. Lägg märke till att objektet inte är obligatoriskt &ndash; Phaser stödjer ett fullständig system med tillstånd som låter dig dela upp din kod i mycket renare enstaka objekt. Men för en enkel kom igång-handledning som denna gör vi så här eftersom det här sättet låter oss prototypa snabbare.
