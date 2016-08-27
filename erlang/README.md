# Erlang - Un langage concurrentiel pour le monde réel

Le titre  de cette petite  fiche est  odacieux, mais en  quelque sorte
résume  parfaitement   et  simplement  le  langage   de  programmation
Erlang. Les chercheurs de chez Ericsson  ont voulu créé un langage qui
fonctionne exactement comme  le monde réel. Le monde  dans lequel nous
vivons  est  concurrentiel  et   parallèle.  Lorsque  nous  parlons  à
quelqu'un,  une   autre  personne   parle  peut-être   avec  quelqu'un
d'autres. Durant  le dialogue,  une phrase, ou  un mot,  pourrait vous
intéresser.  Cet évènement  va  alors arrêter  votre communication  et
détourner votre attention de votre premier interlocuteur.

Dans  cet  exemple, une  grande  partie  de  la logique  d'Erlang  est
présenté: des acteurs,  qui communiquent ensemble et  qui réagissent à
des évènements. Erlang  fonctionne de la même façon.  Essayons donc de
rentrer un peu plus dans le vif du sujet.

## Il était une fois...

Une grande société qui faisait des téléphones. Cette société utilisait
de nombreux outils, de nombreuses  machines, toutes différentes, et de
nombreux langages, tous différents, pour  parler avec ces machines. Le
coût  de développement,  de maintenance,  et de  formation était  très
élevé. A  vrai dire,  il était  même énorme.  Imaginez-vous travailler
avec  plusieurs  100ènes  de   personnes  parlant  tous  des  dialects
différents  et  ayant  chacun  leurs propres  coutumes!  Il  y  aurait
rapidement une rupture de stock d'aspirine.

Dans  un soucis  de normalisation,  une équipe  de chercheur  de cette
société décida de créer un  langage permettant de répondre à plusieurs
problèmes en même temps:

 * Un langage portable, que tous les équipements comprendraient
 
 * Un langage sécurisant, basé sur la programmation fonctionnelle
 
 * Un langage qui simplierait l'exécution des tâches en parallèles
 
 * Un langage qui serait productif et simpliefierait la vie des
   développeurs
 
 * Un langage sécurisé, qui mettrait en avant des principes
   d'isolations forts
   
 * Et pleins d'autres arguments que nous verrons au fur-et-à-mesure.
 
Une  équipe  fut  alors  formé  pour travailler  sur  ce  projet,  Joe
Armstrong,  Robert Virding,  et Mike  Williams furent  les premiers  à
mettre en place  le design, s'inspirant de nombreux  langages, tel que
Lisp, Ada ou encore Cobol, et rajoutant de nouveaux concepts.

La première version de ce langage sort au milieux des années 80, et la
première   application   est   l'utilisation  pour   un   service   de
télécommunication filaire: un switch  téléphonique. Le temps passe, et
le  langage   ne  fait  pas  autant   de  bruit  que  prévu   au  sein
d'Ericsson. En  1998, Ericsson se sépare  de ce dernier, et  libère le
code, qui passe alors en open-source sous une licence Apache 2.0.

Il faut attendre 10ans de plus pour  voir plus de projets basés sur ce
langage, tout  d'abord, eJabberd, serveur  de chat basé sur  XMPP, qui
utilise  Erlang  depuis le  début.  Arrive  ensuite d'autres  sociétés
intéressés  par  ce  langage,  tel   que  Google,  Amazon,  ou  encore
Facebook.  La société  ayant fait  le  plus de  bruit étant  WhatsApp,
valorisé à  plus de 40  milliard de $ pour  une équipe d'une  30ène de
personne, toute la plateforme fonctionnant sous Erlang!

## Pourquoi Erlang?

Développeur Shell, Perl, Python avec un  peu de C, je me suis toujours
confronté au problème du parallélisme.  Que celui qui n'a jamais voulu
lancé son PC par la fenêtre quand il est arrivé à la gestion des forks
ou des threads me  lance une pierre. Pour ceux qui  ne saurait pas, un
ordinateur, basé  sur la machine  de Turing, exécute  linéairement les
instructions qu'il doit  traiter. Quand nous utilisons  des threads ou
des  forks, nous  faisons  simplement  en sorte  de  diviser le  temps
d'exécution, mais vu qu'un ordinateur traite l'information rapidement,
nous avons l'impression que les tâches sont exécutés en même temps.

