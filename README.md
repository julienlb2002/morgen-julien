# Morgen, Julien

Persönliches Politik-Briefing im Story-Format. Erscheint montags, mittwochs und freitags um 7 Uhr.

## Aufbau

- `index.html`: die App (Story-Player, Design, Illustrationen)
- `data/edition.json`: die Inhalte der aktuellen Ausgabe plus Archiv. **Nur diese Datei ändert sich pro Ausgabe.**
- `manifest.webmanifest`, `sw.js`, `icons/`: machen die Seite zur installierbaren App mit Offline-Lesemodus
- `.github/workflows/notify.yml`: schickt bei jeder neuen Ausgabe eine Push-Nachricht über ntfy

## Ablauf einer Ausgabe

1. Eine geplante Claude-Aufgabe recherchiert und schreibt die neue Ausgabe in `data/edition.json`.
2. GitHub Pages veröffentlicht die Änderung automatisch.
3. Der Workflow `notify.yml` schickt die Benachrichtigung „Morgen, Julien – Ausgabe N ist da“. Ein Tipp darauf öffnet die App.

## Datenschema `data/edition.json`

```
{
  "current": {
    "edition": 1, "date": "JJJJ-MM-TT",
    "glance": [{"r": "de|eu|us|intl", "text": "…"}],
    "topics": [{
      "r": "de|eu|us|intl", "lead": true, "motif": "parliament|conflict|eu|summit|money|capitol|ballot|oil|globe|chart|megaphone|microphone|shield|gavel",
      "tags": ["…"], "title": "…", "figure": {"value": "…", "label": "…"},
      "paras": ["…"], "concepts": ["…"], "lens": "…", "question": "…",
      "sources": [{"name": "…", "url": "…"}]
    }],
    "poll": {"institute": "…", "date": "JJJJ-MM-TT", "n": 0, "prev": "TT.MM.", "source": "…",
             "parties": [{"id": "afd|union|gruene|spd|linke|bsw|fdp|sonst", "name": "…", "value": 0, "change": 0}],
             "coalitions": [{"name": "…", "parties": ["…"]}]},
    "dates": [{"date": "JJJJ-MM-TT", "r": "…", "label": "…"}]
  },
  "archive": []
}
```

## App auf dem Handy installieren (Android, Chrome)

1. Die Seite in Chrome öffnen.
2. Menü (⋮) → „Zum Startbildschirm hinzufügen“ bzw. „App installieren“.

## Benachrichtigungen

1. Die App **ntfy** aus dem Play Store installieren.
2. Den Kanal abonnieren, der im Workflow hinterlegt ist (Repository-Variable `NTFY_TOPIC` oder Standardwert in `notify.yml`).
3. Test: unter „Actions“ → „Push-Benachrichtigung bei neuer Ausgabe“ → „Run workflow“.
