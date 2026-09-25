# Modèles KARD°ASH

Catalogue public de modèles de Kards. JSON uniquement : aucun script, aucune donnée utilisateur.

Dans KARD°ASH : **K+ → Modèles à télécharger → Aperçu → Ajouter à mes modèles**. Les modèles installés restent disponibles hors connexion. Une mise à jour d’un modèle ne modifie jamais les Kards déjà créées.

- [Recette de cuisine](models/recette.json) — Photo, ingrédients, quantités et étapes.
- [Courses](models/courses.json) — Un article et sa quantité par ligne ; cases à cocher dans la Kard.
- [Tâche / rappel](models/tache.json) — Organiser une tâche et son échéance. La répétition est une indication, sans alarme automatique.
- [Rendez-vous](models/rendez-vous.json) — Date, heure, adresse, contact et documents.
- [Colis](models/colis.json) — Transporteur et informations de suivi.
- [Entretien](models/entretien.json) — Historique et prochaine intervention d’un objet ou véhicule.
- [Prêt / emprunt d’objet](models/pret-objet.json) — Objet, personne, retour et rappel facultatif à 9 h.
- [Prêt / emprunt d’argent](models/pret-argent.json) — Montant, taux annuel et échéances ; aucun calcul financier automatique.
- [Note](models/note.json) — Texte rapide, photos et fichiers.
- [Mesures / tailles](models/mesures.json) — Vêtements, chaussures ou dimensions d’un meuble.
- [État des lieux](models/etat-des-lieux.json) — Pièce, état, observations et photos.
- [Entretien piscine](models/piscine.json) — Relevés et interventions ; aucune recommandation de dosage automatique.
- [Inventaire du matériel](models/inventaire.json) — Référence, quantité, emplacement et photo.

## Importer / proposer un modèle

Téléchargez un JSON individuel puis utilisez **Mes modèles → Importer**. Pour contribuer, ajoutez un fichier dans `models/` et mettez à jour `catalog.json` dans une pull request. N’incluez aucune information personnelle, photo, pièce jointe, clé ou lien privé.

## Format version 1

Un modèle contient `format: kardash-template`, `schemaVersion: 1`, un `id` stable, une `version` entière, `name`, `description`, une `icon` du jeu embarqué, une `color` hexadécimale, `baseType` (custom, recipe, shopping, loan), et `fields`.

Chaque champ contient `id`, `label`, `type`, `default` et éventuellement `key` pour une fonction de la Kard de base. Types : text, number, date, time, datetime-local, photo, file, scan, email, phone, web, postaladdress, exactlocation, password, iban, bic, last4, month, codevalue, codeformat, security, member, chip. Aucun HTML, script ni image distante n’est interprété.

L’export de la structure depuis l’application efface les valeurs, fichiers, photos, coordonnées, icônes personnelles et résultats de contrôle. Il demande un nom de modèle distinct du titre de la Kard. Vérifiez aussi que les libellés de champs ne contiennent pas de données personnelles avant une publication.

Les champs « échéance » et « répétition » des modèles génériques sont des données : ils ne programment pas automatiquement une notification. Le prêt d’objet utilise le rappel facultatif intégré à sa catégorie. Aucune synchronisation de Kards via GitHub.

## Validation

Avec Node.js 22 ou supérieur, exécutez `node validate.cjs` à la racine du dépôt. GitHub vérifie également chaque contribution. Le catalogue utilisé par l’application est [catalog.json](https://raw.githubusercontent.com/noonelche-cyber/kardash-templates/main/catalog.json).
