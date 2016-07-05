## Del 6 &ndash; Styra spelaren med tangentbordet

*[Engelskt original](http://phaser.io/tutorials/making-your-first-phaser-game/index) av [Alvin Ourrad and Richard Davey](https://twitter.com/photonstorm) den 7 december 2013   [@photonstorm](https://twitter.com/photonstorm)*

[YouTube-versionen hittar du här](https://www.youtube.com/playlist?list=PL39Sm336N_h-I3mGTtj3q--BtLWpH13sa)

Att kollidera är utmärkt och bra, men vi behöver verkligen få spelaren att röra sig.
Du funderar kanske på att gå till dokumentationen och söka upp hur man lägger till en händelselyssnare, men det behövs inte här.
Phaser har en inbyggd tangentbordshanterare, *keyboard*, och en av fördelarna med den är den här behändiga lilla funktionen:

`cursors = game.input.keyboard.createCursorKeys();`

Den förser objektet `cursors` med fyra egenskaper: *up*, *down*, *left* och *right*, som alla är objekt av typen `Phaser.Key`.
Sen är det bara bara att polla (läsa av) dem i vår `update`-loop:

```javascript
    //  Reset the player's velocity (movement)
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

Fast vi lagt till mycket kod bör den vara ganska läsbar.
Det första vi gör att att återställa sprajtens horisontella hastighet.
Sen kollar vi om vänster markörknapp är nertryckt.
Om den är det så sätter vi en negativ horisontell hastighet och startar löpanimeringen `left`.
Om spelaren håller ner `right` istället gör vi bokstavligen motsatsen.
Genom att återställa och sen sätta hastigheten på det här sättet, för varje ruta, skapar vi ett rörelsemönster av typen stanna/starta.

Spelarsprajten kommer att röra sig bara när en knapp hålls nere och stanna meddetsamma när den släpps. 
Phaser låter dig också skapa mer sammansatta rörelser med masströghet och acceleration, men det vi gjort så här långt ger oss effekten vi behöver för det här spelet.
Sista delen av knappkoden, *else*, sätter rutan till 4 om ingen knapp hålls nertryckt.
Ruta 4 i sprajtkartan är den där spelaren ser på dig, stillastående.

### Hoppa till den

Sista delen av koden lägger till möjligheten att hoppa.
Uppåtpil är vår hoppknapp och vi kollar om den är nertryckt.
Men vi kollar också om spelaren rör marken; annars skulle man kunna hoppa fast man är i luften.
Om båda villkoren är uppfyllda så ger vi en vertikal acceleration på 350 pixlar per sekund i kvadrat.
Spelaren kommer att ramla ner på marken automatiskt på grund av gravitationsvärdet som vi satte.
Med kontrollerna på plats har vi nu en spelvärld som vi kan utforska.
Ladda [part7.js](../phaser_tutorial_02/part7.js) och provspela.
Pröva att ändra på värdena som t.ex. talet 350 för hoppet till mindre eller större värden för att se vad effekten blir.

![image](http://phaser.io/content/tutorials/making-your-first-phaser-game/part7.png)

# [<< Tillbaka till del 5](part5.md) [&ndash; Fortsätt till del 7 >>](part7.md)

## Vill du veta mer?
* API-länkar kommer här

## Referenser
[Källkodsfiler i original](https://github.com/photonstorm/phaser/raw/master/resources/tutorials/02%20Making%20your%20first%20game/phaser_tutorial_02.zip)

[Skriv ut sidan](https://gitprint.com/coderdojolund/phaser-tutorials/blob/master/making-your-first-phaser-game/part6.md)
