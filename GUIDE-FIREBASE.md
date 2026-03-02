# 🔥 Guide Firebase - Distribution CIDEX

## 📍 Accéder à votre base de données

### 1. Se connecter à Firebase
1. Allez sur https://console.firebase.google.com/
2. Connectez-vous avec votre compte Gmail
3. Vous verrez la liste de vos projets

### 2. Sélectionner votre projet
1. Cliquez sur le projet **"distriapp-12bd3"**
2. Vous arrivez sur la page d'accueil du projet

### 3. Accéder à la base de données
1. Dans le menu de gauche, cliquez sur **"Realtime Database"**
2. Vous verrez votre base de données avec toutes les sessions

---

## 📊 Structure de la base de données

Votre base de données est organisée comme ceci :

```
distriapp-12bd3-default-rtdb/
└── sessions/
    ├── cidex-clean-admin/          ← Votre session de nettoyage
    │   ├── cidexList/               ← Liste des 149 CIDEX
    │   ├── etats/                   ← États (fait/à faire)
    │   ├── users/                   ← Utilisateurs actifs
    │   └── createdAt                ← Date de création
    │
    ├── bernin2024/                  ← Autre session
    │   ├── cidexList/
    │   ├── etats/
    │   └── users/
    │
    └── test-mars/                   ← Autre session
        └── ...
```

---

## 🔍 Voir vos données

### Voir toutes les sessions
1. Dans "Realtime Database", vous voyez l'arbre `sessions/`
2. Cliquez sur la flèche `▶` à côté de `sessions` pour déplier
3. Vous verrez toutes vos sessions (ex: cidex-clean-admin, bernin2024, etc.)

### Voir les CIDEX d'une session
1. Dépliez la session (ex: `cidex-clean-admin`)
2. Cliquez sur `cidexList`
3. Vous verrez tous les CIDEX avec leurs coordonnées

### Voir les états de distribution
1. Dépliez la session
2. Cliquez sur `etats`
3. Vous verrez quels CIDEX sont marqués comme "fait"

### Voir les utilisateurs actifs
1. Dépliez la session
2. Cliquez sur `users`
3. Vous verrez les utilisateurs connectés avec leur dernière activité

---

## ✏️ Modifier les données

### Supprimer une session complète
1. Cliquez sur le nom de la session (ex: `bernin2024`)
2. Cliquez sur l'icône **🗑️** (poubelle) ou clic droit → **Delete**
3. Confirmez la suppression

**⚠️ Attention :** Cela supprime toutes les données de cette session (CIDEX, états, utilisateurs)

### Supprimer uniquement les états
1. Dépliez la session
2. Cliquez sur `etats`
3. Cliquez sur l'icône **🗑️** ou clic droit → **Delete**
4. Les CIDEX restent, mais tous redeviennent "à faire"

### Modifier un CIDEX
1. Dépliez `cidexList`
2. Cliquez sur un CIDEX
3. Vous pouvez modifier :
   - `name` : le nom du CIDEX
   - `address` : l'adresse
   - `lat` : la latitude
   - `lon` : la longitude
4. Cliquez sur l'icône **✏️** pour éditer
5. Modifiez la valeur et appuyez sur **Entrée**

---

## 📥 Exporter les données

### Exporter toute la base
1. Cliquez sur l'icône **⋮** (trois points) en haut à droite
2. Sélectionnez **"Export JSON"**
3. Un fichier JSON sera téléchargé

### Exporter une session spécifique
1. Cliquez sur la session (ex: `cidex-clean-admin`)
2. Cliquez sur l'icône **⋮** à droite
3. Sélectionnez **"Export JSON"**

---

## 🔐 Gérer les règles de sécurité

### Voir les règles actuelles
1. Dans "Realtime Database", cliquez sur l'onglet **"Rules"** (en haut)
2. Vous verrez les règles de sécurité actuelles

### Règles actuelles (développement)
```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
```

**⚠️ Attention :** Ces règles permettent à tout le monde de lire et écrire. C'est OK pour le développement, mais pas pour la production.

### Règles recommandées pour la production
```json
{
  "rules": {
    "sessions": {
      "$sessionId": {
        ".read": true,
        ".write": true
      }
    }
  }
}
```

Pour modifier les règles :
1. Cliquez sur **"Rules"**
2. Modifiez le JSON
3. Cliquez sur **"Publish"**

---

## 📊 Surveiller l'utilisation

### Voir les statistiques
1. Dans "Realtime Database", cliquez sur l'onglet **"Usage"**
2. Vous verrez :
   - **Storage** : Espace utilisé (limite gratuite : 1 GB)
   - **Downloads** : Données téléchargées (limite gratuite : 10 GB/mois)
   - **Connections** : Connexions simultanées (limite gratuite : 100)

### Limites du plan gratuit (Spark)
- ✅ 1 GB de stockage
- ✅ 10 GB de transfert/mois
- ✅ 100 connexions simultanées

**Votre usage actuel :**
- Avec 149 CIDEX et quelques sessions, vous utilisez probablement moins de 1 MB
- Largement en dessous des limites gratuites ! 🎉

---

## 🆘 Problèmes fréquents

### Je ne vois pas mes données
1. Vérifiez que vous êtes connecté avec le bon compte Gmail
2. Vérifiez que vous avez sélectionné le bon projet ("distriapp-12bd3")
3. Cliquez sur "Realtime Database" dans le menu de gauche

### Les données ne se synchronisent pas
1. Vérifiez les règles de sécurité (onglet "Rules")
2. Vérifiez que l'application utilise le bon code de session
3. Regardez la console du navigateur (F12) pour voir les erreurs

### J'ai supprimé des données par erreur
- Firebase ne garde pas d'historique automatique
- Il faut restaurer depuis un export JSON si vous en avez fait un
- **Conseil :** Faites des exports réguliers !

---

## 💡 Bonnes pratiques

### 1. Faire des exports réguliers
- Exportez votre base avant de faire des modifications importantes
- Gardez une copie de sauvegarde

### 2. Nettoyer les anciennes sessions
- Supprimez les sessions de test qui ne servent plus
- Gardez uniquement les sessions actives

### 3. Surveiller l'utilisation
- Vérifiez régulièrement l'onglet "Usage"
- Vous êtes alerté si vous approchez des limites

### 4. Utiliser des codes de session clairs
- ✅ Bon : "bernin-mars-2026", "distribution-printemps"
- ❌ Mauvais : "test123", "aaa"

---

## 🔗 Liens utiles

- Console Firebase : https://console.firebase.google.com/
- Documentation Firebase : https://firebase.google.com/docs/database
- Votre projet : https://console.firebase.google.com/project/distriapp-12bd3

---

**Besoin d'aide ?** Consultez la documentation Firebase ou demandez de l'aide ! 😊
