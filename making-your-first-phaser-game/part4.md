## Del 3 &ndash; Grupper

*[Engelskt original](http://phaser.io/tutorials/making-your-first-phaser-game/index) av [Alvin Ourrad and Richard Davey](https://twitter.com/photonstorm) den 7 december 2013   [@photonstorm](https://twitter.com/photonstorm)*

[YouTube-versionen hittar du här](http://youtube.com)

Groups are really powerful. As their name implies they allow you to group together similar objects and control them all as one single unit. You can also check for collision between Groups, and for this game we'll be using two different Groups, one of which is created in the code above for the platforms.

`platforms = game.add.group();`

As with sprites `game.add` creates our Group object. We assign it to a new local variable called `platforms`. Now created we can add objects to it. First up is the ground. This is positioned at the bottom of the game and uses the 'ground' image loaded earlier. The ground is scaled to fill the width of the game. Finally we set its `immovable` property to true. Had we not done this the ground would move when the player collides with it (more on this in the Physics section).

With the ground in place we create two smaller ledges to jump on to using the exact same technique as for the ground.

### Ready Player One

Create a new local variable called `player` and add the following code to the create function. You can see this in `part5.html`:

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

This creates a new sprite called 'player', positioned at 32 pixels by 150 pixels from the bottom of the game. We're telling it to use the 'dude' asset previously loaded. If you glance back to the preload function you'll see that 'dude' was loaded as a sprite sheet, not an image. That is because it contains animation frames. This is what the full sprite sheet looks like:

![image](http://phaser.io/content/tutorials/making-your-first-phaser-game/dude.png)

You can see 9 frames in total, 4 for running left, 1 for facing the camera and 4 for running right. Note: Phaser supports flipping sprites to save on animation frames, but for the sake of this tutorial we'll keep it old school.

We define two animations called 'left' and 'right'. The 'left' animation uses frames 0, 1, 2 and 3 and runs at 10 frames per second. The 'true' parameter tells the animation to loop. This is our standard run-cycle and we repeat it for running in the opposite direction. With the animations set we create a few physics properties.

# [<< Tillbaka till del 3](part3.md) [&ndash; Fortsätt till del 5 >>](part5.md)

## Vill du veta mer?
* 

## Referenser
[Källkodsfiler i original](https://github.com/photonstorm/phaser/raw/master/resources/tutorials/02%20Making%20your%20first%20game/phaser_tutorial_02.zip)

[Skriv ut sidan](https://gitprint.com/coderdojolund/phaser-tutorials/blob/master/making-your-first-phaser-game/part3.md)
