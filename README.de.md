[English](README.md) · [Türkçe](README.tr.md) · **Deutsch** · [Español](README.es.md)

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/logo-dark.png">
    <img src="assets/logo-light.png" alt="modsweep" width="460">
  </picture>
</p>

<p align="center"><b>Projekte aufräumen. Weiterbauen.</b><br>
<code>node_modules</code> in deinen JavaScript-Projekten finden, analysieren und sicher aufräumen — eine native macOS-App.</p>

<p align="center">
  <a href="https://github.com/caglarergul/modsweep-macos/releases/latest"><b>Neueste Version herunterladen</b></a>
  · macOS 14 Sonoma oder neuer · Apple Silicon und Intel
</p>

---

## Installation

**Download:** lade `modsweep-<version>.dmg` aus der [neuesten Version](https://github.com/caglarergul/modsweep-macos/releases/latest),
öffne sie und ziehe **modsweep** in **Programme**. Jede Version ist mit Developer ID signiert und von Apple notarisiert
und öffnet sich ohne Warnung.

**Homebrew:**

```bash
brew install --cask caglarergul/tap/modsweep   # installieren
brew upgrade --cask modsweep                   # aktualisieren
brew uninstall --cask --zap modsweep           # App und Daten entfernen
```

**Voraussetzungen:** macOS 14 Sonoma oder neuer. Zum Installieren von Projekten (Installieren & prüfen) wird
[pnpm](https://pnpm.io/installation) gebraucht; npm-, yarn- und bun-Projekte werden ebenfalls unterstützt.

## Was die App macht

| | |
|---|---|
| **Scannen** | Findet die JavaScript-Projekte in einem Ordner und zeigt, wie viel Platz jedes `node_modules` belegt, den Paketmanager, die letzte Aktivität und den git-Stand, dazu npm/pnpm/yarn/bun-Caches und freien Speicher. Die Summe steht in der Menüleiste. |
| **Analysieren** | Findet Installations- und Startprobleme, bevor sie auftreten — Lockfiles nicht synchron oder doppelt, abweichende Node-Versionen, `node-sass`, altes webpack auf neuem Node, Next 16 mit webpack-Konfiguration, Prisma, fehlende `.env`, Probleme mit Stencil-Shops … — und schlägt jeweils eine Lösung vor. |
| **Aufräumen** | Legt die ausgewählten `node_modules`-Ordner in den **Papierkorb**, von wo du sie zurückholen kannst. Ordner mit laufendem Node-Prozess oder von git verfolgten Dateien bleiben unangetastet. |
| **Teilen** | npm und yarn legen in jedes Projekt eine vollständige Kopie jedes Pakets. modsweep zeigt, welche Versionen sich in deinen Projekten wiederholen, und verschiebt die ausgewählten in **einen gemeinsamen pnpm-Store** auf diesem Mac, sodass jede Version nur einmal gespeichert wird. Nur zwei lokale Dateien kommen hinzu (in `.git/info/exclude` eingetragen): für git und dein Team ändert sich nichts. Jedes Projekt wird vorher gesichert und bei jedem Fehler zurückgesetzt, das alte `node_modules` wandert in den Papierkorb, und du kannst jederzeit zu npm/yarn zurück. Benötigt pnpm 10 oder neuer. |
| **Installieren & prüfen** | Installiert die ausgewählten Projekte und prüft Abhängigkeiten, Befehle, Typecheck, Build und optional einen Dev-Server — mit Live-Log, Stopp-Taste und anschließender Wiederherstellung. |

Verfügbar auf **English, Türkçe, Deutsch und Español** (Einstellungen → Sprache).

## Sicherheit

modsweep ist für echte Projekte gemacht, die an Live-Systeme angebunden sind.

- **Nichts wird gepusht oder deployt.** Skripte mit deploy, publish, push, migrate, vercel, shopify … laufen beim
  Test nie.
- **Datenbanken sind unerreichbar.** Datenbank-, Redis- und Mongo-Adressen aus `.env`-Dateien zeigen beim Test ins
  Leere.
- **Deine Dateien werden wiederhergestellt.** `package.json`, Lockfiles und der git-Stand werden vor dem Test
  gesichert und danach zurückgelegt — auch beim Stoppen.
- **Kein Prozess bleibt zurück.** Testserver werden über Prozessbaum und Ordner beendet.
- **Absturzsicher.** Bricht der Mac oder die App mitten im Test ab, stellt modsweep das Projekt beim nächsten Start
  wieder her, bevor es irgendetwas anderes tut.
- **Aufräumen landet im Papierkorb.** Die App löscht nichts endgültig.

## Erster Start

modsweep schlägt deinen Benutzerordner vor, scannt aber nichts von selbst. Wähle den Ordner mit deinen Projekten (zum
Beispiel `~/Developer` oder `~/www`) und starte den Scan. Ändern kannst du ihn jederzeit in der Seitenleiste oder in
den Einstellungen.

Kommen Node, pnpm oder andere Werkzeuge über nvm, asdf oder mise, füge ihren Ordner unter **Einstellungen →
Werkzeuge** hinzu.

## Datenschutz

modsweep hat kein Konto, keine Analyse und kein Tracking. Online geht die App nur, wenn du es willst: beim
Installieren von Paketen in Installieren & prüfen und bei der optionalen Stencil-Shop-Prüfung der Analyse (in den
Einstellungen abschaltbar).

## Deinstallieren

`brew uninstall --cask --zap modsweep`, oder modsweep aus Programme in den Papierkorb ziehen und
`~/Library/Application Support/modsweep` löschen.

## Haftungsausschluss

modsweep ist kostenlos und wird „wie besehen“ ohne Gewährleistung bereitgestellt. Es verändert Dateien auf deinem
Computer (Papierkorb, Paketinstallation, Builds); die Nutzung erfolgt auf eigenes Risiko. Sichere deine Projekte und
nutze eine Versionsverwaltung. Vollständiger Text: [Haftungsausschluss](DISCLAIMER.de.md).

---

Dieses Repository enthält nur die Release-Dateien; der Quellcode ist nicht öffentlich.

Copyright © 2026 Caglar Ergul. Alle Rechte vorbehalten.
