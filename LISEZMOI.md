# Rapport – mise en place

Application web installable (Android, iPhone/iPad, PC) pour réaliser un rapport avec photos annotées et commentaires, exportable en **Word** et en **PDF**. Elle fonctionne hors ligne une fois installée.

## 1. Fichiers à publier
À la racine du dépôt GitHub (le dépôt doit être public) :

- `index.html`
- `sw.js`
- `manifest.webmanifest`
- `icon-192.png`, `icon-512.png`, `icon-maskable-512.png`, `apple-touch-icon.png`, `favicon.png`
- `LISEZMOI.md` (facultatif)

Puis : *Settings → Pages* → Source : branche `main`, dossier `/ (root)`. L’adresse obtenue est en **https**, indispensable pour l’installation et l’appareil photo.

Les anciens fichiers de « Visite sécurité » (`memo.json`, `zones.json`) ne servent plus et peuvent être supprimés. Aucune connexion GitHub, Supabase ou intranet n’est nécessaire.

## 2. Installer l’application
- **Android (Chrome)** : bouton « 📲 Installer l’application » en bas de page, ou menu ⋮ → *Installer l’application*.
- **iPhone / iPad (Safari)** : bouton Partager → *Sur l’écran d’accueil*.
- **PC (Chrome ou Edge)** : icône d’installation à droite de la barre d’adresse.

## 3. Utilisation
1. Renseigner le **nom**, la **date** (jour du jour par défaut), le **titre général** et, si besoin, le **commentaire général** (optionnel, dictée vocale 🎙️ possible).
2. Sous le titre **A**, toucher « 📷 Photo A1 » (ou « 🖼️ Galerie »). Sur la photo : **croix rouge** ✚ ou **rond rouge** ◯ (annuler ↶, tout effacer 🗑, zoom 🔍), puis un **commentaire** et « ✅ Valider la photo ».
3. Ajouter autant de photos que voulu sous le même titre : **A1, A2, A3…**
4. « ＋ Ajouter un titre B » crée la série suivante (photos **B1, B2…**), puis **C**, etc.
5. ✏️ rouvre une photo avec ses croix, ronds et son commentaire, pour les modifier. 🗑 supprime une photo (la numérotation se met à jour). 🗑 dans l’en-tête violet supprime un titre et ses photos.
6. **Sauvegarde automatique** sur l’appareil, en continu : on peut fermer l’application et reprendre plus tard (même appareil, même navigateur).
7. **Exports** : « 📝 Exporter en Word » (.docx mis en page : bannière, titre, auteur et date, commentaire général, puis chaque titre suivi de ses photos et commentaires) et « 📄 Exporter en PDF ». « 🆕 Nouveau rapport » efface le rapport en cours après confirmation.

Sur iPhone, l’export ouvre la feuille de partage pour enregistrer ou envoyer le fichier.

## 4. Mises à jour et version
- Le service worker renouvelle l’application dès qu’Internet est disponible ; un message propose alors de recharger. Le bouton « 🔄 Vérifier la mise à jour » force la vérification.
- Pour publier une nouvelle version, modifier le numéro dans `sw.js` (`const VERSION='v1.0.0'`, ainsi que la première ligne de commentaire) et dans `index.html` (`const APP_VERSION='v1.0.0';const APP_DATE='28/10/2026';`). Si vous gardez votre workflow GitHub Actions et `bump-version.js`, ils continuent de repérer ces mêmes lignes.

## 5. Ce qui a changé par rapport à « Visite sécurité »
- Titre de l’application et de la bannière : **Rapport**. Nouvelle icône (bloc-notes avec photo et coche).
- Un seul nom, la date ; ajout du titre général et du commentaire général optionnel (l’heure, le 2ᵉ nom et la photo de comparaison sont retirés).
- Photos organisées par titres lettrés (A, B, C…) et numérotées (A1, A2, B1…). Les champs Action, Zone et Gravité sont retirés.
- Retirés : aide-mémoire, emplacements/zones, paramètres, sauvegarde Supabase, enregistrement intranet, export Excel, export « base complète », comptage « À corriger / Corrigé / Bonne pratique ».
- Ajouté : export Word. L’export PDF est conservé, avec la nouvelle structure.
- La sauvegarde automatique sur le téléphone est conservée (nouvelle base locale « rapportDB » : les anciennes visites ne sont pas reprises).

## 6. Bibliothèques externes (mises en cache pour le hors ligne)
`jsPDF 2.5.2` (PDF) et `docx 8.5.0` (Word), chargées depuis cdn.jsdelivr.net, et la police Inter (Google Fonts). La première ouverture doit se faire avec Internet pour qu’elles soient mises en cache.
