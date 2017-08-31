###### Tags: `IndieCamp` `Kerbors` `atelier geek` `Elm` `JavaScript`

# [[IndieCamp Kerbors](https://frama.link/indiecamp-kerbors-2017)] Atelier Geek - Session #2

* [Atelier #0](https://hackmd.io/s/rJw31KgDb), sur les commandes d'un terminal pour un ordianteur sous Linux
* [Atelier #1](https://hackmd.io/s/rJDXkRHDW), sur le langage markdown utile àla documentation de projet
* [Atelier #2](https://hackmd.io/s/SyHcRZPPb), sur les langage de programmation JavaScript et Elm
* [Atelier #3](https://hackmd.io/s/BkvQpmmY-#) apprendre JavaScript en MobProgramming

Ce PAD décrit un atelier d'initiation aux **langages JavaScript et ELM** réalisé sur l'indiecamp à Kerbors.

Ce document est mis à disposition par tou.te.s les contributeurs et contributrices de l'Indiecamp Kerbors 2017, selon les termes de la [licence Creative Commons CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).

<img style="display: block; margin: 0 auto;" src="https://mirrors.creativecommons.org/presskit/buttons/88x31/png/by-sa.png" width="40%">

## JavaScript

Session co-organisée le 7 Août à Kerbors et animée par Stépnahe Langlois. Avec une méthode "Mob Programming" (Voir [Doing with Mob, learning by Mob - eng / fr](https://storify.com/XavierCoadic/doing-with-mob-learning-bu-mob))

Ouvrir un `index.html` puis un serveur local.

```
 <title>Kerbors JS</title>
 <meta charset=utf-8>
 <h1 class=town-title></h1>
<script>
  const h1 = document.querySelector('h1.town-title')
</script>
```

Quand tu lui donnes un mot en minuscule elle le rend en majuscule.


```
 <title>Kerbors JS</tilte>
 <meta charset=utf-8>
 <h1 class=town-title></h1>
<script>
   const tonws = ['Paris', 'Barcelone', 'Nantes', 'Bordeaux', 'Toulouse']
   function toMaj = str =>str.toUpperCase()
</script>
```

Les paranthèses ont le role d'invocation de la fonction. 

:::info
+ Se renseigner sur l'inférence en programmation fonctionnelle : Defi [Inférence](https://fr.wikipedia.org/wiki/Inf%C3%A9rence), [L'inférence de types](https://fr.wikipedia.org/wiki/Inf%C3%A9rence_de_types) est un mécanisme qui permet à un compilateur ou un interpréteur de rechercher automatiquement les types associés à des expressions, sans qu'ils soient indiqués explicitement dans le code source.
+ Tips JS: ne pas utiliser 'var' mais utliser 'let'
:::

Ou encore pour construire une liste html de villes en utilisant map pour vouloir chaque ville avec du zerofonction.

```
 <title>Kerbors JS</tilte>
 <meta charset=utf-8>
 <h1 class=town-title></h1>
<script>
   const tonws = ['Paris', 'Barcelone', 'Nantes', 'Bordeaux', 'Toulouse']
   tonws.map(town => return toUpperCase())
</script>
```

Pour aller plus loin avec les fonctions

```
 <title>Kerbors JS</tilte>
 <meta charset=utf-8>
 <h1 class=town-title></h1>
<script>
   const tonws = ['Paris', 'Barcelone', 'Nantes', 'Bordeaux', 'Toulouse']
   tonws.map(town => {return toUpperCase()}
</script>
```

Utiliser `ul>li*5` pour faire une nodelist

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
Pour aller plus loin

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

[Voir](github.com/oncletom/nodebook) pour un livre numérique à plusieurs mains sur JavaScprit. Node.js permet d'avoir le même langage coté serveur et coté client, "ce qui peut être très utile pour du jeu vidéo" relève Arthur Masson

## ELM

Session co-organisée le 7 août à Kerbors et animée par Stépnahe Langlois. 

ELM est un langage fonctionnel avec une capacité d'inferrence. Ce n'est pas un framework mais un langage qui embarque le 'beiginnerProgram'. Site de référence : elm-lang.org (avec un bac à sable pour faire un 'hello world').

Pour installer ELM https://guide.elm-lang.org/install.html.

**Avec Linux**

```
$ sudo apt-get update
$ sudo apt-get install nodejs npm
$ sudo apt install nodejs-legacy
$ npm install elm
```
Pour afficher un text Hello, Wolrd en langage Elm sur un serveur local ou sur http://elm-lang.org/try
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
Avec Elm c'est une virtualisation du DOM qui est engagée. [Document Object Model](https://fr.wikipedia.org/wiki/Document_Object_Model) (DOM) est une interface de programmation normalisée par le W3C, qui permet à des scripts d'examiner et de modifier le contenu du navigateur web

Exemple pour la mise en place de boutons + et - sur une page web http://elm-lang.org/examples/buttons

```
-- Read more about this program in the official Elm guide:
-- https://guide.elm-lang.org/architecture/user_input/buttons.html

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


> NB : le début de la programmation fonctionnelle est le pattern matching. Le pattern matching est une technique provenant des langages fonctionnels. D'après sa définition, elle a pour but de valider la présence de patterns dans une séquence. Une séquence, dans le monde fonctionnel, est représentée par des données en entrée. Dans le monde objet, la séquence est une instance d'une classe

Mainteant, se créer un répertoire 'elm-kerbors' Puis lancer elm-repl 0.18.0 (github.com/elm-long/elm-repl) pour utiliser et vérifier dans une fonction un typage fort implicite capable d'inferrence. 

```
add num + 2
<fonction> : number -> number
add 5
10 number

add num num1 = num + num1
<fonction> : number -> number -> number
toOdd = add 2
```

Dans le répertoire `elm-kerbors`, faire un document index.htlm

```
<script scr=kerbors.js></script>

<div class=main></dic>
<script>
   const node = document.querySelector('div.main')
   const app = Elm.Kerbors.embed(node)
</script> 
```
Puis créer un document Kerbors.elm

```
import module Kerbors exposing (..)

import Html exposing (text, h1)

--pour typer la fonction
main: Htlm.Html msg

main=
   h1 [] ["Hello, World"]
```

Pour un environemment live dans le terminal

```
$ cd elm-kerbors
$ elm-live Kerbors.elm --open --debug --output=kerbors.js
```

