# Journal de santé — Documentation d'installation

Suivi quotidien des repas et des selles (échelle de Bristol), avec aperçu visuel au mois et à la semaine.

## Structure du vault

```
obsidian/
├── README.md                       ← ce document
├── Templates/
│   └── Santé quotidienne.md        ← template de la note journalière
├── Vues/
│   └── Santé - Aperçu.md           ← dashboard visuel (mois, tendance, 7 jours)
└── Journal/                        ← notes quotidiennes (créé automatiquement)
```

## Prérequis

- [Obsidian](https://obsidian.md) (version récente, interface propriétés incluse)
- Connexion internet pour l'installation des plugins communautaires

## 1. Ouvrir le vault

1. Lancer Obsidian
2. « Open folder as vault » → sélectionner ce dossier (`obsidian`)
3. Le dossier `.obsidian/` est créé automatiquement (config du vault)

## 2. Installer les plugins communautaires

1. Paramètres → **Community plugins** (Plugins communautaires)
2. **Turn off restricted mode** (désactiver le mode restreint)
3. **Browse** et installer :
   - **Tracker** (auteur : pyrochlore) — vues mensuelles colorées, graphiques
   - **Dataview** (auteur : Michael Brenan) — tableaux dynamiques
4. **Enable** les deux plugins

## 3. Configurer les notes quotidiennes

Plugin core « Daily notes » (Notes quotidiennes) :

| Paramètre | Valeur |
|---|---|
| Date format | `YYYY-MM-DD` |
| New file location | `Journal` |
| Template file location | `Templates/Santé quotidienne.md` |

Le dossier `Journal/` n'existe pas encore : il sera créé à la première note quotidienne.

## 4. Créer la première note

1. Commande **« Daily notes: Open today's daily note »** (Palette `Ctrl/Cmd+P`) ou icône calendrier dans la barre latérale gauche
2. La note du jour s'ouvre, pré-remplie avec le template
3. Remplir les propriétés en haut de la note

## Utilisation quotidienne

### Remplir les propriétés

| Champ | Type | Description |
|---|---|---|
| `repas` | liste | Heure (modifiable), contenu, notes — 3 créneaux par défaut |
| `selles` | liste | Heure, Bristol (0–7), sang (0–5), glaires (0–5), notes — ajouter une entrée par selle |
| `bristol` | nombre | **Pire valeur du jour** parmi les selles (0 = pas de selles) |
| `sang` | nombre | **Pire valeur du jour** (0–5) |
| `glaires` | nombre | **Pire valeur du jour** (0–5) |
| `douleur` | nombre | 0–5 (0 = aucune, 5 = insupportable) |
| `fatigue` | nombre | 0–5 (0 = aucune, 5 = épuisement total) |
| `notes` | texte | Notes libres de la journée |

**Règle importante** : les champs plats `bristol`, `sang`, `glaires` doivent refléter la pire valeur des selles du jour. Ce sont eux que lisent les vues mensuelles. Aucune selle dans la journée → laisser 0.

### Échelle de Bristol

| Valeur | Type |
|---|---|
| 0 | pas de selles |
| 1 | billes dures séparées (constipation sévère) |
| 2 | saucisse grumeleuse (constipation) |
| 3 | saucisse fissurée (normal) |
| 4 | saucisse lisse et molle (normal) |
| 5 | morceaux mous à bords nets (tendance diarrhée) |
| 6 | selles molles en fragments (diarrhée) |
| 7 | liquide, sans morceau (diarrhée sévère) |

## Aperçu visuel

Ouvrir `Vues/Santé - Aperçu.md` :

- **Mois — Bristol** : grille du mois, cercles colorés par valeur. Naviguer avec `<` `>` (mois précédent/suivant) et `◦` (mois courant)
- **Mois — Sang, Glaires, Douleur, Fatigue** : cliquer sur le nom de la métrique pour changer de dataset
- **Tendance — Bristol** : graphique des 30 derniers jours
- **7 derniers jours — scores** : tableau récapitulatif
- **7 derniers jours — repas** : détails des repas

## Personnalisation

- **Couleurs** : dans `Vues/Santé - Aperçu.md`, modifier `color:` des blocs Tracker (noms CSS ou codes hex)
- **Créneaux repas par défaut** : modifier les heures dans `Templates/Santé quotidienne.md`
- **Échelles** : ajuster `yMin`/`yMax` des blocs si une échelle change

## Dépannage

| Problème | Solution |
|---|---|
| Blocs Tracker vides | Vérifier que des notes existent dans `Journal/` et que les champs plats (`bristol`, etc.) sont bien des nombres |
| Vue mensuelle figée sur un mauvais mois | Cliquer sur `◦` pour revenir au mois courant |
| Tableaux Dataview absents | Vérifier que le plugin Dataview est activé |
| Note quotidienne sans template | Vérifier « Template file location » dans les réglages Notes quotidiennes |
| Valeur erronée dans la grille | La grille lit les champs plats, pas les entrées du tableau `selles` — mettre à jour la pire valeur |
