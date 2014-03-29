# Really Smart Calculator Protocol V1.0 Spécification

    Author              : Yann Malherbe, Cédric Rudareanu, HEIG-VD
    Last revision date  : 21.03.2014

    Revision history
             27.03.2014 : First version

# Introduction

Le protocole RSCP (Really Smart Calculator Protocol) permet une
communication simple entre un client et un serveur.

Son but est d'être utilisé entre une smart calculatrice et un serveur.

Il est basé sur des commandes de type texte en UTF-8.

# Terminologie

Cette spécification utilise un certain nombre de termes pour se référer
aux rôles des différents participants à la communication RSCP.

## Connexion

Il y a une couche de transport virtuelle qui permet d'établir la
communication entre le client et le serveur.

## Messages

La base de la communication RSCP consiste en un échange de messages
structuré via la connection dont la syntaxe est définie dans la section
"Type de message, syntaxe et sémantique".

### Requêtes

Un message de requête RSCP (tel que définit dans la section "Type de
message, syntaxe et sémantique").

### Réponses

Un message de réponse RSCP (tel que définit dans la section "Type de
message, syntaxe et sémantique").

# Protocole Overview

La connection RSCP est initiée par le client en envoyant un message de
requête au serveur. Ce dernier répond soit par une authentification ok
dans le cas d'un serveur public. Soit par une demande d'authentification
qui amenera le client à se connecter ou créer un compte.

Une fois l'authentification établie, des messages standard de type
requête/réponse transitent entre le Smart Calculator et le serveur comme
ci-dessous.

Client----[Requête]----\>Server

Client\<---[Reponse]-----Server

## Architecture du système

Ci-dessous l'architecture du système de communication entre le client et
le serveur.

|-------| |---------|

| Client | \<-------------\>| Server |

|-------| |---------|

## Composants du système

Il y a deux composants dans ce système, le client et le serveur.

### Client

Le client est une machine qui a le système "Smart Calculator" est qui
communique avec un serveur. Le système a pour but de proposer diverses
opérations mathématique ou autre possibles. Lors de la sélection d'une
de ces dernières alors la machine va envoyer les informations à un
serveur distant afin que les calculs soit effectué sur celui-ci. Une
fois le calcul effectuer le serveur retourne le résultat et ainsi le
système client peut afficher le résultat de l'opération souhaitée.

### Serveur

Le serveur a pour but d'être présent pour établir des connexions avec
des "Smart Calculator" et permet d'effectuer les opérations souhaitées
par les systèmes client. Il peut soit être en mode ouvert ou soit en
mode authentification. Cette dernière agit de la même façon sauf qu'elle
requiert avant tout que le client s'authentifie auprès du serveur.

## Interactions entre composants

Ci dessous les différentes interactions entre le client et le serveur.

Client Server

 | 1 Connection demand |

 |----------------------------\>|

 | |

 | 2 Authentification request |

 |\<----------------------------|

 | |

 | 3 Authentification response |

 |----------------------------\>|

 | |

 | 4 Connection status |

 |\<----------------------------|

 | |

 | 5 Operation request |

 |----------------------------\>|

 | |

 | 6 Operation response |

 |\<----------------------------|

 | |

 | 7 Disconnect |

 |----------------------------\>|

Le message 1 est la demande de connexion du client vers le serveur.

Les messages 2 et 3 n'a lieu que dans la mode authentification du
serveur. Ce sont donc les messages d'authenfications.

Le message 4 indique si la connexion est établie ou non. Dans ce dernier
cas le client peut reprendre au point 3.

Si la connexion est établie, le client peut alors envoyer des requêtes
d'opération et le serveur des réponses. (5 et 6).

Une fois les échanges terminés, le client peut envoyer un message de
déconnexion au serveur afin de finir l'interaction (message 7).

# Détails du protocole

## Protocoles de transport et de connexions

La communication RSCP s'effectue à travers une connection TCP sur le
port 6556.

La partie serveur créé une socket serveur TCP qui écoute ce port afin
d'être en attente d'une connexion. La partie client va créer une socket
TCP et tenter de se connecter au serveur par celle-ci.

Une fois les sockets connectées, elles sont conservées durant toute la
durée des échanges jusqu'à un message de déconnexion venant du client ou
au bout de 30 minutes d'inactivité de la part des composants.

## Gestion d'états

|---------| connect[A] |--------|\<---¦

| inactif |----------------\> | auth. | ¦ failed[A]

|---------| |--------|-----¦

 \^ ¦ ¦

disc ¦ ¦ connect[P] ¦

 ¦ ¦ ¦

 ¦ v ¦ success[A]

|----------| ¦

| connect |\<-------------------¦

|----------|

Les interactions [A] signifie que c'est lorsque le serveur est en mode
Authentification, tandis que les [P] signifie que le serveur est public,
il est donc ouvert.

## Type de message, syntaxe et sémantique

### Requête

#### Connection C-\>S

La connection du client au serveur se fait par un message texte "CONNECT
REQUEST"

### Réponse

## Diverses considérations

## Sécurité

# Exemples

# Références
