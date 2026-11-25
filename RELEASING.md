# Publication des mises à jour Android

Le dépôt public distribue uniquement les versions approuvées de Bunker Wars. Le code source reste dans le dépôt privé.

## Convention de version

- `0.0.1` : première version bêta.
- Incrémenter le dernier chiffre pour une mise à jour ordinaire (`0.0.2`).
- Incrémenter le chiffre du milieu pour une mise à jour majeure de la bêta (`0.1.0`).
- Passer le premier chiffre à `1` pour la sortie officielle sur Google Play (`1.0.0`).
- `version_code` doit augmenter strictement à chaque APK publié, même si le nom de version suit une autre convention.

## Procédure de publication manuelle

1. Tester l'APK Android signé avec la même clé que la version installée chez les testeurs.
2. Créer une GitHub Release et y joindre l'APK. Ne jamais publier de clé de signature.
3. Calculer le SHA-256 de l'APK et copier l'URL HTTPS directe de l'asset GitHub Release.
4. Mettre à jour `version.json` : `version`, `version_code`, `apk_url`, `sha256`, `release_notes`, `published_at` et `published: true` **seulement après validation de la Release**.
5. Vérifier le téléchargement et l'installation sur un téléphone de test avant d'annoncer la version.

## Fonctionnement Android

Au lancement, le jeu pourra consulter `version.json` et proposer le téléchargement d'un APK uniquement si `published` vaut `true` et que sa version est plus récente. Android exige une confirmation utilisateur pour installer une mise à jour hors Google Play : l'installation silencieuse n'est pas disponible pour une application ordinaire. L'APK doit conserver le même identifiant de package et être signé avec la même clé. Une fois distribué sur Google Play, utiliser le mécanisme de mise à jour de Google Play plutôt que l'installation directe d'APK.

Le manifeste initial `0.0.1` est volontairement **non publié** : aucun APK n'est encore annoncé comme disponible.
