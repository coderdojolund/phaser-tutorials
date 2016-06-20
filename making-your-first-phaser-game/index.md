# Del 1 -- Inledning

_By [Alvin Ourrad and Richard Davey](https://twitter.com/photonstorm)_ on 7th December 2013   [@photonstorm](https://twitter.com/photonstorm)

![image](http://phaser.io/content/tutorials/making-your-first-phaser-game/tutorial_header.png)

Welcome to the our first tutorial on Making a Game with Phaser. Here we will learn how to create a small game involving a player running and jumping around platforms collecting stars. While going through this process we'll explain some of the core features of the framework.

### What is Phaser?

Phaser is an HTML5 game framework which aims to help developers make powerful, cross-browser HTML5 games really quickly and, unlike some others, has solely been built to work with the mobile browsers. The only browser requirement is the support of the canvas tag. It also borrows a lot from Flixel.

## Requirements

[Download the source files](https://github.com/photonstorm/phaser/raw/master/resources/tutorials/02%20Making%20your%20first%20game/phaser_tutorial_02.zip) and assets that go with this tutorial. If you have already checked out the Phaser repository from github then you have these files already. Just look in the resources/tutorials folder.

You need to have a very, very basic knowledge of JavaScript.

Also make sure you go through the [Getting Started Guide](/tutorials/getting-started), it will show you how to download the framework, set up a local development environment, and give you a glimpse of the structure of a Phaser project and its core functions.

If you've gone through the Getting Started Guide you will have downloaded Phaser and got everything set-up and ready to code. Download the resources for this tutorial and unzip them into your web root.

Open the `part1.html` page in your editor of choice and let's have a closer look at the code. After a little boilerplate HTML that includes Phaser the code structure looks like this:

```javascript
var game = new Phaser.Game(800, 600, Phaser.AUTO, '', { preload: preload, create: create, update: update });

function preload() {
}

function create() {
}

function update() {
}
```
Line 1 is where you bring Phaser to life by creating an instance of a Phaser.Game object and assigning it to a local variable called 'game'. Calling it 'game' is a common practice, but not a requirement, and this is what you will find in the Phaser examples.

The first two parameters are the width and the height of the canvas element that Phaser will create. In this case 800 x 600 pixels. Your game world can be any size you like, but this is the resolution the game will display in. The third parameter can be either Phaser.CANVAS, Phaser.WEBGL, or Phaser.AUTO. This is the rendering context that you want to use. The recommended parameter is Phaser.AUTO which automatically tries to use WebGL, but if the browser or device doesn't support it it'll fall back to Canvas.

The fourth parameter is an empty string, this is the id of the DOM element in which you would like to insert the canvas element that Phaser creates. As we've left it blank it will simply be appended to the body. The final parameter is an object containing four references to Phasers essential functions. Their use is thoroughly explained here. Note that this object isn't required - Phaser supports a full State system allowing you to break your code into much cleaner single objects. But for a simple Getting Started guide such as this we'll use this approach as it allows for faster prototyping.
