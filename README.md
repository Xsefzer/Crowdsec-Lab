# Laboratoire CrowdSec — Détection et protection d’un environnement Windows

> Projet réalisé dans un environnement de laboratoire dans le cadre du cours **Piratage et sécurité**. Il présente la préparation des machines, l’intégration de CrowdSec et du pare-feu Windows, puis l’observation d’événements d’authentification et d’alertes.**Périmètre autorisé :** les essais illustrés ont été réalisés uniquement dans un environnement contrôlé et sur des systèmes de laboratoire.

## Objectifs

- Préparer un hôte Windows et une machine Kali Linux dédiés aux essais.

- Configurer CrowdSec et vérifier l’enregistrement du bouncer Windows Firewall.

- Observer les événements d’échec de connexion Windows, notamment l’Event ID **4625**.

- Corréler les essais avec les événements et alertes visibles dans CrowdSec.

- Évaluer le mécanisme de notification Telegram et consigner son état.

## Environnement

| Composant | Rôle dans le laboratoire |
| --- | --- |
| Windows | Hôte surveillé; comptes de laboratoire, journaux de sécurité et pare-feu Windows |
| Kali Linux | Machine de test utilisée dans le réseau de laboratoire |
| CrowdSec | Analyse des événements et remontée d’alertes |
| Windows Firewall bouncer | Composant d’application des décisions de blocage sur l’hôte Windows |
| CrowdSec Console | Vue de l’instance et des alertes |
| Telegram | Canal de notification testé; non fonctionnel lors de cet essai |

## Déroulement et preuves

### 1. Préparation du compte de laboratoire

Création d’un compte de test dédié à l’exercice. Un compte distinct limite l’utilisation d’identifiants personnels et facilite l’identification des événements générés pendant les essais.

![Création du compte de laboratoire](Screenshots/Creation_user.png)

Ajout du compte au groupe requis pour l’accès RDP au laboratoire. Cette étape prépare l’accès distant utilisé dans le scénario; elle doit rester limitée à une machine isolée et à un compte de test.

![Ajout du compte au groupe RDP](Screenshots/Ajout_Au_Grp.png)

### 2. Préparation de la machine de test

La capture montre le terminal de Kali prêt pour le scénario de test. La machine doit communiquer uniquement avec les hôtes prévus dans le réseau de laboratoire.

![Terminal Kali prêt pour le laboratoire](Screenshots/Terminal_Ready.png)

### 3. Vérification de CrowdSec et du bouncer

La première vérification en ligne de commande présente la version de CrowdSec installée. Elle permet de confirmer que l’outil est disponible sur l’hôte avant de poursuivre les tests.

![Vérification de la version CrowdSec](Screenshots/Commande1.png)

La seconde vérification affiche la liste des bouncers CrowdSec. Elle sert à confirmer l’enregistrement du bouncer Windows Firewall chargé d’appliquer les décisions de sécurité sur l’hôte.

![Vérification de l’enregistrement du bouncer](Screenshots/Commande2.png)

### 4. Enregistrement et état de l’instance

La console CrowdSec fournit la vue centralisée de l’instance. Cette capture documente l’interface de gestion utilisée pour suivre l’environnement.

![Console CrowdSec](Screenshots/CrowdSec_Console.png)

Cette capture montre l’état de l’instance Windows dans la console CrowdSec. Elle permet de vérifier que l’hôte apparaît en ligne au moment de l’observation.

![Instance Windows visible en ligne dans CrowdSec](Screenshots/Wtatus_Online%28Crowd%29.png)

### 5. Génération et observation des événements

Une série d’essais contrôlés est lancée depuis Kali dans le cadre du laboratoire. La capture documente l’activité de l’outil de test; elle ne doit pas être interprétée comme une autorisation de tester des systèmes tiers.

![Essais d’authentification contrôlés depuis Kali](Screenshots/Hydra_PsswdTest.png)

Les journaux Windows permettent ensuite d’examiner les événements produits par les tentatives de connexion. L’Event ID **4625** correspond à un échec d’ouverture de session; l’analyse du contexte et de l’horodatage aide à corréler l’événement avec le scénario de test.

![Journaux Windows associés aux essais](Screenshots/Logs.png)

### 6. Alertes CrowdSec

La console CrowdSec affiche les alertes observées pendant le scénario. Cette preuve illustre la visibilité des événements dans la plateforme après les essais; l’interprétation dépend des événements effectivement reçus par l’instance.

![Alertes observées dans CrowdSec](Screenshots/Alerts_OnCrowd.png)

## Résultat et limites

Les captures documentent la préparation des machines, les vérifications CrowdSec, la présence de l’instance dans la console, les essais contrôlés et l’observation des journaux et alertes. La notification Telegram **n’a pas fonctionné lors du test**; elle reste à dépanner et à valider avant de pouvoir être présentée comme opérationnelle.

## Améliorations possibles

- Ajouter les versions exactes de Windows, CrowdSec, du bouncer et des autres composants.

- Documenter les étapes d’installation et les paramètres réellement appliqués, sans inclure de secrets.

- Diagnostiquer la notification Telegram et ajouter une preuve uniquement après un test réussi.

- Clarifier les critères de corrélation entre l’événement Windows, l’alerte CrowdSec et toute décision du bouncer.

## Sécurité et confidentialité

Les commandes de test doivent être exécutées uniquement dans un environnement isolé et explicitement autorisé. Ne publiez aucun mot de passe, jeton Telegram, clé privée, adresse publique sensible ou renseignement personnel. Les comptes et identifiants de laboratoire doivent être fictifs.
