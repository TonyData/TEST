# RiskAmbiguity

Jeu Demineur autonome pour integration Qualtrics.

## Fichier principal

- `RiskAmbiguity/index.html`

## Parametres d'URL

- `rows`: nombre de lignes, de 5 a 16.
- `cols`: nombre de colonnes, de 5 a 16.
- `mines`: nombre de mines.
- `seed`: graine deterministe, utile avec `${e://Field/ResponseID}`.
- `lock=1`: masque les boutons de format.
- `compact=1`: mode compact pour iframe.

## Exemple iframe Qualtrics

```html
<iframe
  id="riskambiguity-frame"
  src="https://tonydata.github.io/TEST/RiskAmbiguity/?rows=8&cols=8&mines=10&seed=${e://Field/ResponseID}&lock=1&compact=1"
  style="width: 100%; max-width: 720px; height: 620px; border: 0;"
  title="RiskAmbiguity"
></iframe>
```

## Evenements `postMessage`

La page emet des messages avec `source: "qualtrics-minesweeper"` et un objet `summary`.

Evenements:

- `ready`
- `playing`
- `complete`
- `lost`

Exemple de listener Qualtrics:

```html
<script>
Qualtrics.SurveyEngine.addOnload(function () {
  window.addEventListener("message", function (event) {
    if (!event.data || event.data.source !== "qualtrics-minesweeper") return;
    var summary = event.data.summary || {};
    Qualtrics.SurveyEngine.setEmbeddedData("minesweeper_event", event.data.event);
    Qualtrics.SurveyEngine.setEmbeddedData("minesweeper_status", summary.status || "");
    Qualtrics.SurveyEngine.setEmbeddedData("minesweeper_elapsed", String(summary.elapsedSeconds || 0));
    Qualtrics.SurveyEngine.setEmbeddedData("minesweeper_moves", String(summary.moves || 0));
    Qualtrics.SurveyEngine.setEmbeddedData("minesweeper_revealed", String(summary.revealed || 0));
    Qualtrics.SurveyEngine.setEmbeddedData("minesweeper_flags", String(summary.flags || 0));
    Qualtrics.SurveyEngine.setEmbeddedData("minesweeper_seed", summary.seed || "");
  });
});
</script>
```

## Activer GitHub Pages

Dans GitHub: `Settings` > `Pages` > `Build and deployment` > `Deploy from a branch`.

Choisir:

- Branch: `main`
- Folder: `/ (root)`

L'URL devrait ensuite etre:

```text
https://tonydata.github.io/TEST/RiskAmbiguity/
```
