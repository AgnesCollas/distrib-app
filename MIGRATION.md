# 🔄 Migration vers l'application unifiée

## Changements

Nous avons fusionné les deux versions (Solo et Multi) en une seule application pour simplifier la maintenance et l'utilisation.

## Nouvelle structure

### Avant
- `app.html` → Mode Solo uniquement
- `app-multi.html` → Mode Multi uniquement
- Deux fichiers à maintenir séparément

### Maintenant
- `app.html` → Application unifiée (Solo + Multi)
- Choix du mode au démarrage
- Un seul fichier à maintenir

## Avantages

1. **Code unique** : Plus facile à maintenir et à mettre à jour
2. **Flexibilité** : Changez de mode sans changer de fichier
3. **Simplicité** : Une seule URL à partager
4. **Cohérence** : Même interface pour les deux modes

## Comment utiliser

1. Ouvrez `app.html` dans votre navigateur
2. Un modal s'affiche au démarrage
3. Choisissez votre mode :
   - **Solo** : Cliquez sur "Mode Solo" → Commencez immédiatement
   - **Multi** : Cliquez sur "Mode Multi" → Entrez code de session et prénom

## Compatibilité des données

### Mode Solo
- Les données existantes dans `localStorage` sont conservées
- Aucune migration nécessaire

### Mode Multi
- Les sessions Firebase existantes continuent de fonctionner
- Utilisez le même code de session qu'avant

## Fichiers obsolètes

Ces fichiers peuvent être supprimés (mais gardez-les en backup si vous préférez) :
- `app-backup.html`
- `app-multi.html`
- `app-multi-backup.html`
- `app-multi-broken.html`
- `firebase-multi.js` (le code Firebase est maintenant intégré dans app.html)

## Test

Pour tester l'application :

1. **Test Mode Solo** :
   - Ouvrez `app.html`
   - Sélectionnez "Mode Solo"
   - Cliquez sur quelques marqueurs
   - Rechargez la page → Les données doivent être conservées

2. **Test Mode Multi** :
   - Ouvrez `app.html` dans deux onglets différents
   - Sélectionnez "Mode Multi" dans les deux
   - Utilisez le même code de session (ex: "test123")
   - Entrez des prénoms différents
   - Cliquez sur un marqueur dans un onglet
   - Vérifiez que l'autre onglet se met à jour automatiquement

## Support

Si vous rencontrez des problèmes :
1. Vérifiez que vous utilisez un navigateur récent
2. Vérifiez votre connexion internet (pour le mode Multi)
3. Effacez le cache du navigateur si nécessaire
4. Consultez la console du navigateur (F12) pour les erreurs

## Retour en arrière

Si vous souhaitez revenir à l'ancienne version :
1. Les fichiers `app-backup.html` et `app-multi-backup.html` sont toujours disponibles
2. Renommez-les si nécessaire
3. Mettez à jour `index.html` pour pointer vers ces fichiers

---

**Date de migration** : Février 2026
**Version** : 2.0 (Application unifiée)
