# Rapport – mise en place

Application web installable (Android, iPhone/iPad, PC) pour réaliser un rapport avec photos annotées et commentaires, exportable en **Word** et en **PDF**. Elle fonctionne hors ligne une fois installée. Version **v1.4.0**.

## 1. Fichiers à publier
À la racine du dépôt GitHub (le dépôt doit être public) :

- `index.html`
- `sw.js`
- `manifest.webmanifest`
- `icon-192.png`, `icon-512.png`, `icon-maskable-512.png`, `apple-touch-icon.png`, `favicon.png`
- `LISEZMOI.md` (facultatif)

Puis : *Settings → Pages* → Source : branche `main`, dossier `/ (root)`. L’adresse obtenue est en **https**, indispensable pour l’installation et l’appareil photo.

Aucune connexion GitHub, Supabase ou intranet n’est nécessaire.

## 2. Installer l’application
- **Android (Chrome)** : bouton « Installer l’application » en bas de page, ou menu ⋮ → *Installer l’application*.
- **iPhone / iPad (Safari)** : bouton Partager → *Sur l’écran d’accueil*.
- **PC (Chrome ou Edge)** : icône d’installation à droite de la barre d’adresse.

## 3. Utilisation
1. Renseigner le **nom**, la **date**, le **titre général** et, si besoin, le **commentaire général** (optionnel, dictée vocale possible).
2. Sous le titre **A**, toucher « Photo A1 » (ou « Galerie »). Dans l’appareil photo : curseur pour **éclaircir** la photo, bouton **Flash** (lampe) et **mise au point manuelle** en touchant l’image, si le téléphone et le navigateur le permettent (Android/Chrome ; non disponible sur iPhone/Safari). Annoter, commenter, puis « Valider la photo ». Les photos d’un même titre sont numérotées **A1, A2…** ; « Ajouter un titre B » crée la série suivante (B1, B2…), puis C, etc.
3. **Replier / déplier** les photos d’un titre avec la flèche à gauche de l’en-tête violet.
4. **Réordonner** : glisser-déposer la poignée (6 points) à gauche d’une photo, dans son titre ou vers un autre titre. La numérotation suit.
5. **Annotations** : croix, flèche, rond, rectangle ; 4 couleurs (rouge, jaune, bleu, vert) ; annuler, tout effacer, rotation de 90°, zoom. Le bouton « Annotations » réduit la barre d’outils.
6. **Temps (optionnel)** : heures (hh) et minutes (min) par photo. Somme affichée par titre, et temps total à côté du titre général. « Masquer tous les temps » les retire de l’écran, de l’éditeur photo, du chronomètre et des exports.
7. **Chronomètre** : bouton « Chrono » en haut. Petit chrono flottant, fixe à l’écran, déplaçable par sa poignée. Départ / Arrêt ; après l’arrêt, le bouton **0** remet à zéro, et Départ reprend où le chrono s’était arrêté. Dans l’éditeur de photo, « Chrono » copie son temps dans hh/min ; la saisie manuelle reste possible.
8. **Sauvegarde automatique** sur l’appareil, en continu. Photos compressées à 80 % (JPEG).
9. **Nom du fichier** : menu au choix, mémorisé. Toujours « Rapport » suivi de : titre + date, nom + date, nom + titre + date, titre + date + numéro, ou nom + date + numéro. Date au format aammjj (ex. `Rapport_Visite-atelier_261028.pdf`). Le numéro s’incrémente à chaque nouveau rapport et reste modifiable.
10. **Exports** Word et PDF : en-tête Onoré / Rapport sur chaque page, titre, auteur, date, temps total, commentaire général, puis chaque titre avec ses photos (même taille, 3 par ligne, au moins 6 par page) et leurs commentaires. Un titre n’est jamais seul en bas de page.

« Nouveau rapport » efface le rapport en cours après confirmation. Sur iPhone, l’export ouvre la feuille de partage.

## 4. Mises à jour et version
- Le service worker renouvelle l’application dès qu’Internet est disponible ; un message propose de recharger. « Vérifier la mise à jour » force la vérification.
- Pour publier une nouvelle version, modifier le numéro dans `sw.js` (`const VERSION='v1.4.0'` et la première ligne de commentaire) et dans `index.html` (`const APP_VERSION='v1.4.0';const APP_DATE='28/10/2026';`).

## 5. Bibliothèques externes (mises en cache pour le hors ligne)
`jsPDF 2.5.2` (PDF), chargée depuis cdn.jsdelivr.net, et la police Inter (Google Fonts). La première ouverture doit se faire avec Internet pour qu’elles soient mises en cache. L’export Word est généré directement par l’application, sans bibliothèque.
