# Travaux dirigés

## SSH

_Un serveur ssh est normalement déjà installé sur la machine._

- Vérifier si sa configuration est « sécurisée » au sens décrit dans les slides. 
- Créer deux comptes `user1` et `user2`; le premier avec un mot de
passe dérivé du nom du compte et le second avec un mot de passe de 4 caractères minuscules aléatoires.  
    Demander l’IP de son voisin et essayer de cracker le mot de passe
d’un de ses comptes.


## DNS

| Objectif  | Description      |
|-----------|------------------|
| Serveur DNS « à cache seul » | Installation et mise en pratique d’un serveur DNS qui résout et met en cache les requêtes.    |
| Serveur DNS maître d'une zone locale  | Installation d’un serveur DNS maître pour gérer une zone locale et sa configuration.          |
| Serveur DNS menteur          | Mise en place d’un serveur DNS capable de bloquer ou de rediriger certaines résolutions.      |


**Durée estimée :** 4 heures (exposé oral compris)

:::tip Conseil 
Au fur et à mesure de vos travaux, complétez un document reprenant toutes vos manipulations.  
Incluez :
- Les contenus de vos fichiers de configuration
- Vos démarches
- Les problèmes rencontrés
- Les solutions et moyens utilisés

Ce document vous sera utile pour vos révisions.
:::

:::tip Conseil
Les pages de manuel restent toujours intéressantes : 
- `man named`
- `man named.conf`
- `man dig`
- Répertoire `/usr/share/doc/bind`
:::

### Serveur DNS à cache seul (Résolveur)

Implémentez sur votre machine un serveur DNS à cache seul.  
Ce serveur doit :
- Résoudre les noms (ex. `example.org` → adresse IP)
- Faire la résolution inverse

**Test :**  
Utilisez la commande `dig` (probablement à installer via le paquet `dnsutils`).

**Choix du logiciel :**
- `bind9`
- `unbound`

:::tip Conseil
Lire ou relire le fonctionnement du gestionnaire de paquet `apt`.
:::

### Serveur DNS maître

Implémentez un serveur maître pour :
- La zone `<my>.esigoto.info` (où `<my>` est un _placeholder_ pour votre matricule)
- La zone inverse

Ajoutez :
- Champs `A`, `AAAA`, `CNAME`
- Champ `TXT` (réfléchir à son contenu)
- Champs `MX` (déterminer de « bonnes » valeurs)
- `DNSSEC` à votre zone

:::warning
Si vous avez utilisé `unbound` précédemment, passez à `bind9`.
:::

### Serveur DNS menteur

Un serveur DNS peut :
- Mentir
- Bloquer des résolutions de noms

**Mise en place :**
- Utilisez RPZ (Response Policy Zone)
- Bloquez `http://facebook.com`
- Redirigez `http://google.com` vers `http://ddg.gg`

:::tip Réflexion 
Considérez les implications politiques d’un DNS menteur ou bloquant.
:::

**Lectures complémentaires :**
- [Quand ton serveur DNS te bloque ou te ment](https://blog.namok.be/2016-10-18-quand-ton-serveur-dns-te-bloque-ou-te-ment.html)
- [Mise en place d’un DNS menteur](https://blog.namok.be/2017-03-05-mise-en-place-dns-menteur.html)

