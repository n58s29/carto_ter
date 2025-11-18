# 📋 GUIDE D'INSTALLATION - Carte ferroviaire interactive

## ✅ Fichiers fournis

Vous avez reçu 4 fichiers à placer dans votre repository GitHub :

1. **index.html** (14 KB) - La page web principale avec la carte interactive
2. **railway_data.json** (15 MB) - Les données géographiques et d'état des lignes
3. **README.md** (4.2 KB) - Documentation du projet
4. **.gitignore** - Configuration Git (optionnel)

## 🎯 MÉTHODE RAPIDE : Installation via GitHub Web

### Étape 1 : Créer le repository

1. Allez sur https://github.com
2. Cliquez sur le bouton **"+"** en haut à droite → **"New repository"**
3. Remplissez :
   - Repository name: `railway-competition-map` (ou un autre nom)
   - Description: "Carte interactive de l'ouverture à la concurrence des lignes ferroviaires françaises"
   - Public ✓ (pour GitHub Pages gratuit)
   - Cochez "Add a README file" (vous le remplacerez après)
4. Cliquez sur **"Create repository"**

### Étape 2 : Uploader les fichiers

1. Dans votre nouveau repository, cliquez sur **"Add file"** → **"Upload files"**
2. Glissez-déposez ou sélectionnez les 4 fichiers téléchargés :
   - index.html
   - railway_data.json
   - README.md (remplacera celui créé automatiquement)
   - .gitignore
3. Ajoutez un message de commit : "Initial commit: Carte ferroviaire interactive"
4. Cliquez sur **"Commit changes"**

### Étape 3 : Activer GitHub Pages

1. Dans votre repository, allez dans **Settings** (onglet en haut)
2. Dans le menu de gauche, cliquez sur **Pages**
3. Sous "Build and deployment" :
   - Source: sélectionnez **"Deploy from a branch"**
   - Branch: sélectionnez **"main"** et **"/ (root)"**
   - Cliquez sur **Save**
4. Attendez 1-2 minutes

### Étape 4 : Accéder à votre site

Votre carte sera disponible à l'URL :
```
https://VOTRE-USERNAME.github.io/railway-competition-map/
```

Par exemple, si votre username GitHub est "jean-dupont" :
```
https://jean-dupont.github.io/railway-competition-map/
```

**Note** : Remplacez `VOTRE-USERNAME` par votre nom d'utilisateur GitHub réel !

---

## 💻 MÉTHODE ALTERNATIVE : Ligne de commande Git

Si vous préférez utiliser Git en ligne de commande :

### Prérequis
- Git installé sur votre ordinateur
- Compte GitHub configuré

### Commandes

```bash
# 1. Créer un dossier local
mkdir railway-competition-map
cd railway-competition-map

# 2. Initialiser Git
git init
git branch -M main

# 3. Copier vos 4 fichiers téléchargés dans ce dossier

# 4. Ajouter et committer
git add .
git commit -m "Initial commit: Carte ferroviaire interactive"

# 5. Lier au repository GitHub (créez-le d'abord sur github.com)
git remote add origin https://github.com/VOTRE-USERNAME/railway-competition-map.git

# 6. Pousser vers GitHub
git push -u origin main
```

Puis suivez l'Étape 3 ci-dessus pour activer GitHub Pages.

---

## 🧪 Test local avant publication

Pour tester la carte sur votre ordinateur avant de la publier :

### Avec Python (préinstallé sur Mac/Linux)
```bash
# Naviguez vers le dossier contenant index.html
cd chemin/vers/railway-competition-map

# Lancez un serveur local
python3 -m http.server 8000

# Ouvrez dans votre navigateur
# http://localhost:8000
```

### Avec Node.js
```bash
# Si Node.js est installé
npx http-server
```

### Ou simplement
Double-cliquez sur `index.html` (peut avoir des limitations de sécurité pour le chargement du JSON)

---

## 🎨 Personnalisation (optionnel)

### Changer les couleurs

Ouvrez `index.html` et trouvez cette section (vers la ligne 160) :

```javascript
const statusColors = {
    'attribue_SNCF': '#4CAF50',        // Vert - Changez ce code couleur
    'attribue_concurrent': '#2196F3',   // Bleu
    'mis_en_concurrence_pas_attribue': '#FF9800'  // Orange
};
```

Vous pouvez utiliser un outil comme https://htmlcolorcodes.com/ pour choisir vos couleurs.

### Changer le titre

Ligne 11 de `index.html` :
```html
<title>Ouverture à la concurrence des lignes ferroviaires françaises</title>
```

### Modifier la densité des points sur les lignes

Ligne 202 de `index.html`, changez le `5` :
```javascript
const coords = simplifyCoordinates(lignesGeo[idx], 5);
// Plus petit = plus détaillé (mais plus lent)
// Plus grand = moins détaillé (mais plus rapide)
```

---

## ❓ FAQ - Problèmes courants

### Le site ne s'affiche pas après l'activation de GitHub Pages
- Attendez 2-5 minutes, GitHub Pages prend du temps à se déployer
- Vérifiez que tous les fichiers sont bien dans la racine du repository
- Vérifiez l'URL : elle doit être `username.github.io/nom-du-repo/` (pas `github.com`)

### Erreur "Failed to load railway_data.json"
- Assurez-vous que `railway_data.json` est bien dans le même dossier que `index.html`
- Vérifiez que le fichier a bien été uploadé (15 MB)
- Si test en local, utilisez un serveur HTTP (pas juste double-clic sur index.html)

### La carte est vide
- Ouvrez la console du navigateur (F12) pour voir les erreurs
- Vérifiez que `railway_data.json` se charge bien (Network tab)
- Le fichier JSON est volumineux, donnez-lui quelques secondes

### Le fichier JSON est trop lourd
GitHub accepte jusqu'à 100 MB par fichier, donc 15 MB est OK. Si vous voulez réduire :
- Modifiez le script Python pour simplifier davantage les coordonnées
- Ou utilisez un service comme GitHub LFS (Large File Storage)

---

## 📞 Support

Si vous rencontrez des problèmes :

1. **Vérifiez d'abord** :
   - Tous les fichiers sont dans le bon dossier
   - GitHub Pages est activé (Settings → Pages)
   - L'URL est correcte

2. **Console du navigateur** (F12) :
   - Regardez les erreurs éventuelles
   - Vérifiez que railway_data.json se charge

3. **GitHub Issues** :
   - Créez une issue dans votre repository pour documenter le problème

---

## 🚀 Prochaines étapes

Une fois votre carte en ligne :

1. **Partagez l'URL** avec vos collègues
2. **Personnalisez** les couleurs et le style selon vos préférences
3. **Ajoutez des fonctionnalités** (filtres, recherche, etc.)
4. **Mettez à jour les données** quand de nouvelles attributions sont faites

---

## ✨ Checklist finale

- [ ] Repository GitHub créé
- [ ] Les 4 fichiers sont uploadés
- [ ] GitHub Pages est activé
- [ ] Le site est accessible via l'URL GitHub Pages
- [ ] La carte s'affiche correctement
- [ ] Les popups fonctionnent au clic sur les lignes
- [ ] La légende affiche les bons compteurs

---

**Bravo ! Votre carte interactive est en ligne ! 🎉**

URL finale : `https://VOTRE-USERNAME.github.io/railway-competition-map/`
