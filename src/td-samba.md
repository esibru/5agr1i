# Laboratoire Samba

Mise en place d'un serveur **Samba**, gestion de quelques partages et compréhension des divers paramètres.

> Pour cette manipulation, vous travaillez seul, chacun mettant en place son propre serveur Samba.  
> N'oubliez pas de compléter vos notes.

## Lectures

Les lectures suivantes pourront être utiles…

- Eckstein, R., Collier, Brown, D., and Kelly, P. (2000).  *Samba, installation et mise en œuvre.* O’REILLY. ISBN : 2-84177-090-7 — pp. 1–28, 81–105, 111–144, 151–168

- Les pages de manuel : `man nmbd`,`man smbd`,`man smb.conf`,`man smbmount`,`man smbclient`,`man smbpasswd`

- Les HOWTO officiels :
  - **Samba3-HOWTO**
  - **Samba3-ByExample**

  Disponibles sur le site officiel : [https://www.samba.org/samba/docs/](https://www.samba.org/samba/docs/)

- Le site du projet : [https://www.samba.org](https://www.samba.org)


## Préalables pratiques

### Installation

Inutile de compiler, les paquets de la distribution font très bien l’affaire.  
Les paquets suivants devraient suffire :

```bash
samba (et samba-common)
cifs-utils
smbclient
```

> ✏️ Notez dans vos notes ce que fournissent chacun de ces paquets.


## Modus operandi

Pour prévenir une mauvaise manipulation, il est conseillé de **conserver le fichier de configuration initial de Samba**.

1. Copier le fichier de configuration initial fourni par la distribution :
   ```bash
   cp /etc/samba/smb.conf /etc/samba/smb.conf.debian
   ```

2. Modifier le fichier `smb.conf` selon les besoins de l’exercice.

## Manipulation

Même si la documentation propose de créer un fichier de configuration Samba de toutes pièces, contentez-vous de **modifier le fichier de configuration original** (celui fourni par Debian).

Refaites la manipulation proposée dans le document *Samba3-HOWTO*, **Sections 2.3.1.1 et 2.3.1.2** (pp. 17–27).

- Étape 1 : Serveur anonyme read-only
Implémentez un serveur **anonyme** (tout le monde peut s’y connecter sans mot de passe) **en lecture seule**.

- Étape 2 : Partage anonyme read-write
Ajoutez un partage **anonyme** accessible en **lecture et écriture**.

- Étape 3 : Tests
    - Testez les accès **localement**.  
    - Testez également les accès aux partages **depuis d’autres machines**.


Écarts par rapport à l’énoncé

| Valeurs de l’énoncé | Vos valeurs |
|----------------------|-------------|
| `/export` | `~/exercice1/export` |
| `workgroup = MIDEARTH` | `workgroup = BBEER` |

