## Del 8 &ndash; Finputsning

*[Engelskt original](http://phaser.io/tutorials/making-your-first-phaser-game/index) av [Alvin Ourrad and Richard Davey](https://twitter.com/photonstorm) den 7 december 2013   [@photonstorm](https://twitter.com/photonstorm)*

[YouTube-versionen hittar du här](http://youtube.com)

The final tweak we'll make is to add a score. To do this we'll make use of a Phaser.Text object. Here we create two new variables, one to hold the actual score and the text object itself:

```javascript
var score = 0;
var scoreText;
```

The scoreText is set-up in the create function:

`scoreText = game.add.text(16, 16, 'score: 0', { fontSize: '32px', fill: '#000' });`

16&times;16 is the coordinate to display the text at. 'score: 0' is the default string to display and the object that follows contains a font size and fill colour. By not specifying which font we'll actually use the browser will default, so on Windows it will be Arial. Next we need to modify the collectStar function so that when the player picks-up a star their score increases and the text is updated to reflect this:

```javascript
function collectStar (player, star) {
    // Removes the star from the screen
    star.kill();

    //  Add and update the score
    score += 10;
    scoreText.text = 'Score: ' + score;
}
```

So 10 points are added for every star and the scoreText is updated to show this new total. If you run part9.html you will see the final game.
[Så här ser koden ut nu](../phaser_tutorial_02/part9.js).

![image](http://phaser.io/content/tutorials/making-your-first-phaser-game/part9.png)

### Conclusion

You have now learned how to create a sprite with physics properties, to control its motion and to make it interact with other objects in a small game world. There are lots more things you can do to enhance this, for example there is no sense of completion or jeopardy yet. Why not add some spikes you must avoid? You could create a new 'spikes' group and check for collision vs. the player, only instead of killing the spike sprite you kill the player instead. Or for a non-violent style game you could make it a speed-run and simply challenge them to collect the stars as quickly as possible. We've included a few extra graphics in the zip file to help inspire you.

With the help of what you have learned in this tutorial and the 450+ examples available to you, you should now have a solid foundation for a future project. But as always if you have questions, need advice or want to share what you've been working on then feel free to ask for help in the Phaser forum.

# [<< Tillbaka till del 7](part7.md)

## Vill du veta mer?
* API-länkar kommer här

## Referenser
[Källkodsfiler i original](https://github.com/photonstorm/phaser/raw/master/resources/tutorials/02%20Making%20your%20first%20game/phaser_tutorial_02.zip)

[Skriv ut sidan](https://gitprint.com/coderdojolund/phaser-tutorials/blob/master/making-your-first-phaser-game/part8.md)
