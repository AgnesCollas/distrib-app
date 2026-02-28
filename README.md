# 🗺️ Distribution CIDEX - Bernin

Application web collaborative pour gérer la distribution de flyers dans les CIDEX (boîtes aux lettres groupées) de Bernin.

## 🚀 Démarrage rapide

1. Ouvrez `index.html` dans votre navigateur
2. Cliquez sur "Lancer l'Application"
3. Entrez un code de session (ex: "bernin2024") et votre prénom
4. Partagez le code avec votre équipe pour collaborer
5. Commencez la distribution !

## 📱 Fonctionnalités

### Synchronisation temps réel 🔄
- ☁️ Sauvegarde automatique dans le cloud (Firebase)
- 👥 Voir les membres de l'équipe connectés
- 🔐 Code de session partagé pour coordonner l'équipe
- 📊 Statistiques de progression en temps réel
- 🔄 Synchronisation des CIDEX (ajout, déplacement, suppression)

### Gestion des CIDEX 📍
- 📍 62 CIDEX géolocalisés sur la carte
- ➕ Ajout de CIDEX manquants
- 🔄 Déplacement de CIDEX
- 🗑️ Suppression de CIDEX
- 🎨 Interface professionnelle et intuitive

**Utilisation :**
1. Cliquez sur un marqueur bleu pour le marquer comme "distribué" (devient vert)
2. Cliquez à nouveau pour annuler
3. Vos données sont synchronisées automatiquement avec l'équipe

## 🎯 Menu d'actions

Cliquez sur le bouton ☰ en bas à droite pour accéder au menu :

- **➕ Ajouter un CIDEX** : Ajouter un CIDEX manquant
  - Remplissez le nom et l'adresse
  - Cliquez sur la carte pour le positionner
  - Cliquez sur "Annuler" pour abandonner

- **📍 Déplacer un CIDEX** : Corriger la position d'un CIDEX
  - Cliquez sur un marqueur pour le sélectionner (devient orange)
  - Cliquez sur la carte pour le déplacer
  - Déplacez plusieurs CIDEX si besoin
  - Cliquez sur "Annuler" pour restaurer les positions d'origine
  - Cliquez sur "💾 Sauvegarder" pour enregistrer les changements

- **🗑️ Supprimer un CIDEX** : Supprimer un CIDEX erroné
  - Cliquez sur un marqueur pour le supprimer
  - Confirmation demandée avant suppression
  - Cliquez sur "Annuler" pour quitter le mode suppression

- **🔄 Tout réinitialiser** : Remettre tous les états à "à faire"
  - Confirmation demandée
  - Ne supprime pas les CIDEX, seulement les états de distribution

## 🔧 Configuration Firebase

Firebase est **gratuit** pour votre usage (Plan Spark) :
- 1 GB de stockage
- 10 GB de transfert/mois
- 100 connexions simultanées

**Note :** La configuration Firebase est déjà intégrée dans l'application. Vous n'avez rien à configurer !

### Ce qui est synchronisé :
- ✅ États de distribution (fait/à faire)
- ✅ Liste des CIDEX (ajout/suppression)
- ✅ Positions des CIDEX (déplacements)
- ✅ Utilisateurs actifs en temps réel

## 📊 Fonctionnalités

### Carte interactive
- Marqueurs bleus : CIDEX à distribuer
- Marqueurs verts : CIDEX distribués
- Marqueurs orange : CIDEX sélectionné (mode déplacement)
- Zoom et navigation sur la carte

### Panneau de statistiques (toujours visible)
- Total de CIDEX
- Nombre distribués
- Nombre restants
- Barre de progression avec pourcentage
- Liste des membres actifs

### Menu d'actions (bouton ☰)
- ➕ Ajouter un CIDEX manquant
- 📍 Déplacer un CIDEX (avec annulation possible)
- 🗑️ Supprimer un CIDEX (avec confirmation)
- 🔄 Réinitialiser la distribution (avec confirmation)

### Bandeau d'édition
Apparaît lors des actions d'ajout, déplacement ou suppression :
- Affiche le mode actif
- Bouton "Annuler" pour abandonner l'action
- Bouton "💾 Sauvegarder" pour valider (mode déplacement uniquement)

## 🎨 Design

Interface moderne avec :
- Couleurs professionnelles : bleu (#4a90e2), gris (#6b7c93), blanc nacré (#f8f9fb)
- Panneau de stats fixe à droite (280px)
- Menu burger en bas à droite
- Responsive mobile (stats en bas sur petit écran)

## 📁 Structure des fichiers

```
cidex-bernin-map/
├── index.html              # Page d'accueil
├── app.html                # Application collaborative
├── README.md               # Ce fichier
├── GUIDE-UTILISATEUR.md    # Guide utilisateur détaillé
├── FIREBASE-SETUP.md       # Guide détaillé Firebase (référence)
├── DEPLOIEMENT.md          # Guide de déploiement
└── cidex-final.json        # Données des 62 CIDEX
```

**Fichiers obsolètes (peuvent être supprimés) :**
- `app-backup.html`
- `app-multi.html`
- `app-multi-backup.html`
- `app-multi-broken.html`
- `firebase-multi.js`

## 🌐 Déploiement

### GitHub Pages (recommandé)
1. Créer un dépôt GitHub
2. Pousser les fichiers
3. Activer GitHub Pages dans les paramètres
4. Accéder via `https://votre-username.github.io/cidex-bernin-map/`

Voir `DEPLOIEMENT.md` pour d'autres options (Netlify, Vercel, etc.)

## 💾 Données

- Sauvegarde dans Firebase Realtime Database
- Accessible depuis n'importe quel appareil avec le code de session
- Données persistantes dans le cloud
- Synchronisation en temps réel entre tous les membres de l'équipe
- Peut être utilisé seul (un seul distributeur) ou en équipe

## 🔒 Sécurité

- Règles Firebase à configurer pour la production
- Code de session = mot de passe partagé
- Possibilité d'ajouter une authentification

## 🐛 Dépannage

### La carte ne s'affiche pas
- Vérifier la connexion internet
- Vérifier la console du navigateur (F12)

### L'application ne synchronise pas
- Vérifier la configuration Firebase
- Vérifier que tous utilisent le même code de session
- Vérifier les règles Firebase

### Les données sont perdues
- Vérifier la connexion Firebase
- Vérifier que vous utilisez le bon code de session

## 📝 Licence

Projet open source pour la commune de Bernin.

## 👥 Contribution

Pour toute amélioration ou bug, créer une issue sur le dépôt GitHub.

---

Fait avec ❤️ pour Bernin
