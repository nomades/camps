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

Reprennons notre histoire du début et essayons de reproduire le
comportement des personnages qui parlent ensemblent.

```
Alice parle avec Bob.
Bob parle avec Alice.

```

Nous avons donc 2 acteurs qui parlent ensemblent et qui sont dépendant
l'un de l'autre. Le fait de parler avec une autre personne peut-être
considéré comme un état. "Alice parle avec Bob", "Bob parle avec
Alice", peut-être écrit de la façon suivante:

```erlang

alice(Etat) ->
  receive
    {parle, Avec} -> 
	  io:format("Alice parle avec ~p~n", [Avec])
  end,
  ok.
  
bob(Etat) ->
  receive
    {parle, Avec} ->
	  io:format("Bob parle avec ~p~n", [Avec])
  end,
  ok.

```

Je suppose que vous n'avez jamais fais d'Erlang, je vais donc vous
expliquer le fonctionnement de ce petit bout de code.

```erlang

% Les commentaires en Erlang sont définis par un %, tout ce qui se 
% trouve derrière n'est pas interprété.

% nous allons déclarer une fonction, alice(), qui va prendre un 
% argument (variable) qui s'appelera Etat.
alice(Etat) ->
  % À partir d'ici, nous sommes dans le contexte d'exécution
  % de la fonction alice/1. alice/1 est une notation propre
  % à Erlang, et qui signifie simplement le nombre d'argument
  % que va prendre la fonction. Dans notre cas, alice ne prends
  % qu'un seul argument, donc, son nom est alice/1.
  
  receive
    % receive est une fonction spécial d'Erlang, qui fait d'ailleurs
	% partit de sa syntaxe. Cette fonction permet de lire la boite 
	% au lettre du processus. À partir de là, nous avons accès au
	% contenu de la queue. Pour y accéder, nous utilisons ce que 
	% nous appelons du pattern matching. Nous récupérons tout
	% simplement ce que nous connaissons déjà.
	
	{parle, Avec} ->
	  % ici, nous recherchons dans la boite mail, tout message qui
	  % est un tuple de longueur 2, ayant pour première valeur un
	  % atom 'parle' et pour deuxième valeur, n'importe quelle
	  % donnée.
	  
	  io:format("Alice parle avec ~p~n", [Avec])
	  % cette fonction permet simplement d'afficher un message
	  % sur la sortie standard.

  end,
  % nous sortons de la boite mail. En Erlang, les instructions
  % sont séparés par une ","
  
  ok.
  % et nous retournons simplement la valeur 'ok' qui est un atome.
  % Le "." à la fin de la ligne indique la fin du contexte
  % d'exécution de la fonction alice.

```

Tiens... Vous avez remarquez? 2 fonctions qui font la même chose? Ce
n'est pas très jolie tout ça! Nous allons donc dire que le nom des
personnages fait partit des états.

```erlang
personnage(Name, Etat) ->
  receive
    {parle, Avec} ->
	  io:format("~p parle avec ~p~n", [Name, Avec])
  end,
  ok.
```

Mieux! Maintenant que nous avons notre fonction, comment faire pour
créer un processus à partir de cette fonction? Tout simplement avec
l'aide de la fonction ```spawn/1```. 

```erlang

start_personnage(Name, Etat) ->
  % contexte d'exécution de la fonction start_personnage
  
  spawn(fun() -> personnage(Name, Etat) end).
  % spawn/1 prend comme argument une fonction anonyme (ou lambda).
  % une fonction anonyme en erlang est définie de la façon suivante:
  %   fun(Arg1, Arg2, ArgN) -> 
  %     function(Arg1), function(Arg2), function(ArgN) 
  %   end.
  % Si l'exécution est réussie, spawn retourne l'identifiant du
  % processus.
```

## Voyons grand!

Erlang a  été prévu dès  son origine  pour fonctionner dans  un réseau
décentralisé et maillé. Qu'est-ce que  ça veux dire? Simplement que la
machine virtuelle peut s'interconnecté  à d'autres machines virtuelles
et créé un réseau où tous les noeuds connectés se connaissent.

```
  ________ 	    ________
 |	  |	   (   	    )
 | noeud1 |-------( internet )	       	  
 |________|  	   (________)	      	  
	      	     |	    	      	  
	      	     | 	    	      	  
  ________     	     | 	       	      	  
 |	  |	     |	 	      	  
 | noeud2 |---+	     | 	       	       	  
 |________|   |	    _|__________      	  
	      |	   (		)     	  
	      +---( réseau local )    	  
  ________    |	   (____________)     	  
 |     	  |   |			      
 | noeud3 |---+			      
 |________|			      
				      
				      
```				      

Ce schéma  montre qu'il est possible  d'interconnecté plusieurs noeuds
au  travers   de  plusieurs  réseaux.  Ces   derniers  pourront  alors
communiquer ensemble et  ainsi partager la charge ou  avoir des tâches
spécifiques.

Ce qui est probablement le plus  intéressant dans ce modèle, c'est que
les structures  de données entre  les noeuds sont compatibles,  et que
les méthodes  de communications entre  les noeuds ne changent  pas! Il
donc possible de  communiquer simplement entre le noeud3  et le noeud1
avec les commandes que nous avons vu avant!

Encore mieux, Erlang intègre un système de RPC (Remote Procedure Call)
très performant,  permettant d'exécuter n'importe quelle  tâche sur la
totalité du réseau  interconnecté. Si vous avez un noeud  qui est sous
linux et un autre sous windows, qu'un outil n'est présent que sur l'un
ou  l'autre  système, Erlang  permet  d'y  avoir simplement  accès  en
faisant abstration des données!

Évidemment,  tout  n'est  pas  rose. Un  environnement  clusterisé  et
distribué devrait être  sécurisé en amont et  en aval. Habituellement,
dans un lieux connu. La sécurité  de connexion est enfantine mais fera
l'affaire dans des petites structures  où les réseaux locaux suffisent
le pluspart du temps.

Les noeuds partagent simplement une  information: un cookie. Ce cookie
est créé  par l'utilisateur ou  généré au  lancement du noeud.  Si les
autres  noeuds  n'ont pas  le  même  cookie,  la connexion  est  alors
impossible et le noeud reste isolé.

Plus récemment,  depuis les dernières versions  d'Erlang, la connexion
chiffrée entre  les noeuds  a été  améliorée et  simplifié, permettant
d'utiliser des certificats pour les autorisations de connexions.

Et si on  essayait de faire un petit cluster  rapidement, en local? Le
petit script suivant  va vous permettre de lancer 3  noeuds qui seront
interconnectés ensemble et ainsi de voir ce qui se passe d'un point de
vue réseau.

```sh

```

Lançons un processus  sur le noeud1. Ce  dernier doit-être enregistré,
un  processus "anonyme"  (seulement avec  son  pid) ne  peux pas  être
directement join simplement.

```erlang

MyProcess = fun() F ->
  Hide = "my data!",
  receive 
    {Node, Pid, Message} ->
      {Node, Pid } ! { received, {Node, Pid}, Hide, Message },
	  F();
	_ ->
	  F()
  end end.

Pid = spawn(MyProcess).
erlang:register(myprocess, Pid).

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

