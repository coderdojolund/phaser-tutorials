## Del 6 &ndash; Styra spelaren med tangentbordet

*[Engelskt original](http://phaser.io/tutorials/making-your-first-phaser-game/index) av [Alvin Ourrad and Richard Davey](https://twitter.com/photonstorm) den 7 december 2013   [@photonstorm](https://twitter.com/photonstorm)*

[YouTube-versionen hittar du här](http://youtube.com)

Colliding is all good and well, but we really need the player to move. You would probably think of heading to the documentation and searching about how to add an event listener, but that is not necessary here. Phaser has a built-in Keyboard manager and one of the benefits of using that is this handy little function:

`cursors = game.input.keyboard.createCursorKeys();`

This populates the cursors object with four properties: up, down, left, right, that are all instances of Phaser.Key objects. Then all we need to do is poll these in our update loop:

```javascript
    //  Reset the players velocity (movement)
    player.body.velocity.x = 0;

    if (cursors.left.isDown) {
        //  Move to the left
        player.body.velocity.x = -150;
        player.animations.play('left');
    } else if (cursors.right.isDown) {
        //  Move to the right
        player.body.velocity.x = 150;
        player.animations.play('right');
    } else {
        //  Stand still
        player.animations.stop();
        player.frame = 4;
    }

    //  Allow the player to jump if they are touching the ground.
    if (cursors.up.isDown && player.body.touching.down) {
        player.body.velocity.y = -350;
    }
```

Although we've added a lot of code it should all be pretty readable. The first thing we do is reset the horizontal velocity on the sprite. Then we check to see if the left cursor key is held down. If it is we apply a negative horizontal velocity and start the 'left' running animation. If they are holding down 'right' instead we literally do the opposite. By clearing the velocity and setting it in this manner, every frame, it creates a 'stop-start' style of movement.

The player sprite will move only when a key is held down and stop immediately they are not. Phaser also allows you to create more complex motions, with momentum and acceleration, but this gives us the effect we need for this game. The final part of the key check sets the frame to 4 if no keyis held down. Frame 4 in the sprite sheet is the one of the player looking at you, idle.

### Jump to it

The final part of the code adds the ability to jump. The up cursor is our jump key and we test if that is down. However we also test if the player is touching the floor, otherwise they could jump while in mid-air. If both of these conditions are met we apply a vertical velocity of 350 px/sec sq. The player will fall to the ground automatically because of the gravity value we applied to it. With the controls in place we now have a game world we can explore. Load up [part7.js](../phaser_tutorial_02/part7.js) and have a play. Try tweaking values like the 350 for the jump to lower and higher values to see the effect it will have.

![image](http://phaser.io/content/tutorials/making-your-first-phaser-game/part7.png)

# [<< Tillbaka till del 5](part5.md) [&ndash; Fortsätt till del 7 >>](part7.md)

## Vill du veta mer?
* API-länkar kommer här

## Referenser
[Källkodsfiler i original](https://github.com/photonstorm/phaser/raw/master/resources/tutorials/02%20Making%20your%20first%20game/phaser_tutorial_02.zip)

[Skriv ut sidan](https://gitprint.com/coderdojolund/phaser-tutorials/blob/master/making-your-first-phaser-game/part6.md)
