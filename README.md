# Conception d'un réseau sécurisé pour un campus universitaire

Projet de conception et de configuration d'un réseau sécurisé pour une université, réalisé avec Cisco Packet Tracer pour l'entreprise fictive **EduNet Solutions**.

## Description

L'université a besoin d'une infrastructure réseau robuste et sécurisée. Le réseau est divisé en trois zones (administrative, pédagogique et recherche), reliées par un routeur principal. Chaque zone est protégée par des listes de contrôle d'accès (ACL), des pare-feux et le NAT, afin que seuls les utilisateurs autorisés puissent accéder aux ressources sensibles.

## Objectifs

- Segmenter le campus en trois sous-réseaux distincts
- Contrôler les accès entre les zones avec des ACL et des pare-feux
- Protéger les données de recherche contre tout accès non autorisé
- Masquer les adresses internes avec le NAT pour l'accès à Internet
- Activer les logs et les alertes pour détecter les activités suspectes
- Valider la configuration avec des tests de connectivité et d'accès

## Architecture du réseau

| Zone | Réseau | Équipements |
|---|---|---|
| Administratif | `172.20.10.0/24` | 20 postes de travail, un switch et un point d'accès Wi-Fi, adresses IP fixes |
| Pédagogique | `172.20.20.0/24` | Serveur de fichiers `172.20.20.10`, serveur web `172.20.20.20`, un switch dédié, protégé par un pare-feu |
| Recherche | `172.20.30.0/24` | Serveur de stockage `172.20.30.10`, un switch sécurisé, protégé par un pare-feu supplémentaire |

**Routeur principal** : `172.20.1.1`. Il assure le routage entre les sous-réseaux et le NAT vers Internet.

## Sécurité

### ACL (routeur principal)
- Seuls les chercheurs (`172.20.10.100` à `172.20.10.110`) peuvent accéder au réseau Recherche.
- Les autres adresses du réseau Administratif sont bloquées vers le réseau Recherche.

### Pare-feux
- Un pare-feu entre chaque zone pour contrôler les accès.
- Réseau Pédagogique : les connexions externes sont autorisées uniquement vers les services web éducatifs.

### NAT
- Masquage des réseaux `172.20.10.0/24`, `172.20.20.0/24` et `172.20.30.0/24` pour l'accès Internet.

## Surveillance et tests

- Logs activés sur les pare-feux et le routeur principal pour capturer les tentatives d'accès non autorisé.
- Alertes configurées pour toute activité suspecte.
- Tests de connectivité avec `ping` et `traceroute` entre les zones.
- Simulation de tentatives d'accès pour vérifier l'efficacité des ACL et des pare-feux.

## Livrables

- [ ] Fichier Packet Tracer (`.pkt`) : configuration et segmentation du réseau
- [ ] Schéma du réseau : zones, sous-réseaux et équipements de sécurité
- [ ] Captures d'écran : configurations ACL, NAT et pare-feu
- [ ] Rapport détaillé : règles de sécurité, résultats des tests et analyse

> Cochez chaque case et ajoutez les liens vers vos fichiers une fois ceux-ci déposés dans le dépôt.

## Technologies et concepts

- Cisco Packet Tracer
- Adressage IPv4 et sous-réseaux
- Routage inter-réseaux
- ACL (listes de contrôle d'accès)
- Pare-feux et segmentation des zones
- NAT
- Journalisation et surveillance
- Tests avec `ping` et `traceroute`

## Auteur

**Aymane**
DEC en programmation, Collège LaSalle

## Contexte

Projet académique. L'entreprise EduNet Solutions est fictive.
