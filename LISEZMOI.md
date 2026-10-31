# Rapport – mise en place

Application web installable (Android, iPhone/iPad, PC) pour réaliser un rapport, une procédure ou un inventaire avec photos annotées et commentaires, exportable en **Excel, Word et PDF**. Elle fonctionne hors ligne une fois installée. Version **v1.11.1**.

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
1. **Nom**, **date**, **titre** (libellé du bandeau, ex. « Titre Rapport », avec à droite le nombre de sections et de photos) et **commentaire général** (optionnel, dictée vocale possible). « Section 1, 2, 3… » s’affiche en gris clair tant qu’une section n’est pas nommée. **Avant tout export ou envoi**, l’application vérifie que nom, date, titre et nom de chaque section sont remplis ; sinon elle liste les manques et entoure les champs en rouge.
2. Dans chaque **section** (A, B, C…), « Photo A1 » ou « Galerie ». Appareil photo : curseur pour éclaircir, **Flash** et **mise au point** au toucher quand le téléphone le permet (Android/Chrome ; pas sur iPhone/Safari). Annotations : croix, flèche, rond, rectangle, 4 couleurs, annuler, tout effacer, rotation 90°, zoom ; barre réductible. Commentaire, champs supplémentaires et temps, puis « Valider la photo ».
3. Un petit **commentaire de début de section** est proposé sous chaque section (option).
4. **Replier / déplier** les photos d’une section (flèche à gauche de son en-tête) ou de **toutes les sections** (icône à double flèche au-dessus de la liste). **Glisser-déposer** de la poignée à 6 points pour réordonner, dans une section ou vers une autre.
5. **Temps** : hh/min par photo, somme par section, total à côté du titre. **Chrono 1** (bouton en haut), **Chrono 2** (à gauche, option) et **chrono par photo** (option, uniquement dans l’édition d’une photo). Chronos flottants, déplaçables, fixes à l’écran ; Départ / Arrêt, puis **0** pour remettre à zéro ; Départ reprend là où il s’était arrêté. Dans l’éditeur, les boutons « Chrono 1 », « Chrono 2 » et « Chrono photo » copient leur temps dans hh/min. Le **chrono photo** continue de tourner après « Valider la photo » : une icône rouge clignotante s’affiche sur la photo et sur sa section ; toucher cette icône **arrête** le chrono et **enregistre son temps dans la photo** (sur l’icône d’une section : tous ses chronos photo s’arrêtent). Dans l’éditeur, le bouton « Chrono photo » l’arrête aussi et copie son temps dans hh/min. Avant d’enregistrer ou d’envoyer, l’application vérifie qu’aucun chrono ne tourne et, sinon, indique la photo et le n° de section concernés. « Masquer tous les temps » (dans Paramètres) les retire partout (écran, éditeur, chronos, exports).
6. **Sauvegarde automatique** sur l’appareil. Photos compressées à 80 % (JPEG).
7. **Tags** : si des tags sont activés dans les Paramètres, ils apparaissent sous forme de boutons dans l’édition d’une photo (plusieurs tags possibles). Ils s’affichent sous la photo, dans la liste et dans les exports.
8. **Signature électronique** (si activée dans les Paramètres) : cadre « Signature » sous les sections → *Signer le rapport*, nom du signataire, tracé au doigt ou à la souris, *Valider*. *Signer de nouveau* la remplace, *Supprimer* la retire. Elle est ajoutée à la fin des exports (« Signé électroniquement par … le … à … »). C’est une signature manuscrite numérisée, non une signature certifiée ; en cas de modification du rapport, la signer de nouveau. Un rapport dupliqué ne reprend pas la signature.

## 3 bis. Rapports enregistrés
- Chaque rapport est conservé sur le téléphone. « Nouveau rapport » ne supprime plus rien : le rapport en cours est mis de côté.
- Le bouton **Rapports** (en haut) liste les rapports (nom de fichier, date, nombre de photos, taille). **Ouvrir** reprend un rapport pour le modifier ; **Dupliquer** ouvre une copie datée du jour, l’original reste intact ; la corbeille supprime.
- L’icône de téléchargement d’un rapport crée un fichier **.json** de sauvegarde ; « Importer un rapport (.json) » le remet dans la liste (pour changer de téléphone, par exemple).
- Impossible de changer de rapport tant qu’un chrono photo tourne.

