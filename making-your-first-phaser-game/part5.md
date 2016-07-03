## Del 5 &ndash; Kroppen och hastigheten: en värld av fysik

*[Engelskt original](http://phaser.io/tutorials/making-your-first-phaser-game/index) av [Alvin Ourrad and Richard Davey](https://twitter.com/photonstorm) den 7 december 2013   [@photonstorm](https://twitter.com/photonstorm)*

[YouTube-versionen hittar du här](http://youtube.com)

Phaser stödjer ett antal olika fysiksystem.
Som standard ingår *Arcade Physics*, *Ninja Physics* and *P2.JS Full-Body Physics*.
I den här handledningen kommer vi att använda systemet *Arcade Physics*, wom är enkelt och lättviktigt, perfekt för mobila webbläsare.
I koden kommer du att märka att vi måste starta fysiksystemet och sen behöver vi aktivera det för varje sprajt eller grupp som vi vill tillämpa fysik på.

När detta är gjort får sprajterna en ny egenskap, `body`, som är en instans av `ArcadePhysics.Body`. 
Detta representerar sprajten som en fysikalisk kropp i Phasers *Archade Physics*-motor.
Själva `body`-objektet har många egenskaper som vi kan leka med.
För att simulera gravitationens inverkan på en sprajt är det helt enkelt bara att skriva så här:

`player.body.gravity.y = 300;`

Detta (300) är ett godtyckligt värde, men logiskt nog ju högre värde, desto tyngre känns föremålet och det faller fortare.
Om du lägger till detta i din kod eller kör `part5.js` 
kommer du att se att spelaren faller neråt utan att stanna utan hänsyn till marken vi skapade tidigare:

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
