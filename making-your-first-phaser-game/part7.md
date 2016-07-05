## Del 7 &ndash; Stjärnljus

*[Engelskt original](http://phaser.io/tutorials/making-your-first-phaser-game/index) av [Alvin Ourrad and Richard Davey](https://twitter.com/photonstorm) den 7 december 2013   [@photonstorm](https://twitter.com/photonstorm)*

[YouTube-versionen hittar du här](http://youtube.com)

It's time to give our little game a purpose. Let's drop a sprinkling of stars into the scene and allow the player to collect them. To achieve this we'll create a new Group called 'stars' and populate it. In our create function we add the following code (this can be seen in [part8.js](../phaser_tutorial_02/part8.js)):

```javascript
    stars = game.add.group();

    stars.enableBody = true;

    //  Here we'll create 12 of them evenly spaced apart
    for (var i = 0; i < 12; i += 1) {
        //  Create a star inside of the 'stars' group
        var star = stars.create(i * 70, 0, 'star');

        //  Let gravity do its thing
        star.body.gravity.y = 6;

        //  This just gives each star a slightly random bounce value
        star.body.bounce.y = 0.7 + Math.random() * 0.2;
    }
```

The process is similar to when we created the platforms Group. Using a JavaScript 'for' loop we tell it to create 12 stars in our game. They have an x coordinate of `i * 70`, which means they will be evenly spaced out in the scene 70 pixels apart. As with the player we give them a gravity value so they'll fall down, and a bounce value so they'll bounce a little when they hit the platforms.

Bounce is a value between 0 (no bounce at all) and 1 (a full bounce). Ours will bounce somewhere between 0.7 and 0.9\. If we were to run the code like this the stars would fall through the bottom of the game. To stop that we need to check for their collision against the platforms in our update loop:

`game.physics.arcade.collide(stars, platforms);`

As well as doing this we will also check to see if the player overlaps with a star or not:

`game.physics.arcade.overlap(player, stars, collectStar, null, this);`

This tells Phaser to check for an overlap between the player and any star in the stars Group. If found then pass them to the 'collectStar' function:

```javascript
function collectStar (player, star) {
    // Removes the star from the screen
    star.kill();
}
```

Quite simply the star is killed, which removes it from display. Running the game now gives us a player that can dash about, jumping, bouncing off the platforms and collecting the stars that fall from above. Not bad for a few lines of hopefully mostly quite readable code :)

![image](http://phaser.io/content/tutorials/making-your-first-phaser-game/part8.png)

[Så här ser koden ut nu](../phaser_tutorial_02/part8.js).

# [<< Tillbaka till del 6](part6.md) [&ndash; Fortsätt till del 8 >>](part8.md)

## Vill du veta mer?
* API-länkar kommer här

## Referenser
[Källkodsfiler i original](https://github.com/photonstorm/phaser/raw/master/resources/tutorials/02%20Making%20your%20first%20game/phaser_tutorial_02.zip)

[Skriv ut sidan](https://gitprint.com/coderdojolund/phaser-tutorials/blob/master/making-your-first-phaser-game/part7.md)
