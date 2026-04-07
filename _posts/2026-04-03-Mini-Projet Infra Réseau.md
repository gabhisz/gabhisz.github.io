---
title: "Mini-Projet Réseau INFRA avec supervision SysLog XML"
image:
  path: /assets/img/mini-projet-infra.png
  alt: Schéma réseau INFRA
date: 2026-04-01 10:00:00 +0000
categories: [Projets, Réseau]
tags: [cisco, réseau, voip, syslog, xml, dhcp, vlan, csharp]
---



## Présentation du projet

![Schéma réseau du projet](/assets/mini-projet-infra.png)
_Schéma de l'infrastructure réseau INFRA_

Dans le cadre de mes études en réseau informatique, j'ai participé à la mise en 
place d'une infrastructure réseau d'entreprise complète incluant de la 
téléphonie IP et un système de supervision des logs en temps réel.
Ce travail à été réalisé par une équipe de 3 élèves

---

## Architecture mise en place

L'infrastructure est composée de deux réseaux locaux distincts :

- **Réseau Data** (`192.168.20+n.0/24`) — hébergeant les postes de travail et 
  un serveur virtuel
- **Réseau Voix** (`192.168.80+n.0/24`) — dédié aux téléphones IP Cisco (SCCP)

Un **routeur ISR Cisco** (2801 / 2901 / 4331) assure le routage entre ces 
réseaux, la translation d'adresse NAT pour l'accès Internet, ainsi que la 
distribution d'adresses IP via DHCP. Une **borne Wifi** sécurisée en WPA2 
permet un accès sans fil au réseau Data.

---

## Compétences réseau mobilisées

- Configuration des **interfaces et VLANs** sur routeur Cisco
- Mise en place de serveurs **DHCP** pour les réseaux Data et Voix
- Configuration **NAT/PAT** (translation Many-to-One)
- Synchronisation horaire via **NTP** avec gestion du fuseau horaire GMT+1
- Configuration **DNS** du domaine `INFRA.IL`
- Sécurisation Wifi **WPA2**

---

## Téléphonie IP (VoIP)

Le routeur assure également la fonction de **Call Manager Express (CME)** pour 
gérer les téléphones Cisco :

- Configuration du **plan de numérotation** (ephone-dn)
- Mise en place d'une **musique d'attente** en multicast (239.0.0.2)
- Service de **présence** entre les postes
- Ligne **interphone** prioritaire entre les postes
- **Liste d'appel** (diffusion simultanée vers plusieurs postes)

---

## Application Syslog XML (développement C#)

En parallèle de la partie réseau, une **application serveur Syslog** a été 
développée sous **Visual Studio 2022** en C# / WPF :

- **Réception UDP** des messages Syslog émis par le routeur et la borne Wifi
- **Décodage des messages** au format XML
- **Stockage en base de données** SQL Server
- **Affichage dans une interface WPF** avec tri par date ou par priorité

---

## Répartition des tâches

Mon rôle dans ce projet portait sur :

- Configuration du routeur (adressage IP, DHCP, NAT)
- Partie globale du service de téléphonie (`telephony-service`)
- Développement de la classe `ServeurUDP` pour la réception des logs Syslog XML
- Participation à l'interface graphique WPF

---

## Compétences développées

- Administration et configuration de **routeurs Cisco** en environnement réel
- Mise en place d'une infrastructure **VoIP** complète
- Développement d'une application **C# / WPF** communicant sur le réseau
- Travail en équipe sur un projet technique pluridisciplinaire

---

## Logiciels utilisés

- Putty
- Visual Studio 
