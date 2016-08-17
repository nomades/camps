# S'inniter à JavaScript avec un jeu collaboratif

Un développeur confirmé lance l'idée de s'amuser avec deux ou trois personnes présentes afin de monter en compétence dans l'écriture et la compréhension des du langage [JavaScript](https://fr.wikipedia.org/wiki/JavaScript)

* L'initatuer et animateur de jeu exerce ses capacités padégogiques
* Les apprenants élèvent leur niveau de pratiques numériques
* le format court et ludique interpelle les personnes passant dans le même espace (Développeur ou non inititié) qui demandent à leur tour d'essayer l'exercice

Ce test/exercice est inspiré d'un jeu pour enfant en colonie de vacances ([Cf la toile scoute Fizz Buzz](https://www.latoilescoute.net/fizz-buzz))

## Contexte technologique de l'initation

* [Fizz Buzz Test](http://c2.com/cgi/wiki?FizzBuzzTest) 
* [Using FizzBuzz to Find Developers who Grok Coding](https://imranontech.com/2007/01/24/using-fizzbuzz-to-find-developers-who-grok-coding/)

Le «test Fizz - Buzz " est souent utilisé lorsd'entretien d'emploi, il est conçu pour aider à filtrer le 99,5% des candidats à la programmation. Le cahier des charges de l' attribution de programmation est le suivant:

> " Ecrire un programme qui imprime les numéros de 1 à 100. Mais pour des multiples de 3 print" Fizz " au lieu du numéro et pour les multiples de 5 print" Buzz " . Pour les nombres qui sont des multiples de 3 et 5 print" FizzBuzz " . "

## Lancer le Jeu

Challenge annoncé à voix haute : **Le but est d'écrire un tel programme en moins de 10 minutes**

* Un ordinatuer par participant
 *  une invite de commande
 *  éditeur de text (ex: sublime texte)

**OU**

* [FizzBuzz en ligne](https://www.codecademy.com/courses/fizzbuzz/0/1) via code academy

* Expliquer la règle :

> Pour les multiples de 3, il faudra remplacer le nombre par Fizz.
Pour les multiples de 5, il faudra remplacer le nombre par Buzz.
Pour les multiples et 3 et de 5, il faudra remplacer le nombre par FizzBuzz.

Cela donne

> // Write a program that prints the numbers from 1 to 100. But for multiples of three print “Fizz” instead of the number and for the multiples of five print “Buzz”. For numbers which are multiples of both three and five print “FizzBuzz”


Cet exercice peut être perçu comme utile pour estimer les programmeurs étant capable de penser par eux-mêmes face à ceux ayant une tendance copier-coller la solution d'un autre.

## Laisser les participants penser par-eux mêmes


## Un exemple de solution

> for (var number = 1; number <100 ; number++) {
    if (number % 3 === 0 && i % 5 === 0) {
        console.log("FizzBuzz");
    }
    else if (number % 5 === 0) {
        console.log("Buzz");
    }
    else if (i % 3 === 0) {
        console.log("Fizz");
    }
    else {
        console.log(number);
    }
}

# Ressources pour progresser

*  Twenty Ways to FizzBuzz
[An exercise in Javascript](http://ditam.github.io/posts/fizzbuzz/)

* [Ressources recommandées par la NodeSchool Lyon pour apprendre le JS](https://github.com/nodeschool/lyon/blob/master/learnjavascript.md)
