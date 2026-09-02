# Aperçu santé

## Mois — Bristol

Cliquer sur « ◦ » pour revenir au mois courant, « < » et « > » pour naviguer.

``` tracker
searchType: frontmatter
searchTarget: bristol
datasetName: Bristol
folder: Journal
month:
    startWeekOn: 'Mon'
    circleColorByValue: true
    yMin: 0
    yMax: 7
    color: steelblue
    showSelectedValue: true
    todayRingColor: orange
    selectedRingColor: steelblue
```

## Mois — Sang, Glaires, Douleur, Fatigue

Cliquer sur le nom du dataset pour changer de métrique.

``` tracker
searchType: frontmatter
searchTarget: sang, glaires, douleur, fatigue
datasetName: Sang, Glaires, Douleur, Fatigue
folder: Journal
month:
    dataset: 0, 1, 2, 3
    startWeekOn: 'Mon'
    circleColorByValue: true
    yMin: 0
    yMax: 5
    color: crimson
    showSelectedValue: true
    todayRingColor: orange
    selectedRingColor: steelblue
```

## Tendance — Bristol (30 derniers jours)

``` tracker
searchType: frontmatter
searchTarget: bristol
datasetName: Bristol
folder: Journal
line:
    title: Bristol — 30 derniers jours
    yMin: 0
    yMax: 7
    lineColor: steelblue
    pointColor: steelblue
```

## 7 derniers jours — scores

```dataview
TABLE bristol AS "Bristol", sang AS "Sang", glaires AS "Glaires", douleur AS "Douleur", fatigue AS "Fatigue"
FROM "Journal"
SORT file.name DESC
LIMIT 7
```

## 7 derniers jours — repas

```dataview
TABLE WITHOUT ID file.link AS "Jour", repas AS "Repas"
FROM "Journal"
SORT file.name DESC
LIMIT 7
```

## Légende

| Valeur | Type |
|---|---|
| 0 | pas de selles |
| 1–2 | constipation (selles dures) |
| 3–4 | normal |
| 5 | selles molles |
| 6–7 | diarrhée (liquides) |

Intensité de couleur = valeur (plus foncé = plus élevé). Échelle Sang/Glaires/Douleur/Fatigue : 0 à 5.
