## Del 5 &ndash; Kroppen och hastigheten: en värld av fysik

*[Engelskt original](http://phaser.io/tutorials/making-your-first-phaser-game/index) av [Alvin Ourrad and Richard Davey](https://twitter.com/photonstorm) den 7 december 2013   [@photonstorm](https://twitter.com/photonstorm)*

[YouTube-versionen hittar du här](http://youtube.com)

Phaser has support for a variety of different physics systems. It ships with Arcade Physics, Ninja Physics and P2.JS Full-Body Physics. For the sake of this tutorial we will be using the Arcade Physics system, which is simple and light-weight, perfect for mobile browsers. You'll notice in the code that we have to start the physics system running, and then for every sprite or Group that we wish to use physics on we enable them.

Once done the sprites gain a new body property, which is an instance of `ArcadePhysics.Body`. This represents the sprite as a physical body in Phaser's Arcade Physics engine. The body object has itself a lot of properties that we can play with. To simulate the effects of gravity on a sprite, it's as simple as writing this:

`player.body.gravity.y = 300;`

This is an arbitrary value, but logically, the higher the value, the heavier your object feels and the quicker it falls. If you add this to your code or run `part5.js` you will see that the player falls down without stopping, completely ignoring the ground we created earlier:

![image](http://phaser.io/content/tutorials/making-your-first-phaser-game/part5.png)

The reason for this is that we're not yet testing for collision between the ground and the player. We already told Phaser that our ground and ledges would be immovable. Had we not done that when the player collided with them it would stop for a moment and then everything would have collapsed. This is because unless told otherwise, the ground sprite is a moving physical object (also known as a dynamic body) and when the player hits it, the resulting force of the collision is applied to the ground, therefore, the two bodies exchange their velocities and ground starts falling as well.

So to allow the player to collide and take advantage of the physics properties we need to introduce a collision check in the update function:

```javascript
function update() {
    //  Collide the player and the stars with the platforms
    game.physics.arcade.collide(player, platforms);
}
```

The update function is called by the core game loop every frame. The Physics.collide function is the one that performs the magic. It takes two objects and tests for collision and performs separation against them. In this case we're giving it the player sprite and the platforms Group. It's clever enough to run collision against all Group members, so this one call will collide against the ground and both ledges. The result is a firm platform:

![image](http://phaser.io/content/tutorials/making-your-first-phaser-game/part6.png)

## Vill du veta mer?
* API-länkar kommer här

## Referenser
[Källkodsfiler i original](https://github.com/photonstorm/phaser/raw/master/resources/tutorials/02%20Making%20your%20first%20game/phaser_tutorial_02.zip)

[Skriv ut sidan](https://gitprint.com/coderdojolund/phaser-tutorials/blob/master/making-your-first-phaser-game/part5.md)
