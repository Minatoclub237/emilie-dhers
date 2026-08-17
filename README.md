# Émilie Dhers — Décoratrice & architecte d'intérieur à Paris

Site vitrine d'une page, sans dépendance de build : `index.html` embarque le CSS
et le JavaScript, et `media/` porte les vidéos, photographies et icônes.

## Lancer en local

```bash
npx serve -l 5710 .
```

Puis http://localhost:5710

## Contenu

Contacts : **06 83 30 25 84** · **interieur-design@hotmail.fr** · Paris intra-muros,
petite couronne (92 · 93 · 94) et Île-de-France (77 · 78 · 91 · 95).

Grille tarifaire affichée sur le site, reprise de celle annoncée par le studio :
visite conseil 90 €/h remboursée dès lors que l'étude suit, étude à
80 / 60 / 50 / 40 €/m² selon la surface, suivi des artisans à 9 % du montant des
travaux. Tarifs HT.

## Sections

| # | Section | Mécanique |
|---|---|---|
| 001 | Hero | vidéo de fond |
| 002 | Deux métiers | apparition par mots |
| 003–005 | Se projeter | vidéo scrubbée au scroll |
| 006 | La méthode | quatre étapes, panneau synchronisé |
| 007 | Portrait | vidéo scrubbée + brouillage de texte |
| 008 | Prestations | deux colonnes défilantes |
| 009 | Le relevé | contre-parallaxe, tracés qui se dessinent, palette relevée dans les photos |
| 010 | La planche | convergence 3D depuis le fond, barre de palette proportionnelle |
| 011 | Réalisations | trois familles, panneau bento |
| 012 | Le devis | surface pilotée par le scroll, règle horizontale, calcul en direct |
| — | FAQ, contact, pied de page | |

## Points techniques à connaître avant d'intervenir

- **Vidéos scrubbées** : encodées avec une image-clé toutes les 15 images. Sans ce
  GOP court, le `seek` retombe sur la dernière clé et l'animation avance par
  paliers. Voir `portrait-scrub.mp4`.
- **Deux encodages par vidéo** : les cadres sont portrait sur desktop et paysage
  sur mobile. Les variantes `-m.mp4` / `-mobile.mp4` sont choisies par
  `matchMedia('(max-width: 760px)')`.
- **Boucles de scroll** : un `requestAnimationFrame` par section, armé par
  `IntersectionObserver`, avec `offsetTop` / `offsetHeight` mis en cache. Les lire
  dans la boucle force un recalcul de layout à chaque image.
- **Couleurs de la section 010** : extraites par k-moyennes des photographies
  elles-mêmes ; la largeur de chaque bande est la part de surface réelle de la
  teinte.

## À remplacer avant mise en production

- L'adresse de l'atelier (« communiquée au rendez-vous »).
- Les **photographies** : elles proviennent du portfolio publié par l'agence
  Créateurs d'intérieur, où Émilie Dhers exerce. Aucun projet n'y est crédité
  individuellement — à valider avec elle avant diffusion.
- La **section « avis clients »**, retirée du HTML faute de témoignages
  attribuables. Le carrousel se réactive dès que `#tm-track` et le tableau `AVIS`
  sont renseignés.
- Les pages **Législation & RGPD** et **Politique de confidentialité**, liées en
  pied de page mais pas encore écrites.
