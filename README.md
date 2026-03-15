# Ferienwohnung Alpenstraße 8 — Dresden

Statische Website für die Ferienwohnung der Familie Schuster in Dresden Oberloschwitz.  
Gebaut mit [Revela](https://revela.website/) und dem **Panorama**-Theme.

## Funktionen

- **Verfügbarkeitskalender** — Automatisch aus booking.com iCal-Feed generiert
- **Responsive Bilder** — Automatische Größenanpassung und Formatkonvertierung
- **Dark Mode** — Automatisch basierend auf Systemeinstellung
- **Kein JavaScript** — Rein statisches HTML + CSS, CSS-only Lightbox
- **SEO** — Individuelle Meta-Descriptions, Open Graph Tags, Sitemap

## Architektur

```
source/                     Inhalte (Markdown + Frontmatter)
├── _index.revela           Homepage
├── _images/                Bilder (werden von Revela verarbeitet)
├── _static/                Statische Dateien (Favicon, robots.txt)
├── 01-07 */                Inhaltsseiten
│   └── _index.revela
themes/
└── Panorama/               Eigenes Theme
    ├── Layout.revela        Seitenlayout
    ├── Body/                Body-Templates (Home, Page, Calendar)
    ├── Partials/            Wiederverwendbare Teile
    ├── Assets/main.css      Styling
    └── Configuration/       Theme-Konfiguration
```

## Lokal entwickeln

[Revela](https://github.com/Spectara/Revela/releases) herunterladen, dann:

```bash
revela plugin install Spectara.Revela.Plugins.Calendar
revela plugin install Spectara.Revela.Plugins.Source.Calendar
revela plugin install Spectara.Revela.Plugins.Serve

revela source calendar fetch
revela generate all
revela serve
```

## Deployment

Die Seite wird automatisch über GitHub Actions generiert und auf GitHub Pages veröffentlicht.

- **Bei jedem Push** auf `main`
- **Alle 6 Stunden** (Kalender-Aktualisierung aus booking.com)
- **Manuell** über den Actions-Tab

## Kalender

Die Belegungsdaten kommen aus einem booking.com iCal-Feed.  
Das [Calendar-Plugin](https://github.com/Spectara/Revela) für Revela parst den Feed und erzeugt einen 12-Monats-Kalender mit Anreise-/Abreise-Diagonalen.

## Lizenz

Inhalte und Bilder: © Familie Gottfried Schuster  
Theme und Code: MIT
