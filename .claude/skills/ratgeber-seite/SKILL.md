---
name: ratgeber-seite
description: Use when creating or updating a Nachklang SEO Ratgeber page under marketing/website/ratgeber/, or when asked to draft a new guide/checklist article for nachklang.app.
---

# Ratgeber-Seite (SEO Guide Page)

## Overview

Nachklang hat 17+ SEO-Ratgeber-Seiten (`marketing/website/ratgeber/<slug>/index.html`) nach einem festen, reinen HTML/CSS-Muster (kein Framework, kein Build-Step). Neue Seiten müssen exakt diesem Muster folgen, damit Optik, SEO-Struktur und interne Verlinkung konsistent bleiben.

**Kanonisches Referenzbeispiel:** `marketing/website/ratgeber/erste-schritte/index.html` — bei Unsicherheit immer diese Datei ansehen, nicht raten.
**Template-Skelett:** `template.html` in diesem Skill-Ordner (Platzhalter in `{{...}}`).

## Checkliste pro neuer Seite

1. **Slug & Pfad:** `marketing/website/ratgeber/<slug>/index.html` (Bindestrich-Slug, Thema-beschreibend, z.B. `testament-eroeffnen`)
2. **SEO-Kopf:** `<title>` im Format `{{H1}} – Ratgeber | Nachklang`, `<meta description>` (~160 Zeichen, konkretes Versprechen), `canonical` = `https://nachklang.app/ratgeber/<slug>/`, Open Graph Tags, Schema.org `Article` JSON-LD (`dateModified`/`datePublished` = heutiges Datum)
3. **CSS 1:1 übernehmen NUR aus der kanonischen Referenzdatei** `erste-schritte/index.html` — nicht aus anderen Ratgeber-Seiten kopieren. Mehrere bestehende Seiten haben eigene, leicht abweichende Zusatzklassen (z.B. `.warning-box`) eingeführt, die NICHT in der Referenzdatei stehen — diese sind Altlast, nicht Standard, und nicht übernehmen. Für Warn-/Pflichthinweise stattdessen `.tip-box` verwenden (steht in der Referenzdatei). Variablen `--beige` `#f9f6f1`, `--navy` `#1a1a2e`, `--gold` `#c9922a`, Fonts Cormorant Garamond (Headlines) + Source Sans 3 (Body). Klassennamen nicht neu erfinden.
4. **Seitenaufbau (fest, in dieser Reihenfolge):** Header (Logo + Zurück-Link) → Hero (H1 + Untertitel + Lesezeit/Datum) → PDF-CTA-Banner (nur falls im Zielordner bereits eine `checkliste-<slug>.pdf` existiert oder im selben Task neu erstellt wird — sonst Block komplett weglassen; das Erstellen einer neuen PDF-Checkliste ist ein separater Task und nicht Teil dieses Skills) → 1–3 `.section-block` mit `.step`-Elementen (nummerierte Schritte, optional `.tip-box`) → Ratgeber-Karten (`.ratgeber-grid`, Links zu 2–6 verwandten Themen) → Nachklang-CTA (`.cta-section`, Formspree-Formular, identisch auf allen Seiten) → Footer (identisch)
5. **Interne Verlinkung:** Neue Seite in den `.ratgeber-grid`-Karten ALLER bestehenden Seiten ergänzen, deren Thema direkt verwandt ist (typischerweise 1–3 Seiten, nicht nur die naheliegendste) bzw. vorhandene "Ratgeber folgt bald"-Platzhalter (`badge-soon`) durch einen echten Link auf die neue Seite ersetzen
6. **Rechtliche Pflichtregeln beachten**, sobald der Text Kündigungen/Vollmachten behandelt (siehe `/CLAUDE.md`): Sterbeurkunde ist Nachweis des Todes, KEINE Vollmacht; Absender immer "Erbe/Hinterbliebener", nie "Bevollmächtigter"; Hinweis "Kopie der Sterbeurkunde beilegen"; Sonderkündigungsrecht nur beim Mietvertrag (§580 BGB), sonst nur Kulanz
7. **DACH-Varianten:** Bei länderspezifischen Unterschieden (z.B. Standesamt-Prozess, GEZ vs. ORF vs. Serafe) im Text klar nach DE/AT/CH trennen statt zu vermischen

## Häufige Fehler

- CSS-Klassen umbenennen, Variablen-Werte leicht ändern, oder Zusatzklassen aus anderen (nicht-kanonischen) Seiten übernehmen → bricht visuelle Konsistenz
- Vollmacht statt Erbe/Hinterbliebener schreiben → rechtlich falsch, siehe CLAUDE.md
- Neue Seite erstellen, aber keine bestehende Seite darauf verlinken → Seite bleibt unauffindbar (kein internes Linkjuice, keine Navigation dorthin)
- Sonderkündigungsrecht für andere Verträge als Miete behaupten → nur Kulanz möglich, nicht Recht
