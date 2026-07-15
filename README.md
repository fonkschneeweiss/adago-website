# AdaGo Website

Statische Unternehmenswebsite der AdaGo GbR, gebaut mit Hugo Extended und veröffentlicht über GitHub Pages.

## Lokal starten

Voraussetzung: Hugo Extended in der in `.github/workflows/pages.yaml` verwendeten Version oder neuer.

```sh
hugo server --disableFastRender
```

Die lokale Vorschau läuft standardmäßig unter `http://localhost:1313`.

## Inhalte bearbeiten

- Startseite: `content/_index.md`
- Lösungen: `content/loesungen/`
- Branchen: `content/branchen/`
- Projekte: `content/projekte/_index.md`
- Team: `content/ueber-uns.md`
- Kontakt und Rechtliches: einzelne Dateien unter `content/`

Jede Inhaltsseite beginnt mit YAML-Frontmatter. `title`, `description`, `weight`, `kicker` und `outcome` steuern Darstellung und Reihenfolge. Neue Seiten lassen sich mit `hugo new loesungen/meine-loesung.md` anlegen.

## Design und Templates

- Layouts: `layouts/`
- Styles: `static/css/site.css`
- JavaScript: `static/js/site.js`
- Statische Dateien: `static/`

Es gibt kein externes Theme und keine JavaScript-Abhängigkeiten. Dadurch bleibt die Seite auch nach Hugo-Aktualisierungen überschaubar.

## Produktions-Build

```sh
hugo --minify --gc
```

Die Ausgabe landet in `public/` und wird nicht versioniert.

## Veröffentlichung

Pushes auf `main` starten den Workflow `.github/workflows/pages.yaml`. In den Repository-Einstellungen muss unter **Pages > Build and deployment** die Quelle **GitHub Actions** gewählt sein. Die Custom Domain ist `adago.org`; DNS-Einträge werden beim Domainanbieter gepflegt. `adago.cloud` sollte dauerhaft auf `https://adago.org` weiterleiten.

## Wartung

1. Inhalte als Markdown ändern und lokal prüfen.
2. `hugo --minify --gc` ausführen.
3. Änderungen per Pull Request prüfen und nach `main` übernehmen.
4. Vierteljährlich Links, Teamangaben und Datenschutzhinweise kontrollieren.
5. Hugo-Version im Workflow bewusst aktualisieren und den Build testen.
