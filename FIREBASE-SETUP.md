# Configuration Firebase pour le mode Multi-utilisateurs

## Étapes pour activer Firebase

### 1. Créer un projet Firebase
1. Aller sur https://console.firebase.google.com/
2. Cliquer sur "Ajouter un projet"
3. Nommer le projet (ex: "cidex-bernin")
4. Désactiver Google Analytics (optionnel)
5. Créer le projet

### 2. Activer Realtime Database
1. Dans le menu de gauche, cliquer sur "Realtime Database"
2. Cliquer sur "Créer une base de données"
3. Choisir un emplacement (ex: europe-west1)
4. Commencer en "mode test" (règles ouvertes pour 30 jours)
5. Cliquer sur "Activer"

### 3. Configurer les règles de sécurité
Dans l'onglet "Règles", remplacer par:
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

### 4. Récupérer la configuration
1. Cliquer sur l'icône "⚙️" > "Paramètres du projet"
2. Descendre jusqu'à "Vos applications"
3. Cliquer sur l'icône "</>" (Web)
4. Enregistrer l'application (ex: "cidex-app")
5. Copier l'objet `firebaseConfig`

### 5. Ajouter la configuration dans app-unified.html
Remplacer dans le fichier la section:
```javascript
// TODO: Remplacer par votre configuration Firebase
const firebaseConfig = {
  apiKey: "VOTRE_API_KEY",
  authDomain: "VOTRE_PROJECT_ID.firebaseapp.com",
  databaseURL: "https://VOTRE_PROJECT_ID.firebaseio.com",
  projectId: "VOTRE_PROJECT_ID",
  storageBucket: "VOTRE_PROJECT_ID.appspot.com",
  messagingSenderId: "VOTRE_SENDER_ID",
  appId: "VOTRE_APP_ID"
};
```

## Structure des données dans Firebase

```
sessions/
  └── [sessionCode]/
      ├── etats/
      │   ├── cidex-1: "fait"
      │   ├── cidex-2: "a_faire"
      │   └── ...
      ├── positions/
      │   ├── cidex-1: {lat: 45.xxx, lon: 5.xxx}
      │   └── ...
      ├── cidexList/
      │   └── [array of CIDEX]
      └── users/
          ├── user1: {name: "Alice", lastSeen: timestamp}
          └── user2: {name: "Bob", lastSeen: timestamp}
```

## Sécurité

Pour la production, modifier les règles Firebase pour:
- Limiter l'accès aux sessions avec un mot de passe
- Ajouter une expiration automatique des sessions
- Limiter le nombre de modifications par utilisateur

Exemple de règles sécurisées:
```json
{
  "rules": {
    "sessions": {
      "$sessionId": {
        ".read": "auth != null",
        ".write": "auth != null",
        ".validate": "newData.hasChildren(['etats', 'users'])"
      }
    }
  }
}
```
