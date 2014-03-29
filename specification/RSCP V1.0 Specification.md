# Really Smart Calculator Protocol V1.0 Spécification

    Author              : Yann Malherbe, Cédric Rudareanu, HEIG-VD
    Last revision date  : 21.03.2014

    Revision history
             27.03.2014 : First version

## Introduction

Le protocole RSCP (Really Smart Calculator Protocol) permet une
communication simple entre un client et un serveur.

Son but est d'être utilisé entre une smart calculatrice et un serveur.

Il est basé sur des commandes de type texte en UTF-8.

## Terminologie

Cette spécification utilise un certain nombre de termes pour se référer
aux rôles des différents participants à la communication RSCP.

### Connection

Il y a une couche de transport virtuelle qui permet d'établir la
communication entre le client et le serveur.

### Messages

La base de la communication RSCP consiste en un échange de messages
structuré via la connection dont la syntaxe est définie dans la section
"Type de message, syntaxe et sémantique".

### Requêtes 

Un message de requête RSCP (tel que définit dans la section "Type de
message, syntaxe et sémantique").

### Réponses

Un message de réponse RSCP (tel que définit dans la section "Type de
message, syntaxe et sémantique").

## Protocole Overview

La connection RSCP est initiée par le client en envoyant un message de
requête au serveur. Ce dernier répond soit par une authentification ok
dans le cas d'un serveur public. Soit par une demande d'authentification
qui amenera le client à se connecter ou créer un compte.

Une fois l'authentification établie, des messages standard de type
requête/réponse transitent entre le Smart Calculator et le serveur comme
ci-dessous.

Client----[Requête]----\>Server

Client\<---[Reponse]-----Server

### Architecture du système

Ci-dessous l'architecture du système de communication entre le client et
le serveur.

|-------|

|Server | |------|

| |\<------------\>|Client|

| | |------|

|-------|

### Composants du système

### Interaction entre composants

## Détails du protocole

### Protocoles de transport et de connections

### Gestion d'états

### Type de message, syntaxe et sémantique

### Diverses considérations

### Sécurité

## Exemples

## Références
