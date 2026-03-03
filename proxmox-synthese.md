# Fiche Synthèse — Sécurisation des VMs d'évaluation sur Proxmox PVE

---

## 1. Backup de toutes les machines (horodatage)

### Lancer le backup des VMs 600 à 700
```bash
pvesh get /pools --output-format json | jq -r '.[].poolid' | while read pool; do pvesh get /pools/$pool --output-format json | jq -r '.members[] | select(.vmid >= 600 and .vmid <= 700) | .vmid'; done | sort -n | while read vmid; do vzdump $vmid --storage storage --mode snapshot --compress zstd --notes-template "{{cluster}} {{guestname}} {{node}} {{vmid}}"; done
```

Options utilisées :
- `--storage storage` : nom du storage de destination
- `--mode snapshot` : backup sans interruption de la VM
- `--compress zstd` : compression ZSTD
- `--notes-template` : métadonnées cluster, nom, nœud, ID

### Lister les backups effectués
```bash
pvesm list storage --content backup
```

---

## 2. Création du pool d'archivage

### Créer le pool
```bash
pvesh create /pools --poolid examens-archives
```

### Lister tous les pools existants
```bash
pvesh get /pools --output-format json | jq -r '.[].poolid'
```

---

## 3. Migration des VMs dans le pool d'archivage

### Déplacer les VMs 600 à 700 vers `examens-archives`
```bash
pvesh get /pools --output-format json | jq -r '.[].poolid' | while read pool; do pvesh get /pools/$pool --output-format json | jq -r --arg pool "$pool" '.members[] | select(.vmid >= 600 and .vmid <= 700) | .vmid'; done | sort -n | while read vmid; do pvesh set /pools/examens-archives --vms $vmid --allow-move 1; done
```

> Note : `--allow-move 1` est nécessaire si les VMs appartiennent déjà à un autre pool.

### Vérifier les VMs dans le pool `examens-archives`
```bash
pvesh get /pools/examens-archives --output-format json | jq -r '.members[] | "\(.vmid) - \(.name)"' | sort -n
```

---

## 4. Listage des VMs par pool

### VMs d'un pool spécifique
```bash
pvesh get /pools/NOM_POOL --output-format json | jq -r '.members[] | "\(.vmid) - \(.name)"' | sort -n
```

### VMs de tous les pools existants
```bash
pvesh get /pools --output-format json | jq -r '.[].poolid' | while read pool; do echo "=== $pool ==="; pvesh get /pools/$pool --output-format json | jq -r '.members[] | "\(.vmid) - \(.name)"' | sort -n; done
```

---

## Notes importantes

| Élément | Description |
|---|---|
| `jq` | Installer via `apt install jq -y` si absent |
| Permissions Proxmox | Les droits sont attachés au **pool**, pas aux VMs individuellement |
| Effet de la migration | En déplaçant les VMs vers `examens-archives`, les étudiants perdent automatiquement l'accès car ils n'ont aucun droit sur ce nouveau pool |
| Vérification des accès | `pvesh get /access/acl --output-format json \| jq -r '.[] \| select(.ugid == "NOM_USER_OU_GROUPE")'` |

---

*Document généré suite à la sécurisation des VMs d'évaluation — Proxmox PVE*
