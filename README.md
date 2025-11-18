# 🚆 Carte de l'ouverture à la concurrence des lignes ferroviaires françaises

Une visualisation interactive de l'état d'ouverture à la concurrence des lignes ferroviaires TER et TET en France (hors Île-de-France et Corse).

## 📊 Source des données

- **Données d'état des lignes** : Article Contexte "Ouverture du rail à la concurrence : les régions en ordre dispersé" (17 novembre 2025)
- **Données géographiques** : Lignes ferroviaires par région administrative (fichier Excel)

## 🗺️ Fonctionnalités

- **Visualisation cartographique interactive** avec Leaflet
- **Tracés réels des lignes** ferroviaires (pas de lignes droites)
- **Code couleur par statut** :
  - 🟢 Vert : Attribué à la SNCF
  - 🔵 Bleu : Attribué à un concurrent
  - 🟠 Orange : Mis en concurrence (non attribué)
- **Popups informatives** au clic sur chaque ligne avec :
  - Relation (villes)
  - Région
  - Type de marché (TER/TET)
  - Lot
  - Statut
  - Opérateur (si attribué)
- **Légende dynamique** avec compteurs

## 📁 Structure du projet

```
railway-competition-map/
│
├── index.html              # Page web principale
├── railway_data.json       # Données combinées (géographie + état)
└── README.md              # Ce fichier
```

## 🚀 Installation sur GitHub Pages

### Méthode 1 : Upload direct

1. Créez un nouveau repository sur GitHub (ex: `railway-competition-map`)
2. Uploadez les fichiers suivants :
   - `index.html`
   - `railway_data.json`
   - `README.md`
3. Allez dans Settings → Pages
4. Sélectionnez la branche `main` et le dossier `/root`
5. Cliquez sur Save
6. Votre site sera disponible à : `https://votre-username.github.io/railway-competition-map/`

### Méthode 2 : Ligne de commande

```bash
# Cloner votre repository
git clone https://github.com/votre-username/railway-competition-map.git
cd railway-competition-map

# Copier les fichiers
cp chemin/vers/index.html .
cp chemin/vers/railway_data.json .
cp chemin/vers/README.md .

# Commit et push
git add .
git commit -m "Initial commit: Carte ferroviaire interactive"
git push origin main

# Activer GitHub Pages dans Settings → Pages
```

## 🔧 Utilisation locale

Pour tester localement avant de publier :

```bash
# Serveur Python simple
python3 -m http.server 8000

# Ou avec Node.js
npx http-server
```

Puis ouvrez : `http://localhost:8000`

## ⚠️ Important

- **Taille du fichier JSON** : Le fichier `railway_data.json` fait environ 15 MB. GitHub accepte les fichiers jusqu'à 100 MB.
- **Performances** : La carte charge toutes les données au démarrage. Le temps de chargement peut varier selon la connexion.
- **Navigateurs supportés** : Tous les navigateurs modernes (Chrome, Firefox, Safari, Edge)

## 🎨 Personnalisation

### Modifier les couleurs

Dans `index.html`, section `<script>`, modifiez :

```javascript
const statusColors = {
    'attribue_SNCF': '#4CAF50',        // Vert
    'attribue_concurrent': '#2196F3',   // Bleu
    'mis_en_concurrence_pas_attribue': '#FF9800'  // Orange
};
```

### Modifier la simplification des lignes

Pour afficher plus ou moins de points sur les lignes, modifiez la fonction :

```javascript
const coords = simplifyCoordinates(lignesGeo[idx], 5);  // Changer 5 à une autre valeur
```

- Valeur plus petite = plus de détails (mais plus lent)
- Valeur plus grande = moins de détails (mais plus rapide)

## 📝 Licence

Les données proviennent de sources publiques. La visualisation est libre d'utilisation.

## 🐛 Problèmes connus

- **Mapping des lignes** : La correspondance entre les relations de villes et les tracés géographiques est approximative (basée sur les régions)
- **Lignes multiples** : Certaines lignes peuvent être représentées plusieurs fois si elles traversent plusieurs régions

## 💡 Améliorations futures possibles

- [ ] Ajout d'un système de filtres par région
- [ ] Recherche de lignes spécifiques
- [ ] Export des données en CSV
- [ ] Animation du passage des lignes en concurrence
- [ ] Statistiques détaillées par région

## 📧 Contact

Pour toute question ou suggestion d'amélioration, n'hésitez pas à ouvrir une issue sur GitHub.

---

**Dernière mise à jour** : Novembre 2025
