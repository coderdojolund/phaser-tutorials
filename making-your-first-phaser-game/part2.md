## Part 2 - Loading Assets


*Av [Alvin Ourrad and Richard Davey](https://twitter.com/photonstorm) den 7 december 2013   [@photonstorm](https://twitter.com/photonstorm)*

Let's load the assets we need for our game. You do this by putting calls to game.load inside of a function called preload. Phaser will automatically look for this function when it starts and load anything defined within it.

Currently the `preload` function is empty. Change it to:

```javascript
    game.load.image('sky', 'assets/sky.png');
    game.load.image('ground', 'assets/platform.png');
    game.load.image('star', 'assets/star.png');
    game.load.spritesheet('dude', 'assets/dude.png', 32, 48);
```

This will load in 4 assets: 3 images and a sprite sheet. It may appear obvious to some of you, but I would like to point out the first parameter, also known as the asset key. This string is a link to the loaded asset and is what you'll use in your code when creating sprites. You're free to use any valid JavaScript string as the key.

### Create a Sprite

In order to add a sprite to our game place the following code in the create function:

`game.add.sprite(0, 0, 'star');`

If you bring up the page in a browser you should now see a black game screen with a single star sprite in the top left corner:

![image](http://phaser.io/content/tutorials/making-your-first-phaser-game/part3.png)

The order in which items are rendered in the display matches the order in which you create them. So if you wish to place a background behind the star sprite you would need to ensure that it was added as a sprite first, before the star.
