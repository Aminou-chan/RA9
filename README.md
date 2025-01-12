---
title: "Manuel d’utilisateur ChatbotMD pour la plateforme Middleware"
version: "1.0"
---

# Manuel d’utilisateur : ChatbotMD sur les environnements de TEST

Bienvenue dans le manuel d’utilisateur dédié à **ChatbotMD** intégré pour notre **plateforme Middleware CATS ON TREES**.  

1. [Menu principal](Menu principal)


## Menu principal

1. [Introduction](Introduction)  
2. [Avertissements et conventions utilisées](2-avertissements-et-conventions-utilisées)  
3. [Présentation de ChatbotMD](3-présentation-de-chatbotmd)  
4. [Installation et configuration](4-installation-et-configuration) 




## 1. Introduction

Ce manuel décrit l’utilisation de **ChatbotMD**, un agent conversationnel (chatbot) conçu pour s’intégrer à la **plateforme COT** . Il vous guidera pas à pas dans :

- La compréhension du fonctionnement de ChatbotMD  
- L’installation et la configuration  
- L’utilisation au quotidien (commandes, automatisations, etc.)  
- La résolution de problèmes et la maintenance

1. [Retour au menu principal](Menu principal)  
2. [Section suivante : Avertissements et conventions](Avertissements et conventions utilisées)  



## 2. Avertissements et conventions utilisées

- **Avertissements de sécurité** : veillez à ne pas divulguer de données sensibles (identifiants, mots de passe, etc.) dans le chatbot.  
- **Conventions d’écriture** :  
  - Les commandes à taper sont présentées dans un bloc de code, par exemple :  
    ```bash
    npm install chatbotmd
    ```
  - Les éléments d’interface (boutons, champs) sont en **gras** ou *italique*.
  - Les chemins de fichiers sont au format `/chemin/vers/fichier`.


1. [Retour au menu principal](Menu principal)  
2. [Section suivante : Présentation de ChatbotMD](Présentation de ChatbotMD)  


## 3. Présentation de ChatbotMD

### 3.1 Objectifs

1. **Fournir** un outil de conversation et d’assistance pour la plateforme COT.  
3. **Guider** les utilisateurs (internes/developpeurs de COT ou externes à notre équipe) dans l’utilisation de la plateforme et la recherche d'informations dans notre documentation (enduser et internal).

### 3.2 Fonctionnalités clés

- **Réponses rapides et contextuelles** aux questions liées à la plateforme.  
- **Intégration** avec les API internes de COT.  
- **Traçabilité** : possibilité de stocker et d’exporter l’historique des conversations.

### 3.3 Environnement requis

- **Système d’exploitation** : RHEL8+  
- **Dépendances (!sera installées avec ansible)** : Node.js (version 16 ou +).  
- **Réseau** : Port ouvert (HTTP).  
- **Accès** : Crédentials/API Key pour la plateforme COT si nécessaire (partie à developper plus tard).

1. [Retour au menu principal](Menu principal)  
2. [Section suivante : Installation et configuration](Installation et configuration)  

## 4. Installation et configuration

### 4.1 initiliser ansible

- Procéder comme suit à partir de votre user sur l'ansible de DEV `<user>@<machine_dev_ansible>`

```sh
cd /env/ambz/cot_ansible/playbook-init

git pull

# puis basculer sur la branche feature/chatbotMD

git checkout feature/chatbotMD

# mettre à jour les roles via ansible-galaxy
ansible-galaxy install -f -g -r requirements.txt
```

### 4.2 installation

Mise à jour du composant GUI de l'EXEC

```sh
cd ~/cot_ansible/playbook-init

ansible-playbook inst_CM.yml -i inventory/test --tags="install_GUI_CM"
```

1. [Retour au menu principal](Menu principal)  
2. [Section suivante :  Guide d’utilisation](5. Guide d’utilisation)  


## 5. Guide d’utilisation
### 5.1 Premier démarrage

    Accédez à l’URL (ex. https://votreserveur/chatbotmd)(entreprise)
    
    Connectez-vous à l’aide de vos identifiants (si la plateforme le requiert/plus tard).

5.2 Interactions de base

    Saisir votre question ou commande dans le champ de texte.
    Envoyer la demande (bouton Envoyer ou touche Entrée).
    Lire la réponse produite par ChatbotMD.

5.3 Fonctionnalités avancées

    Commandes spécifiques : exemple !restart moduleX pour redémarrer un module.
    Scripts personnalisés : ex. !script backupDB.
    Historique : possibilité de revoir et/ou exporter les conversations.

    Bulles de proposition :

        Retour au menu principal
        Section suivante : Maintenance et mises à jour

6. Maintenance et mises à jour
6.1 Consignes de maintenance

    Surveiller les logs (logs/chatbotmd.log) pour détecter des erreurs.
    Sauvegarder régulièrement la configuration (fichiers .env, config.yaml).

6.2 Procédure de mise à jour

    Arrêter ChatbotMD :

systemctl stop chatbotmd

Mettre à jour via git pull ou un paquet interne.
Réinstaller les dépendances si besoin :

npm install

Redémarrer :

    systemctl start chatbotmd

    Vérifier le fonctionnement dans les logs.

    Bulles de proposition :

        Retour au menu principal
        Section suivante : Résolution des problèmes

7. Résolution des problèmes
7.1 Problèmes courants

    Le chatbot ne se lance pas : vérifier la config et les ports (logs).
    Réponses incohérentes : vérifier l’API ou la base de connaissances.
    Temps de réponse élevé : regarder la charge serveur et la connectivité.

7.2 Dépannage avancé

    Logs détaillés : passer LOG_LEVEL à debug dans le fichier de config.
    Réinitialisation : supprimer le cache/dossier sessions puis redémarrer.
    Support : contacter l’équipe Middleware si rien ne fonctionne.

    Bulles de proposition :

        Retour au menu principal
        Section suivante : FAQ

8. FAQ

    ChatbotMD gère-t-il plusieurs langues ?
    Oui, si les modules linguistiques sont installés et configurés.
    Comment personnaliser l’interface ?
    Modifier les fichiers .css et .js dans public/.
    Existe-t-il des limites ?
    Les performances dépendent du serveur et de la configuration réseau.

    Bulles de proposition :

        Retour au menu principal
        Section suivante : Annexes

9. Annexes
9.1 Glossaire

    API : Interface de programmation, permet à plusieurs apps de communiquer.
    Middleware : Logiciel d’interfaçage entre différents systèmes ou services.
    Chatbot : Agent conversationnel automatisé.

9.2 Références

    Wikibooks – Rédaction d’un manuel d’utilisation
    Documentation interne de la plateforme Middleware

    Bulles de proposition :

        Retour au menu principal
        Section suivante : Historique des révisions

10. Historique des révisions
Version	Date	Auteur	Évolutions
1.0	2025-01-12	Équipe Doc. Middleware	Création du manuel
1.1	À compléter	(Votre nom)	Mises à jour mineures

    Bulles de proposition :

        Retour au menu principal

:star2: Merci d’avoir consulté ce manuel d’utilisation

ChatbotMD est conçu pour améliorer l’expérience utilisateur et simplifier la gestion de votre plateforme Middleware.
Pour tout complément d’information ou problème spécifique, consultez la section de résolution des problèmes ou contactez le support interne.








