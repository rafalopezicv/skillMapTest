# Exercici llistes aleatories

```python-template
myMenu = miniMenu.create_menu()
nombres =
numeros = 

def on_update():
    nombre_aleatorio = 
    numero_aleatorio = 

    game.splash("Nombre: " + nombre_aleatorio)
    game.splash("Número: " + str(numero_aleatorio))


game.on_update(on_update)
```

```template
myMenu = miniMenu.create_menu()
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

Ara farem un exercici on el que generarem dues llistes, una amb noms i un altre amb edats.

Un cop tinguem les llistes agafarem un dels valors dels noms i de les edats i les mostrarem per pantalla.


## Crear les llistes

El primer que necessitarem per aquesta activitat seran les llistes que mostrarem per pantalla.

<hr>

🔲 En una de les llistes guardarem noms, pots utilitzar els noms dels teus companys per fer servir a la llista de noms, fes la que tinguí almenys 5 noms diferents

🔲 Per la llista d'edats posa numeros diferents que puguin ser edats. No fa falta que hi hagi la mateixa quantitat d'edats que de noms!

<hr/>

>>*Tip: Recorda com es declaren les llistes, ho pots consultar en els apunts del Github del Moodle 😉*


```python
lista = ["Hola"]
```

## Seleccionar un número de manera aleatoria

Ara que tenim les llistes preparades, hem d'agafar un valor aleatori per mostrar per pantalla.
<hr/>

🔲 Recorda com se selecciona un valor dins d'una llista

🔲 Llavors fes ús de la funció randint per seleccionar un valor de dins

<hr/>

>>*Tip: Utilitza la funció de len per no haver d'utilitzar números màgics per la longitud de la llista*

```python
valor = lista[randint(0, len(lista))]
```

## Fet

🔥 **Ja està, així és com agafem un valor aleatori d'una llista** 🔥  

En la següent lliçó farem un altre cosa


```package
arcade-mini-menu=github:riknoll/arcade-mini-menu
```