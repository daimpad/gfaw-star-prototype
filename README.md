# Klickbares Mockup (statischer Build)

Fertig gebauter, **klickbarer UI-Prototyp** des neuen STAR-Frontends — **nur Mock-Daten, kein Backend, keine echten Daten**. Gedacht zum schnellen Testen/Zeigen ohne Entwicklungsumgebung.

## Öffnen

**`index.html` im Browser öffnen (Doppelklick) — fertig.** Alles (JS + CSS) steckt in dieser einen Datei; sie funktioniert direkt über `file://`, ohne Server und ohne Installation.

## Was ist drin

Login/Rollenwahl (Kunde/Auditor/Admin) · Übersicht · STAR ausfüllen (Live-Stern, Bearbeitungsstand, KI-Vorschlag lokal) · **Bericht-Import (CSRD/VSME)** mit Zuordnungs-Vorschlägen · Stern-Grafik (echte 6 CSE-Rubriken + Regler) · Audit (5 Bewertungen, 3 Prüfmethoden, Abweichungs-Banner, Abschluss-Fluss) · Controlling/CO₂ (Mock-Charts) · Bericht-Vorschau · **Firmenprofil** (Unternehmensart + Vollzeitstellen).

## Aktualisieren

Der Build stammt aus [`cse-star-app/`](../cse-star-app/) (Single-File-Build, weil Browser ES-Module über `file://` blockieren):

```bash
cd cse-star-app
npm run build:prototype
cp dist/index.html ../prototype/index.html
```
