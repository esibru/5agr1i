---
marp: true
headingDivider: 1
paginate: true
footer: 'Pierre Bettens _pbt_'  
header: 'SAMBA'
style: |
    h1, h2 {
      color: #3e8ea3;
    }
    footer {
      background: #D2D2D2;
      color: peru;
      position: absolute;
      left: 0px;
      right: 0px;
      height: 25px;
      bottom: 0px;
      padding: 5px 20px;
    }
    section::after {
      /* Layout of pagination content */
      background-color: darkgrey;
      color:#3e8ea3;
      position: absolute;
      bottom: 0px;
      right: 0px;
      width: 150px;
      height: 25px;
      line-height: 20px;
      padding: 5px 2px 5px 35px;
      text-align: center;
      /* Add number of pages*/
      content: attr(data-marpit-pagination) ' / ' attr(data-marpit-pagination-total);
    }
    section.inverted {
      background-color: #3e8ea3;
      color: white;
    }
    section.inverted h1,
    section.inverted h2 {
      color: white;
    }
    section.inverted-orange a,
    section.inverted-orange h1,
    section.inverted-orange h2 {
      color: white;
    }
    section.inverted-orange {
      background-color:rgb(217, 124, 30);
      color: white;
    }
    section.highlight h1, 
    section.highlight h2, 
    section.highlight p {
      background-color: white;
      display: inline-block;
      padding:.32rem;
    }
    .columns {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 1rem;
    }
    .columns30 {
        display: grid;
        grid-template-columns: 30% 70%;
        gap: 1rem;
    }
    /* Add center option for image */
    img[alt~="center"] {
      display: block;
      margin: 0 auto;
    }
    blockquote {
      padding: .3rem;
      border-left: 4px solid #ccc;
      border-radius: 6px;
      position: relative;
      background-color: #f9f9f9;
    }

    /* Base icon style */
    blockquote::before {
      content: "";
      position: absolute;
      left: 1em;
      top: 1.1em;
      width: 1em;
      height: 1em;
      background-repeat: no-repeat;
      background-size: contain;
    }

    /* Note: blue info icon */
    section.note blockquote {
      padding-left: 3rem;
      border-left: 4px solid #0078d4;
      background: #f3f9fd;
    }
    section.note blockquote::before {
      background-image: url("data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAxNiAxNiIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2Ij48cGF0aCBkPSJNMCA4YTggOCAwIDEgMSAxNiAwQTggOCAwIDAgMSAwIDhabTgtNi41YTYuNSA2LjUgMCAxIDAgMCAxMyA2LjUgNi41IDAgMCAwIDAtMTNaTTYuNSA3Ljc1QS43NS43NSAwIDAgMSA3LjI1IDdoMWEuNzUuNzUgMCAwIDEgLjc1Ljc1djIuNzVoLjI1YS43NS43NSAwIDAgMSAwIDEuNWgtMmEuNzUuNzUgMCAwIDEgMC0xLjVoLjI1di0yaC0uMjVhLjc1Ljc1IDAgMCAxLS43NS0uNzVaTTggNmExIDEgMCAxIDEgMC0yIDEgMSAwIDAgMSAwIDJaIj48L3BhdGg+PC9zdmc+");
    }

    /* Tip: green lightbulb */
    section.tip blockquote {
      padding-left: 3rem;
      border-left: 4px solid #107c10;
      background: #f1faf1;
    }
    section.tip blockquote::before {
      background-image: url("data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAxNiAxNiIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2Ij48cGF0aCBkPSJNOCAxLjVjLTIuMzYzIDAtNCAxLjY5LTQgMy43NSAwIC45ODQuNDI0IDEuNjI1Ljk4NCAyLjMwNGwuMjE0LjI1M2MuMjIzLjI2NC40Ny41NTYuNjczLjg0OC4yODQuNDExLjUzNy44OTYuNjIxIDEuNDlhLjc1Ljc1IDAgMCAxLTEuNDg0LjIxMWMtLjA0LS4yODItLjE2My0uNTQ3LS4zNy0uODQ3YTguNDU2IDguNDU2IDAgMCAwLS41NDItLjY4Yy0uMDg0LS4xLS4xNzMtLjIwNS0uMjY4LS4zMkMzLjIwMSA3Ljc1IDIuNSA2Ljc2NiAyLjUgNS4yNSAyLjUgMi4zMSA0Ljg2MyAwIDggMHM1LjUgMi4zMSA1LjUgNS4yNWMwIDEuNTE2LS43MDEgMi41LTEuMzI4IDMuMjU5LS4wOTUuMTE1LS4xODQuMjItLjI2OC4zMTktLjIwNy4yNDUtLjM4My40NTMtLjU0MS42ODEtLjIwOC4zLS4zMy41NjUtLjM3Ljg0N2EuNzUxLjc1MSAwIDAgMS0xLjQ4NS0uMjEyYy4wODQtLjU5My4zMzctMS4wNzguNjIxLTEuNDg5LjIwMy0uMjkyLjQ1LS41ODQuNjczLS44NDguMDc1LS4wODguMTQ3LS4xNzMuMjEzLS4yNTMuNTYxLS42NzkuOTg1LTEuMzIuOTg1LTIuMzA0IDAtMi4wNi0xLjYzNy0zLjc1LTQtMy43NVpNNS43NSAxMmg0LjVhLjc1Ljc1IDAgMCAxIDAgMS41aC00LjVhLjc1Ljc1IDAgMCAxIDAtMS41Wk02IDE1LjI1YS43NS43NSAwIDAgMSAuNzUtLjc1aDIuNWEuNzUuNzUgMCAwIDEgMCAxLjVoLTIuNWEuNzUuNzUgMCAwIDEtLjc1LS43NVoiPjwvcGF0aD48L3N2Zz4=");
    }

    /* Important: purple icon */
    section.important blockquote {
      padding-left: 3rem;
      border-left: 4px solid #8a2be2;
      background: #f6f0fb;
    }
    section.important blockquote::before {
      background-image: url("data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAxNiAxNiIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2Ij48cGF0aCBkPSJNMCAxLjc1QzAgLjc4NC43ODQgMCAxLjc1IDBoMTIuNUMxNS4yMTYgMCAxNiAuNzg0IDE2IDEuNzV2OS41QTEuNzUgMS43NSAwIDAgMSAxNC4yNSAxM0g4LjA2bC0yLjU3MyAyLjU3M0ExLjQ1OCAxLjQ1OCAwIDAgMSAzIDE0LjU0M1YxM0gxLjc1QTEuNzUgMS43NSAwIDAgMSAwIDExLjI1Wm0xLjc1LS4yNWEuMjUuMjUgMCAwIDAtLjI1LjI1djkuNWMwIC4xMzguMTEyLjI1LjI1LjI1aDJhLjc1Ljc1IDAgMCAxIC43NS43NXYyLjE5bDIuNzItMi43MmEuNzQ5Ljc0OSAwIDAgMSAuNTMtLjIyaDYuNWEuMjUuMjUgMCAwIDAgLjI1LS4yNXYtOS41YS4yNS4yNSAwIDAgMC0uMjUtLjI1Wm03IDIuMjV2Mi41YS43NS43NSAwIDAgMS0xLjUgMHYtMi41YS43NS43NSAwIDAgMSAxLjUgMFpNOSA5YTEgMSAwIDEgMS0yIDAgMSAxIDAgMCAxIDIgMFoiPjwvcGF0aD48L3N2Zz4=");
    }

    /* Warning: orange triangle */
    section.warning blockquote {
      padding-left: 3rem;
      border-left-color: #b58900;
      background: #fffbe6;
    }
    section.warning blockquote::before {
      background-image: url("data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAxNiAxNiIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2Ij48cGF0aCBkPSJNNi40NTcgMS4wNDdjLjY1OS0xLjIzNCAyLjQyNy0xLjIzNCAzLjA4NiAwbDYuMDgyIDExLjM3OEExLjc1IDEuNzUgMCAwIDEgMTQuMDgyIDE1SDEuOTE4YTEuNzUgMS43NSAwIDAgMS0xLjU0My0yLjU3NVptMS43NjMuNzA3YS4yNS4yNSAwIDAgMC0uNDQgMEwxLjY5OCAxMy4xMzJhLjI1LjI1IDAgMCAwIC4yMi4zNjhoMTIuMTY0YS4yNS4yNSAwIDAgMCAuMjItLjM2OFptLjUzIDMuOTk2djIuNWEuNzUuNzUgMCAwIDEtMS41IDB2LTIuNWEuNzUuNzUgMCAwIDEgMS41IDBaTTkgMTFhMSAxIDAgMSAxLTIgMCAxIDEgMCAwIDEgMiAwWiI+PC9wYXRoPjwvc3ZnPg==");
    }

    /* Caution: red icon */
    section.caution blockquote {
      padding-left: 3rem;
      border-left-color: #d13438;
      background: #fdf3f4;
    }
    section.caution blockquote::before {
      background-image: url("data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAxNiAxNiIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2Ij48cGF0aCBkPSJNNC40Ny4yMkEuNzQ5Ljc0OSAwIDAgMSA1IDBoNmMuMTk5IDAgLjM4OS4wNzkuNTMuMjJsNC4yNSA0LjI1Yy4xNDEuMTQuMjIuMzMxLjIyLjUzdjZhLjc0OS43NDkgMCAwIDEtLjIyLjUzbC00LjI1IDQuMjVBLjc0OS43NDkgMCAwIDEgMTEgMTZINWEuNzQ5Ljc0OSAwIDAgMS0uNTMtLjIyTC4yMiAxMS41M0EuNzQ5Ljc0OSAwIDAgMSAwIDExVjVjMC0uMTk5LjA3OS0uMzg5LjIyLS41M1ptLjg0IDEuMjhMMS41IDUuMzF2NS4zOGwzLjgxIDMuODFoNS4zOGwzLjgxLTMuODFWNS4zMUwxMC42OSAxLjVaTTggNGEuNzUuNzUgMCAwIDEgLjc1Ljc1djMuNWEuNzUuNzUgMCAwIDEtMS41IDB2LTMuNUEuNzUuNzUgMCAwIDEgOCA0Wm0wIDhhMSAxIDAgMSAxIDAtMiAxIDEgMCAwIDEgMCAyWiI+PC9wYXRoPjwvc3ZnPg==");
    }
