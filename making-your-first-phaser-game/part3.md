## Del 3 &ndash; Bygga världen

*[Engelskt original](http://phaser.io/tutorials/making-your-first-phaser-game/index) av [Alvin Ourrad and Richard Davey](https://twitter.com/photonstorm) den 7 december 2013   [@photonstorm](https://twitter.com/photonstorm)*

[YouTube-versionen hittar du här](http://youtube.com)

Under the hood game.add.sprite is creating a new Phaser.Sprite object and adding the sprite to the “game world”. This world is where all your objects live, it can be compared to the Stage in Actionscript3.

Note: The game world has no fixed size and extends infinitely in all directions, with `0, 0` being the center of it. For convenience Phaser places `0, 0` at the top left of your game for you, but by using the built-in Camera you can move around as needed.

The world class can be accessed via game.world and comes with a lot of handy methods and properties to help you distribute your objects inside the world. It includes some simple properties like game.world.height, but also some more advanced ones that we will use in another tutorial.

For now let's build up the scene by adding a background and platforms. Here is the updated create function:
```javascript
var platforms;

function create() {

    //  We're going to be using physics, so enable the Arcade Physics system
    game.physics.startSystem(Phaser.Physics.ARCADE);

    //  A simple background for our game
    game.add.sprite(0, 0, 'sky');

    //  The platforms group contains the ground and the 2 ledges we can jump on
    platforms = game.add.group();

    //  We will enable physics for any object that is created in this group
    platforms.enableBody = true;

    // Here we create the ground.
    var ground = platforms.create(0, game.world.height - 64, 'ground');

    //  Scale it to fit the width of the game (the original sprite is 400x32 in size)
    ground.scale.setTo(2, 2);

    //  This stops it from falling away when you jump on it
    ground.body.immovable = true;

    //  Now let's create two ledges
    var ledge = platforms.create(400, 400, 'ground');

    ledge.body.immovable = true;

    ledge = platforms.create(-150, 250, 'ground');

    ledge.body.immovable = true;

}
```

If you run this, which you'll find as `part4.html` in the tutorial zip file, you should see a much more game-like scene:

![image](http://phaser.io/content/tutorials/making-your-first-phaser-game/part4.png)

The first part is the same as the star sprite we had before, only instead we changed the key to 'sky' and it has displayed our sky background instead. This is an 800x600 PNG that fills the game screen.

# [<< Tillbaka till del 2](part2.md) [&ndash; Fortsätt till del 4 >>](part4.md)

## Att läsa på
* [Mer om `Phaser.Loader.image` hittar du här](http://phaser.io/docs/2.5.0/Phaser.Loader.html#image)
* [Mer om `Phaser.Loader.image` hittar du här](http://phaser.io/docs/2.5.0/Phaser.Loader.html#spritesheet)

## Referenser
[Källkodsfiler i original](https://github.com/photonstorm/phaser/raw/master/resources/tutorials/02%20Making%20your%20first%20game/phaser_tutorial_02.zip)

[Skriv ut sidan](https://gitprint.com/coderdojolund/phaser-tutorials/blob/master/making-your-first-phaser-game/part3.md)
