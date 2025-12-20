# Simple Platformer



```python
for i in range(100):
    mobs.spawn(CHICKEN, pos(0, 10, 0))
```

```template
scene.setBackgroundColor(11)
tiles.setTilemap(tilemap`level`)
```

## Welcome @unplugged

Now let's take a look at the [__*sidescrolling*__](#scrolld "games that are viewed from the side, with most of the action happening horizontally") 
[__*platformer*__](#plat "games that rely on jump and run as their main mechanic").  

This kind of game peeks in on the action from the side, using "jump" and "run"
as the main mechanic.  

By the time you finish this set of tutorials, you should know all you need 
to make a fun and engaging arcade game worth sharing.

![Our first platformer](/static/skillmaps/platformer/platformer1.gif "Look what we're about to learn today!")


## Create the player

The first thing any good platformer needs is a main character. 🐒

In Arcade, our characters are [__*sprites*__](#sprote "2-D images that move on the screen").  
We'll want to create our main sprite and get it moving before we do anything else. 
<hr>

🔲 From the ``||sprites:Sprites||`` category, drag the ``||variables:set [mySprite] to sprite [ ] of kind [Player]||`` 
block to the end of the ``||loops:on start||`` container.

🔲 Click on the grey box in the middle of your
 ``||variables:set [mySprite] to sprite [ ] of kind [Player]||`` block
 to open the sprite editor.  From there, you can switch over to "Gallery"
 and choose a pre-drawn character.
<hr/>
>>*Tip: Don't like any of the predrawn characters? Stay in the "Editor"
and create one of your own*!


```blocks
scene.setBackgroundColor(11)
tiles.setTilemap(tilemap`level`)
// @highlight
let mySprite = sprites.create(img`
. . . . . f f f f f . . . . . . 
. . . . f e e e e e f . . . . . 
. . . f d d d d d e e f . . . . 
. . f f f d d f f d e f f . . . 
. c d d e e d d d d e d d f . . 
. c c d d d d c d d e d f f f . 
. c d c c c c d d d e d f b d f 
. . c d d d d d d e e f f d d f 
. . . c d d d d e e f f e f f f 
. . . . f f f e e f e e e f . . 
. . . . f e e e e e e e f f f . 
. . . f e e e e e e f f f e f . 
. . f f e e e e f f f f f e f . 
. f b d f e e f b b f f f e f . 
. f d d f e e f d d b f f f f . 
. f f f f f f f f f f f f f . . 
    `, SpriteKind.Player)
```

## Move the player

🢀 Now we need to get the player moving 🢂
<hr/>

🔲 Drag a ``||controller:move [mySprite] with buttons ⊕||`` block.   
to the end of the ``||loops:on start||`` container

🔲 Press the ⊕ button on the new block and change the [__*vy*__](#whatVY "vertical velocity") 
argument to **0** so that the player won't move up or down with the joypad.

<hr/>
**Now you're ready to give your game a try in the simulator!**
<br/>

```blocks
scene.setBackgroundColor(11)
tiles.setTilemap(tilemap`level`)
let mySprite = sprites.create(img`
. . . . . f f f f f . . . . . . 
. . . . f e e e e e f . . . . . 
. . . f d d d d d e e f . . . . 
. . f f f d d f f d e f f . . . 
. c d d e e d d d d e d d f . . 
. c c d d d d c d d e d f f f . 
. c d c c c c d d d e d f b d f 
. . c d d d d d d e e f f d d f 
. . . c d d d d e e f f e f f f 
. . . . f f f e e f e e e f . . 
. . . . f e e e e e e e f f f . 
. . . f e e e e e e f f f e f . 
. . f f e e e e f f f f f e f . 
. f b d f e e f b b f f f e f . 
. f d d f e e f d d b f f f f . 
. f f f f f f f f f f f f f . . 
    `, SpriteKind.Player)
    // @highlight
controller.moveSprite(mySprite, 100, 0)
```

## Add gravity

To make the game feel more realistic, let's add some gravity.

To accomplish that, we can add [__*acceleration*__](#accel "increased speed in a direction") to "pull down" on our sprite.
<hr/>
🔲 Drag a ``||sprites:set [mySprite] [x] to [0]||`` block to the end of 
the ``||loops:on start||`` container.

🔲 Click the dropdown to change **x** to **ay (acceleration y)** 

🔲 Replace **0** with **500**.
<br/>



```blocks
scene.setBackgroundColor(11)
tiles.setTilemap(tilemap`level`)
let mySprite = sprites.create(img`
. . . . . f f f f f . . . . . . 
. . . . f e e e e e f . . . . . 
. . . f d d d d d e e f . . . . 
. . f f f d d f f d e f f . . . 
. c d d e e d d d d e d d f . . 
. c c d d d d c d d e d f f f . 
. c d c c c c d d d e d f b d f 
. . c d d d d d d e e f f d d f 
. . . c d d d d e e f f e f f f 
. . . . f f f e e f e e e f . . 
. . . . f e e e e e e e f f f . 
. . . f e e e e e e f f f e f . 
. . f f e e e e f f f f f e f . 
. f b d f e e f b b f f f e f . 
. f d d f e e f d d b f f f f . 
. f f f f f f f f f f f f f . . 
    `, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 0)
// @highlight
mySprite.ay = 500
```

## Jump Pt. 1

Now that the player is on the ground, we can make them jump!

Let's attach a jumping action to the 🅐 button.
<hr/>

🔲 Start by dragging an ``||controller:on [A] button [pressed]||`` block into the workspace.

🔲 Inside of that, add ``||sprites:set [mySprite] [x] to [0]||`` . 

🔲 To choose the attribute for the player's [__*vertical velocity*__](#whatVelY "speed in the up/down direction"),
click the dropdown menu and change **x** to **vy (velocity y)**.

🔲 The player will jump upward if you change **0** to something smaller.
Try  **-150** or **-200**.  
<br/>


```blocks
scene.setBackgroundColor(11)
tiles.setTilemap(tilemap`level`)
let mySprite = sprites.create(img`
. . . . . f f f f f . . . . . . 
. . . . f e e e e e f . . . . . 
. . . f d d d d d e e f . . . . 
. . f f f d d f f d e f f . . . 
. c d d e e d d d d e d d f . . 
. c c d d d d c d d e d f f f . 
. c d c c c c d d d e d f b d f 
. . c d d d d d d e e f f d d f 
. . . c d d d d e e f f e f f f 
. . . . f f f e e f e e e f . . 
. . . . f e e e e e e e f f f . 
. . . f e e e e e e f f f e f . 
. . f f e e e e f f f f f e f . 
. f b d f e e f b b f f f e f . 
. f d d f e e f d d b f f f f . 
. f f f f f f f f f f f f f . . 
    `, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 0)
mySprite.ay = 500
// @highlight
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    mySprite.vy = -200
})
```

## Done

🔥 **That's it! We've created a simple platformer game.** 🔥  

In the next lesson we'll learn how to add obstacles and goals.
