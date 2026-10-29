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
├── README.md
└── assets/
    └── img/        (14 photos : hero, histoire, 12 produits)
```

---

## 2. Ce que contient le site

- Bandeau d'annonce, en-tête collant, menu mobile, tiroir panier.
- Hero « L'élégance d'Istanbul, pour la femme marocaine ».
- 3 univers : Accessoires, Parfums, Vêtements.
- Catalogue de 12 produits avec filtres par catégorie, recherche et tri.
- Fiche produit (modal) : tailles, couleurs, quantité, ajout au panier.
- Panier avec seuil de livraison offerte, calcul des frais et **bon de commande PDF automatique**.
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
2. Un fichier **`GY-YYYYMMDD-XXXX-guzel-yildiz.pdf`** se télécharge automatiquement : c'est le bon de commande officiel (logo, référence, articles, tailles/couleurs, totaux, nom, téléphone, ville).
3. Le client l'envoie sur WhatsApp (bouton « Envoyer sur WhatsApp » proposé) et vous confirmez.
4. Le panier est vidé automatiquement.

### Mot de passe
```
12345
```

Une fois connecté, une petite pastille « Admin » apparaît en haut à droite.
Pour la changer : ouvrez `index.html`, ligne **1518** :

```js
const ADMIN_PASSWORD = "12345";   // remplacez par votre mot de passe
```

> ⚠️ Ce mot de passe est visible dans le code source : il protège l'interface, pas les fichiers. Pour une vraie sécurité, ajoutez un back-end.

---

## 4. Gérer le contenu depuis l'admin

L'onglet **Tableau de bord** permet de :

- **Produits** : créer, modifier, dupliquer, masquer, supprimer. Champs : nom, catégorie, prix, ancien prix, description, tailles, couleurs, étiquette, stock, image, mise en avant.
- **Contenu du site** : nom de marque, signature, bandeau d'annonce, titres et textes du hero, texte de la section histoire, coordonnées, réseaux sociaux, seuil de livraison offerte, frais de livraison.
- **Photos d'accueil** : dans « Bannière principale » et « Notre histoire », bouton **Changer la photo** — choisissez une image depuis votre téléphone ou ordinateur (JPG/PNG). Elle est redimensionnée et enregistrée automatiquement. « Réinitialiser » remet la photo d'origine.
- **Sauvegarde** : export / import d'un fichier JSON, réinitialisation des données.

Les modifications sont enregistrées dans le navigateur (`localStorage`) et visibles immédiatement sur cet appareil.
Elles ne sont **pas** envoyées aux autres visiteurs : pour publier pour tout le monde, utilisez l'export JSON / un back-end, ou modifiez directement les valeurs par défaut du fichier.

### Données stockées
| Clé | Contenu |
|---|---|
| `gz_products_v1` | catalogue |
| `gz_site_v1` | textes et réglages |
| `gz_cart_v1` | panier |
| `gz_admin_session` | session admin (onglet en cours) |

Pour repartir de zéro : dans l'admin → **Sauvegarde** → réinitialiser, ou videz le stockage du site dans les réglages du navigateur.

---

## 5. À personnaliser avant la mise en ligne

1. **Numéro WhatsApp** : admin → Contenu → `WhatsApp (indicatif + numéro, sans espaces)`, par exemple `212661234567`. Actuellement un numéro fictif `212600000000`.
2. **Téléphone, e-mail, adresse, horaires** : mêmes écran (affichés aussi sur le PDF).
3. **Photo d'accueil** : admin → Contenu → Bannière principale → **Changer la photo**.
4. **Frais de livraison** et **seuil de livraison offerte** (600 MAD par défaut).
5. **Réseaux sociaux** (Instagram, Facebook, TikTok).
6. **Photos produits** : remplacez les fichiers dans `assets/img/` en gardant les mêmes noms, ou changez le chemin de l'image dans la fiche produit.
7. **Mot de passe admin** (ligne 1518).

---

## 6. Notes techniques

- Bon de commande : PDF généré sans aucune bibliothèque (moteur interne du site), nommé `GY-YYYYMMDD-XXXX-guzel-yildiz.pdf`. Le message WhatsApp reste disponible en secours.
- Aucun cookie, aucun tracker, aucune requête externe.
- Accessibilité : contrastes, libellés ARIA, navigation clavier, `prefers-reduced-motion`.
- Testé sur Chrome / Edge, largeurs 390 px, 800 px et 1440 px.

---

## 7. Crédits photos

Photos libres de droits issues d'**Unsplash** et **Pexels**, téléchargées localement dans `assets/img/` (aucun hotlink).
Vous pouvez les remplacer par vos propres visuels : gardez simplement les mêmes noms de fichiers.
