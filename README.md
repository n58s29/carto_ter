# 🚄 Carte de l'ouverture à la concurrence des lignes TER

Une visualisation interactive des lignes ferroviaires TER en France et de leur statut d'ouverture à la concurrence.

![Aperçu de la carte](https://img.shields.io/badge/Lignes-131-blue) ![Statut](https://img.shields.io/badge/Concurrence-13_lignes-red) ![Source](https://img.shields.io/badge/Source-Contexte-orange)

## 📋 Description

Ce projet visualise l'état de l'ouverture à la concurrence des lignes ferroviaires TER (Transport Express Régional) en France, suite à la libéralisation du secteur ferroviaire. La carte interactive permet de voir en un coup d'œil :

- Les lignes restées chez **SNCF** (en bleu)
- Les lignes attribuées à des **opérateurs concurrents** (en rouge)
- Les lignes **mises en concurrence mais non encore attribuées** (en orange)

## 🗺️ Visualisation

La carte affiche **131 liaisons ferroviaires** réparties comme suit :

- 🔵 **46 lignes gérées par SNCF**
- 🔴 **13 lignes gérées par des concurrents** (RATP, Transdev)
- 🟠 **72 lignes mises en concurrence** (non attribuées)

### Opérateurs concurrents présents :

- **RATP** : Étoile de Caen (10 lignes en Normandie)
- **Transdev** : Nancy-Contrexéville (Grand Est), Marseille-Toulon-Nice (PACA)

## 🚀 Utilisation

### Voir la carte en ligne

Ouvrez simplement le fichier `carte_lignes_ter.html` dans votre navigateur web.

### Utiliser les données

Les données sources sont disponibles dans le fichier `etat_ligne.json` avec la structure suivante :

```json
{
  "region": "Normandie",
  "type_marche": "TER",
  "lot": "Étoile de Caen",
  "relation": "Caen>Rouen",
  "statut": "attribue_concurrent",
  "operateur": "RATP"
}
```

## 📊 Structure des données

### Fichiers

- **`etat_ligne.json`** : Données sur les lignes TER et leur statut de concurrence
- **`lignes-par-type.xlsx`** : Données géographiques des lignes ferroviaires (coordonnées GPS)
- **`carte_lignes_ter.html`** : Carte interactive générée

### Statuts possibles

| Statut | Description | Couleur |
|--------|-------------|---------|
| `attribue_SNCF` | Ligne attribuée à la SNCF | 🔵 Bleu |
| `attribue_concurrent` | Ligne attribuée à un opérateur concurrent | 🔴 Rouge |
| `mis_en_concurrence_pas_attribue` | Ligne mise en concurrence mais pas encore attribuée | 🟠 Orange |

## 🛠️ Génération de la carte

### Prérequis

```bash
pip install pandas openpyxl unidecode
```

### Exécution

```bash
python generate_map_json_only.py
```

Le script :
1. Charge les données du fichier JSON
2. Géocode les villes françaises (coordonnées GPS)
3. Crée des liaisons entre chaque paire de villes
4. Génère une carte interactive avec Leaflet.js

## 📖 Technologies utilisées

- **Python** : Traitement des données
- **Leaflet.js** : Cartographie interactive
- **OpenStreetMap** : Fond de carte
- **pandas** : Manipulation des données

## 📚 Sources

- **Source des données** : [Contexte](https://www.contexte.com/) - Article "Ouverture du rail à la concurrence : les régions en ordre dispersé" (17/11/2025)
- Les données concernent les lignes TER et TET (hors Île-de-France et Corse)

## 🔍 Fonctionnalités de la carte

- **Survol** : Les lignes s'agrandissent et s'illuminent au passage de la souris
- **Clic** : Affiche un popup avec les détails complets :
  - Nom de la liaison
  - Région
  - Relation complète
  - Lot de marché
  - Statut d'attribution
  - Opérateur
- **Légende interactive** avec compteurs par catégorie
- **Responsive** : Fonctionne sur desktop et mobile

## 📄 Licence

Données utilisées sous réserve des droits de Contexte. Carte et code générés à des fins d'information et de visualisation.

## 🤝 Contribution

Les contributions sont les bienvenues ! N'hésitez pas à :

- Signaler des erreurs dans les données
- Proposer des améliorations de la visualisation
- Ajouter de nouvelles fonctionnalités

## 📧 Contact

Pour toute question ou suggestion concernant ce projet, n'hésitez pas à ouvrir une issue sur GitHub.

---

**Note** : Ce projet est à but informatif et pédagogique. Les données reflètent l'état de l'ouverture à la concurrence des lignes TER au 17 novembre 2025.
