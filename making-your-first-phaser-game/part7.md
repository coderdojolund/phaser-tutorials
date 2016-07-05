## Del 7 &ndash; Stjärnljus

*[Engelskt original](http://phaser.io/tutorials/making-your-first-phaser-game/index) av [Alvin Ourrad and Richard Davey](https://twitter.com/photonstorm) den 7 december 2013   [@photonstorm](https://twitter.com/photonstorm)*

[YouTube-versionen hittar du här](http://youtube.com)

Det är dags att ge vårt lilla spel ett syfte.
Vi strör stjärnor på scenen och låter spelaren samla upp dem.
För att uppnå det behöver skapa en ny `Group` som heter `stars` och fylla den. I vår `create`-funktion lägger vi till följande kod; du kan se koden i [part8.js](../phaser_tutorial_02/part8.js):

```javascript
    var i, 
        star = game.add.group();

    stars.enableBody = true;

    //  Here we'll create 12 of them evenly spaced apart
    for (i = 0; i < 12; i += 1) {
        //  Create a star inside of the 'stars' group
        star = stars.create(i * 70, 0, 'star');

        //  Let gravity do its thing
        star.body.gravity.y = 6;

        //  This just gives each star a slightly random bounce value
        star.body.bounce.y = 0.7 + Math.random() * 0.2;
    }
```

Sättet är samma som när vi skapade `platforms`-gruppen. Med en `for`-slinga i JavaScript ber vi den att skapa 12 stjärnor i vårt spel.
De har *x*-koordinat `i * 70`, vilket betyder att de blir jämnt fördelade med 70 pixlar mellan.
Precis som med spelaren ger vi dem ett gravitationsvärde så att de ramlar ner, och ett studsvärde så att de studsar lite när de träffar avsatserna.

Bounce (studs) är ett värde mellan 0 (ingen studs) och 1 (fullständig studs).
Våra kommer att studsa någonstans mellan 0,7 och 0,9.
Om vi skulle köra koden som den är nu så skulle stjärnorna falla igenom spelets underkant. *Testa gärna.* För att hindra det behöver vi känna av kollision med `platforms` i vår `update`-slinga:

`game.physics.arcade.collide(stars, platforms);`

Förutom att göra det ska vi också testa om spelaren överlappar en stjärna eller inte:

`game.physics.arcade.overlap(player, stars, collectStar, null, this);`

Detta ber Phaser att kolla överlapp mellan spelaren och någon av stjärnorna i gruppen `stars`.
Om det är något överlapp så skicka vidare till funktionen `collectStar`:

```javascript
function collectStar (player, star) {
    // Removes the star from the screen
    star.kill();
}
```

Stjärnan dödas helt enkelt, vilket tar bort den från skärmen.
Kör man spelet nu så har vi en spelare som kan skutta omkring, hoppa, studsa från avsatserna och samla stjärnorna som faller från ovan. Inte så illa för få rader med förhoppningsvis ganska läslig kod.

![image](http://phaser.io/content/tutorials/making-your-first-phaser-game/part8.png)

# [<< Tillbaka till del 6](part6.md) [&ndash; Fortsätt till del 8 >>](part8.md)

## Vill du veta mer?
* API-länkar kommer här

## Referenser
[Källkodsfiler i original](https://github.com/photonstorm/phaser/raw/master/resources/tutorials/02%20Making%20your%20first%20game/phaser_tutorial_02.zip)

[Skriv ut sidan](https://gitprint.com/coderdojolund/phaser-tutorials/blob/master/making-your-first-phaser-game/part7.md)
