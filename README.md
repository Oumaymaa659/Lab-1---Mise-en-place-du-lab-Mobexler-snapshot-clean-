# Lab 1 : Mise en place du Lab Mobexler Snapshot Clean

## Description
Ce document détaille la mise en place d'un environnement d'audit complet pour la sécurité des applications mobiles, centré sur la distribution **Mobexler**. L'objectif est de préparer une station de travail (Mobexler) et une cible Android, configurées pour communiquer entre elles de manière sécurisée et reproductible.

## 2. Objectifs pédagogiques
Ce laboratoire vise à maîtriser les compétences suivantes :
- Installer et configurer une machine virtuelle dédiée au pentest mobile (Mobexler).
- Comprendre les mécanismes d'importation d'image OVA dans un hyperviseur.
- Vérifier la configuration réseau pour assurer la communication entre l'attaquant et la cible.
- Sécuriser l'état initial de l'environnement via la gestion des snapshots ("baseline").
- Préparer un émulateur ou un appareil Android pour le débogage et l'analyse.

## 3. Prérequis
Avant de commencer ce laboratoire, assurez-vous de disposer de :
- Un ordinateur hôte avec la virtualisation activée (VT-x / AMD-V).
- Un logiciel de virtualisation installé : **VirtualBox** (recommandé) ou **VMware Player/Workstation**.
- L'image OVA de **Mobexler** téléchargée.
- Une cible Android (Émulateur Genymotion, Android Studio AVD, ou appareil physique) prête à être utilisée.
- Espace disque suffisant (environ 20 Go) et au moins 4 Go de RAM alloués à la VM.

## 4. Étape 1 — Télécharger Mobexler (OVA) et tracer le téléchargement
Récupération de l'image disque officielle de Mobexler. Il est recommandé de vérifier l'intégrité du fichier téléchargé (hash SHA-256) pour s'assurer qu'il n'a pas été corrompu ou altéré.

![Téléchargement de Mobexler](screenshots/step1-download.png)

## 5. Étape 2 — Importer l’OVA dans VirtualBox/VMware
Processus d'importation de l'application virtuelle (fichier `.ova`) dans l'hyperviseur. Cette étape configure automatiquement la majorité des paramètres de la machine virtuelle (CPU, RAM, Disque). Il est possible d'ajuster ces ressources selon la puissance de l'hôte.

![Importation de la VM](screenshots/step2-import.png)

## 6. Étape 3 — Premier démarrage + connexion
Lancement initial de la machine virtuelle Mobexler. Une fois le système chargé, l'authentification se fait avec les identifiants par défaut (généralement `mobexler` / `1234`). Cette étape valide que l'importation s'est déroulée correctement.

![Premier démarrage](screenshots/step3-first-boot.png)

## 7. Étape 4 — Vérifier le réseau (tests “santé”)
Vérification de la connectivité réseau de la VM (commande `ping`, `ifconfig`/`ip a`). Il est crucial de s'assurer que Mobexler peut accéder à Internet pour les mises à jour et communiquer avec le réseau local pour atteindre la cible Android.

![Vérification réseau](screenshots/step4-network.png)

## 8. Étape 5 — Créer le snapshot “CLEAN” (baseline)
Création d'un point de restauration sain avec la VM éteinte ou allumée. Ce snapshot "CLEAN" sert de référence (baseline). Il permet de revenir instantanément à un état propre après avoir effectué des tests destructifs ou installé des malwares, garantissant ainsi la pérennité de l'environnement de lab.

![Création du snapshot Clean](screenshots/step5-clean-snapshot.png)

## 9. Étape 6 — Préparer la cible Android (choisir 1 option)
Configuration de l'appareil cible (smartphone physique ou émulateur). Cette étape implique l'activation du débogage USB (ADB Debugging) et la connexion de l'appareil à l'ordinateur hôte ou au réseau de la VM, afin qu'il soit détecté par les outils d'audit de Mobexler (via la commande `adb devices`).

![Préparation cible Android](screenshots/step6-android-target.png)

---

## Résultat
L'environnement est maintenant opérationnel avec une machine d'attaque (Mobexler) saine, sauvegardée, et capable de communiquer avec une cible Android.

## Technologies utilisées
- **Mobexler**
- **VirtualBox / VMware**
- **Android Debug Bridge (ADB)**
- **Genymotion / AVD (Cible Android)**

## Auteur
**Oumayma Benhilal**
