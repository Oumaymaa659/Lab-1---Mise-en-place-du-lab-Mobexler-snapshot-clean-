# Lab 1 : Mise en place de l'environnement d'audit mobile avec Mobexler

## Description
Ce projet documente la mise en place d'un environnement de laboratoire complet pour l'audit de sécurité d'applications mobiles Android. L'objectif est d'installer et de configurer la machine virtuelle **Mobexler**, une plateforme spécialisée contenant tous les outils nécessaires (ADB, Frida, Drozer, etc.), et de préparer une cible Android pour les tests d'intrusion.

Ce lab constitue la fondation essentielle pour tout test de sécurité mobile, garantissant un environnement isolé, contrôlé et reproductible.

## Étapes de mise en place

### Étape 1 : Téléchargement de Mobexler
Récupération de l'image OVA officielle de Mobexler depuis le site de l'éditeur. Cette distribution Linux basée sur Elementary OS est pré-constuite avec les outils de pentest mobile.

![Téléchargement de Mobexler](screenshots/step1-download.png)

### Étape 2 : Importation dans la solution de virtualisation
Importation du fichier OVA dans le logiciel de virtualisation (VMware ou VirtualBox). Cette étape consiste à configurer les ressources allouées (RAM, CPU) pour assurer la fluidité de l'environnement d'audit.

![Importation de la VM](screenshots/step2-import.png)

### Étape 3 : Premier démarrage et authentification
Lancement de la machine virtuelle pour la première fois. La connexion s'effectue avec les identifiants par défaut (`mobexler` / `1234`), donnant accès au bureau et aux outils préinstallés.

![Premier démarrage](screenshots/step3-first-boot.png)

### Étape 4 : Configuration et vérification réseau
Vérification de la connectivité réseau de la VM pour s'assurer qu'elle peut communiquer avec l'hôte et internet. Cette étape est cruciale pour télécharger des paquets supplémentaires ou interagir avec des cibles sur le réseau local.

![Vérification réseau](screenshots/step4-network.png)

### Étape 5 : Création du Snapshot "Clean" (Baseline)
Après la configuration initiale et avant toute modification risquée, un snapshot (point de sauvegarde) nommé "Clean" est créé. Cela permet de restaurer rapidement l'état initial de la machine en cas de problème ou de corruption lors des tests ultérieurs.

![Création du snapshot Clean](screenshots/step5-clean-snapshot.png)

### Étape 6 : Préparation de la cible Android
Configuration de l'émulateur ou de l'appareil Android cible (ici Genymotion ou AVD) pour qu'il communique avec Mobexler. Cela inclut l'activation du débogage USB et la vérification de la connexion ADB depuis Mobexler.

![Lancement de la cible Android](screenshots/step6-android-target.png)

## Résultat
À l'issue de ce laboratoire, nous disposons d'un poste de travail d'audit opérationnel (Mobexler) et d'une cible Android connectée. L'environnement est sécurisé par un snapshot, prêt pour l'installation d'une application vulnérable et le début des tests d'intrusion.

## Technologies utilisées
- **Mobexler** : Plateforme d'audit de sécurité mobile.
- **VMware / VirtualBox** : Hyperviseur pour la virtualisation.
- **Android Debug Bridge (ADB)** : Outil de communication avec les appareils Android.
- **Linux (Elementary OS)** : Système d'exploitation hôte de Mobexler.

## Auteur
**Oumayma Benhilal**
