
---
marpit: true
---

# PAM – Pluggable Authentication Modules
_HE2B-ÉSI – Pierre Bettens_

---

## 🔐 Définition

Ensemble de bibliothèques responsables de la **centralisation de l'authentification**.

- Évolution
- Délégation

---

## 👥 Rôles

- **Développeur** : délègue l'authentification à PAM
- **Administrateur** : configure le comportement des applications

---

## 📁 Fichiers de configuration

- `/etc/pam.d` : un fichier par application
- `/etc/pam.conf` : ancienne méthode

---

## 🧾 Format du fichier de configuration

```
module-type control-flag module-path args
```

### module-type

- `auth`
- `account`
- `session`
- `password`

---

## 🧾 Format du fichier de configuration (suite)

### control-flag

- `required`
- `requisite`
- `sufficient`
- `optional`

---

## 🧾 Format du fichier de configuration (suite)

### module-path

Chemin vers le module (absolu ou relatif)

### args

Arguments pour le module

---

## 🧪 Exemple de configuration

```text
auth required /lib/security/pam_securetty.so
auth required /lib/security/pam_env.so
auth sufficient /lib/security/pam_ldap.so
auth required /lib/security/pam_unix.so try_first_pass
```

---

## 👨‍💻 Côté développeur

### Code source

```c
#include <security/pam_appl.h>
#include <security/pam_misc.h>
...
pam_authenticate();
```

### Compilation

```bash
cc -o application ... -lpam -lpam_misc -ldl
```

---

## 📚 Références

- *TCP/IP Network Administration* (Craig Hunt)
- Pages de manuel : `pam`, `liens`

---

## 👤 Auteur

Pierre Bettens (pbt)  
pbettens@he2b.be  
[blog.namok.be](http://blog.namok.be)  
[esi.namok.be](http://esi.namok.be)

---