## 4. Page Paramètres
Aperçu de page dessiné à main levée qui suit vos choix. Réglages :
- **Bandeau et logo** : libellé sous le logo (Procédure, Rapport par défaut, Inventaire ou personnalisé ; il préfixe aussi le nom des fichiers, ex. `Inventaire_titre_261029.pdf`). **Importer mon logo** remplace Onoré / Boncolac ; « Logo d’origine » le rétablit. Logo à respecter : **PNG à fond transparent, 1500 × 400 px** (3,75 : 1), marge de 5 %, couleurs claires si le fond est foncé, moins de 1 Mo ; il est ajusté dans une zone de 760 × 196 px du bandeau (900 × 374 px). Quatre **couleurs** modifiables : fond du bandeau (avec le logo d’origine comme avec un logo personnalisé), libellé, barres de section et numéros de section ; « Couleurs d’origine » les rétablit. « Enregistrer le bandeau (image PNG) » exporte le bandeau actuel. Le gabarit et l’entête extraits sont dans `entete.zip`.
- **Numérotation** des sections (lettres, chiffres, rien, puces) et des photos (A1, chiffres, lettres, rien, puces).
- **Affichage** : commentaire de début de section ; photos affichées ou non (décochées, chaque section ne reçoit plus que des commentaires, via le bouton « Commentaire ») ; contenu « photo et commentaire », « photo seule » ou « commentaire seul » (exports et aperçu). En mode commentaire seul, les lignes par page ne sont plus prises en compte.
- **Temps et chronos** : masquer tous les temps, chrono 2, chrono par photo.
- **Champs supplémentaires par photo** : Outillage, Emplacement et jusqu’à 5 champs personnalisés. **Chaque champ s’active séparément** par sa propre case (un champ décoché est masqué, sa valeur est conservée).
- **Tags** : 5 tags à nommer ; chaque tag s’active séparément (case à cocher). Seuls les tags activés et nommés sont proposés dans l’édition des photos.
- **Signature électronique** : case « Permettre de signer le rapport » ; fait apparaître le cadre « Signature » sous les sections.
- **Filigrane** : case « Ajouter un filigrane dans les exports », texte personnalisable, **couleur** et **épaisseur** réglables, aperçu. Il est tracé en diagonale, en transparence, sur chaque page des exports PDF et Word ; dans Excel, une image transparente est répétée environ toutes les pages.
- **Nom des fichiers** : libellé + titre ou nom + date aammjj (+ numéro). Choix mémorisé.
- **Exportations** : photos par ligne (1 à 4) et lignes par page (1 à 5), séparément pour le PDF et le Word.
- **Dossier de stockage** : sur PC (Chrome ou Edge), « Choisir le dossier » y range les exports Excel/Word/PDF et permet d’y copier une sauvegarde .json de tous les rapports. Sur téléphone, le champ indique le dossier réel (Téléchargements) ; sous Android, Chrome → ⋮ → Paramètres → Téléchargements → « Demander où enregistrer les fichiers » permet de choisir le dossier à chaque export. Les rapports de la liste, eux, vivent dans la mémoire privée de l’application (aucun dossier visible).
- **Bouton Envoyer** affiché ou non.

## 5. Exports et envoi
- **Excel** : bandeau et titre en haut, puis une ligne par photo, photos en colonne, avec section, numéro, commentaire, temps, tags et champs. Signature en fin de feuille.
- **Word** et **PDF** : en-tête Onoré avec le libellé choisi sur chaque page, titre, mention **« Réalisé par Didier le 12/11/2026 »** (nom et date du rapport), temps total, commentaire général, puis chaque section avec ses photos de même taille (tags et champs sous chaque photo) et, en fin de document, la signature si le rapport est signé. Une section n’est jamais seule en bas de page.
- Les fichiers sont **enregistrés dans le téléphone** (Téléchargements sous Android ; sur iPhone, la feuille de partage propose « Enregistrer dans Fichiers »). Le nom prévu s’affiche sous les boutons.
- **Envoyer** : cocher les fichiers, puis Mail ou WhatsApp. Les fichiers sont enregistrés, puis l’application choisie s’ouvre avec un message pré-rempli ; les fichiers se joignent à la main (un site ne peut pas les joindre automatiquement).

## 6. Mises à jour et version
- Le service worker renouvelle l’application dès qu’Internet est disponible ; un message propose de recharger. « Vérifier la mise à jour » force la vérification.
- Pour publier une nouvelle version, modifier le numéro dans `sw.js` (`const VERSION='v1.11.1'` et la première ligne de commentaire) et dans `index.html` (`const APP_VERSION='v1.11.1';const APP_DATE='30/10/2026';`).

## 7. Bibliothèques externes (mises en cache pour le hors ligne)
`jsPDF 2.5.2` (PDF), chargée depuis cdn.jsdelivr.net, et la police Inter (Google Fonts). La première ouverture doit se faire avec Internet. Les exports Word et Excel sont générés directement par l’application, sans bibliothèque.
