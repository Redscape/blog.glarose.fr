+++
categories = ["Tech"]
title = "Installation de Vaultwarden avec Docker Compose"
date = "2022-06-01T00:00:00+02:00"
author = "Redscape"
authorTwitter = "redscape_music"
cover = "/img/vaultwarden.png"
tags = ["Tech"]
keywords = ["", ""]
description = ""
showFullContent = false
readingTime = true
draft = true
+++

Si vous me suivez sur [Twitter](https://twitter.com/redscape_music), vous savez sans doute que je me suis remis dans l'hébergement de certains de mes services, plus pour la partie financière que pour de réelles convictions, ça me permet de tester mes connaissances acquises dans le cadre de mon travail de devops et de continuer à développer mes compétences dans ce domaine.
C'est pourquoi j'ai décidé d'installer [Vaultwarden](https://github.com/dani-garcia/vaultwarden), une solution open-source, forké à partir de [Bitwarden](https://bitwarden.com), une solution logicielle permettant le stockage de mots de passe de façon sécurisé.

J'utilise Bitwarden depuis 2018, après avoir passé des années avec Keepass. Mais comme beaucoup, j'ai quitté Keepass à cause de son interface plus que vieillote, ses clients mobiles développés sans réel volonté de flatter l'oeil (et ouais, je suis aussi un utilisateur final comme les autres), et le fait qu'un fichier contenant l'ensemble de mes mots de passes, ça me faisait un peu flipper (même si je n'ai connu qu'une seule casse réelle de ce fichier, heureusement réparé assez rapidement grâce à une sauvegarde, on ne le répètera jamais assez FAITES DES SAUVEGARDES !!).

Je donne également 10€/an pour Bitwarden, ce qui me permet d'avoir des fonctionnalités supplémentaires (une sorte de premium, mais que eux qualifient volontiers de soutien à l'équipe de dev), fonctionnalités que je n'utilise même pas.
J'ai même hébergé cette appli fût-il un temps, mais il était vraiment overload par rapport à sa fonction primaire, comprendre stocker des mots de passes. Qui plus est, il tournait sur une base SQL Server, j'ai vu mieux en terme de briques logicielles logique.

Face à ce constat, je suivais d'un coin de l'oeil un fork qui s'appelait à l'époque bitwarden_rs, développé en Rust si je ne m'abuse, et surtout, avec un autre type de base de données, à savoir SQLite ou PostgreSQL (à confirmer, je ne sais pas si c'était proposé à l'époque). 

Devant cela, et comme je le disais en introduction, j'ai décidé de remonter une stack contenant quelques applis essentiels, et c'est comme ça que je me suis mis à m'intéresser à ce fork qui s'était renommé Vaultwarden entre-temps.

C'est du classique, Traefik pour la partie reverse proxy, et une stack toute simple composé de l'appli seul.
Sans plus attendre, le fichier `docker-compose.yml`

```yaml
version: "3"
services:
  vaultwarden:
    image: vaultwarden/server:latest
    container_name: vaultwarden
    restart: always
    volumes:
      - /srv/docker_stack/vaultwarden/bw-data:/data
    environment:
      - WEBSOCKET_ENABLED=true
      - SIGNUPS_ALLOWED=true
      - DISABLE_ADMIN_TOKEN=true
      - INVITATIONS_ALLOWED=false
      - DOMAIN=https://xxx.xxx.fr
    ports:
      - 85:80
      - 3012:3012
    networks:
      - traefik
    labels:
      - "traefik.enable=true"
      - "traefik.http.routers.vault-http.entrypoints=http"
      - "traefik.http.routers.vault-http.rule=Host(`xxx.xxx.fr`)"
      - "traefik.http.routers.vault-http.middlewares=vault-https@docker"
      - "traefik.http.routers.vault.entrypoints=https"
      - "traefik.http.routers.vault.rule=Host(`xxx.xxx.fr`)"
      - "traefik.http.routers.vault.tls=true"
      - "traefik.http.routers.vault.tls.certresolver=cloudflare"
      - "traefik.docker.network=traefik"
      - "traefik.http.middlewares.vault.headers.customrequestheaders.X-Forwarded-Proto=https"
      - "traefik.http.middlewares.vault.headers.accessControlAllowOrigin=*"
      - "traefik.http.routers.vault.service=vault@file"
      - "traefik.http.services.vault.loadbalancer.servers.port=85"
networks:
  traefik:
    external: true
```

Rien d'extraordinaire dans la configuration de ce docker-compose, étudions simplement les variables d'environnements (que j'aurai pu mettre dans un .env) :

- WEBSOCKET_ENABLED=true
*Obligatoire, sinon, ça ne communique pas*

- SIGNUPS_ALLOWED=true
*Grâce à cette variable, vous pouvez bloquer l'enregistrement d'un tiers...voire de vous-même. A désactiver pour une 1ère inscription au service*

- DISABLE_ADMIN_TOKEN=true

- INVITATIONS_ALLOWED=false

- DOMAIN=https://xxx.xxx.fr
*Il ne me semble pas que ça soit nécessaire*

Bref, une config toute bête, que vous pouvez complexifier avec du PostgreSQL si vous le souhaitez. N'ayant jamais testé cette configuration particulière, impossible de savoir si ça a une réelle valeur ajoutée face à la base SQLite que j'utilise.

L'avantage de ce fork, c'est que, outre sa légèreté par rapport au mastodonte qui lui sert d'aieul, il est compatible avec les clients Bitwarden, que ça soit sur navigateur, applis de bureaux (beurk, Electron), et applis mobiles (iOS et Android).
Pas de pertes en fonctionnalités donc. En terme de paramètres c'est très simple, il suffit d'indiquer sur quelle serveur taper en cliquant sur la roue crantée, exemple ici avec l'application sous Linux (mais cette roue crantée existe également sur tous les autres environnements) :

{{< figure src="/img/bitwarden-reglage.png" caption="C'est beau quand c'est aussi simple" >}}

Indiquez simplement votre URL d'accès au service, *et voilà* le tour est joué, connectez-vous avec les identifiants crées précédemment, et vous aurez accès à votre coffre-fort.