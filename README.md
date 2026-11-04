# CrowdSec — Protection collaborative sur Windows

Laboratoire réalisé dans un environnement contrôlé dans le cadre du cours **Piratage et sécurité**. L’objectif est d’observer la détection d’essais de connexion échoués sur Windows et d’intégrer CrowdSec avec le pare-feu Windows.

> Projet pédagogique. Les tests doivent être réalisés uniquement sur des machines et comptes de laboratoire autorisés.

## Objectifs

- Préparer un environnement Windows et une machine Kali Linux dédiée aux tests.

- Installer et vérifier CrowdSec ainsi que le bouncer Windows Firewall.

- Générer des événements d’échec d’authentification et repérer l’Event ID **4625** dans l’Observateur d’événements.

- Observer les alertes remontées dans CrowdSec Console.

- Évaluer l’envoi d’une notification Telegram.

## Environnement de laboratoire

- Windows avec l’Observateur d’événements et le pare-feu Windows

- Kali Linux, utilisé comme machine de test dans le laboratoire

- CrowdSec Console

- CrowdSec Windows Firewall bouncer

- Telegram (notification testée; voir les résultats)

## Démarche

1. Préparer le compte de laboratoire et l’accès RDP sur la machine Windows.

1. Démarrer la machine Kali dans le réseau isolé du laboratoire.

1. Installer/configurer CrowdSec et enregistrer le bouncer du pare-feu Windows.

1. Vérifier l’installation et l’état du bouncer avec les commandes CrowdSec, notamment `cscli version` et `cscli bouncers list`.

1. Générer des tentatives de connexion de test dans l’environnement autorisé.

1. Vérifier les événements d’échec de connexion (Event ID **4625**) et les alertes CrowdSec.

1. Tester la notification Telegram et consigner le résultat.

## Résultats et observations

- La présence du bouncer Windows Firewall a été vérifiée avec `cscli bouncers list`.

- Le laboratoire vise à corréler les échecs de connexion Windows avec les alertes affichées dans CrowdSec Console.

- **Notification Telegram : non fonctionnelle lors du test initial.** Le dépannage et une nouvelle validation restent à effectuer.

## Captures à ajouter

Ajoutez vos propres captures dans un dossier `Screenshots/`, puis remplacez les noms ci-dessous par les fichiers réels. Masquez les adresses IP, noms d’utilisateur, jetons, clés et autres informations sensibles avant publication.

- ![Création du compte de laboratoire](screenshots/creation_user.png)

- `screenshots/kali-ready.png` — environnement Kali prêt

- `screenshots/crowdsec-bouncer.png` — version CrowdSec et bouncer enregistré

- `screenshots/crowdsec-console-online.png` — instance visible dans la console

- `screenshots/event-id-4625.png` — événement d’échec de connexion

- `screenshots/crowdsec-alert.png` — alerte observée dans la console

- `screenshots/telegram-test.png` — résultat du test Telegram, si une capture existe

## Limites et prochaines étapes

- Dépanner la notification Telegram et documenter la correction, si possible.

- Ajouter les versions des composants et les étapes exactes d’installation/configuration.

- Ajouter des captures d’écran réelles et expurgées; les mentions de captures attendues dans le document source ne sont pas elles-mêmes des preuves de résultat.

## Notes de sécurité

Ce dépôt ne doit contenir aucun mot de passe, jeton Telegram, clé privée, adresse publique sensible ni donnée personnelle. Utilisez uniquement des identifiants fictifs et un réseau de laboratoire isolé. Ne lancez pas de tests contre des systèmes tiers.
