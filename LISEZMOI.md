# Rapport – mise en place

Application web installable (Android, iPhone/iPad, PC) pour réaliser un rapport, une procédure ou un inventaire avec photos annotées et commentaires, exportable en **Excel, Word et PDF**. Elle fonctionne hors ligne une fois installée. Version **v1.6.1**.

## 1. Fichiers à publier
À la racine du dépôt GitHub (le dépôt doit être public) :

- `index.html`
- `sw.js`
- `manifest.webmanifest`
- `icon-192.png`, `icon-512.png`, `icon-maskable-512.png`, `apple-touch-icon.png`, `favicon.png`
- `LISEZMOI.md` (facultatif)

Puis : *Settings → Pages* → Source : branche `main`, dossier `/ (root)`. L’adresse obtenue est en **https**, indispensable pour l’installation et l’appareil photo. Aucune connexion GitHub, Supabase ou intranet n’est nécessaire.

## 2. Installer l’application
- **Android (Chrome)** : bouton « Installer l’application » en bas de page, ou menu ⋮ → *Installer l’application*.
- **iPhone / iPad (Safari)** : bouton Partager → *Sur l’écran d’accueil*.
- **PC (Chrome ou Edge)** : icône d’installation à droite de la barre d’adresse.

## 3. Utilisation
1. **Nom**, **date**, **titre général** et **commentaire général** (optionnel, dictée vocale possible).
2. Dans chaque **section** (A, B, C…), « Photo A1 » ou « Galerie ». Appareil photo : curseur pour éclaircir, **Flash** et **mise au point** au toucher quand le téléphone le permet (Android/Chrome ; pas sur iPhone/Safari). Annotations : croix, flèche, rond, rectangle, 4 couleurs, annuler, tout effacer, rotation 90°, zoom ; barre réductible. Commentaire, champs supplémentaires et temps, puis « Valider la photo ».
3. Un petit **commentaire de début de section** est proposé sous chaque section (option).
4. **Replier / déplier** les photos d’une section (flèche à gauche de son en-tête) ou de **toutes les sections** (icône à double flèche au-dessus de la liste). **Glisser-déposer** de la poignée à 6 points pour réordonner, dans une section ou vers une autre.
5. **Temps** : hh/min par photo, somme par section, total à côté du titre général. **Chrono 1** (bouton en haut), **Chrono 2** (à gauche, option) et **chrono par photo** (option, uniquement dans l’édition d’une photo). Chronos flottants, déplaçables, fixes à l’écran ; Départ / Arrêt, puis **0** pour remettre à zéro ; Départ reprend là où il s’était arrêté. Dans l’éditeur, les boutons « Chrono 1 », « Chrono 2 » et « Chrono photo » copient leur temps dans hh/min. Le **chrono photo** continue de tourner après « Valider la photo » : une icône rouge clignotante s’affiche sur la photo et sur sa section ; toucher cette icône **arrête** le chrono et **enregistre son temps dans la photo** (sur l’icône d’une section : tous ses chronos photo s’arrêtent). Dans l’éditeur, le bouton « Chrono photo » l’arrête aussi et copie son temps dans hh/min. Avant d’enregistrer ou d’envoyer, l’application vérifie qu’aucun chrono ne tourne et, sinon, indique la photo et le n° de section concernés. « Masquer tous les temps » (dans Paramètres) les retire partout (écran, éditeur, chronos, exports).
6. **Sauvegarde automatique** sur l’appareil. Photos compressées à 80 % (JPEG).

## 4. Page Paramètres
Aperçu de page dessiné à main levée qui suit vos choix. Réglages :
- **Bandeau** sous Onoré : Procédure, Rapport (défaut), Inventaire ou libellé personnalisé. Ce libellé préfixe aussi le nom des fichiers (ex. `Inventaire_titre_261029.pdf`).
- **Numérotation** des sections (lettres, chiffres, rien, puces) et des photos (A1, chiffres, lettres, rien, puces).
- **Affichage** : commentaire de début de section ; photos affichées ou non (décochées, chaque section ne reçoit plus que des commentaires, via le bouton « Commentaire ») ; contenu « photo et commentaire », « photo seule » ou « commentaire seul » (exports et aperçu). En mode commentaire seul, les lignes par page ne sont plus prises en compte.
- **Temps et chronos** : masquer tous les temps, chrono 2, chrono par photo.
- **Champs supplémentaires par photo** : Outillage, Emplacement et jusqu’à 5 champs personnalisés.
- **Nom des fichiers** : libellé + titre ou nom + date aammjj (+ numéro). Choix mémorisé.
- **Exportations** : photos par ligne (1 à 4) et lignes par page (1 à 5), séparément pour le PDF et le Word.
- **Bouton Envoyer** affiché ou non.

## 5. Exports et envoi
- **Excel** : bandeau et titre en haut, puis une ligne par photo, photos en colonne, avec section, numéro, commentaire, temps et champs.
- **Word** et **PDF** : en-tête Onoré avec le libellé choisi sur chaque page, titre, auteur, date, temps total, commentaire général, puis chaque section avec ses photos de même taille. Une section n’est jamais seule en bas de page.
- Les fichiers sont **enregistrés dans le téléphone** (Téléchargements sous Android ; sur iPhone, la feuille de partage propose « Enregistrer dans Fichiers »). Le nom prévu s’affiche sous les boutons.
- **Envoyer** : cocher les fichiers, puis Mail ou WhatsApp. Les fichiers sont enregistrés, puis l’application choisie s’ouvre avec un message pré-rempli ; les fichiers se joignent à la main (un site ne peut pas les joindre automatiquement).

## 6. Mises à jour et version
- Le service worker renouvelle l’application dès qu’Internet est disponible ; un message propose de recharger. « Vérifier la mise à jour » force la vérification.
- Pour publier une nouvelle version, modifier le numéro dans `sw.js` (`const VERSION='v1.6.1'` et la première ligne de commentaire) et dans `index.html` (`const APP_VERSION='v1.6.1';const APP_DATE='30/10/2026';`).

## 7. Bibliothèques externes (mises en cache pour le hors ligne)
`jsPDF 2.5.2` (PDF), chargée depuis cdn.jsdelivr.net, et la police Inter (Google Fonts). La première ouverture doit se faire avec Internet. Les exports Word et Excel sont générés directement par l’application, sans bibliothèque.
