# Güzel Yıldız — Site e-commerce (Maroc)

Site vitrine + boutique **en un seul fichier** : `index.html`.
Aucun serveur, aucune base de données, aucune dépendance en ligne : tout le CSS, le JavaScript et les images sont locaux.

---

## 1. Ouvrir le site

- Double-cliquez sur `index.html` (Chrome, Edge, Safari, Firefox).
- Le site fonctionne aussi hors connexion.
- Pour le mettre en ligne, envoyez `index.html` **et** le dossier `assets/` sur n'importe quel hébergement statique (Hostinger, Netlify, GitHub Pages, cPanel…).

```
guzel-yildiz/
├── index.html
├── index-sauvegarde.html   (copie de secours — pouvant être supprimée)
├── README.md
└── assets/
    └── img/        (14 photos : hero, histoire, 12 produits)
```

---

## 2. Ce que contient le site

- Bandeau d'annonce, en-tête collant, menu mobile, tiroir panier.
- Hero « L'élégance d'Istanbul, pour la femme marocaine ».
- 3 univers : Accessoires, Parfums, Vêtements.
- Catalogue de 12 produits avec filtres par catégorie, **favoris ♡**, recherche et tri.
- Fiche produit (modal) : tailles, couleurs, quantité, ajout au panier, **ajout aux favoris** et **zoom sur la photo** (cliquez la photo pour l'agrandir, Échap ou clic en dehors pour fermer).
- Panier avec seuil de livraison offerte, **code promo**, calcul des frais et **bon de commande PDF automatique**.
- Section « Notre histoire », témoignages, formulaire de contact (WhatsApp), newsletter.
- Pied de page complet, bouton WhatsApp flottant, retour en haut.
- **Bon de commande PDF** : à la commande, le client reçoit un vrai fichier PDF (référence, articles, tailles, couleurs, totaux, coordonnées). Il l'envoie ensuite sur WhatsApp pour confirmer. Le bouton WhatsApp reste disponible en secours.
- Design rose poudré / prune, typographie système simple, 100 % responsive (téléphone, tablette, ordinateur).

---

## 3. Accéder à l'espace de gestion (admin)

L'accès est **volontairement caché** — aucun lien visible dans la navigation.

### Sur ordinateur
- Cliquez **5 fois rapidement sur le logo** « Güzel Yıldız » (en haut à gauche), en moins de 3 secondes.
- Ou utilisez le raccourci **Ctrl + Alt + G**.

### Sur téléphone
- **Tapez 5 fois rapidement sur le logo**, en haut à gauche.

### Flux de commande du client
1. Le client remplit son panier et clique sur **Commander — recevoir le bon PDF**.
2. Un fichier **`GY-YYYYMMDD-XXXX-guzel-yildiz.pdf`** se télécharge automatiquement : c'est le bon de commande officiel (logo, référence, articles, tailles/couleurs, sous-total, **code promo et réduction éventuelle**, livraison, total, nom, téléphone, ville).
3. Le client l'envoie sur WhatsApp (bouton « Envoyer sur WhatsApp » proposé) et vous confirmez.
4. Le panier est vidé automatiquement.

### Mot de passe
```
12345
```

Une fois connecté, une petite pastille « Admin » apparaît en haut à droite.
Pour la changer : ouvrez `index.html`, ligne **1698** :

```js
const ADMIN_PASSWORD = "12345";   // remplacez par votre mot de passe
```

> ⚠️ Ce mot de passe est visible dans le code source : il protège l'interface, pas les fichiers. Pour une vraie sécurité, ajoutez un back-end.

---

## 4. Gérer le contenu depuis l'admin

L'onglet **Tableau de bord** permet de :

- **Produits** : créer, modifier, dupliquer, masquer, supprimer. Champs : nom, catégorie, prix, ancien prix, description, tailles, couleurs, étiquette, stock, image, mise en avant. **Photo réelle** : dans le formulaire de l'article, bouton **Choisir une photo** — prenez la photo depuis votre appareil (JPG/PNG) ; elle est redimensionnée enregistrée automatiquement (max 900 px de large). « Retirer » remet le visuel généré. Vous pouvez aussi coller une URL dans le champ Image : le dernier choix gagne.
- **Codes promo** : créez des codes (pourcentage 1–90 % ou montant fixe en MAD). La cliente les entre dans le panier : la réduction s'affiche dans le panier, dans le message WhatsApp et sur le bon PDF. Un code peut être **masqué** (plus utilisable mais conservé) ou supprimé définitivement.
- **Contenu du site** : nom de marque, signature, bandeau d'annonce, titres et textes du hero, texte de la section histoire, coordonnées, réseaux sociaux, seuil de livraison offerte, frais de livraison.
- **Photos d'accueil** : dans « Bannière principale » et « Notre histoire », bouton **Changer la photo** — choisissez une image depuis votre téléphone ou ordinateur (JPG/PNG). Elle est redimensionnée et enregistrée automatiquement. « Réinitialiser » remet la photo d'origine.
- **Sauvegarde** : export / import d'un fichier JSON (inclut les codes promo et les favoris), **import d'un catalogue CSV / XML** (voir section 5), réinitialisation des données.
- **Côté cliente** : chaque produit a un cœur ♡ (sur la carte et dans la fiche). Le filtre « ♡️ Favoris » de la boutique affiche uniquement les produits aimés — ils restent enregistrés sur l'appareil de la cliente.

Les modifications sont enregistrées dans le navigateur (`localStorage`) et visibles immédiatement sur cet appareil.

### Publier pour vos visiteurs (GitHub Pages)

Un site GitHub Pages est **statique** : il ne peut pas enregistrer vos modifications à distance. Ajouter un article dans l'admin le change **uniquement sur votre appareil**. Pour que tout le monde le voie :

1. Admin → **Sauvegarde** → **Télécharger le site à jour (index.html)**.
2. Sur GitHub, ouvrez votre dépôt (`guzelmoda/store`), cliquez sur `index.html` → **Upload file** (ou remplacez le fichier), puis **Commit changes**.
3. GitHub Pages publie la nouvelle version en **1 à 2 minutes**. Rechargez `https://guzelmoda.github.io/store/` (Ctrl + F5 si l'ancienne version reste affichée).

Le fichier téléchargé contient **vos articles, vos textes, vos codes promo et vos photos** : il remplace le catalogue de démonstration par le vôtre. Chaque publication reçoit une **version interne** : les visiteurs déjà venus reçoivent automatiquement la mise à jour à leur prochaine ouverture, **sans perdre leur panier ni leurs favoris**.

> ⚠️ Le bouton lit le fichier du site pour le réécrire : utilisez-le depuis le site en ligne (https://…) ou un serveur local, **pas en double-cliquant le fichier** (`file://`).
>
> La première fois que vous installez cette version, vos données locales déjà saisies sont conservées. Ensuite, chaque publication met à jour tous les appareils.
>
> Sans cette étape de publication, vos modifications restent privées sur votre navigateur. L'export JSON, lui, sert de sauvegarde ou de transfert vers un autre appareil — ce n'est pas une publication.

Pour un vrai catalogue partagé et modifiable en direct (sans republier), il faudra un back-end (Firebase, Supabase, etc.) : le fichier statique seul ne peut pas stocker de données côté serveur.

### Données stockées
| Clé | Contenu |
|---|---|
| `gz_products_v1` | catalogue |
| `gz_site_v1` | textes et réglages |
| `gz_cart_v1` | panier |
| `gz_fav_v1` | favoris de la cliente (liste d'identifiants) |
| `gz_promos_v1` | codes promo créés dans l'admin |
| `gz_promo_v1` | code promo actuellement appliqué |
| `gz_build_v1` | version du site déjà chargée (sert à appliquer les publications) |
| `gz_admin_session` | session admin (onglet en cours) |

Pour repartir de zéro : dans l'admin → **Sauvegarde** → réinitialiser (efface aussi les favoris et les codes promo), ou videz le stockage du site dans les réglages du navigateur.

---

## 5. Importer un catalogue CSV / XML

Admin → **Sauvegarde** → panneau **« Importer un catalogue CSV / XML »**.

1. Cliquez sur **Choisir un fichier CSV / XML** (formats `.csv`, `.xml`, `.txt` — 8 Mo maximum, UTF-8 ou Windows-1252).
2. Un **aperçu** s'affiche : nombre de produits, **catégories détectées** et lignes ignorées. Rien n'est enregistré tant que vous ne confirmez pas.
3. Cliquez sur **Importer ces produits**. Les catégories et les filtres de la boutique sont mis à jour automatiquement.

**Fusion ou remplacement**
- Par défaut, l'import **fusionne** : un produit déjà présent (même `id` ou même **nom**, casse ignorée) est **mis à jour** ; les autres sont **ajoutés**. Aucun doublon.
- Cochez **« Remplacer tout le catalogue existant »** pour repartir uniquement des produits du fichier.

Deux **modèles prêts à remplir** sont téléchargeables depuis le panneau : **Modèle CSV** et **Modèle XML**.

### Colonnes CSV

L'en-tête est obligatoire ; le séparateur (`;`, `,` ou tabulation) est détecté automatiquement. Les en-têtes français ou anglais sont acceptés (accents et majuscules ignorés).

| Colonne | Obligatoire | Exemple |
|---|---|---|
| `nom` | **oui** | `Foulard Bosphore` |
| `categorie` | non (défaut : Accessoires) | `Accessoires` |
| `prix` | non | `249` |
| `ancien_prix` | non | `320` |
| `description` | non | `Carré de soie lavée 90 × 90 cm` |
| `tailles` | non | `90 × 90 cm; 70 × 70 cm` |
| `couleurs` | non | Ivoire:#efe6d7 \| Noir:#161616 |
| `etiquette` | non | `Best-seller` |
| `stock` | non | `En stock` |
| `image` | non | `assets/img/foulard-bosphore.jpg` ou URL `https://…` |
| `en_avant` | non | `1` (mis en avant) / `0` |
| `actif` | non | `1` (visible) / `0` (masqué) |
| `id` | non | `gz-01` (sert à retrouver le produit) |

- **Prix** : `249`, `249.00`, `249,00` et `1 249,00` sont compris.
- **Listes** (`tailles`, `couleurs`) : séparez les valeurs par `;`, `|` ou `,`.
- **Couleurs** : `Nom:#hex` (ex. `Ivoire:#efe6d7`). Sans code, une teinte dorée est appliquée.
- **Booléens** : `1/0`, `oui/non`, `true/false`, `actif/inactif`.
- Les guillemets CSV sont gérés (`"texte; avec; points-virgules"`), ainsi que le BOM Excel.

### Fichier XML

Mêmes champs, en balises ou en attributs. Les listes `tailles` et `couleurs` peuvent être imbriquées :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<catalogue>
  <produit id="gz-01">
    <nom>Foulard Bosphore</nom>
    <categorie>Accessoires</categorie>
    <prix>249</prix>
    <ancien_prix>320</ancien_prix>
    <description>Carré de soie lavée 90 × 90 cm.</description>
    <tailles>
      <taille>90 × 90 cm</taille>
    </tailles>
    <couleurs>
      <couleur nom="Ivoire" hex="#efe6d7"/>
      <couleur nom="Noir" hex="#161616"/>
    </couleurs>
    <etiquette>Best-seller</etiquette>
    <stock>En stock</stock>
    <image>assets/img/foulard-bosphore.jpg</image>
    <en_avant>0</en_avant>
    <actif>1</actif>
  </produit>

  <!-- Attributs acceptés aussi -->
  <produit nom="Coussin Iznik" categorie="Décoration" prix="149" actif="0"/>
</catalogue>
```

Les balises racine `catalogue`, `catalog`, `produits` ou `products` sont reconnues, ainsi que les noms `produit`, `product`, `article` ou `item`.

### Images

- Un produit **sans image** reçoit automatiquement un visuel de marque généré (SVG).
- Une image introuvable (chemin erroné) est **remplacée à l'affichage** par ce même visuel : la carte, la fiche produit, le panier, la liste admin et le zoom restent propres.
- Une valeur `image` qui n'est ni un chemin, ni une URL, ni un nom de fichier image est ignorée à l'import.

---

## 6. À personnaliser avant la mise en ligne

1. **Numéro WhatsApp** : admin → Contenu → `WhatsApp (indicatif + numéro, sans espaces)`, par exemple `212661234567`. Actuellement un numéro fictif `212600000000`.
2. **Téléphone, e-mail, adresse, horaires** : mêmes écran (affichés aussi sur le PDF).
3. **Photo d'accueil** : admin → Contenu → Bannière principale → **Changer la photo**.
4. **Frais de livraison** et **seuil de livraison offerte** (600 MAD par défaut).
5. **Réseaux sociaux** (Instagram, Facebook, TikTok).
6. **Photos produits** : le plus simple est d'**uploader la photo directement dans l'admin** (formulaire de l'article → Choisir une photo) — aucun fichier à gérer. Sinon, remplacez les fichiers dans `assets/img/` en gardant les mêmes noms, ou changez le chemin de l'image dans la fiche produit.
7. **Mot de passe admin** (ligne 1698).

> ℹ️ Les photos uploadées tiennent dans le navigateur (localStorage) : elles sont redimensionnées à max 900 px de large en JPEG (~100–300 Ko chacune). Si le catalogue en contient beaucoup, utilisez des URLs d'images ( champ Image ) ou l'export JSON pour transférer vers un autre appareil.

---

## 7. Notes techniques

- Bon de commande : PDF généré sans aucune bibliothèque (moteur interne du site), nommé `GY-YYYYMMDD-XXXX-guzel-yildiz.pdf`. Si un code promo est appliqué, la ligne « Code XXX − réduction » apparaît en rose entre le sous-total et la livraison. Le message WhatsApp reste disponible en secours.
- Aucun cookie, aucun tracker, aucune requête externe.
- Accessibilité : contrastes, libellés ARIA, navigation clavier, `prefers-reduced-motion`.
- Testé sur Chrome / Edge, largeurs 390 px, 800 px et 1440 px (panier promo, admin codes promo, fiche produit avec zoom, filtre favoris).

---

## 8. Crédits photos

Photos libres de droits issues d'**Unsplash** et **Pexels**, téléchargées localement dans `assets/img/` (aucun hotlink).
Vous pouvez les remplacer par vos propres visuels : gardez simplement les mêmes noms de fichiers.
