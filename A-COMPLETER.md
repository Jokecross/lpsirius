# À compléter — page Anthony Sirius

## Contenus d'Anthony

- [x] **Vidéo d’ouverture** : videos/vsl-sirius-02.mp4 (1080p, depuis « video 02 - final.mov » le 03/11) + img/vsl-affiche-02.webp. Cache 7 j : renommer le fichier si la vidéo change
- [x] Photo de profil → `img/anthony-profil.webp` (original dans `photos-brutes/`)
- [x] Photos « Le constat » (Porsche, villa) et « Qui est Anthony » (McLaren) → `img/` (originaux dans `photos-brutes/`). Contraires à la règle « pas de voiture » du brief, choix de Martin le 28/10 (la règle n'est pas dans design.md)
- [ ] **Chiffres réels** (abonnés, membres IA Money Club…) si on veut remplacer les 3 chiffres
      actuels, tirés du brief : 7 jours, 5 services, coach 24h/24
- [x] **Citation** : « Le premier client, c'est le plus dur. Après, tu sais faire. » (texte du brief), mention « à valider » retirée le 03/11 à la demande de Martin
- [x] **Son parcours** : rédigé le 03/11 à partir des faits connus (SIRIUS LIFE, IA Money Club, Skool Games 3x). À relire par Anthony
- [x] **FAQ « Combien de temps par jour ? »** : « Une à deux heures par jour pendant 7 jours. » (texte du brief)
- [ ] **Nom du programme**, s'il en a un (badge du hero « Programme 7 jours », étiquette du formulaire)
- [ ] **Polices Blackheat et Nexa** (.otf/.ttf), si elles existent → voir README
- [ ] Orthographe du lower-third : la charte relève « ANTONY SIRIUS » (sans H) sur un montage.
      La page écrit « Anthony ».

## Légal

- [x] Mentions légales, CGV, Confidentialité → `legal.html` (`/legal#mentions`, `#cgv`, `#confidentialite`), texte du PDF d'Anthony du 02/11/2026
- [x] Différences avec le PDF du 02/11, faites le 03/11 : hébergeur Vercel + Supabase, formulaire, appels enregistrés, espace membre, facture, durées (3 ans, 6 mois). Base44 reste nommé. À faire valider par Anthony et à reporter dans son PDF
- [ ] Purge à mettre en place : rien ne supprime encore les enregistrements après 6 mois ni les leads après 3 ans

## Branchements (plus tard)

- [ ] Projet Supabase → `SUPABASE_URL`, `SUPABASE_ANON_KEY` dans `index.html` (fait le 29/10), la réservation (`~/Reservation Sirius`), le CRM (`~/CRM Sirius`) et l'espace membre (`~/Espace Membre Sirius/.env`)
- [ ] Colonne `situation` (et colonnes `ref` + UTM si on veut `COLONNES_SUIVI = true`)
- [ ] Alertes Slack : nos templates n'en ont plus. Lesquelles ?
- [ ] Pixels Meta / TikTok → `PIXELS`
- [ ] Horaires d'appel des setters → `HORAIRES`
- [x] `og:image` en adresse absolue sur lpsirius.vercel.app (à changer si un domaine arrive)
- [ ] Lead de test marqué « test » dans le CRM + événement pixel vérifié
