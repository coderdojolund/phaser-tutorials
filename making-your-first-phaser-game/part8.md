## Del 8 &ndash; Finputsning

*[Engelskt original](http://phaser.io/tutorials/making-your-first-phaser-game/index) av [Alvin Ourrad and Richard Davey](https://twitter.com/photonstorm) den 7 december 2013   [@photonstorm](https://twitter.com/photonstorm)*

[YouTube-versionen hittar du här](http://youtube.com)

Vår slutjustering blir att lägga till poängräkning.
För att göra det använder vi ett `Phaser.Text`-objekt.
Här skapar vi två nya variabler, en för att spara aktuell poäng och en för själva textobjektet:

```javascript
var score = 0,
    scoreText;
```

`scoreText` sätts upp i funktionen `create`:

`scoreText = game.add.text(16, 16, 'score: 0', { fontSize: '32px', fill: '#000' });`

16&times;16 är koodinaterna där texten ska visas.
`score: 0` är startvärdet som ska visas och objektet efter innehåller en teckensnittsstorlek och fyllnadsfärg.
Genom att inte ange vilket teckensnitt vi vill använda så tar webbläsaren sitt standardteckensnitt, så på Windows blir det Arial.
Sen behöver vi ändra funktionen `collectStar` så att poängen ökar och texten uppdateras när spelaren fångar en stjärna.

```javascript
function collectStar (player, star) {
    // Removes the star from the screen
    star.kill();

    //  Add and update the score
    score += 10;
    scoreText.text = 'Score: ' + score;
}
```

Så 10 poäng läggs till för varje stjärna och `scoreText` uppdateras för att visa den nya summan. Om du kör `part9.html` ser du det färdiga spelet.

[Så här ser koden ut nu](../phaser_tutorial_02/part9.js).

![image](http://phaser.io/content/tutorials/making-your-first-phaser-game/part9.png)

### Avslutning

Du har nu lärt dig att skapa en sprajt med fysikegenskaper, att styra hur den rör sig och att få den att samverka med andra föremål i en liten spelvärld.
Det finns många saker du kan göra för att förbättra spelet; till exempel finns det ingen känsla av att spela klart eller någon spänning så här långt.
Varför inte lägga till några piggar som man måste undvika? 
Du kan skapa en ny `spikes`-grupp och känna av kollision med spelaren, men istället för att döda piggens sprajt så dödar du spelaren istället.
Eller, för att få ett mindre våldsamt spel, kan du göra det till en löptävling och utmana spelaren att samla upp stjärnorna på kortast möjliga tid. Vi har skickat med några extra bildfiler i ZIP-filen för att inspirera dig. 

Med hjälp av det du lärt dig i den här handledningen och de över 450 tillgängliga exemplen, bör du nu ha en stadig grund för ett kommande projekt. Men som alltid om du har frågor, behöver hjälp eller vill dela något du jobbat på så tveka inte att fråga om hjälp i forumet för Phaser.

# [<< Tillbaka till del 7](part7.md)

## Vill du veta mer?
* API-länkar kommer här

## Referenser
[Källkodsfiler i original](https://github.com/photonstorm/phaser/raw/master/resources/tutorials/02%20Making%20your%20first%20game/phaser_tutorial_02.zip)

[Skriv ut sidan](https://gitprint.com/coderdojolund/phaser-tutorials/blob/master/making-your-first-phaser-game/part8.md)
