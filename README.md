# Modèles KARD°ASH

Catalogue public de modèles de Kards. JSON uniquement : aucun script, aucune donnée utilisateur.

Le catalogue privilégie les **usages professionnels** : suivi de clients, interventions, chantiers, documents et historique. Les modèles personnels restent disponibles.

Sur Windows, **Configuration → Modèles à télécharger** ouvre ce dépôt dans le navigateur. Téléchargez un JSON individuel (lien « Télécharger » ci-dessous, puis enregistrer le fichier) et importez-le via **Mes modèles → Importer**. Dans les versions proposant le catalogue intégré : aperçu, puis **Ajouter à mes modèles**. Les modèles installés restent utilisables hors connexion ; leurs mises à jour ne modifient pas les Kards existantes.

## Modèles professionnels

Trois ensembles, chacun avec une Kard principale et un modèle de suivi :

| Usage | Kard principale | Historique / sous-Kard |
|---|---|---|
| Commercial | [Client / prospect](models/client-prospect.json) · [Télécharger](https://raw.githubusercontent.com/noonelche-cyber/kardash-templates/main/models/client-prospect.json) | [Visite commerciale](models/visite-commerciale.json) · [Télécharger](https://raw.githubusercontent.com/noonelche-cyber/kardash-templates/main/models/visite-commerciale.json) |
| Technique | [Équipement client](models/equipement-client.json) · [Télécharger](https://raw.githubusercontent.com/noonelche-cyber/kardash-templates/main/models/equipement-client.json) | [Intervention technique](models/intervention-technique.json) · [Télécharger](https://raw.githubusercontent.com/noonelche-cyber/kardash-templates/main/models/intervention-technique.json) |
| Chantier | [Dossier chantier](models/chantier.json) · [Télécharger](https://raw.githubusercontent.com/noonelche-cyber/kardash-templates/main/models/chantier.json) | [Suivi de chantier](models/suivi-chantier.json) · [Télécharger](https://raw.githubusercontent.com/noonelche-cyber/kardash-templates/main/models/suivi-chantier.json) |

### Organiser l’historique

1. Importez les deux modèles de l’ensemble choisi.
2. Créez la Kard principale, puis une Kard de suivi à chaque visite, intervention ou étape.
3. Dans les versions qui prennent en charge les sous-Kards (Windows à partir du build 68), ouvrez la fiche principale et utilisez **Sous-Kards → rattacher une Kard existante** pour ajouter le suivi.

Les JSON décrivent les champs d’une seule Kard : ils ne créent pas automatiquement une hiérarchie. Le rattachement conserve les Kards existantes. La prochaine relance ou échéance peut être renseignée sur la Kard principale pour être visible rapidement ; elle n’est pas recopiée automatiquement depuis les sous-Kards. Les dates de ces modèles ne déclenchent pas d’alarme automatique. Les statuts et natures proposés dans les libellés sont des textes libres, pas des menus déroulants. L’identifiant fiscal est un champ libre ; ce modèle n’active pas un contrôle VIES.

## Autres modèles

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

## Proposer depuis KARD°ASH

Dans l’aperçu d’un modèle ou lors de l’export de la structure d’une Kard, choisissez **Proposer au catalogue GitHub**. Vérifiez les libellés publics et confirmez, puis soumettez la proposition préremplie sur GitHub avec votre compte. Les valeurs et pièces jointes sont retirées. Pour un grand modèle, le bouton Copier permet de coller le JSON dans la proposition.

Les propositions sont des issues examinées par les mainteneurs, qui peuvent ensuite ouvrir une pull request ajoutant le modèle et actualisant le catalogue. Aucune proposition n’est intégrée automatiquement.