Concrètement, avec  un exemple dans la  vie de tous les  jours... Nous
pourrions  prendre le  fait que  vous  ne pouvez  pas faire  plusieurs
choses  en meme  temps, donc,  pour optimiser  au maximum,  vous allez
diviser vos tâches  en plusieurs sous-tâches, qui  seront exécutées au
fur et  à mesure.  Dès que vous  faites une tâche,  si elle  n'est pas
finis, vous notez l'avancement et vous passez à une autre tâche, ainsi
de  suite,  jusqu'au  moment  ou   plus  aucunes  tâches  restera.  Ce
raisonnement, appliqué dans  le monde de l'infortique,  est vraie pour
les systèmes  possédant un processeur mono-core  (un seul calculateur)
multi-threadé (découpage des tâches.

Aujourd'hui, nous possédons probablement  tous des systèmes multi-core
multi-threadés, pour  revenir à l'analogie précédente,  c'est comme si
maintenant, au lieux d'être seul, vous étiez 2 ou plus. Votre liste de
tâche est partagée, et les personnes viennent piocher dedans au fur et
à mesure de  l'avancement du projet. C'est à partir  de maintenant que
les problèmes arrivent!

Imaginons  que  vous commenciez  une  tâche,  que cette  dernière  est
nécessaire pour réaliser d'autres  tâches. Longue et fastidieuse, vous
prennez  beaucoup  de  temps  à  la  réaliser.  Les  autres  personnes
attendent  après vous!  Donc, le  temps d'exécution  est ralentie  par
"votre  faute". Imaginons  maintenant  que cette  tâche est  tellement
complexe  que vous  décidiez d'abandonner...  Que ce  passe-t-il? Vous
gardez la tâche et personne d'autre ne le sait, vous venez de créer un
dead-lock!  Par la  même occasion,  vous venez  de comprendre  tout le
problème du parallélisme et du concurrentiel: le partage de donnée.

La  majorité des  autres langages  laissent la  liberté de  choisir au
développeur  sur  comment gérer  le  partage  de l'information  et  sa
transmission. Ce  qui peut-être  louable pour une  personne réellement
expériementé,  mais qui  n'est pas  le cas  pour une  personne qui  ne
possède pas  cette connaissance. Les développeurs  d'Erlang ont décidé
de tranché et  de créer leur propre modèle de  gestion du parallélisme
ainsi que des  exécutions concurrentes. Nous n'avons donc  plus à nous
en faire!

Bien évidemment, j'ai d'abord testé d'autres langages: Haskell, OCaml,
Miranda, Go... Ils ont tous le même problème: ils laissent le choix au
développeur.

## Comment installer Erlang?

Compatible  avec la  majorité des  systèmes,  il n'est  pas livré  par
défaut  sur  la   pluspart  et  nécessite  donc   l'installer  via  un
package.  Ce dernier  est  volumineux mais  contient un  environnement
complet de développement.

 * sous [Debian](https://packages.debian.org/jessie/erlang) ou
   [Ubuntu](http://packages.ubuntu.com/xenial/erlang):

```sh
apt-get install erlang
```

 * sous [FreeBSD](https://www.freshports.org/lang/erlang), PCBSD, ou
   DragonFlyBSD:

```sh
pkg install erlang
```

 * sous [OpenBSD](http://openports.se/lang/erlang/19):

```sh
pkg_add erlang19
```

 * sous [VoidLinux](https://github.com/voidlinux/void-packages/tree/master/srcpkgs/erlang):
 
```sh
xbps-install erlang 
```

 * sous [Gentoo](https://packages.gentoo.org/packages/dev-lang/erlang):
 
```sh
emerge dev-lang/erlang
```

 * sous MaxOS X:
 
```sh
brew install erlang
```

 * sous Windows, vous pouvez récupérer des paquets binaires à
   l'adresse https://www.erlang-solutions.com/resources/download.html
   et les installer.

## Rentrons dans le vif du sujet.

Erlang  offre  de  nombreuses  fonctionnalités peu  communes  pour  la
majorité des  langages, pas étonnant, vu  qu'il n'y a que  très peu de
langage orienté concurrentiel, la  majorité étant orienté impératif ou
objet. Erlang se  rapproche plus d'un système  d'exploitation que d'un
langage traditionnel. 

Quand vous  utilisez un langage  objet, vous avez l'habitude  de créer
des classes (modèles  d'objets) qui seront ensuite, une  fois que vous
en aurez  besoin, instanciés  en objet. Ce  concept d'objet  permet de
regrouper  une  structure de  donnée  et  les  fonctions liées  à  ces
informations. Erlang  utilise un système  un peu comparable  mais avec
une isolation forte: des micro-processus.

Un micro-processus est  un objet totalement isolé du  reste des autres
micro-processus.  Ce dernier possède différent moyen de communication.
Par exemple, il a une  "boite aux lettres".  Cette fonctionnalité, qui
n'est  simplement  qu'une  "queue"   ou  FIFO,  permet  d'envoyer  des
instructions  qui s'empilent.  Le micro-processus  récupère alors  les
instructions contenu dans les messages et les exécutent à la suite.

Erlang étant  un langage  concurrentiel et fonctionnel,  de nombreuses
personnes   ne  seront   pas   surprises  de   ne   pas  trouver   les
traditionnelles boucles (while, for,  foreach), structure de controles
importantes dans pratiquement tous  les langages.  Malheureusement (ou
heureusement), avec le paradigme  fonctionnel, tout est fonction. Pour
générer donc une boucle (infinie ou non), nous utilisons des fonctions
récursives!

```erlang

boucle_infinie() ->
  io:format("Je suis une boucle qui n'en finie pas de boucler!~n"),
  boucle_infinie().
  
```

Une   boucle   infinie   peu    se   faire   dans   n'importe   quelle
langage. D'ailleurs,  le paradigme fonctionnel peut-être  réalisé dans
tous  les langages,  mais  la  syntaxe ne  se  prête  pas forcement  à
l'exercice. Une fonction  récursive en C par exemple,  n'est pas aussi
simple à faire.

```c

void 
boucle_infinie(void) {
  printf("Je suis une boucle qui n'en finie pas de boucler!\n");
  boucle_infinie();
}

```

ou encore en python,

```python

def boucle_infinie:
  print "Je suis une boucle qui n'en finie pas de boucler!"
  boucle_infinie()

```

ou bien en javascript.

```javascript

function boucle_infinie() {
  console.log("Je suis une boucle qui n'en finie pas de boucler!");
  boucle_infinie();
}

```

Vous   me   direz...    Il   n'y   a  qu'une   ou   deux   lignes   en
plus. Malheureusement, ça  se complique quand nous  parlons d'état. Un
état, pour  faire simple, est  l'image de  quelque chose à  un instant
T. Reprennons l'exemple de la conversation. Lorsque vous êtes en train
de parler avec  Bob, vous êtes dans l'état: "Parler  avec Bob". Durant
votre  conversation, Eve  vous  bouscule, vous  changez alors  d'état:
"Réagir à  la bousculade". Eve  s'excuse et repars, vous  pouvez alors
reprendre votre état  de départ, l'état "initial":  "Parler avec Bob".
Nous verrons  un peu plus loin  que ce modèle s'appelle  une machine à
état  finis,  ou "Finite  State  Machine"  (FSM) en  anglais.  Comment
réaliser ce code en Erlang?

```erlang

alice_fsm(Etat) ->
	receive
	  "initial" -> 
	     io:format("Alice parle avec Bob!~n"),
	     alice_fsm("Parler avec Bob");
	  "bousculer" ->
	     io:format("Alice se fait bousculer par Eve"),
	     alice_fsm("bousculer par Eve")
	end.

start() ->
  spawn(fun() -> alice_fsm("initial") end).

```

Ce petit bout de code permet de définir grossièrement 2 états:

 1. l'état initial, où Alice parle avec Bob
 2. l'état perturber, où Eve bouscule Alice.

Avant de vous laisser baver devant  le code à essayer de le comprendre
par vous même, je vais essayer de l'expliquer simplement:

```alice_fsm(Etat) ->``` est la  déclaration de la fonction alice_fsm,
qui prend  un argument  nommé Etat. En  Erlang, les  variables doivent
obligatoirements  commencées par  une  lettre  majuscule. La  "flèche"
définit donc les actions qui vont être effectuée par la fonction.

```receive``` est  un mot  clé du  langage qui  permet de  regarder la
boite mail  du processus. Les messages  qui se trouvent dans  la boite
aux lettres  ne sont  que des structures  de données  Erlang (integer,
atom,  liste, tuples,  etc).  Cette fonction  utilise  le principe  de
"pattern matching" propre aux langages fonctionnels.

Le pattern  matching, pour  faire simple,  c'est de  se dire  que nous
savons déjà  la valeur que  va prendre  une variable. Dans  notre cas,
nous savons que nous avec que 2 états, et nous savons la valeur de ces
états (initial  ou bousculer).  Donc,  quand le processus  va regarder
dans sa boite  aux lettres et va recevoir le  message "initial", il va
passer dans l'état "initial". Si  il reçoit le message "bousculer", il
passera dans l'état bousculer.

```io:format("String")```    est    une   fonction    équivalente    à
```printf()``` en C, ou ```echo``` en  PHP ou bien encore ```put``` en
Ruby.  Cette  fonction permet  d'afficher  un  message sur  la  sortie
standard.

Vous  noterez qu'après  avoir appeler  la fonction  ```io:format()```,
nous  utilisons le  principe de  la boucle  récursive en  rappelant la
fonction ```alice_fsm()``` avec pour argument le nouvel état!

La dernière partie du code, qui déclare la fonction ```start()```
permet simplement de créer un micro-processus en appelant la fonction
```spawn()```, cette dernière prend pour argument une fonction
anonyme, qui doit elle lancé la fonction qui va boucler.

À noter que cette fonction retourne un ```pid``` ou process-id, qui va
nous servir pour parler avec notre micro-processus, en lui envoyant du
courrier! D'ailleurs... Et si on lui parlait?

```erlang
parler(Pid) ->
  Pid ! "initial".
  
bousculer(Pid) ->
  Pid ! "bousculer".
```

Ces  2 fonctions  permettent  de faire  changer  l'état d'Alice,  elle
prenne chacune le process-id comme  argument et utilise un petit sucre
syntaxique   ```!```  qui   est   un  raccourcis   pour  la   fonction
```send```.  Nous  envoyons  simplement "bousculer"  ou  "initial"  ou
process-id contenu dans la variable ```Pid```.

Que neni! Je vous avais promis de vous le faire dans un autre langage!
Essayons de reproduire "simplement" ce comportement en C. Déjà de quoi
avons nous besoins?

 . d'une queue permettant de recevoir les messages
 . d'une fonction qui va être dans 2 états
 . d'un moyen d'envoyer des messages à la fonction lancée.

```c

```
 
# Annexes

## Liens

 * http://www.erlang.org/
 * http://www.erlang-factory.com/
 * http://www.tryerlang.org/

## Bibliographie

### Introducing Erlang

 * http://shop.oreilly.com/product/0636920025818.do
 
Un  petit  livre bien  sympas  qui  fait  office de  référentiel.  Une
personne qui connait déjà un peu Erlang s'y retrouvera mieux.
 
### Learn You Some Erlang for Great Good

 * http://learnyousomeerlang.com/
 
Un apprentissage en profondeur  pour débutant/avancé et la possibilité
de lire le livre directement sur le web en fait la référence.
 
### Erlang and OTP in action

 * http://www.manning.com/logan/
 
Très bon livre avec des  exemples concrets (création d'un serveur RPC,
d'un   serveur   http   basique),  permettant   de   voir   réellement
l'application d'Erlang  au monde  réel. Une connaissance  d'Erlang est
plus que recommandée.
 
### Erlang Programming, A Concurrent Approach to Software Development

 * http://oreilly.com/catalog/9780596518189
 
Un livre  qui pourrait  être en quelque  sorte la  suite d'Introducing
Erlang. Il permet de voir d'autres applications et quelques usages peu
connu d'Erlang (programmation d'interface graphique par exemple).
 
### Programming Erlang, Software for a Concurrent World

 * http://pragmaticprogrammer.com/titles/jaerlang/index.html
 
Seconde  édition  sortie récemment,  ce  livre  a  été écrit  par  Joe
Armstrong, l'un des concepteurs d'Erlang  et est actuellement le livre
le  plus  complet pour  avoir  de  bonnes  bases  et voir  toutes  les
possibilités offertes par ce langage.
 
### Designing for Scalability with Erlang/OTP

 * http://shop.oreilly.com/product/0636920024149.do

Vous savez développer  en Erlang, vous voulez en savoir  plus sur OTP,
sur  le concurrentiel,  sur  la haute  disponibilité et  l'évolutivité
d'Erlang? Ce livre  est une petite merveille qui  permet d'étendre son
champ de vision. Je recommande.

### Building web applications with Erlang

 * http://shop.oreilly.com/product/0636920021452.do
 
Un livre  qui présente YAWS (Yet  Another Web Server), un  serveur web
intégralement  écrit   en  Erlang   et  supportant   la  configuration
apache. Actuellement, si vous voulez créer un simple site web, cowboy,
mokiweb  ou   webmachine  seront  suffisant  (et   souvent  bien  plus
performant).

### Handbook of Neuroevolution Through Erlang
 
 * https://www.springer.com/us/book/9781461444626
 * https://www.youtube.com/watch?v=TcUqGIHq8rA
 * http://www.erlang-factory.com/upload/presentations/536/ErlangConferencePresentation_2012.pdf

Livre très complexe, issue directement  du monde de la recherche, mais
permet de voir l'application d'Erlang  dans un domaine particulier: la
neuroscience.

###  Stuff Goes Bad: Erlang in Anger 

 * https://www.erlang-in-anger.com/

Par l'auteur de "Learn You Some  Erlang for Great Good", un contenu un
peu  plus étendu  sur des  sujets  plus complexe,  comme l'analyse  de
trace, des optimisations etc...

### Seven Concurrency Models in Seven Weeks

 * https://pragprog.com/book/pb7con/seven-concurrency-models-in-seven-weeks
 
Un  livre qui  montre plusieurs  modèles pour  gérer la  programmation
concurrentiel, passant  par Java, C, Erlang,  Clojure... Uniquement si
vous voulez en savoir plus sur le parallélisme et le concurrentiel.

## Videos

La  communauté Erlang  est très  active et  partage ses  connaissances
facilement!

 * https://www.youtube.com/channel/UCKrD_GYN3iDpG_uMmADPzJQ
 * https://www.youtube.com/channel/UC_QIfHvN9auy2CoOdSfMWDw

## Papers

Quelques  papiers  en  provenance  du  monde de  la  recherche  et  de
l'industrie   permettant   de   montrer   encore   d'autres   exemples
d'applications réelles  avec Erlang.  Certains de  ces papiers  ont un
niveau très élevé, donc... À lire à tête reposée!

 * [A History of Erlang](http://www.math.bas.bg/bantchev/place/erlang/a-history-of-erlang.pdf)

 * [Making reliable distributed systems in the presence of sofware errors](http://erlang.org/download/armstrong_thesis_2003.pdf)
 
 * [Parameterized modules in Erlang](http://www.erlang.se/workshop/2003/paper/p29-carlsson.pdf)
 
 * [A Practical Subtyping System For Erlang](http://homepages.inf.ed.ac.uk/wadler/papers/erlang/erlang.pdf)

 * [JErlang: Erlang with Joins](http://www.doc.ic.ac.uk/teaching/distinguished-projects/2009/h.plociniczak.pdf)
 
 * [A Comparative Study of Refactoring Haskell and Erlang Programs](https://www.cs.kent.ac.uk/projects/refactor-fp/publications/huiqing-ComparativeStudyRefactoringHaskellErlangPrograms.pdf)
 
 * [Investigating the Scalability Limits of Distributed Erlang](http://www.dcs.gla.ac.uk/~amirg/publications/DE-Bench.pdf)
 
 * [Hyper-Erlang Distribution Model and its Application in Wireless Mobile Networks](http://www.fang.ece.ufl.edu/mypaper/winet01_5.pdf)
 
 * [Erlang Security 101](https://www.nccgroup.trust/globalassets/our-research/uk/whitepapers/2014/erlang_security_101_v1-0.pdf)
 
 * [Bit-level Binaries and Generalized Comprehensions in Erlang](http://user.it.uu.se/~pergu/papers/erlang05.pdf)
 
 * [Automatic Veri cation of Erlang-Style Concurrency](http://mjolnir.cs.ox.ac.uk/soter/papers/sas13.pdf)
 
 * [Concurrent Programming in Erlang](http://erlang.org/download/erlang-book-part1.pdf)

