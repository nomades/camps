###### tags: `tcpdump` `digital privacy` `web security`

# [[IndieCamp Nevez](frama.link/indiecamp-nevez-2017)] Atelier d'initiation à la sécurité informatique (commande `tcpDump`)

![](https://i.imgur.com/Xt5EY7n.jpg)
> Photo prise par Matthieu Brient (licence CC-BY-NC)

## Contexte de l'atelier

Le mardi 04 juillet 2017, après notre arrivée et installation à Nevez (pour l'[indiecamp](https://github.com/LeBiome/camps/blob/master/indie_camp_2017/nevez_2017.md)), @Xavier C nous proposé une initiation à la sécurité informatique autour de la commande [tcpDump](https://fr.wikipedia.org/wiki/Tcpdump). 

En pratique, cette commande permet de "sniffer" le flux de données (qui peut être volumineux) d'un réseau informatique. Dans le cadre de cette initiation, elle a été testée avec MacOS. 

[Lien vers la section dédiée du wiki de l'Indie Camp](http://movilab.org/index.php?title=IndieCamp_2017_N%C3%A9vez#Tcpdump_Internets_et_libert.C3.A9s)

## Hacker son adresse MAC

### A propos de tcpdump

`tcpdump` permet d'avoir une analyse en direct d'un réseau ou d'enregistrer la capture dans un fichier. Il permet d'écrire des filtres pour sélectionner les paquets à capturer/analyser.

### Installer tcpdump

Pour commencer, il faut installer tcpdump. Ouvrir un terminal et taper : 

    apt-get install tcpdump
    
### Comprendre tcpdump

Une fois l'installation complète, lancer la commande tcpdump en tapant : 

    tcpdum
 
Ex. de capture (Source : Tony Chenau, [Lea-linux/tcpdump](http://lea-linux.org/documentations/Tcpdump),  GNU free doc)

![](https://i.imgur.com/ww5MjsO.jpg "source Lea-linux")

Détails champ à champ de la ligne bleue (attention, le format de sortie dépend du type de protocole analysé et des options passées) :

* l'heure
* le type de protocole (ici, IP)
* l'IP source.port_source > l'IP
* destination.port_destination
* les flags TCP : il peut y en avoir plusieurs pour un même paquet, on verra apparaître les lettres suivantes pour symboliser un drapeau levé :
  * S (SYN)
  * F (FIN)
  * P (PUSH)
  * R (RST)
  * W (ECN CWR)
  * E (ECN-Echo)
  * ou juste un point comme ici quand on n'a pas de drapeaux
* ack numéro : le numéro de séquence que l'on attend de la part de l'autre interlocuteur à son prochain envoi de paquets
* win numéro : le numéro représente la taille de la fenêtre TCP
* <des options> : les options TCP portées par le paquet, ici, on n'a que le timestamp

Les trois dernières lignes de la capture représentent :

* 11 packets captured : c'est le nombre de paquet que tcpdump a reçu de l'OS et a traité
* 22 packets received by filter : c'est le nombre de paquets qui ont été capturés car ils correspondaient aux filtres, cela ne signifie pas qu'ils auront été traités par tcpdump
* 0 packets dropped by kernel : les paquets qui n'ont pas été capturés par l'OS car il n'y avait pas assez de place dans son buffer de réception.
 
### Test de tcpdump

Dans un terminal lancer pour "Affichage verbeux (verbose)":

    tcpdump -v
   
Il s'agit simplement de brancher - par le port USB - son téléphone mobile (ou tout autre objet communicant) à l'ordinateur avec un terminal en route sur "tcpdump". Cela renvoie : 
- passage de données remontées dans le terminal en IP à une IP6
- une adresse mac affichée et tout un tas de données (à anonymiser)

## Ressources à consulter 

* https://openmaniak.com/fr/tcpdump.php
* http://lea-linux.org/documentations/Tcpdump
* Pour aller plus loin et s'entraîner, [MalTran](http://malware-traffic-analysis.net/) source and exercice for trafic analysis and malware


## Licence du document

_Initiation à la recherche d'une sécurité internet_ (Indiecamp et contributeurs) est mis à disposition selon les termes de la <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">licence Creative Commons Attribution 4.0 International</a>.

<img style="display: block; margin: 0 auto;" src="https://mirrors.creativecommons.org/presskit/buttons/88x31/png/by.png" width="40%">


