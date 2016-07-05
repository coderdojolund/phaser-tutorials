## Del 3 &ndash; Bygga världen

*[Engelskt original](http://phaser.io/tutorials/making-your-first-phaser-game/index) av [Alvin Ourrad and Richard Davey](https://twitter.com/photonstorm) den 7 december 2013   [@photonstorm](https://twitter.com/photonstorm)*

[YouTube-versionen hittar du här](https://www.youtube.com/playlist?list=PL39Sm336N_h-I3mGTtj3q--BtLWpH13sa)

Under täcket skapar 
`game.add.sprite` ett nytt `Phaser.Sprite`-objekt och lägger till sprajten i &raquo;spelvärlden&laquo;.
Alla dina objekt lever i den här världen; den liknar Stage i Actionscript3. 

Obs! Spelvärlden har ingen fast storlek och fortsätter obegränsat i alla riktningar med `0, 0` i centrum.
För enkelhets skull låter Phaser koordinaterna `0, 0` vara övre vänstra hörnet i spelet men genom att använda det inbyggda `Camera`-objektet kan du flytta runt efter behov.

Världsklassen kommer man åt via `game.world` och den har många behändiga metoder och egenskaper som hjälper till att fördela ut dina objekt inuti världen. Den har några enkla egenskaper som `game.world.height` men också några mer avancerade som vi kommer att använda i en annan handledning.

Men nu bygger vi upp scenen genom att lägga till en bakgrund och avsatser. Här är den uppdaterade `create`-funktionen.
```javascript
var platforms;

function create() {
    var ground,
        ledge;

    //  We're going to be using physics, so enable the Arcade Physics system
    game.physics.startSystem(Phaser.Physics.ARCADE);

    //  A simple background for our game
    game.add.sprite(0, 0, 'sky');

    //  The platforms group contains the ground and the 2 ledges we can jump on
    platforms = game.add.group();

    //  We will enable physics for any object that is created in this group
    platforms.enableBody = true;

    // Here we create the ground.
    ground = platforms.create(0, game.world.height - 64, 'ground');

    //  Scale it to fit the width of the game (the original sprite is 400x32 in size)
    ground.scale.setTo(2, 2);

    //  This stops it from falling away when you jump on it
    ground.body.immovable = true;

    //  Now let's create two ledges
    ledge = platforms.create(400, 400, 'ground');

    ledge.body.immovable = true;

    ledge = platforms.create(-150, 250, 'ground');

    ledge.body.immovable = true;
}
```
Om du kör det här, som finns i [part4.js](../phaser_tutorial_02/part4.js) i ZIP-filen som hör till handledningen, bör du se en mycket mer spelliknande scen:

![image](http://phaser.io/content/tutorials/making-your-first-phaser-game/part4.png)

Första delen är samma som stjärnsprajten som vi hade innan, men vi har istället ändrat nyckeln till `'sky'` och vår himmelsbakgrund visas istället. Detta är en PNG-fil på 800&times;600 pixlar som fyller spelskärmen.

# [<< Tillbaka till del 2](part2.md) [&ndash; Fortsätt till del 4 >>](part4.md)

## Vill du veta mer?
* [game.world.height](http://phaser.io/docs/2.5.0/Phaser.World.html#height)
* [game.physics.startSystem](http://phaser.io/docs/2.5.0/Phaser.Physics.html#startSystem)
* [game.add.group](http://phaser.io/docs/2.5.0/Phaser.World.html#add)
* [platforms.enableBody](http://phaser.io/docs/2.5.0/Phaser.Group.html#enableBody)
* [platforms.create](http://phaser.io/docs/2.5.0/Phaser.Group.html#create)
* [platforms.scale.setTo](http://phaser.io/docs/2.5.0/Phaser.Group.html#scale)
* [platforms.body.immovable](http://phaser.io/docs/2.4.4/Phaser.Physics.Arcade.Body.html#immovable)

## Referenser
[Källkodsfiler i original](https://github.com/photonstorm/phaser/raw/master/resources/tutorials/02%20Making%20your%20first%20game/phaser_tutorial_02.zip)

[Skriv ut sidan](https://gitprint.com/coderdojolund/phaser-tutorials/blob/master/making-your-first-phaser-game/part3.md)
