# Phénix Bâtiment — Site vitrine

Site multi-pages statique (HTML/CSS/JS, sans dépendance ni build) pour Phénix Bâtiment — façade, ITE et rénovation.

## Structure

```
phenix-batiment/
├── index.html          Accueil (hero, diagramme ITE, services, réalisations, partenaires, CTA)
├── services.html        Détail des 3 services : Façade, ITE, Rénovation
├── realisations.html    Portfolio filtrable (Tout / Façade / ITE / Rénovation)
├── partenaires.html     Fournisseurs, partenaires, certifications
├── contact.html         Formulaire de contact + coordonnées + emplacement carte
├── devis.html           Simulateur de prix (Façade / ITE) + formulaire de demande de devis
└── assets/
    └── logo.png          Logo Phénix Bâtiment
```

Chaque page est autonome (CSS et JS intégrés dans le fichier), il n'y a donc rien à compiler : ouvrez simplement un fichier `.html` dans un navigateur, ou déployez le dossier tel quel.

## À personnaliser en priorité

Recherchez ces mentions dans les fichiers et remplacez-les par vos informations réelles :

- **Coordonnées** : adresse, téléphone, email → présents dans le pied de page de chaque fichier et sur `contact.html`
- **Carte** (`contact.html`) : encart "Carte à intégrer" → à remplacer par un `<iframe>` Google Maps ou OpenStreetMap une fois l'adresse confirmée
- **Photos de chantiers** (`index.html`, `realisations.html`) : blocs à motifs en attendant vos vraies photos
- **Logos partenaires et certifications** (`partenaires.html`) : encarts "Fournisseur A/B/C..." et "RGE / Qualibat / Assurance décennale" à remplacer par vos partenaires et numéros réels
- **Formulaires** (`contact.html`, `devis.html`) : fonctionnels côté design mais n'envoient rien pour l'instant. Pour recevoir réellement les messages, deux options simples :
  - un service comme [Formspree](https://formspree.io) ou [Web3Forms](https://web3forms.com) (ajout d'un `action="https://formspree.io/f/VOTRE_ID"` sur la balise `<form>`)
  - un petit backend (Netlify Forms, une fonction serverless, etc.)

## Simulateur de prix (`devis.html`)

Les tarifs indicatifs utilisés par le simulateur sont isolés en haut du `<script>` de `devis.html`, dans l'objet `PRICING` :

```js
const PRICING = {
  facade: {
    m2: [35, 55],        // €/m² de façade ravalée
    ouverture: [70, 95]  // €/ouverture (fenêtre, porte)
  },
  ite: {
    isolant: {
      pse:   [95, 120],
      laine: [115, 140],
      fibre: [135, 165]
    },
    ouverture: [100, 140]
  }
};
```

Modifiez ces chiffres pour refléter vos tarifs réels — aucune autre partie du code n'a besoin d'être touchée.

## Déploiement

Le site est 100% statique, il peut être hébergé gratuitement en quelques minutes sur :

- **Netlify** : glisser-déposer le dossier sur [app.netlify.com/drop](https://app.netlify.com/drop)
- **GitHub Pages** : dans les paramètres du dépôt GitHub → *Pages* → source = branche `main`, dossier `/ (root)`
- **Vercel** : `vercel` en ligne de commande depuis le dossier, ou import du dépôt GitHub sur [vercel.com](https://vercel.com)

Aucune variable d'environnement ni base de données n'est nécessaire.

## Prochaines évolutions possibles

- Connecter les formulaires à un vrai service d'envoi
- Ajouter de vraies photos de chantiers (avant / après)
- Ajouter un blog ou une page "Avis clients"
- Multilingue si besoin (structure HTML simple à dupliquer par langue)
