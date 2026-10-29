# Page de vente — Anthony Sirius, premier client en 7 jours

Page de vente d'Anthony Sirius (SIRIUS LIFE, Digital Circle). Un seul objectif : le
formulaire. Un setter rappelle le lead dans les 10 minutes, puis lui ouvre l'espace membre.

Même structure et même logique que nos pages clients (JVJ, Marcus, Mexed, Maxence),
aux couleurs et aux polices d'Anthony (charte : `~/Desktop/design.md`).

```
index.html      la page (CSS et JS dans la page, sans build)
fonts/          Anton et Poppins en local (préchargées, font-display: swap)
img/            partage.png (Open Graph 1200 × 630) + photos d'Anthony à déposer
favicon.svg     carré rouge #AE0000 provisoire (Anthony n'a pas de logo)
vercel.json     URLs propres, liens courts /nom, noindex
captures/       captures ordi 1440 et mobile 390
A-COMPLETER.md  tout ce qui attend un contenu réel
```

## En local

```
python3 -m http.server 8197
```

puis http://localhost:8197. Les liens courts `/nom` ne marchent qu'une fois sur Vercel
(utiliser `?ref=nom` en local).

## Structure (celle de nos pages clients)

Bandeau rouge → hero (profil, badge « Nouveau », titre avec « en 7 jours. » en aplat
rouge, VSL 16:9 encadrée, CTA) → 3 chiffres → carte « Le constat » (lettre signée) →
carte d'offre « Ce que tu reçois » (Inclus + « le prix d'un resto ») → bandeau qui
défile → les 4 services → les 7 jours sur un rail qui se remplit → pour qui →
3 étapes → qui est Anthony (+ citation) → FAQ en cartes → carte finale rouge → pied de page.
Formulaire en modale (`#formulaire` dans l'adresse l'ouvre à l'arrivée), message
« C'est noté. » dans la modale après l'envoi. Barre fixe en bas sur mobile.

## Charte

| Rôle | Valeur |
|---|---|
| Rouge (seul accent) | `#AE0000` : aplats, boutons, étiquettes, numéros |
| Fond | `#050607` |
| Texte | blanc, secondaire en blanc à 68 % / 48 % |
| Cartes | blanc à 3,5 %, bord blanc à 10 %, rayon 4 px |
| Titres | Anton (à la place de Blackheat), capitales |
| Texte, boutons | Poppins 400 / 600 (à la place de Nexa) |

Les polices sont dans les variables `--font-display` et `--font-ui`. Si Anthony
fournit Blackheat et Nexa : les déposer dans `fonts/`, déclarer leurs `@font-face`
et les placer en tête de ces variables.

## Les photos

Déposer les WebP sous ces noms, la page les affiche toute seule :

| Fichier | Où | Format conseillé |
|---|---|---|
| `img/anthony-profil.webp` | pastille du hero + signature | carré, 256 × 256 |
| `img/anthony-constat.webp` | carte « Le constat » | portrait, 1000 px de large |
| `img/anthony-portrait.webp` | « Qui est Anthony » | portrait 4:5, 1000 × 1250 |

## Comment circule un lead (à brancher)

```
Tous les boutons « Je veux mon premier client »  →  modale du formulaire
        │  POST /rest/v1/leads avec la clé anon
        ▼
Table public.leads (schéma des templates)  →  setters
        │
        └──►  « C'est noté. » + Lead (Meta) / SubmitForm (TikTok)
```

Tout se règle en tête du script : `SUPABASE_URL`, `SUPABASE_ANON_KEY`, `PIXELS`,
`LIENS`, `VSL`, `HORAIRES`. Tant que Supabase est vide, le formulaire n'envoie rien
et le dit.

- `source` = `anthony-sirius` sur chaque lead.
- Suivi : `?ref=`, `?src=`, `/nom` et UTM retenus 30 jours. Sans colonnes dédiées
  (`COLONNES_SUIVI = false`), ils partent dans `page_url`.
- « Ta situation » : `COLONNE_SITUATION = true` une fois la colonne `situation` créée.
- Anti-spam : champ leurre `company`. Bouton bloqué pendant l'envoi.
- Hors horaires d'appel (`HORAIRES`), le message devient « On t'appelle dès … ».
