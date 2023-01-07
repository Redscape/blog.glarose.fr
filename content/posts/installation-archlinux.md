+++
categories = ["Tech"]
title = "Une installation d'ArchLinux en moins de 30 minutes, c'est possible !"
date = "2021-11-30T23:00:00"
author = "Redscape"
authorTwitter = "redscape_tech"
cover = "/img/arch.png"
tags = ["Tech"]
showFullContent = false
readingTime = true
draft = false
+++

Vous l'aurez remarqué, ce blog, et bien, oui, il est un peu sombre.

{{< figure src="/img/michael-mouritz-WXX_DhjlmD4-unsplash.jpg" caption="J'aime ces ambiances. Et prends toi une grosse image à charger au passage." >}}

Ceci dit, la photo est assez raccord avec le temps actuel.

Alors, on va sortir un peu de tout ça et parler tech !
A l'occasion, si jamais j'ai de l'inspiration, j'en ferai un blog à part, mon logiciel de notes commençant à être rempli de trucs, astuces, que j'aimerais bien partager.

BREF.

Aujourd'hui, retour, en quelque sorte, aux sources.

Retour sur mon retour sur Archlinux... 
Il y a tant de choses à dire sur cet OS, qui attire autant les archifans que les haters.
Il y a aussi [The Elite](https://music.apple.com/fr/album/the-elite/1457603296?i=1457603297) (oui, je mets du hardstyle, parce que je n'ai pas peur du mauvais goût) qui vouent à cet OS un culte sans fin, traitant allègrement les autres de gros noobs (si, si, allez faire un tour sur [Reddit](https://reddit.com/r/archlinux)). Que voulez-vous, le monde des OS Linux peut tout autant se révéler le merveilleux quand on souhaite l'utiliser, mais tout aussi imbécile quand le prosélytisme y est pratiqué.

Donc ici, point de critiques sur d'autres OS, chacun fait ce qu'il veut.

Alors, qu'est ce qui m'a conduit à mettre Arch sur ma machine de boulot ?

Je me suis aperçu au fur et à mesure des missions confiés par mon ESN que Linux me serait plus utile que Windows (spoiler : sans blague ?!)

*(Parenthèse, avant de continuer : je sais que l'on dit GNU/Linux et non pas Linux, mais j'ai la flemme.)*

J'ai donc installé tour à tour 2 OS, Ubuntu puis Fedora, et puis j'ai fait la moue. 
Mouais. 
Ca marche hein, mais ça n'est pas bandant. Comme Windows en fait. Et fait étonnant, des bugs ! Rien à voir avec ceux que j'ai connu il y a 15 ans, quand j'ai commencé à toucher mon 1er Linux (Ubuntu 7.04), mais bordel, la sortie de veille, quand même.
Côté DM, comme je suis connu pour être original, je suis parti sur GNOME, plus parce que je le connaissais que par choix esthétique. 
Sauf que j'ai remarqué une étange sensation de lourdeur. Il est vrai que GNOME transporte avec lui foultitude de logiciel, et qu'il peut devenir pachyderme, avant même de faire quelque chose de sa session. C'est autant le cas sur Ubuntu que sur Fedora.

Alors, le week-end dernier (je finis de rédiger ce billet Mardi 30 Novembre 2021), il faisait moche, et je me suis souvenu de 2 choses :
- ça faisait longtemps que je ne m'étais pas pris la tête à installer un truc badass-compliqué.
- je ne me souviens plus de la 2ème raison.

Ca tombe bien, Next Inpact en a fait [un article dis donc](https://www.nextinpact.com/article/49005/installer-simplement-arch-linux-cest-possible) ! 
La mission : tuer Windows pour faire redéclarer ma flamme à Linux.

{{< figure src="/img/la_flamme_5f6a012978534_0.webp" caption="Je n'ai toujours pas honte, oui j'ai aimé cette série." >}}

Cependant, 7 ans que je ne l'avais plus installé cet Arch, rouillé je l'étais, mais bizarrement, toujours aussi excité.

L'article de NXi nous apprends qu'un nouvel outil, `archinstall`, est désormais disponible pour simplifier l'installation. Le moins que l'on puisse dire, c'était que j'étais loin d'imaginer à quel point le mot "simple" allait être aussi respecté au pied de la lettre. La capacité de cet outil pour installer un système "aussi" complexe (faut pas déconner, j'ai l'impression d'être un connard d'élitiste) tiendrait presque de la magie si je n'étais pas informaticien. 
Sans rire, il m'a fallu 10 minutes entre le temps où j'ai entré la commande dans l'installeur d'Arch et le moment où GNOME m'a accueilli. 
C'est stupéfiant. C'est même plus rapide qu'une installation d'Ubuntu ou Fedora. 

L'outil, construit en Python, pose quelques questions, comme le zone temporel, le disque à utiliser et son partitionnement, le type de machine que vous souhaitez avoir entre minimal, server, desktop, et quelques autres questions que je vous laisserai le soin de découvrir (si je n'avais pas la flemme, je vous aurai mis quelques captures, veuillez excuser l'auteur).
Et ensuite, y'a plus qu'à attendre.

{{< figure src="/img/pub-zelda-III.jpg" caption="Parce que j'ai envie." >}}

10 petites minutes plus tard (qui ne m'auront pas fait devenir squelette), on a le droit à l'écran de login de GNOME et surtout à un bureau propre et épuré, sans aucun ajout superflu. Bien sûr il manque un tas de choses, mais c'est à vous d'apporter les paquets, grâce au célèbre `pacman`, mais également à [AUR`](https://aur.archlinux.org) permettant d'obtenir ainsi une bibliothèque quasiment illimité (attention quand même, ce sont des paquets communautaires, ne provenant pas de l'équipe derrière Archlinux, à vos chats, risques et périls).

On peut se construire un environnement sur-mesure, sans avoir de logiciels ou de dépendances inutiles. Pour ma part, il a été facile de retrouver mes logiciels favoris, dont le Visual Studio Code que j'affectionne tant et dans lequel j'ai écrit ce billet. 
Oui, je sais, vous êtes en train de vous étrangler, cet exemple est valable uniquement dans le cadre de ce billet.
Il est marrant de voir que c'est un logiciel Microsoft que j'installe en premier sur un Linux. Tout comme Edge d'ailleurs. Naaaan, je déconne.

En vrai, la situation a vraiment changé en 10 ans, époque à laquelle j'animais [une émission sur le logiciel libre](https://enfluxlibre.lepodcast.fr)... Ce temps semble désormais totalement révolu.

{{< figure src="/img/steve-ballmer-microsoft-offers-best-both-worlds-windows-8.jpg" caption="VF = Coucou Steve ! Version j'en n'ai rien péter = Coucou connard !" >}}

Mais je crois que ce qui m'avait tant manqué sous Windows, c'est la personnalisation. Je peux avoir un environnement de bureau utilisant les codes de couleur que l'on appelle [Nord](https://nordtheme.com) permettant d'avoir une ambiance sombre et bleuté, très en vogue en ce moment et surtout, agréable à l'oeil.

Alors, désormais qu'Arch est revenu sur une machine chez moi, quel bilan en tirer ?
Pour le moment, je redécouvre. J'aurai plus de recul dans 1 mois, et surtout, un retour complet en utilisation dans le cadre du travail.

Je crains, comme il y a 7 ans, les `pacman -Syu` qui casserait tout le système, mais je suis bien moins casse-cou qu'à l'époque. Surtout, je remarque que l'envie d'aller voir ailleurs se fait moins en moins pressant. Le distro-hopping que je ne fais plus depuis des années y joue pour beaucoup. La volonté d'avoir une machine de prod fonctionnel, et le fait que Windows, ça ne se bidouille pas, auront eu raison de mon impatience de l'époque.

Et j'aime à me rassurer (oui, j'ai toujours eu un problème d'aimer Linux, alors je me rassure^^) en me disant que Windows est toujours installé sur ma bécane principale et qu'il est hors de question de la passer sous Linux.
Le pragmatisme est une bonne conseillière...
Non, la multiplicité des OS, c'est aussi avoir la curiosité, sans prosélytisme, de faire ce que j'ai envie.

Le fait d'avoier Linux, c'est aussi une manière pour moi de reboucler mon histoire avec le pingouin, et surtout, de commencer ma transition vers l'ops (coucou [WeScale](https://www.wescale.fr) !).

En attendant, un jour, de partir sur Mac :)...

Naaan, je déconne.

Quoique.

*Redscape*