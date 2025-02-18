# Evaluation du 18 février 2025

# Réseau TCP/IP UDP

## 1. Introduction

**Le but général de cette évaluation et des concepts abordés (TCP/IP,
routage, transport, protocoles complémentaires comme DHCP et ARP) est** l'analyse et la compréhentsion des fondamentaux de la communication et l'échange de données sur un réseau informatique. Les concepts abordés permettent de comprendre comment les  réseaux interagissent entre eux, pour assurer une communication rapide et efficace.

**TCP/IP** (Transmission Control Protocol / Internet Protocol) :

**TCP/IP** est un ensemble de protocoles de communication qui définissent la manière dont les données circulent sur un réseau. TCP est responsable de la transmission sûre des données, et IP se charge du routage des paquets à travers différents réseaux. Ensemble, ils forment la base des communications sur internet 

**Le Routage** concerne la manière dont les paquets et les trames sont envoyés d'un appareil à  un autre à travers différents réseaux. Les routeurs sont responsables de cette tâche, en définissant le meilleur chemin pour que les données arrivent à destination.

**Le Transport** assure comment les données sont segmentées et transmises entre les applications sur des ordinateurs distants. TCP est utilisé pour des transmissions fiables, tandis qu'UDP est plus rapide mais sans garantie de réception des données.
Protocoles complémentaires :

**DHCP** : c'est le protocole qui attribue aux appareils d'un réseau, automatiquement, une adresse IP, ce qui facilite leur configuration et organisation sans intervention manuelle.

**ARP**  le protocole ARP est utilisé pour associer une adresse IP à une adresse MAC dans un réseau local, afin de permettre une communication effective et sûre sur  un réseau local (LAN).

L'évaluation permet de comprendre les bases techniques des réseaux et leur fonctionnement, en abordant les protocoles, la gestion des adresses, le transport des données et leur routage. Cela sert à bien appréhender le processus complet d'échange d'informations à travers un réseau informatique.

## 2. Liste des manipulations réalisées  
Décrivez chaque exercice, incluant : 
o Les commandes utilisées (exemple : configura on d'une adresse IP, simula on d'un routage dynamique). 

**1- Insertion de :**
    - Trois *routeurs* : ADMIN - TECH - COMM
	- Un *switch* et trois *serveurs*
	- Six ordinateurs *PC*
	
**2- Cablage et connexion physique:** connexion du matériel inséré avec le cable *copper straight through* 

![insertion.jpg](../_resources/insertion-1.jpg)

**3- Configuration des interfaces réseaux**
Dans cette étape, nous allons procéder à la configuration des routeurs, Pc et serveurs. 

- Routeur Admin :
  *Interface FastEthernet 0/0* :
   IP de configuration : 192.168.1.1
   Masque de sous-réseau : 255.255.255.0

  *Interface FastEthernet 0/1* :
   IP de configuration : 10.0.0.1
   Masque de sous-réseau : 255.255.255.0

Voir prise d'écran suivantes : 
Routeur Admin 

 *Interface FastEthernet 0/0* 
![Routeuradmi.jpg](../_resources/Routeuradmi-1.jpg)

 *Interface FastEthernet 0/1* 
![Routeuradmi1.jpg](../_resources/Routeuradmi1-1.jpg)

- Routeur Tech :
  *Interface FastEthernet 0/0* :
   IP de configuration : 192.168.2.1
   Masque de sous-réseau : 255.255.255.0

  *Interface FastEthernet 0/1* :
   IP de configuration : 10.0.0.2
   Masque de sous-réseau : 255.255.255.0

  *Interface FastEthernet 0/0* :
![tech0.jpg](../_resources/tech0-1.jpg)


  *Interface FastEthernet 0/1* :
![tech1.jpg](../_resources/tech1-1.jpg)


- Routeur Comm :
  *Interface FastEthernet 0/0* :
   IP de configuration : 192.168.3.1
   Masque de sous-réseau : 255.255.255.0

  *Interface FastEthernet 0/1* :
   IP de configuration : 10.0.0.3
   Masque de sous-réseau : 255.255.255.0

*Interface FastEthernet 0/0* :
![comm0.jpg](../_resources/comm0-1.jpg)

*Interface FastEthernet 0/1* :
![comm1.jpg](../_resources/comm1-1.jpg)

**3-Activation  et sauvegarde de la configuration de chaque interface réseau** avec 
 **Activation** : *no shutdown*
 **Sauvegarde** : *write memory*
![noshutdown.jpg](../_resources/noshutdown-1.jpg)


**4- Ajout des routes:**

- *a -Route Admin*
![routeadmin.jpg](../_resources/routeadmin.jpg)

- *b -Route Tech*
![routetech.jpg](../_resources/routetech.jpg)

- *c -Route Comm*
![routecomm.jpg](../_resources/routecomm.jpg)








## 2. Liste des manipulations réalisées  
Décrivez chaque exercice, incluant : 
o Les commandes u lisées (exemple : configura on d'une adresse IP, simula on d'un 
routage dynamique). 
o Le contexte (tests de connectivité, configuration de DHCP, analyse avec Wireshark). 
o Les résultats attendus après chaque manipulation. 

## 3. Problèmes rencontrés et solu ons 
o Énumérez les difficultés rencontrées et la manière dont vous les avez résolues. 
o Décrivez comment vous avez iden fié et résolu ces problèmes. 

## 4. Analyse théorique 
o Expliquez l'importance des protocoles TCP/IP dans les réseaux modernes. 
o Discutez des avantages des différents protocoles (TCP, UDP). 
o Incluez des observa ons faites à l'aide d'ou ls comme Wireshark ou des simulateurs. 

## 5. Conclusion 
o Résumez vos apprentissages sur les protocoles TCP/IP et leur impact sur la connectivité réseau. 

## 6. Ressources 
o Fournissez les liens vers les documents et tutoriels utilisés pendant le TP


## Quizz

**1. La principale différence entre TCP et UDP est :** _A. TCP garantit la fiabilité, UDP est plus rapide._

**2. La couche du modèle TCP/IP qui gère le routage des paquets est :** la couche Internet

**3. Le protocole est utilisé pour résoudre une adresse IP en adresse MAC est :**  _ARP_

**4. La taille d'une adresse IPv6 est** _128 bits_ 

**5. L'outil qui permet d’analyser les performances d’un réseau en capturant les paquets est:**    _Wireshark_ 
