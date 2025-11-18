# 📁 STRUCTURE DU PROJET

## Arborescence des fichiers

```
railway-competition-map/
│
├── 📄 index.html                  (14 KB)
│   └── Page web principale avec carte interactive Leaflet
│
├── 📊 railway_data.json           (15 MB)
│   └── Données combinées : géométries des lignes + états d'attribution
│
├── 📖 README.md                   (4.2 KB)
│   └── Documentation du projet (description, fonctionnalités, licence)
│
├── 📝 GUIDE_INSTALLATION.md       (6.5 KB)
│   └── Instructions détaillées pas-à-pas pour GitHub
│
└── 🚫 .gitignore                  (optionnel)
    └── Fichiers à ignorer par Git
```

## Détail des fichiers

### 1️⃣ index.html
**Rôle** : Page web principale contenant toute l'application
**Contenu** :
- Structure HTML avec header et conteneur de carte
- Styles CSS intégrés (couleurs, légende, popups)
- Script JavaScript avec Leaflet pour la carte interactive
- Logique de chargement et affichage des données
- Gestion des couleurs par statut
- Système de popups informatifs

**Technologies utilisées** :
- HTML5
- CSS3 (avec gradients et animations)
- JavaScript ES6+
- Leaflet.js 1.9.4 (CDN)
- OpenStreetMap (fond de carte)

### 2️⃣ railway_data.json
**Rôle** : Base de données des lignes ferroviaires
**Structure** :
```json
{
  "geo_data": {
    "CODE_LIGNE": [
      {
        "coordinates": [[lon, lat], ...],
        "region": "Nom de région"
      }
    ]
  },
  "etat_lignes": [
    {
      "region": "...",
      "type_marche": "TER|TET",
      "lot": "...",
      "relation": "Ville1>Ville2>...",
      "statut": "attribue_SNCF|attribue_concurrent|mis_en_concurrence_pas_attribue",
      "operateur": "..."
    }
  ]
}
```

**Origine des données** :
- Géométries : Excel "lignes-par-region-administrative_LIGHT.xlsx"
- États : JSON "etat_ligne.json" (article Contexte nov. 2025)

### 3️⃣ README.md
**Rôle** : Documentation principale affichée sur GitHub
**Sections** :
- Présentation du projet
- Source des données
- Fonctionnalités
- Structure du projet
- Instructions d'installation
- Guide d'utilisation locale
- Personnalisation
- Licence

### 4️⃣ GUIDE_INSTALLATION.md
**Rôle** : Instructions détaillées étape par étape
**Sections** :
- Méthode rapide (GitHub Web)
- Méthode alternative (ligne de commande)
- Test local
- Personnalisation
- FAQ et résolution de problèmes
- Checklist finale

### 5️⃣ .gitignore
**Rôle** : Exclure les fichiers inutiles de Git
**Contenu** :
- Fichiers système (DS_Store, Thumbs.db)
- Dossiers d'éditeurs (.vscode, .idea)
- Fichiers temporaires
- Node modules (si extension future)
- Fichiers Python temporaires

## Flux de fonctionnement

```
┌─────────────────┐
│  Utilisateur    │
│  ouvre l'URL    │
└────────┬────────┘
         │
         v
┌─────────────────┐
│  index.html     │ ◄─── Chargé depuis GitHub Pages
│  se charge      │
└────────┬────────┘
         │
         v
┌─────────────────┐
│  Leaflet init   │ ◄─── Carte centrée sur France
│  fond OSM       │
└────────┬────────┘
         │
         v
┌─────────────────┐
│  Fetch          │
│railway_data.json│ ◄─── Chargement asynchrone
└────────┬────────┘
         │
         v
┌─────────────────┐
│  Parsing JSON   │
│  + mapping      │
│  région/géo     │
└────────┬────────┘
         │
         v
┌─────────────────┐
│  Simplification │ ◄─── 1 point tous les 5
│  coordonnées    │
└────────┬────────┘
         │
         v
┌─────────────────┐
│  Affichage      │
│  polylines      │
│  colorées       │
└────────┬────────┘
         │
         v
┌─────────────────┐
│  Mise à jour    │
│  compteurs      │
│  légende        │
└────────┬────────┘
         │
         v
┌─────────────────┐
│  Carte          │
│  interactive    │ ◄─── Clic = popup avec infos
│  prête          │
└─────────────────┘
```

## Statistiques du projet

- **Nombre de lignes référencées** : 84
- **Nombre de tracés géographiques** : 993 codes de lignes
- **Régions couvertes** : 8 régions principales
- **Points géographiques** : ~50,000+ (avant simplification)
- **Taille totale** : ~15 MB
- **Temps de chargement** : 2-5 secondes (selon connexion)

## Technologies et dépendances

### Dépendances externes (CDN)
- Leaflet.js v1.9.4
- OpenStreetMap tiles

### Pas de dépendances locales
- Aucun npm install requis
- Aucun build step
- Fonctionne directement dans le navigateur

## Compatibilité navigateurs

✅ Chrome 90+
✅ Firefox 88+
✅ Safari 14+
✅ Edge 90+
❌ Internet Explorer (non supporté)

## Hébergement

### GitHub Pages (recommandé)
- ✅ Gratuit
- ✅ HTTPS automatique
- ✅ Pas de configuration serveur
- ✅ URL propre : username.github.io/repo-name

### Alternatives possibles
- Netlify
- Vercel
- Firebase Hosting
- AWS S3 + CloudFront

## Performance

### Optimisations appliquées
1. **Simplification des tracés** : 1 point tous les 5 pour réduire la complexité
2. **Échantillonnage** : Max 3 tracés par ligne d'état
3. **Lazy loading** : Chargement asynchrone du JSON
4. **CSS optimisé** : Pas de frameworks lourds

### Métriques estimées
- First Contentful Paint : < 1s
- Time to Interactive : 2-5s (chargement JSON)
- Total file size : ~15 MB (principalement le JSON)

## Évolutions possibles

### Fonctionnalités futures
- [ ] Filtres interactifs par région/statut
- [ ] Recherche de lignes
- [ ] Export CSV des données
- [ ] Mode sombre
- [ ] Graphiques statistiques
- [ ] Timeline des attributions
- [ ] Comparaison avant/après

### Optimisations futures
- [ ] Compression du JSON (gzip)
- [ ] Lazy loading progressif des tracés
- [ ] WebWorkers pour le parsing
- [ ] Cache Service Worker
- [ ] Clustering des lignes proches

---

**Version actuelle** : 1.0.0
**Dernière mise à jour** : Novembre 2025
**Mainteneur** : Votre nom
