# Cassette Deck — mini lecteur audio pour Windows

## Installation

1. Lancez `CassetteDeck-Setup.exe`. L'assistant présente cinq étapes :
   - **Bienvenue** ;
   - **Contrat de licence**, à accepter ;
   - **Dossier et options** : raccourci sur le Bureau, « Ouvrir avec », mises à jour automatiques, lancement au démarrage de Windows ;
   - **Installation**, avec une barre de progression ;
   - **Terminé**.
2. Le lecteur s'installe par défaut dans `%LOCALAPPDATA%\Programs\CassetteDeck`, sans droits administrateur.
3. Windows SmartScreen peut afficher une alerte tant que l'exécutable n'est pas signé : cliquez sur **Informations complémentaires → Exécuter quand même**.

Relancer l'assistant sur un PC où le lecteur est déjà installé fait une **mise à jour** : les listes, favoris et réglages sont conservés, et les options précédentes sont reprises.

Options en ligne de commande :
- `CassetteDeck-Setup.exe /S` : installation silencieuse ;
- `/D=C:\chemin` : dossier d'installation ;
- `/relaunch` : relance le lecteur après l'installation.

Version portable : `CassetteDeck.exe` fonctionne aussi seul, sans installation.

Désinstallation : **Paramètres → Applications → Applications installées → Cassette Deck → Désinstaller**.

Prérequis : Windows 10 ou 11. Le lecteur utilise le moteur WebView2 de Windows, ou à défaut Microsoft Edge, tous deux présents par défaut.

## Fenêtre

- **Fenêtre native sans cadre** (par défaut) : seul le boîtier apparaît, avec des coins arrondis. Faites glisser le boîtier pour déplacer la fenêtre. Ctrl + molette change la taille. Les petits boutons en haut à droite servent à réduire, à masquer dans la zone de notification ou à quitter.
- **Mode compatibilité** : fenêtre Edge classique, avec barre de titre. Le lecteur y bascule tout seul si la fenêtre native ne peut pas s'ouvrir. On peut aussi le choisir par un clic droit, avec le raccourci « Cassette Deck (mode compatibilité) » du menu Démarrer, ou avec l'option `--edge`.
- **Zone de notification** : un clic gauche affiche ou masque le lecteur. Le clic droit ouvre un menu : lecture/pause, suivant, précédent, radio, enregistrement, quitter.
- **Miniature de la barre des tâches** : boutons ⏮ ⏯ ⏭ au survol. La progression de la piste s'affiche sur le bouton (rouge pendant un enregistrement).
- En cas de souci, un journal est disponible dans `%LOCALAPPDATA%\CassetteDeck\journal.txt`.

## Utilisation

| Action | Commande |
|---|---|
| Lecture / pause | Boutons PLAY / PAUSE, ou Espace |
| Piste précédente / suivante | PREV / NEXT, ou P / N |
| Stop | STOP |
| Volume | Glisser le bouton VOLUME, molette, ou ↑ ↓ (double-clic : muet) |
| Se déplacer dans la piste | Cliquer sur la barre de progression, ou ← → (5 s) |
| Aléatoire / Répétition | Voyants ALÉATOIRE, RÉPÉTER, ou S / R |
| Égaliseur 10 bandes | Clic sur ÉGALISEUR, ou Q (E : activer / désactiver) |
| Liste de lecture | Clic sur la cassette, ou L |
| Charger des pistes | Double-clic sur la cassette, clic sur la plaque STEREO, ou O |
| Radio en ligne | Touche T, ou clic droit → Radio en ligne |
| Menu complet | Clic droit n'importe où |

- REPEAT tourne entre trois modes : tout (voyant fixe), une piste (voyant clignotant), désactivé.
- L'égaliseur a 10 bandes (31 Hz à 16 kHz, ±12 dB), un préampli, une courbe de réponse et 12 préréglages (Rock, Jazz, Classique, Électro, Voix, Loudness…). Un double-clic sur un curseur le remet à zéro.
- La pochette de l'album s'affiche à la place de la plaque STÉRÉO. Elle provient de l'image intégrée au MP3 ou au FLAC, ou d'un fichier cover.jpg ou folder.jpg du dossier. En radio, c'est le logo de la station quand il est assez grand.
- Les bobines tournent avec de l'inertie, et le bobinage passe d'une bobine à l'autre au fil de la piste. Un oscilloscope défile entre les deux.
- Au premier lancement, le dossier **Musique** est chargé. Ensuite, la dernière liste, la piste et la position sont reprises.
- Le glisser-déposer de fichiers sur la fenêtre les ajoute pour la session en cours.
- « Ouvrir avec → Cassette Deck » est proposé pour les fichiers audio ; si le lecteur est déjà ouvert, les fichiers s'ajoutent à sa liste.
- Formats : MP3, FLAC, WAV, OGG, Opus, M4A/AAC, WebM. Les titres et artistes sont lus dans les tags ID3 et Vorbis.

