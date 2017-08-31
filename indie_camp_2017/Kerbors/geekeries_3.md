---
title: Atelier apprendre JavaScript en MobProgramming
description: Pour éaliser une pallication de faceblinding sur le sujet de la prosapagnosie.
image_url: 
---

# Atelier apprendre JavaScript en MobProgramming

Par Stéphane Langlois, 23h, lors de l'IndeCamp kerbors 2017

Pour en savoir plus sur le MobProgramming : 

## But de l'atelier

sur un seul ordinateur avec plusieurs apprenant il s'agit de développer une appli web de faceblind, sur le sujet de ,afin de s'acculturer à la pratique du langage informatique JavaScript faisant suite à l'atelier precédent [Atelier JavaScript "style moderne"].

Pour une équipe collborative pluridisciplinaire avec un vrai produit collectivement réalisé. 

Voir le [repository de base sur github](github.com/kerbors-doc/projets/1) pour voir les 5 étapes à suivre sur ce challenge collectif. 

## Présents 

+ Stéphane
+ Arthur
+ Quentin
+ Xavier

## Déroulé

Stéphane en producter owner : nous allons tenter de réalsier le backlog dans le github préparé. 

1. afficher 70 images en boucles
2. en boucle aléatoirement
3. ajouter un bouton ajouter suivant
4. ajouter un bouton déjà

C'est pour tester si tu es prosopagnosique, c'est à dire si tu est capable de reconnaître des visages. 

### Première étape

Quentin s'attaque à la première User Story (us#1) du [dépot github](github.com/kerbors-doc) par une visite des fichiers pré ouverts du repo. 
Puis ouverture d'un fichier index.html guidé par les autres participants.

Pour le src en JS les "" ne sont plus obligatoire dans JavaScript

```
<title>Kerbors prospagnosie</title>
<meta charset="utf-8">
<h1>Prosopagnosie</h1>
<img src=faceblind/1.jpg>
```
Dans le navigateur

document.querySelector("img") puis entrée puis document.querySelector("img").src"faceblinding/2.jpg" pour vérifier si cette manipulation focntionne

dans l'éditeur : 

```
<title>Kerbors prospagnosie</title>
<meta charset="utf-8">
<h1>Prosopagnosie</h1>
<img src=faceblind/1.jpg>
<script >
    let id = 1
	const changeImage = (id) => document.querySelector("img").src`faceblinding/${id}`
	setinterval(()=>changeImage(id++), 1000)
</script>
```

Aussi possible porposé par Athur

```
<title>Kerbors prospagnosie</title>
<meta charset="utf-8">
<h1>Prosopagnosie</h1>
<img src=faceblind/1.jpg>
<script >
    letid = 1
	const changeImage = () => {
	  document.querySelector("img").src`faceblinding/${id}`
    }
	setinterval(changeImage(id++), 1000)
</script>
```

Maintenant Commit sur le repo github pour valider cette US #1 dans la branch master

### Deuxième étape

Création d'un nouvelle branch pour la seconde US

Faire de l'aléatoire

```
<title>Kerbors prospagnosie</title>
<meta charset="utf-8">
<h1>Prosopagnosie</h1>
<img src=faceblind/1.jpg>
<script >
    letid = 1
	const changeImage = () => {
       const i = Math.floor(Math.random()*75)+1
	   document.querySelector("img").src`faceblinding/${i}`
    }
	setinterval(changeImage, 1000)
</script>
```

Créer un nouveau fcihier JS

script.js dans le repo 

du coup index.html devient

```
<title>Kerbors prospagnosie</title>
<meta charset="utf-8">
<link rel="stylesheet" type="text/css">
<h1>Prosopagnosie</h1>
<img src=faceblind/1.jpg>
<script scr= script.js></script>
```

css devient

```
body {
     text-align: center
}

h1 {
	color: yellow
	background-color: black
}
```
Maintenant : commit dans le repo github sur #us2

### Etape 3

ajouter un bouton 'suivant' sur la page web

commit sur #us3

### Pull Request vide et/ou dans une user story

Pourquoi faire ? Et quels gains ?

Ouvrir une pull request avec une page de code ou de text quasi vie reveint à ouvrir un fil de discussions et de contributions pour favoriser :
+ l'écrirure collaborative
+ l'archivage des contributions techniques diretement liées avec les discussions ainsi qu'avec les dates
+ offre une documentation plus compléte en terme de contexte qu'un github/wiki
+ intégrée dans le backlog (to do, en cours, fait) avec des users stories = suivi facilité de l'évolution des taĉhes avec collaborations et bone base de documentation

Utiliser ce principe avec https://travis-ci.org/, outil d'aide à l'intégration continue, pour suivre la qualité des contributions sur les pull requests permet une qualité de travail de haute qualité sur du code collaboratif.
