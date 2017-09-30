---
title: Taleir code informatique
description: Quel JavaScript parle t-on aujourd'hui lorsqu'on utilise ce langage ? 
image_url: 
---

# Geekeries Kerbos 2017

## Atelier JavaScript "style moderne"
soirée, 23h, du 7 août 2017 [IndieCamp Kerbors 2017 ](https://hackmd.io/s/SJ60BmJvb#)par Stéphane Langlois

Quel Java script parle t-on aujourd'hui lorsqu'on utilise ce langage ? 

-> const

### exemple dans un fichier 'korbors-JS'
 ouvrir un index.html puis un serveur local

Tips : Les outils de prédiltections pour cet exercice sont la console et le debugger lors de cet atelier

```
 <title>Kerbors JS</tilte>
 <meta charset=utf-8>
 <h1 class=town-title></h1>
<script>
  const h1 = document.querySelector('h1.town-title')

</script>
```

apprendre à utilser une fonction  : quand tu lui donnes un mot en minuscule, elle le rend en majuscule

```
 <title>Kerbors JS</tilte>
 <meta charset=utf-8>
 <h1 class=town-title></h1>
<script>
   const tonws = ['Paris', 'Barcelone', 'Nantes', 'Bordeaux', 'Toulouse']
   function toMaj = str =>str.toUpperCase()
</script>
```

Les parenthèses ont le role d'invocation de la fonction

_Tips: se renseigner sur l'inférence en programmation fonctionnelle, ne pas utiliser 'var' mais utliser 'let'_

ou encore pour construire une liste html de villes en utilisant map pour vouloir chaque ville avec du zerofonction

```
 <title>Kerbors JS</tilte>
 <meta charset=utf-8>
 <h1 class=town-title></h1>
<script>
   const tonws = ['Paris', 'Barcelone', 'Nantes', 'Bordeaux', 'Toulouse']
   tonws.map(town => return toUpperCase())
</script>
```

Pour aller plus loin avec les focntions

```
 <title>Kerbors JS</tilte>
 <meta charset=utf-8>
 <h1 class=town-title></h1>
<script>
   const tonws = ['Paris', 'Barcelone', 'Nantes', 'Bordeaux', 'Toulouse']
   tonws.map(town => {return toUpperCase()}
</script>
```

Utiliser ul>li*5 pour faire une nodelist

```
 <title>Kerbors JS</tilte>
 <meta charset=utf-8>
 <h1 class=town-title></h1>
 <ul>
 	<li>Paris</li>
 	<li>Barcelone</li>
 	<li>Nantes</li>
 	<li>Bordeaux</li>
 	<li>Rennes</li>
 </ul>
<script>
   const tonws = ['Paris', 'Barcelone', 'Nantes', 'Bordeaux', 'Toulouse']
</script>  
```
Pour aller plus loin...

```
 <title>Kerbors JS</tilte>
 <meta charset=utf-8>
 <h1 class=town-title></h1>
<script>
   const tonws = ['Paris', 'Barcelone', 'Nantes', 'Bordeaux', 'Toulouse']
   const ulTonwns = document.querySelector('ul.towns')
   towns.forEach(tonw => {
   	console.log(ulTonwns)
   	ulTonwns.innerHTML += '<li>${towns}<li>'
   })
</script>
```

Voir aussi le github.com/oncletom/nodebook

Node.js permet d'avoir le même langage coté serveur et coté client, *ce qui peut être très utile pour du jeu vidéo* relève Arthur Masson


## Atelier ELM
soirée, minuit, du 7 août 2017 IndieCamp Kerbors 2017 par Stéphane Langlois

pour linux

```
$ sudo apt-get update
$ sudo apt-get install nodejs npm
$ sudo apt install nodejs-legacy
$ npm install elm
```

ELM est un langage fonctionnel avec une capacité d'inférence. Ce n'est pas un framework mais un langage qui embarque le 'beiginnerProgram'

Tips de documentation sur ELM : elm-lang.org avec un try online pour faire un hello world

```
import Html exposing (text)
main=
text "Hello, World"

```
ou 

```
import Html exposing (h1,text)
main=
h1 [] [text "Hello, Wolrd"]
```
C'est une virtualisation du DOM

- Read more about this program in the official Elm guide : https://guide.elm-lang.org/architecture/user_input/buttons.html

```
import Html exposing (beginnerProgram, div, button, text)
import Html.Events exposing (onClick)


main =
  beginnerProgram { model = 0, view = view, update = update }


view model =
  div []
    [ button [ onClick Decrement ] [ text "-" ]
    , div [] [ text (toString model) ]
    , button [ onClick Increment ] [ text "+" ]
    ]


type Msg = Increment | Decrement


update msg model =
  case msg of
    Increment ->
      model + 1

    Decrement ->
      model - 1
```


NB : Le début de la programmation focntionnelle est le patterMatching

- Se créer un répertoire 'elm-kerbors' 
- puis lancer elm-repl 0.18.0 (github.com/elm-long/elm-repl)

Pour utiliser et vérifier dans une fonction un typage fort implicite capable d'inferrence. 


```
add num + 2
<fonction> : number -> number
add 5
10 number

add num num1 = num + num1
<fonction> : number -> number -> number
toOdd = add 2
```

Dans le répertoir elm-kerbors, faire un document index.htlm

```
<script scr=kerbors.js></script>

<div class=main></dic>
<script>
   const node = document.querySelector('div.main')
   const app = Elm.Kerbors.embed(node)
</script> 
```
puis un document Kerbors.elm

```
port module Kerbors exposing (..)

import Html exposing (text, h1)

--pour typer la fonction
main: Htlm.Html msg

main=
   h1 [] ["Hello, World"]
```

Pour un environmment live

```
$ cd elm-kerbors
$ elm-live Kerbors.elm --open --debug --output=kerbors.js
```