## Radio en ligne

L'onglet **Radio** du panneau de la cassette (touche T) propose :

- **Favoris** : dix stations sont préchargées (FIP, France Inter, France Culture, France Musique, Radio Paradise, SomaFM…). Cliquez sur ★ pour ajouter ou retirer une station, sur ✕ pour la supprimer des favoris.
- **Recherche** : par nom ou par genre (Électro, Jazz, Synthwave…), dans l'annuaire libre Radio Browser, qui compte plus de 40 000 stations.
- **+ URL** : écoute d'un flux par son adresse, au format MP3, AAC, OGG ou via une liste .pls / .m3u. Le bouton « ★ Ajouter » l'enregistre dans les favoris.

En mode radio :

- l'afficheur indique ON AIR, puis le nom de la station et le titre diffusé quand le serveur le transmet (métadonnées ICY) ;
- la durée totale affiche LIVE ;
- PREV et NEXT passent à la station précédente ou suivante ;
- PAUSE coupe le flux, et PLAY le reprend en direct ;
- en cas de coupure, le lecteur se reconnecte automatiquement deux fois.

**Enregistrement** : le bouton ● REC de l'onglet Radio, ou le menu, enregistre la station en cours dans `Musique\Cassette Deck\Enregistrements\<station>\`. Un fichier est créé par titre diffusé, déjà étiqueté (artiste, titre, station). L'afficheur indique ENR. et le voyant d'alimentation passe au rouge.

**Historique** : la puce « Historique » de l'onglet Radio liste les titres entendus, avec leur heure et la station, et des boutons Copier / YouTube / Spotify / Web.

Pour revenir à vos fichiers, cliquez sur une piste dans l'onglet **Liste**.

Les flux HLS (.m3u8) ne sont pas pris en charge.

## Mises à jour automatiques

Si l'option est cochée, le lecteur vérifie une fois par jour s'il existe une nouvelle version. La vérification commence 40 secondes après le lancement. Quand une version est disponible, il propose **Télécharger et installer**, **Plus tard** ou **Ignorer cette version**. L'installation se fait en silence et le lecteur redémarre tout seul.

Le menu clic droit contient aussi **Rechercher des mises à jour…** et **Mises à jour automatiques** (activer ou désactiver).

Sécurité :
- chaque mise à jour est signée avec la clé privée de l'éditeur (Ed25519) ;
- le lecteur vérifie la signature puis l'empreinte SHA-256 du fichier téléchargé ;
- un fichier modifié ou un serveur piraté ne peut donc pas faire installer autre chose.

### Publier une nouvelle version (GitHub Releases)

1. Une seule fois : créez un dépôt **public** sur GitHub, par exemple `utilisateur/cassette-deck`. Mettez dans `update_url.txt` l'adresse :
   `https://github.com/utilisateur/cassette-deck/releases/latest/download/latest.json`
   Puis recompilez avec `sh build.sh`.
2. Pour chaque version : augmentez le numéro de version (`AppVersion` dans `app/main.go`, `appVersion` dans `setup/main.go`, et `res/*.rc`), puis lancez `sh build.sh`.
3. Signez l'installateur :
   ```
   go run ./tools/release sign -key keys/update_private.key -version 2.2.0 \
     -url https://github.com/utilisateur/cassette-deck/releases/download/v2.2.0/CassetteDeck-Setup.exe \
     -notes notes.txt -out dist/latest.json dist/CassetteDeck-Setup.exe
   ```
4. Sur GitHub, créez une release `v2.2.0` et joignez-y **CassetteDeck-Setup.exe** et **latest.json**. Les lecteurs installés la trouveront sous 24 heures.

**La clé privée `update_private.key` est irremplaçable.** Si elle est perdue, les lecteurs déjà installés ne pourront plus recevoir de mises à jour automatiques. Gardez-en deux copies hors ligne, et ne la publiez jamais : ni sur GitHub, ni dans un ZIP.

## Compiler soi-même

Il faut Go 1.22 ou plus récent, sous Linux, macOS ou Windows. Lancez `sh build.sh`. Les fichiers sont produits dans `dist/`.

- `app/` : le lecteur (serveur local Go + interface HTML/JS dans `app/ui/`, relais radio dans `app/radio.go`)
- `setup/` : l'assistant d'installation (Win32), qui embarque le lecteur ; le contrat de licence est dans `setup/licence.txt`
- `tools/release/` : création des clés et signature des mises à jour
- `keys/update_public.txt` : clé publique intégrée au lecteur
- `res/` : icône, manifeste et informations de version Windows
- `work/build_assets.py` : regénère les calques de l'interface à partir de l'image d'origine (`python3 work/build_assets.py image.png app/ui/assets`)
