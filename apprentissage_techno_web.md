---
title: S'initier à une techno web à plusieurs
description: learning by doing, gamefication de l'apprentissage, code
image_url: https://framapic.org/YJK1ICPDaeM3/0RJ01Iptwpk1.jpg
---

# S'inniter à JavaScript avec un jeu collaboratif

Un développeur confirmé lance l'idée de s'amuser avec deux ou trois personnes présentes afin de monter en compétence dans l'écriture et la compréhension des du langage [JavaScript](https://fr.wikipedia.org/wiki/JavaScript)

* L'initiateur et animateur de jeu exerce ses capacités padégogiques
* Les apprenants élèvent leur niveau de pratiques numériques
* le format court et ludique interpelle les personnes passant dans le même espace (Développeur ou non inititié) qui demandent à leur tour d'essayer l'exercice

Ce test/exercice est inspiré d'un jeu pour enfant en colonie de vacances ([Cf la toile scoute Fizz Buzz](https://www.latoilescoute.net/fizz-buzz))

## Contexte technologique de l'initation

* [Fizz Buzz Test](http://c2.com/cgi/wiki?FizzBuzzTest) 
* [Using FizzBuzz to Find Developers who Grok Coding](https://imranontech.com/2007/01/24/using-fizzbuzz-to-find-developers-who-grok-coding/)

Le "test Fizz - Buzz" est souent utilisé lors d'entretien d'emploi, il est conçu pour aider à filtrer des candidats à la programmation. Le cahier des charges de l' attribution de programmation est le suivant:

> " Ecrire un programme qui imprime les numéros de 1 à 100. Mais pour des multiples de 3 print" Fizz " au lieu du numéro et pour les multiples de 5 print" Buzz " . Pour les nombres qui sont des multiples de 3 et 5 print" FizzBuzz " . "

## Lancer le Jeu

Challenge annoncé à voix haute : **Le but est d'écrire un tel programme en moins de 10 minutes**

* Un ordinateur par participant
 *  une invite de commande
 *  éditeur de text (ex: sublime texte)

**OU**

* [FizzBuzz en ligne](https://www.codecademy.com/courses/fizzbuzz/0/1) via code academy

**Expliquer la règle** :

> Pour les multiples de 3, il faudra remplacer le nombre par Fizz.
Pour les multiples de 5, il faudra remplacer le nombre par Buzz.
Pour les multiples et 3 et de 5, il faudra remplacer le nombre par FizzBuzz.

Cela donne

> // Write a program that prints the numbers from 1 to 100. But for multiples of three print “Fizz” instead of the number and for the multiples of five print “Buzz”. For numbers which are multiples of both three and five print “FizzBuzz”

L'animateur de la séance rédige en expliquant la syntaxe :

```js
function fizzbuzz (number) {
    if (number 3 === 0 && number 5 === 0) {
        console.log('FizzBuzz')
    }
    
```

Puis l'animateur demande aux participants de prédire à voix haute le résultat lorsqu'ils rédigent un nombre.

Exemple : "Je pense que le print sera Fizz si j'écris 33"

Le participant rédige :

```js
Fizzbuzz(33)
// Le résultat qui s'affiche est alors : => False
```

L'animateur invite alors les participants à se concerter sur la provenance de l'erreur

Cet exercice peut être perçu comme utile pour estimer les programmeurs étant capable de penser par eux-mêmes face à ceux ayant une tendance copier-coller la solution d'un autre.

## Laisser les participants penser par-eux mêmes

Dans un esprit de Do-ocratie, apprendre par le faire est un axe essentiel lors de cet atelier. Le droit à l'erreur fait partie du processus d'apprentissage et est inaliénable.

**Cela permet l'autonomisation dans les usages et la prise de confiance de la pratique**.

Les participants sont conviés à rédiger individuellemnt ou collaborativement des rédaction en javascript pour corriger l'erreur observée et tendre vers l'atteinte de l'objectif fixé en début d'atelier. Le principe de prédire à voix haute le résultat de l'opération avant de lancer l'éxecution est toujours valable. 

L'animateur peut aider la progression par quelques nouveaux mini challenges, exemple :

>* Commencer par réaliser le challenge avec les multiples de 3 comme unique condition
* Puis avec les multiples de 3 en condition première et les multiples de 5 en condition seconde
* changer les multiples 3 et 5 par 3 et 8
* Si condition 1 remplie  = Fizz , si condition 2 remplie = Buzz , si condition 1 et 2 remplies = Bingo
* remplacer les chiffres par 'Hello' et observer ce qui se passe

Après découverte des subtilités de la syntaxe propre à JavaScript, les participants doivent, seul ou en groupe, rédiger une solution la plus simplement rédigée et commentée au challenge intiale posé dans le temps le plus court possible.

Répéter la séance quelques jours plutard avec le même groupe permet de consilder les acquis.

## Un exemple de solution

```js
function fizzbuzz (number) {
    if (number % 3 === 0 && number % 5 === 0) {
        console.log('FizzBuzz')
    }
    else if (number % 5 === 0) {
        console.log('Buzz')
    }
    else if (number % 3 === 0) {
        console.log('Fizz')
    }
    else {
        console.log(number)
    }
}

fizzbuzz(1)
// => 1
fizzbuzz(1)
// => 2
fizzbuzz(3)
// => Fizz
fizzbuzz(5)
// => Buzz
fizzbuzz(15)
// => FizzBuzz
```

_A NOTER_:

* Plusieurs solutions à ce test existent
* Plusieurs variantes à la règle de base peuvent être testées
* Ce test existe dans de nombreux autres langages de programmation

# Ressources pour progresser

*  Twenty Ways to FizzBuzz
[An exercise in Javascript](http://ditam.github.io/posts/fizzbuzz/)

* [Ressources recommandées par la NodeSchool Lyon pour apprendre le JS](https://github.com/nodeschool/lyon/blob/master/learnjavascript.md)

* Lancer un nouveau test convivial et ludique 
![](https://framapic.org/i7ij85Nl24K3/etPtbrfu3xgf)
