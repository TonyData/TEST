# AmbiguousMines

Jeu autonome pour Qualtrics base sur le demineur, mais avec un niveau eleve d'ambiguite.

Differences avec le demineur classique:

- aucun compteur total de mines n'est affiche;
- aucun chiffre n'indique les mines adjacentes;
- une case sure revelee affiche `OK`;
- le score affiche seulement `Risque ?`, le temps et le nombre de coups.

## URL GitHub Pages

```text
https://tonydata.github.io/TEST/AmbiguousMines/index.html
```

## Exemple iframe Qualtrics

```html
<iframe
  src="https://tonydata.github.io/TEST/AmbiguousMines/index.html?rows=8&cols=8&mines=10&seed=${e://Field/ResponseID}&lock=1&compact=1"
  style="width:100%; max-width:720px; height:620px; border:0;"
  title="AmbiguousMines"
></iframe>
```

## Parametres

- `rows`: nombre de lignes, de 5 a 16.
- `cols`: nombre de colonnes, de 5 a 16.
- `mines`: nombre de mines, non affiche au participant.
- `seed`: graine deterministe, utile avec `${e://Field/ResponseID}`.
- `lock=1`: masque les boutons de format.
- `compact=1`: mode compact pour iframe.

## Evenements postMessage

La page emet des messages avec:

```js
source: "qualtrics-ambiguous-mines"
```

Evenements:

- `ready`
- `playing`
- `complete`
- `lost`

Champs de `summary`:

- `rows`
- `cols`
- `mines: null`
- `revealed`
- `flags`
- `moves`
- `elapsedSeconds`
- `seed`
- `status`
