## Del 5 &ndash; Kroppen och hastigheten: en värld av fysik

*[Engelskt original](http://phaser.io/tutorials/making-your-first-phaser-game/index) av [Alvin Ourrad and Richard Davey](https://twitter.com/photonstorm) den 7 december 2013   [@photonstorm](https://twitter.com/photonstorm)*

[YouTube-versionen hittar du här](https://www.youtube.com/playlist?list=PL39Sm336N_h-I3mGTtj3q--BtLWpH13sa)

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
Om du lägger till detta i din kod eller kör [part5.js](../phaser_tutorial_02/part5.js) 
kommer du att se att spelaren faller neråt utan att stanna utan hänsyn till marken vi skapade tidigare:

![image](http://phaser.io/content/tutorials/making-your-first-phaser-game/part5.png)

Orsaken till det är att vi ännu inte känner av kollisioner mellan marken och spelaren.
Vi har redan sagt åt Phaser att vår mark och avsatserna ska vara oflyttbara.
Hade vi inte gjort det när spelaren krockade med dem så skulle den ha stannat ett ögonblick och sen skulle allting ha rasat.
Detta eftersom marksprajten, om inget annat sagts, är ett rörligt fysiskt föremål (också kallat dynamisk kropp) och när spelaren träffar den så verkar den resulterande kraften på marken; därför utbyter de kropparna rörelseenergi och marken börjar också att falla.

Så för att låta spelaren kollidera och dra nytta av fysikegenskaperna behöver vi införa krockdetektering i `update`-funktionen:

```javascript
function update() {
    //  Collide the player and the stars with the platforms
    game.physics.arcade.collide(player, platforms);
}
```

Funktionen `update` anropas av spelets huvudloop varje ruta. Funktionen `Physics.collide` står för magin. 
Den tar två föremål och upptäcker krockar och får dem att studsa. I det här fallet ger vi funktionen spelarens sprajt och gruppen `platforms`. `collide` är smart nog att upptäcka kollision med alla medlemmar i gruppen, så det här (enda) anropet sköter krockar med marken och båda avsatserna. Resultatet är en orörlig plattform:

![image](http://phaser.io/content/tutorials/making-your-first-phaser-game/part6.png)

[Så här ser koden ut nu](../phaser_tutorial_02/part6.js).

# [<< Tillbaka till del 4](part4.md) [&ndash; Fortsätt till del 6 >>](part6.md)

## Vill du veta mer?
* API-länkar kommer här

## Referenser
[Källkodsfiler i original](https://github.com/photonstorm/phaser/raw/master/resources/tutorials/02%20Making%20your%20first%20game/phaser_tutorial_02.zip)

[Skriv ut sidan](https://gitprint.com/coderdojolund/phaser-tutorials/blob/master/making-your-first-phaser-game/part5.md)
