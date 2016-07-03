## Del 4 &ndash; Grupper

*[Engelskt original](http://phaser.io/tutorials/making-your-first-phaser-game/inddex) av [Alvin Ourrad and Richard Davey](https://twitter.com/photonstorm) den 7 december 2013   [@photonstorm](https://twitter.com/photonstorm)*

[YouTube-versionen hittar du här](http://youtube.com)

Phaser-grupper är mycket kraftfulla. Som namnet antyder låter de dig gruppera ihop liknande objekt och styra dem som en sammanhållen enhet. Man kan också känna av kollisioner mellan grupper och i det här spelet ska vi använda två olika grupper; en av grupperna, `platforms`, skapade vi i [del 3](del3.md).

`platforms = game.add.group();`

Precis som med sprajtar skapar `game.add` vårt `Group`-objekt.
Vi sparar den i en ny lokal variabel som heter `platforms`.
När den skapats kan vi lägga till objekt i den.
Först kommer marken.
Den ligger längst ner på spelytan och använder `ground`-bilden som vi laddade innan.
Marken skalas så att den fyller ut bredden på spelet.
Till slut sätter vi markens `immovable`-egenskap till `true`. Om vi inte hade gjort det skulle marken flytta sig när spelaren krockar med den; mer om detta i fysikavsnittet i [nästa del](part5.md).

Med marken på plats skapar vi två mindre avsatser som man kan hoppa till, med exakt samma metod som för marken.

### Redo, spelare ett

Skapa en ny lokal variabel som heter `player` och lägg till den här koden i funktionen `create`. Du kan se koden i `part5.js`:

```javascript
    // The player and its settings
    player = game.add.sprite(32, game.world.height - 150, 'dude');

    //  We need to enable physics on the player
    game.physics.arcade.enable(player);

    //  Player physics properties. Give the little guy a slight bounce.
    player.body.bounce.y = 0.2;
    player.body.gravity.y = 300;
    player.body.collideWorldBounds = true;

    //  Our two animations, walking left and right.
    player.animations.add('left', [0, 1, 2, 3], 10, true);
    player.animations.add('right', [5, 6, 7, 8], 10, true);
```
Detta skapar en ny sprajt som heter `player` placerad 32x150 pixlar från spelets underkant.
Vi säger åt den att använda resursen `dude` som vi laddat innan.
Om du går tillbaks och tittar på funktionen `preload` ser du att `dude` laddades som en sprajtkarta, inte som bild. 
Detta eftersom den innehåller animeringsrutor.
Så här ser den fullständiga sprajtkartan ut:

![image](http://phaser.io/content/tutorials/making-your-first-phaser-game/dude.png)

Du kan se totalt nio rutor, fyra för att springa åt höger, en för att se mot kameran och fyra för att springa åt höger. Lägg märke till att Phaser har stöd för att spegelvända animeringsrutor men i den här handledningen kör vi det gamla sättet.

Vi definierar två animeringar som heter `left` och `right`.
`left`-animeringen använder rutorna 0, 1, 2 och 3 och den kör 10 rutor per sekund (FPS).

Parametern `true` betyder att animeringen ska loopa.
Detta är vår vanliga slinga för löpanimeringen och vi upprepar den för löpning åt motsatta hållet. 
När vi satt animeringen skapar vi några fysikegenskaper.

# [<< Tillbaka till del 3](part3.md) [&ndash; Fortsätt till del 5 >>](part5.md)

## Vill du veta mer?
* 

## Referenser
[Källkodsfiler i original](https://github.com/photonstorm/phaser/raw/master/resources/tutorials/02%20Making%20your%20first%20game/phaser_tutorial_02.zip)

[Skriv ut sidan](https://gitprint.com/coderdojolund/phaser-tutorials/blob/master/making-your-first-phaser-game/part3.md)
