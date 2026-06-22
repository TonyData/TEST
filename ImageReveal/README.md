# ImageReveal

Jeu autonome pour Qualtrics: les repondants cliquent sur les cases pour faire apparaitre progressivement une image.

## URL GitHub Pages

```text
https://tonydata.github.io/TEST/ImageReveal/
```

## Exemple iframe Qualtrics

```html
<iframe
  src="https://tonydata.github.io/TEST/ImageReveal/?rows=8&cols=8&image=https://URL-DE-TON-IMAGE.jpg&seed=${e://Field/ResponseID}&lock=1&compact=1"
  style="width:100%; max-width:720px; height:620px; border:0;"
  title="ImageReveal"
></iframe>
```

## Parametres

- `image`: URL de l'image a reveler.
- `rows`: nombre de lignes, de 3 a 16.
- `cols`: nombre de colonnes, de 3 a 16.
- `seed`: identifiant participant ou graine, par exemple `${e://Field/ResponseID}`.
- `lock=1`: masque les boutons de format.
- `compact=1`: mode compact pour iframe.

## Evenements postMessage

La page emet des messages avec:

```js
source: "qualtrics-image-reveal"
```

Evenements:

- `ready`
- `playing`
- `complete`

Champs de `summary`:

- `rows`
- `cols`
- `total`
- `revealed`
- `moves`
- `elapsedSeconds`
- `seed`
- `status`
