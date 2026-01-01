# Ejercicio listas aleatorias

```python-template
nombres =
numeros = 

def on_update():
    nombre_aleatorio = 
    numero_aleatorio = 

    game.splash("Nombre: " + nombre_aleatorio)
    game.splash("Número: " + str(numero_aleatorio))


def on_update():
```

```template
nombres =
numeros = 

def on_update():
    nombre_aleatorio = 
    numero_aleatorio = 

    game.splash("Nombre: " + nombre_aleatorio)
    game.splash("Número: " + str(numero_aleatorio))


game.on_update(on_update)
```

## Hola! @unplugged

Ara anem a fer un exercicio on el que generarem dues llistes, una amb noms i una altre amb edats.

Un cop tinguem les llistes agafarem un dels valors dels noms i de les edats i les mostrarem per pantalla.


## Crear les llistes

El primer que necesitarem per aquesta activitat seràn les llistes que mostrarem per pantalla.

<hr>

🔲 En una de les llistes guardarem noms, pots utilitzar els noms dels teus companys per utilitzar a la llista de noms, fes la que tinguí al menys 5 noms diferents

🔲 Per la llista d'edats 

<hr/>

>>*Tip: Recorda com es declaren les llistes, ho pots consultar en els apunts del Github del Moodle 😉


```python
lista = ["Hola"]
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

## Fet

🔥 **Ja està, així es com agafem un valor aleatori d'una llista** 🔥  

En la següent lleso farem una altre cosa
