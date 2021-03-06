## Del 2 &ndash; Ladda resurser

*[Engelskt original](http://phaser.io/tutorials/making-your-first-phaser-game/index) av [Alvin Ourrad and Richard Davey](https://twitter.com/photonstorm) den 7 december 2013   [@photonstorm](https://twitter.com/photonstorm)*

[YouTube-versionen hittar du här](https://www.youtube.com/playlist?list=PL39Sm336N_h-I3mGTtj3q--BtLWpH13sa)

Nu laddar vi resurserna som behövs för vårt spel. Detta gör vi med anrop till `game.load` inuti en funktion som heter `preload`.
Phaser letar automatiskt efter den här funktionen vid start och laddar allt som definieras i den.

Just nu är funktionen `preload` tom. Ändra den till
```javascript
    game.load.image('sky', 'assets/sky.png');
    game.load.image('ground', 'assets/platform.png');
    game.load.image('star', 'assets/star.png');
    game.load.spritesheet('dude', 'assets/dude.png', 32, 48);
```

Detta laddar in fyra resurser: tre bilder och en sprajtkarta. Det kanske är uppenbart för vissa av er, men jag vill lyfta fram den första parametern, som kallas resursnyckeln. Den här strängen är länken till den inlästa resursen och det är den du använder i din kod när du skapar sprajtar. Använd en giltig JavaScript-sträng som nyckel.

### Skapa en sprajt

För att skapa en sprajt i vårt spel lägger vi den här koden i funktionen `create`:

`game.add.sprite(0, 0, 'star');`

Om du tar upp sidan i en webbläsare bör du nu se en svart skärm med en enda stjärnsprajt i övre vänstra hörnet:

![image](http://phaser.io/content/tutorials/making-your-first-phaser-game/part3.png)

Ordningen som elementen visas på skärmen är samma som ordningen som du skapar dem. Så om du vill lägga en bakgrund bakom stjärnsprajten behöver du försäkra dig om att den lades till som en sprajt först, före stjärnan.

[Så här ser koden ut nu](../phaser_tutorial_02/part3.js).

# [<< Tillbaka till del 1 ](index.md) [&ndash; Fortsätt till del 3 >>](part3.md)

## Vill du veta mer?
* [`Phaser.Loader.image`](http://phaser.io/docs/2.5.0/Phaser.Loader.html#image)
* [`Phaser.Loader.spritesheet`](http://phaser.io/docs/2.5.0/Phaser.Loader.html#spritesheet)
* [`Phaser.game.add`](http://phaser.io/docs/2.4.6/Phaser.Game.html#add)

## Referenser
[Källkodsfiler i original](https://github.com/photonstorm/phaser/raw/master/resources/tutorials/02%20Making%20your%20first%20game/phaser_tutorial_02.zip)

[Skriv ut sidan](https://gitprint.com/coderdojolund/phaser-tutorials/blob/master/making-your-first-phaser-game/part2.md)
