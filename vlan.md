# Choix du Routeur et configuration

**Je dois prendre quel routeur pour connecter les deux ?**

Très bonne question ! Pour connecter deux VLANs dans Cisco Packet Tracer, tu peux choisir entre deux méthodes principales :

Suivre ces démarches sans toucher à la configuration dans Config
---

### ✅ **1. Avec un routeur (Router-on-a-Stick)**

#### 🔧 Routeur recommandé :  
**Cisco 2811** (ou tout autre routeur avec une interface FastEthernet ou GigabitEthernet disponible).

#### 🧰 Matériel :
- 1 routeur (ex. : Cisco 2811)
- 1 switch (déjà configuré avec tes VLANs)
- 1 câble **Ethernet** entre le switch (port en mode **trunk**) et le routeur

#### ⚙️ Exemple de configuration sur le routeur :

##### Étape 1 : Configurer l'interface en sous-interfaces (trunk)
```bash
enable
configure terminal
interface fastEthernet 0/0
no shutdown
exit

interface fastEthernet 0/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0
exit

interface fastEthernet 0/0.20
encapsulation dot1Q 20
ip address 192.168.20.1 255.255.255.0
exit
```

##### Étape 2 : Sur le **switch**, mets le port connecté au routeur en **mode trunk** :
```bash
interface fastEthernet 0/24
switchport mode trunk
exit
```

> (Remplace `Fa0/24` par le bon port connecté au routeur.)

---

### ✅ **2. Alternative : Utiliser un switch L3 (comme le Catalyst 3560)**

Ce switch permet de faire du routage inter-VLAN sans routeur. Si tu veux cette méthode, je peux te guider aussi.

---

Souhaites-tu continuer avec la méthode **routeur-on-a-stick** ou préfères-tu la solution avec **switch de niveau 3** ?



# Configuration du Routeur pour les Vlan


Merci pour ta vigilance — c’est **justement là le cœur du problème** : si la sous-interface `FastEthernet0/0.10` **n'a pas l'adresse IP `192.168.10.1`**, alors le routeur **ne pourra pas router le VLAN 10**, ce qui empêche le **ping entre les VLANs**.

* * *

### ✅ Pour corriger ça : configure l’IP manuellement

Connecte-toi à ton routeur et entre les commandes suivantes **exactement** :

```bash
enable
configure terminal

interface FastEthernet0/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0
no shutdown
exit

interface FastEthernet0/0.20
encapsulation dot1Q 20
ip address 192.168.20.1 255.255.255.0
no shutdown
exit
```

> Vérifie aussi que tu **n’as pas mis une IP directement sur l’interface Fa0/0** (ça empêche les sous-interfaces de fonctionner).

* * *

### ❗ Supprimer l’IP de Fa0/0 si nécessaire :

Si tu vois une IP sur l'interface physique `Fa0/0`, supprime-la avec :

```bash
interface FastEthernet0/0
no ip address
exit
```

Puis refais les étapes avec `Fa0/0.10` et `Fa0/0.20` comme indiqué ci-dessus.

![Capture d’écran 2025-04-30 163449.png](:/7006620d0757474895ab980a68e97e9b)

**Il faut qu'elle soit comme ça :**  
![Bonne Config.png](:/718deb478f6a483dba16ec095d7329e4)

* * *

Quand c’est fait, tu peux vérifier avec :

```bash
show ip interface brief
```

Tu dois voir quelque chose comme :

```
FastEthernet0/0.10    192.168.10.1     YES ...
FastEthernet0/0.20    192.168.20.1     YES ...
```

* * *

Souhaites-tu que je t’aide pas à pas à tout vérifier depuis ton fichier Packet Tracer ?
