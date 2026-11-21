# Content-Plan THE COURT – SEO & GEO

Stand: 21.11.2026 · Branch `seo-geo-optimierung` · Sprache: Deutsch, Du-Form

Ziel: Für die Fragen, die Betreiber, Vereine, Hotels und Kommunen vor einem Padel-Projekt stellen, soll the-court.com die beste deutschsprachige Antwort liefern. Das gilt für Suchmaschinen und für KI-Assistenten wie ChatGPT, Perplexity, Claude und Google AI Overviews.

Grundsätze:
- **Nur belegte Fakten:** Zahlen, Preise und Referenzen kommen von der Website, aus Herstellerangaben (gekennzeichnet mit „lt. Hersteller“) oder von dir. Fehlt eine Angabe, steht `[TODO]` da, nichts wird erfunden.
- **Antwort zuerst:** Der erste Satz beantwortet die Frage. Danach kommen Details, Tabellen und Links.
- **Keine Steuerberatung:** Steuerliche und bilanzielle Fragen verweisen immer auf den Steuerberater.
- **Stand-Datum:** Jede Seite mit Preisen nennt ein Stand-Datum.

## 1. Themen-Cluster und Zielseiten

| Cluster | Typische Suchanfrage / Prompt | Hauptseite (Pillar) | Unterstützende Seiten |
|---|---|---|---|
| Padelanlage bauen | „Padelanlage bauen Kosten“, „Was kostet ein Padelplatz?“ | Ratgeber [Padelanlage bauen: Kosten, Ablauf und Finanzierung](blog/padelanlage-bauen-kosten-ablauf-und-finanzierung/) | Blog 1, 2, 3, 8, 9; Start-FAQ |
| Padel-Courts | „Padel Court kaufen“, „Panorama vs. Standard“, „Padel Court Hersteller“ | [/courts/](courts/) | Blog 6, 7, 10; Courts-FAQ |
| Padelhalle | „Padelhalle bauen“, „Padelhalle Kosten pro m²“ | [/courts/#c-hallen](courts/#c-hallen) | Blog 11, 12 |
| Padel im Tennisverein | „Padel Tennisverein“, „Tennisplatz in Padelplatz umwandeln“ | Ratgeber [Padel im Tennisverein](blog/padel-im-tennisverein-der-leitfaden-fuer-vereinsvorstaende/) + [/motions/](motions/) | Blog 4, 13, 14, 15, 16; Motions-FAQ |
| Automaten & Digitalisierung | „Padel Schläger Verleihautomat“, „Padel ohne Personal“ | [/automaten/](automaten/) | Blog 17–20; Automaten-FAQ |
| Referenzen / Vertrauen | „Padelanlage Bayern“, „Padel Projektentwickler“ | [/referenzen/](referenzen/) | Referenzen-FAQ |
| Events | „Rafa Nadal Padel Tour Deutschland“, „Padel f.re.e München“ | [/events/](events/) | Events-FAQ |

## 2. Umgesetzt in Phase 3

- **FAQ-Blöcke** auf 6 Hauptseiten (Start, Courts, Automaten, Motions, Events, Referenzen), insgesamt 37 Fragen. Jede Antwort hat 40 bis 80 Wörter und beginnt mit der direkten Antwort. Der FAQ-Block steht sichtbar und ohne JavaScript im HTML. Dazu gibt es `FAQPage`-Schema mit identischem Wortlaut.
- **Zwei Ratgeber (Pillar-Seiten)** mit Tabellen, Stand-Datum, Steuerhinweis und internen Links:
  - *Padelanlage bauen: Kosten, Ablauf und Finanzierung*
  - *Padel im Tennisverein: der Leitfaden für Vereinsvorstände*
- **Interne Verlinkung:**
  - FAQ-Antworten → Ratgeber, Blogartikel, Unterseiten
  - 12 Blogartikel → passender Ratgeber
  - Ratgeber → Blogartikel und Hauptseiten
- **Blog-Renderer:** Er kann jetzt Tabellen und Links, als statisches HTML und im JavaScript.

## 3. Nächste Inhalte (Priorität)

| Prio | Thema / Titelvorschlag | Typ | Benötigte Fakten (TODO) |
|---|---|---|---|
| 1 | Referenz-Fallstudie: H30 Fitness & Padel / The Hall 68, Memmingen | Case Study | [TODO: Bauzeit, Eröffnungsdatum, Auslastung/Stimmen nur mit Freigabe des Betreibers] |
| 1 | Referenz-Fallstudie: Padel im Verein (z. B. TV Zellingen oder TC BW Neufahrn) | Case Study | [TODO: Projektdaten, Zitat nur mit Freigabe] |
| 2 | Padel-Court Maße und Platzbedarf | Ratgeber | [TODO: Außenmaße Court inkl. Sicherheitsabstand – aus Herstellerunterlagen] |
| 2 | Padel Förderung für Vereine | Ratgeber | [TODO: geprüfte Förderprogramme je Bundesland mit Quelle; nur mit Quellenangabe] |
| 2 | Padel-Court Lärmschutz | Ratgeber | [TODO: Gutachterwerte/Erfahrungen nur mit Quelle] |
| 3 | Pickleball-Anlage bauen | Ratgeber | [TODO: Pickleball-Maße, Preise, eigene Projekte] |
| 3 | Padel im Hotel – Praxisbeispiel | Case Study | [TODO: Hotelprojekt mit Freigabe] |
| 3 | Glossar Padel-Anlage (Panorama, Tragschicht, ThermoRoof …) | Glossar | aus bestehenden Seiten ableitbar |

## 4. Redaktionsrhythmus

- **Blogartikel:** 1 neuer Artikel alle 1–2 Wochen. Abwechselnd Courts/Hallen, Verein, Automaten und Referenzen.
- **Ratgeber:** 1 neuer Ratgeber pro Quartal. Preise und Stand-Datum werden quartalsweise geprüft.
- **Nach jeder neuen Referenz:**
  - Projekt auf /referenzen/ ergänzen
  - FAQ „Wie viele Projekte …“ und die Projektzahl prüfen
- **Preise:** Bei Preisänderungen der Hersteller oder Automatenpartner sind diese Stellen gemeinsam anzupassen:
  - Courts-Seite und Automaten-Seite
  - Ratgeber und FAQ
  - `scripts/faq_content.py` und `scripts/blog_posts.py`

## 5. So pflegst du die Inhalte

- **FAQ ändern:**
  1. `scripts/faq_content.py` bearbeiten.
  2. `python ../scripts/seo_faq.py` und `python ../scripts/seo_jsonld.py` im Repo ausführen.
- **Blogartikel/Ratgeber ändern:**
  1. `scripts/blog_posts.py` bearbeiten.
  2. Nacheinander ausführen: `add_blog_posts.py` → `seo_images.py` → `seo_jsonld.py` → `validate_jsonld.py`.
- **Markdown im Blog:**
  - `## ` / `### ` für Überschriften
  - `- ` für Listen, `1. ` für nummerierte Listen
  - `**fett**` für Hervorhebungen
  - `[Text](courts/)` für Links
  - `| a | b |` für Tabellen