---

# SAMBA

![bg](images/samba.jpg)

<!-- 
_class: highlight
_footer: ''
_paginate: false
-->

# SAMBA 

Mise en œuvre du protocole SMB / CIFS de Microsoft pour le partage de fichiers (et d'imprimantes).

<br/>

Samba est une réimplémentation du protocole SMB / CIFS pour *nix ce qui permet une communication MS Windows / *unix.

# NetBIOS

Mode de nommage dans un voisinage réseaux : API _couche 5 (session)_ utilise les ports `137`, `138` et `139`.

- NetBIOS implémenté (sans IP) par NetBEUI (_obsolète_)
- NetBIOS implémenté (sur IP) par NetBT

Un nom NetBIOS fait 15 + 1 caractères (le 16^{ième} pour le rôle)

<br/>
<small><small>

Cfr NetBIOS-suffix
</small></small>

---
![bg](images/voisinage.png)
<!--
_header: ''
_footer: ''
_paginate: false
-->

# Voisinage réseau

Le **voisinage réseau** (_browse list_) permet de visualiser les machines et leurs partages sur un même segment IP.

---
## Master Browser

<div class="columns30">
<div>
<br/>

![center w:250](images/vote.svg)

</div><div>

Le **master browser** est responsable du maintient de la liste d'exploration (_browse list_)

- élection automatique
- critères d'élection : version OS, type de machine, temps de fonctionnement
- le master browser collecte les annonces `__MSBROWSE__` 

</div></div>

---

| Aspect | Détail |
|:-------|:-------|
| **Fréquence** | Toutes les 12 minutes |
| **Transport** | UDP ports 137 (noms) et 138 (datagrammes) |
| **Mode** | Broadcast sur le segment local |
| **Timeout** | 36 minutes (3 périodes manquées) |
| **Portée** | Segment local uniquement |

<br/>

<!-- class: warning -->
> **Important :** Sans serveur WINS, le voisinage ne fonctionne que sur le segment local (les broadcasts ne traversent pas les routeurs)

# WINS

**WINS** (_Windows Internet Name Service_)

Service de résolution de noms NetBIOS vers adresses IP   
Alternative au broadcast NetBIOS.
<br/>

<!-- class: note -->
> **Tip** 
> WINS est essentiel dans les réseaux routés avec plusieurs segments IP

----
## Configuration Samba comme serveur WINS

Extrait de configuration Samba (_see below_)
```ini
[global]
    wins support = yes
    wins server = 192.168.1.10
    name resolve order = lmhosts wins bcast host
```

# Authentification

Samba supporte plusieurs modes d'authentification pour l'accès à un partage.

<big>

`share` - `user` - `server` - `domain`

</big>

---

### Share-level security (**OBSOLÈTE**)
```ini
[global]
    security = share
```
- Authentification par **partage** (pas par utilisateur)
- Mot de passe demandé pour chaque partage
- **Abandonné depuis Samba 4.0**
- Remplacé par `guest ok = yes` au niveau des partages

---
### User-level security
```ini
[global]
    security = user
    passdb backend = tdbsam
```
- Authentification par **compte utilisateur**
- Base locale des comptes Samba (`/var/lib/samba/private/`)
- Mode par défaut et recommandé pour serveurs autonomes

---
### Server-level security (**OBSOLÈTE**)
```ini
[global]
    security = server
    password server = 192.168.1.100
```
- Délégation vers un **serveur d'authentification**
- **Déprécié depuis Samba 3.x**
- Remplacé par domain security

---
### Domain-level security 
```ini
[global]
    security = domain
    workgroup = MONDOMAINE
    password server = *
```
- Intégration complète dans un **domaine Active Directory**
- Authentification via contrôleur de domaine
- Support Kerberos et NTLM
<br/>

<!-- class: important -->
> **Important** 
> Utiliser `security = user` pour un serveur autonome ou `security = domain` pour l'intégration AD


# Challenge-Response

Protocole sécurisé évitant la transmission du mot de passe en clair sur le réseau.


---
<div class="columns30">
<div>
<br/>

![center](images/puzzle.png)

</div><div>

1. **Client** demande l'accès à une ressource
2. **Serveur** envoie un **challenge** (nombre aléatoire)
3. **Client** chiffre le challenge avec son mot de passe haché
4. **Serveur** vérifie la réponse avec sa copie du hash

</div></div>

# NTLM v1 : LAN Manager et NT Hash

Premier protocole d'authentification Microsoft, aujourd'hui **obsolète**.

- LAN Manager
    - Mot de passe → UPPERCASE → Padding 14 chars → Split 7+7
    - Chaque moitié → DES avec clé fixe "KGS!@#$%" 
    - Concaténation des résultats → LM Hash (32 hex)
- NT Hash
    - Mot de passe → Unicode UTF-16LE → MD4 → NT Hash (32 hex)

<br/>

<!-- class: caution -->
> **Attention** 
> Désactiver NTLM v1

# NTLM v2 

Version améliorée d'NTLM avec une sécurité renforcée

- Username + Domain → Unicode → HMAC-MD5(NT Hash) → NTLMv2 Hash
<br/>

Configuration Samba NTLMv2

```ini
[global]
    ntlm auth = ntlmv2-only # default Samba 4.7
```

# Installation Samba

Paquets : `samba samba-common` `smbclient`
<br/>
Daemons associés
- `smbd` SMB/CIFS File Server  
    Partage de fichiers et imprimantes, gestion des connexions SMB/CIFS, authentification, contrôle d'accès.  
    **Port TCP 445** (SMB direct) et **139** (NetBIOS session service)

---
- `nmbd` NetBIOS Name Server
    Service de noms NetBIOS, gestion du voisinage réseau (_browse list_), élection du Master Browser et serveur WINS (optionnel)
    **Port UDP 137** (NetBIOS name service) et **138** (NetBIOS datagram service)

- `winbind` Domain Integration
    Intégration Active Directory, résolution UIDs/GIDs dynamiques, Single Sign-On avec Windows et support des groupes de domaine.

# Configuration Samba

Fichier `/etc/samba/smb.conf`

```ini
# Section globale (obligatoire)
[global]
    # Paramètres généraux du serveur
    
# Sections de partages
[nom_partage]
    # Configuration spécifique au partage
    
[homes]
    # Partage automatique des répertoires utilisateurs
    
[printers]
    # Configuration des imprimantes
```

---
## Section `[global]`

### Paramètres essentiels
```ini
[global]
    workgroup = WORKGROUP
    server string = Serveur Samba %h
    netbios name = MONSERVEUR
    
    # Sécurité
    security = user
    
    # …
```

---
### Variables Samba

Système de substitution automatique pour personnaliser la configuration.

<div class="columns">
<div>

| Variable | Description |
|:---------|:------------|
| `%u` | nom d'utilisateur actuel |
| `%U` | nom d'utilisateur demandé |
| `%g` | groupe primaire de %u |
| `%G` | groupe primaire de %U |
| `%m` | nom NetBIOS du client |
| `%M` | nom DNS du client |
| `%I` | adresse IP du client |

</div><div>

| Variable | Description |
|:---------|:------------|
| `%h` | nom d'hôte du serveur |
| `%L` | nom NetBIOS du serveur |
| `%S` | nom du service actuel |
| `%P` | répertoire racine du service |
| `%T` | heure/date actuelle |

(cfr. `man smb.conf`)

</div></div>

---
```ini
[global]
    # Log par machine cliente
    log file = /var/log/samba/log.%m
    
    # Message de bienvenue personnalisé
    server string = Serveur %h - Connexion de %m (%I)

[homes]
    # Partage utilisateur dynamique
    path = /home/%u
    comment = Répertoire de %U
    
[profiles]
    # Profils utilisateurs
    path = /srv/samba/profiles/%u
    create mask = 0600
```

---
## Validation de la configuration

`testparm` vérifie la validité syntaxique du fichier de configuration.

```bash
testparm
```
<br/>

<!-- class: tip -->
> **Tip :** Utiliser `testparm` avant chaque redémarrage des services pour éviter les erreurs de configuration

# Gestion des utilisateurs Samba

Les utilisateurs Samba sont **distincts** des utilisateurs Unix mais doivent correspondre.


```bash
# Prérequis : l'utilisateur Unix doit exister
adduser john
passwd john
# Puis créer l'utilisateur Samba
sudo smbpasswd -a john
```

# Tests 

`smbclient` est un client en ligne de commande _à tout faire_
<small>

```bash
smbclient -L //localhost -U username
smbclient //serveur/partage -U username

smb: \> ls
smb: \> cd dossier
smb: \> get fichier.txt
smb: \> put fichier.txt
smb: \> exit
```
</small>

`smbstatus` montre voir l'activité
<small>

```bash
smbstatus
```
</small>

---
## Logs en temps réel

Les logs se trouvent dans le répertoire `/var/log/samba/`

```bash
tail -f /var/log/samba/log.smbd
tail -f /var/log/samba/log.192.168.1.50
```
<br/>

## Vérifier les ports

```bash
# Ports Samba ouverts
netstat -tulpn | grep -E '(smbd|nmbd)'
```

---
## Test de résolution de noms

```bash
# Résolution NetBIOS
nmblookup serveur

# Ping NetBIOS
nmblookup -A 192.168.1.10
```

















---
Slides dans le cadre de mes cours.
<span class="square"></span>

### Qui suis-je ? 
Pierre Bettens (_pbt_)  
[blog.namok.be](https://blog.namok.be)
pbettens@he2b.be · bettensp@helha.be

### Crédits
GNU linux, _markdown_, Codium, Marpit

Licence WTFL

<style scoped>
    section {text-align: center;}
    .square {
        margin: 15px auto;
        display: block;
        width: 150px;
        height: 150px;
        cursor: pointer;
        background-color: peru;
    }
</style>