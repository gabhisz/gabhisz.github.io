---
title: "Projet ADN-Photo — Application de vote WPF"
image:
  path: /assets/projet-adn-photo.png
  alt: Schéma du projet ADN-Photo
date: 2026-03-31 10:00:00 +0000
categories: [Projets, Développement]
tags: [csharp, wpf, mysql, linq, mvvm, dotnet, bdd]
---

## Présentation du projet

Le projet **ADN-Photo** est un projet de fin d'année réalisé en équipe de 4 étudiants 
dans le cadre de mon BTS CIEL option Informatique & Réseaux. Il consiste à mettre en 
place un **système de vote numérique** pour une association de photographes.

Chaque année, l'association organise des expositions sur 2 jours où les visiteurs votent 
pour leur photo préférée. À l'issue de l'exposition, la photo la plus plébiscitée est 
désignée gagnante et un tirage au sort est effectué parmi les votants.

---

## Architecture globale du projet

Le projet repose sur plusieurs composants développés en parallèle par l'équipe :

- **Application de gestion** — pour l'organisateur de l'exposition
- **Site Web** — permettant aux visiteurs de voter via QR code avec leur smartphone
- **API REST** — sécurisant les accès à la base de données
- **Application de vote Windows** — pour les visiteurs sans smartphone *(ma partie)*
- **Base de données MySQL** — hébergée sur un serveur Apache/Windows Server 2022

---

## Mon rôle — Application de vote Windows (Étudiant 4)

Mon rôle était de développer l'**application de vote destinée aux visiteurs ne possédant 
pas de smartphone**. Cette application devait être simple, intuitive et accessible au 
grand public.

### Fonctionnalités développées

- Affichage de la liste des photos sous forme de **pavés cliquables** (titre, auteur, 
  thème, numéro)
- **Fenêtre de confirmation** avant validation du vote
- Saisie des informations du votant (nom, prénom, email ou téléphone)
- **Validation et normalisation automatique** des numéros de téléphone et adresses email
- Vérification du nombre de votes par personne
- **Fenêtre d'administration cachée** (accessible uniquement via combinaison de touches) 
  pour modifier les paramètres de connexion à la BDD

---

## Stack technique

- **Langage** : C# avec .NET Framework 4.8
- **Interface graphique** : WPF (Windows Presentation Foundation) + plugin WPF.UI
- **Architecture** : MVVM (Model-View-ViewModel)
- **Accès BDD** : LINQ (Language-Integrated Query) via Devart LinqConnect
- **Base de données** : MySQL hébergée sur UWamp
- **IDE** : Visual Studio 2022

---

## Architecture MVVM

J'ai structuré l'application selon le patron de conception **MVVM** :

- **View** — Les fenêtres XAML constituant l'interface utilisateur
- **ViewModel** — Les fichiers `.xaml.cs` gérant les événements et le DataBinding
- **Model** — Une DLL contenant les classes métier (`BDDvote`, `Photo`, `Votant`) 
  et le contexte LINQ (`AdnPhotoDataContext`)

Cette séparation a permis de développer et tester la partie graphique indépendamment 
de la logique métier.

---

## Ce que j'ai appris

Ce projet m'a permis de monter en compétences sur plusieurs points :

- **Développement WPF** : concevoir des interfaces ergonomiques adaptées au grand 
  public, avec une attention particulière à l'UX
- **Architecture MVVM** : comprendre et appliquer un patron de conception professionnel
- **LINQ et accès BDD** : intégrer des requêtes SQL directement dans le code C# et 
  manipuler des données en temps réel
- **Gestion des erreurs** : validation et normalisation des entrées utilisateur 
  (téléphones, emails) sans interrompre l'expérience
- **Travail en équipe** : adapter mon code à celui des autres étudiants, communiquer 
  sur les interfaces communes (BDD partagée, API)
- **Gestion de projet** : planifier mes tâches avec un planning détaillé et respecter 
  les délais

---

## Conclusion

Ce projet a été une première immersion dans des conditions proches du monde 
professionnel. Il m'a permis de gagner en autonomie sur le développement d'applications 
C# complètes, connectées à une base de données, et conçues pour un usage réel. 
Une expérience enrichissante tant sur le plan technique qu'humain.

# Logiciels utilisés

- Visual Studio
- Uwamp

## Capture d'écran des fenêtres

![Fenêtre principale](/assets/mainwindow.png)
_Aperçu de la fenêtre de choix de la photo_

![Fenêtre de vote](/assets/fen_vote.png)
_Aperçu de la fenêtre de saisie des informations_

![Fenêtre des paramètres](/assets/fen_param.png)
_Aperçu de la fenêtre de paramètrage de connexion à la BDD_
