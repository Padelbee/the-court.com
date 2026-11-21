# SEO- & GEO-Audit – the-court.com

Stand: 21.11.2026 · Branch `seo-geo-optimierung` · Basis: Commit `d00393b` (live auf GitHub Pages)
Methode: statische Analyse aller HTML-Dateien im Repository (Python-Parser), Link-Prüfung, Sichtprüfung im Browser.
Lighthouse konnte noch **nicht** laufen: Auf diesem Rechner ist kein Node.js installiert (siehe offene Fragen).

---

## 1. Kurzfazit – die fünf größten Hebel

1. **Kerninhalte nur per JavaScript.** Die 25 Referenzen, die Projektkarte (50 Standorte), die Blog-Übersicht und der **komplette Text aller 20 Blogbeiträge** entstehen erst im Browser per JavaScript. Ein Crawler ohne JS (die meisten KI-Crawler) sieht auf jeder Beitragsseite 67 Wörter und eine **leere H1**. Das ist das größte GEO-Problem.
2. **Domain und Canonical passen nicht zusammen.** Alle Canonicals, `og:url` und die Sitemap zeigen auf `https://the-court.com/`. Die Website läuft aber unter `padelbee.github.io/the-court.com/`, weil `CNAME` und DNS noch nicht umgestellt sind. Solange das so ist, verweist jede Seite auf eine Adresse, unter der sie nicht erreichbar ist.
3. **Jede Seite wiegt 258–289 KB reines HTML.** Davon sind 121–141 KB Base64-Bilder (dieselben Logos 6–7× pro Seite, je ca. 9 KB, plus Partnerlogos im Script), 155–184 KB Inline-JavaScript (Kartendaten der DACH-Region und alle Funktionen auf jeder Seite) und 57 KB CSS. Jede Blog-Beitragsseite enthält zusätzlich die Daten aller 20 Beiträge.
4. **Veraltete Kopien der Website sind öffentlich erreichbar.** Unter `/media/` liegen eine alte Startseite, alte Blog-, Referenzen-, Impressums- und Datenschutzseiten, eigene `robots.txt`/`sitemap.xml`, eine README sowie `media/media/` als 28-MB-Duplikat aller Medien. Die Seiten sind indexierbar. Ihr Canonical zeigt zwar auf die echten Seiten, sie sind aber trotzdem Ballast und ein Risiko für Duplicate Content.
5. **Strukturierte Daten nur auf der Startseite.** Es gibt keine `WebSite`, keine `Service`-Einträge, keine `BreadcrumbList`, kein `BlogPosting` und kein `Event`. Dazu fehlen `llms.txt` und Regeln für KI-Crawler.

---

## 2. Seitenliste

Wörter = sichtbarer Text im statischen HTML innerhalb `<main>` (das sehen Crawler ohne JavaScript).
Bilder ohne width/height verursachen Layout-Verschiebungen (CLS).

| Seite | Title (Zeichen) | Description (Zeichen) | H1 | Wörter | Bilder (ohne w/h) |
|---|---|---|---|---|---|
| `/` | THE COURT by Padelbee · Padel-, Pickleball- & Tennisanlagen planen und bauen (**76**) | Projektentwickler und 360°-Plattform … (**180**) | „Wir bauen Padel.“ | 241 | 6 (6) |
| `/courts/` | Padel-Courts & Hallen · Hersteller, Varianten, Preise · THE COURT (**65**) | Standard, Panorama oder Full-Panorama … (**186**) | „Dein Court. Unsere Expertise.“ | 989 | 19 (19) |
| `/automaten/` | Schläger-Verleihautomaten & Verkaufsautomaten für Padel · THE COURT (**67**) | Verleih- und Verkaufsautomaten … (164) | „Mehr Service. Mehr Umsatz.“ | 933 | 10 (10) |
| `/referenzen/` | Referenzen · Padel- und Tennisprojekte · THE COURT (50) | Projekte von Padelbee und The Court … (171) | **keine H1** | 75 | 1 (1), Liste per JS |
| `/events/` | Events · Rafa Nadal Padel Tour und Messen · THE COURT (53) | Rafa Nadal Padel Tour 2026 … (**186**) | „Padel erleben.“ | 196 | 14 (14) |
| `/motions/` | Motions Racket Club - Joint Venture (35, **ohne Marke**) | Padel im Verein ohne eigene Investition … (148) | „Padel im Verein. 0 € Investition.“ | 130 | 0 |
| `/blog/` | Blog · Padel-Wissen für Vereine, Betreiber und Kommunen · THE COURT (**67**) | Kosten, Genehmigung … (135) | „Padel-Wissen.“ + **zweite, leere H1** | 67 | 1 (1), Liste per JS |
| `/blog/<beitrag>/` (20×) | `<Titel> · Blog · THE COURT` (42–**84**) | Teaser (**40–97**, zu kurz) | „Padel-Wissen.“ + **leere H1** | **67** | 1 (1), Text per JS |
| `/impressum/` | Impressum · THE COURT GmbH (26) | (67, zu kurz) | „Impressum.“ | 165 | 0 |
| `/datenschutz/` | Datenschutzerklärung · THE COURT GmbH (37) | (66, zu kurz) | „Datenschutz.“ | 574 | 0 |
| `/404.html` | identisch mit Startseite | identisch | identisch | 241 | Kopie der Startseite mit `noindex` |

### Überschriften-Struktur (Auffälligkeiten)

- **Start:** Die H1 „Wir bauen Padel.“ enthält kein Suchbegriff-Signal außer „Padel“. Das Wort wechselt per JS zu Pickleball und Tennis, statisch steht nur „Padel.“. Die H2 sind überwiegend Slogans („Ready. Play.“, „Stark im Netzwerk.“, „Sehen statt lesen.“).
- **Courts:** Die Struktur ist gut (H2 Varianten → H3 Standard/Panorama/Full-Panorama, H2 Fundament, H2 Hallen). Die H1 „Dein Court. Unsere Expertise.“ enthält aber keinen Suchbegriff wie „Padel-Court“ oder „Padelhalle“.
- **Automaten:** Die Prozessschritte sind **H4 direkt unter H2** (Ebene übersprungen). Die H1 ist ein reiner Slogan.
- **Referenzen:** Es gibt keine H1. Seit der Zusammenlegung beginnt die Seite mit der H2 „Grenzenlos unterwegs.“ Am Seitenende steht eine leere H2 (Detail-Dialog).
- **Blog und Beitragsseiten:** Es gibt zwei H1, eine davon statisch leer. Die echte Beitragsüberschrift wird erst per JS gefüllt.
- **Mehrere Seiten:** Die H2 „Ready. Play.“ wiederholt sich als Abschluss auf Start und Automaten.

---

## 3. Technische Probleme

| # | Problem | Fundstelle | Wirkung |
|---|---|---|---|
| T1 | Referenzen, Projektkarte, Blog-Liste und Blogtexte nur per JS | `referenzen/`, `blog/`, `blog/*/` | Für KI-Crawler und teilweise Bing unsichtbar; leere H1 |
| T2 | Canonical/og:url/Sitemap auf `the-court.com`, Seite läuft auf github.io | alle Seiten | Indexierung unklar, bis die Domain live ist |
| T3 | Base64-Logos mehrfach pro Seite (121–141 KB) | Header, Footer, Partner, Karte | Kein Browser-Caching, großes HTML |
| T4 | 155–184 KB Inline-JS pro Seite, inkl. Karten-Geodaten auf jeder Seite | alle Seiten | Längere Parse-Zeit, schlechtere INP/TBT |
| T5 | Jede Blog-Beitragsseite enthält alle 20 Beiträge als JSON | `blog/*/` | 288 KB je Beitrag |
| T6 | Startseite: Intro-Video 3,3 MB mit `preload="auto"` und Autoplay ganz oben | `/` | Hoher Datenverbrauch, LCP-Risiko auf Mobil |
| T7 | Kein Bild hat `width`/`height` | alle Seiten | Layout-Verschiebungen (CLS) |
| T8 | Kein `fetchpriority` auf dem LCP-Element der Startseite, keine Font-Preloads | `/`, alle | LCP |
| T9 | Alle Bilder JPG/WebP ohne `<picture>`/`srcset`; Bilder bis 1600 px | alle | Zu große Bilder auf Mobil |
| T10 | Veraltete Website-Kopien unter `/media/` (index, blog, referenzen, impressum, datenschutz, 404, robots, sitemap, README) und `media/media/` (28 MB Duplikat) | `/media/` | Duplicate Content, Ballast |
| T11 | `404.html` ist eine Kopie der Startseite mit Canonical auf `/` | `404.html` | Soft-404-Signal; eigene 404-Seite fehlt |
| T12 | `og:image` überall `intro.jpg` (1280×720, nicht 1200×630); nur Blogbeiträge haben eigene Bilder | alle | Schwache Vorschauen beim Teilen |
| T13 | Titles > 60 Zeichen (Start, Courts, Automaten, Blog, 8 Beiträge); Descriptions > 155 (Start, Courts, Events, Referenzen) bzw. < 120 (Impressum, Datenschutz, alle Beiträge) | siehe Tabelle | Abgeschnittene Snippets |
| T14 | Titelschema uneinheitlich („·“ vs. „-“, Motions ohne Marke) | `motions/` | Markenkonsistenz |
| T15 | Visuelle Breadcrumbs vorhanden, aber ohne `BreadcrumbList` | Unterseiten | Keine Breadcrumb-Snippets |
| T16 | Blog-Übersicht verlinkt Beiträge nur per JS; Hauptseiten verlinken nicht in den Blog | `blog/`, alle | Beiträge nur über Sitemap auffindbar |
| T17 | Ungenutzter Admin-/Editor-Code auf `/referenzen/` | – | **Bereits erledigt** (Commit `d00393b`) |
| T18 | Defekte interne Links | – | **Keine gefunden** (alle relativen Links geprüft) |
| T19 | `robots.txt` erlaubt alles und verweist auf die Sitemap; keine expliziten KI-Crawler-Regeln; keine `llms.txt` | Root | GEO |
| T20 | Sitemap: 29 URLs mit `lastmod` (Blog mit echten Veröffentlichungsdaten) | Root | OK |
| T21 | `lang="de"`, `viewport`, `theme-color`, Favicons vorhanden; semantische Elemente `header`/`nav`/`main`/`footer` vorhanden | alle | OK |

---

## 4. Strukturierte Daten (JSON-LD) – Bewertung

**Vorhanden:** nur auf `/` (und als Kopie in `404.html`): ein `@graph` mit `Organization` + `ProfessionalService` (`@id: https://the-court.com/#org`). Darin stehen Name, alternateName (Padelbee, The Court by Padelbee), URL, E-Mail, Logo, Bild, Beschreibung, Adresse (Unterföhring), areaServed (DE, AT, CH), founder (Martin Gaffal, Stefan Möbius), sameAs (nur padelbee.de), knowsAbout und ein `OfferCatalog` mit Leistungen.

**Bewertung:** Die Basis ist solide und der Graph-Ansatz richtig. Es fehlen:
- **Kontakt:** `telephone`, `geo`, `legalName` (THE COURT GmbH), Handelsregister-Angaben.
- **Verknüpfung:** `WebSite` mit `publisher`; die Leistungen als eigene `Service`-Knoten mit `@id`, `provider` und `areaServed`.
- **Seitenbezogene Daten:** `BreadcrumbList` auf Unterseiten, `BlogPosting` (Autor, Datum, Bild) auf 20 Beitragsseiten, `Event` auf `/events/`, `Offer` mit Netto-Preisangaben, wo die Seite Preise nennt (Courts ab 27.000 €, Hallen ab 280 €/m², Automaten).
- **Beschreibung:** Sie nennt „Franchise“ und „360°-Plattform“ und weicht von der sichtbaren Startseiten-Beschreibung ab. Das braucht Entitätskonsistenz.
- **Duplikat:** `404.html` enthält denselben Organisationsgraphen.

---

## 5. Keyword-Mapping

**Wichtig:** Ich habe keinen Zugang zu Suchvolumen-Daten (Keyword Planner, Sistrix, Ahrefs). Die Zuordnung beruht auf der Suchintention. Die Priorisierung solltest du nach dem Livegang mit der Google Search Console überprüfen.

| Seite | Haupt-Keyword | Neben-Keywords | Lücke / Kannibalisierung |
|---|---|---|---|
| `/` | Padelanlage bauen | Padel Projektentwicklung, Padelplatz planen, Padel Tennis Pickleball Anlage, Padel Bayern / München | H1 und Title ohne „Padelanlage bauen“ |
| `/courts/` | Padel Court kaufen | Padelplatz bauen Kosten, Padel Court Preis, Panorama Court, Padelhalle bauen, Padel Halle Kosten pro m², Padel Court Fundament | Bündelt Courts, Hallen und Fundament: drei Intentionen auf einer Seite. Konkurriert mit den Blogbeiträgen 1, 6, 8, 9, 11 |
| `/automaten/` | Schläger-Verleihautomat Padel | Padel Automat, Verkaufsautomat Padel, Ballautomat, Smart Access Padel | Konkurriert mit den Blogbeiträgen 17–20 (gewollt als Ratgeber → Produktseite) |
| `/referenzen/` | Padelanlage Referenzen | Padel Tennisverein Projekt, Padelanlage Bayern | Inhalte nur per JS (T1) |
| `/motions/` | Padel im Tennisverein | Tennisplatz in Padelplatz umbauen, Padel Verein ohne Investition, Padel Pacht Verein | Konkurriert mit den Blogbeiträgen 13–16 |
| `/events/` | Rafa Nadal Padel Tour | Padel Turnier München, Padel Messe f.re.e | Der offizielle Name auf den Bannern lautet „Rafa Nadal **Academy** Padel Tour“ (offen seit 20.11.) |
| `/blog/` + Beiträge | jeweils eigenes Long-Tail-Keyword | z. B. „Was kostet eine Padelanlage“, „Padel Court Fundament“, „Polycarbonat Padelhalle“, „Padel finanzieren“ | Beitragstexte nur per JS (T1) |

**Nicht abgedeckte Suchintentionen** (aus deiner Liste):
- **„Pickleball Platz bauen“:** Pickleball wird nur erwähnt, es gibt keinen Inhalt dazu.
- **„Padel Förderung Verein“:** Es gibt keinen Inhalt dazu. Das Thema ist rechtlich heikel, also nur mit belegten Quellen.
- **„Tennisplatz in Padelplatz umbauen“:** nur im Blogbeitrag 14 angerissen.
- **„Indoor vs. Outdoor“:** fehlt.
- **Regionale Suchen (Bayern, Baden-Württemberg, Österreich):** keine Regionalseiten, obwohl die Projektkarte die Belege liefert.

---

## 6. Priorisierte Maßnahmen (Impact × Aufwand)

| Prio | Maßnahme | Impact | Aufwand | Phase |
|---|---|---|---|---|
| 1 | Domain live schalten (CNAME + DNS), damit Canonicals stimmen | sehr hoch | gering (du) | vorab |
| 2 | Blogtexte, Blog-Liste und Referenzen **statisch ins HTML** rendern (das Generator-Skript schreibt den Text direkt ins HTML, JS bleibt nur für Filter/Galerie) | sehr hoch | mittel | 1/4 |
| 3 | Eine H1 pro Seite mit Suchbegriff (optisch identisch), H-Hierarchie korrigieren (Referenzen, Blog, Automaten-H4) | hoch | gering | 1 |
| 4 | Titles/Descriptions neu (≤ 60 / 140–155 Zeichen), Titelschema vereinheitlichen | hoch | gering | 1 |
| 5 | JSON-LD-Graph: WebSite, Service-Knoten, BreadcrumbList, BlogPosting, Event, Offer (nur echte Preise) | hoch | mittel | 2 |
| 6 | Base64-Logos als Dateien auslagern (cachebar), Inline-JS/CSS in gemeinsame Dateien (`/media/site.css`, `/media/site.js`) | hoch | mittel | 1 |
| 7 | Startvideo: `preload="metadata"` + Poster, `fetchpriority="high"` für das LCP-Element, width/height für alle Bilder | mittel | gering | 1 |
| 8 | `/media/`-Altlasten und `media/media/` (28 MB) löschen, eigene 404-Seite | mittel | gering | 1 |
| 9 | `robots.txt` mit KI-Crawler-Regeln, `llms.txt`, `llms-full.txt` | mittel | gering | 4 |
| 10 | Kurz-Zusammenfassung nach jeder H1 (Wer, Was, Für wen, Wo), einheitliche Definition „THE COURT ist …“ | mittel | gering | 4 |
| 11 | FAQ-Blöcke pro Hauptseite (5–8 Fragen) + `FAQPage` | mittel | mittel | 3 |
| 12 | Eigene og:images 1200×630 pro Hauptseite | mittel | gering | 1 |
| 13 | Interne Verlinkung Ratgeber ↔ Leistungen ↔ Referenzen | mittel | gering | 3 |
| 14 | Neue Ratgeberseiten (Kosten, Padel im Tennisverein, Ablauf, Indoor/Outdoor, Fundament) und Regionalseiten | mittel–hoch | hoch | 3 |
| 15 | `<picture>` mit WebP/AVIF + `srcset` | mittel | mittel | 1 |
| 16 | Team/Über-uns mit Profilen der Geschäftsführer (E-E-A-T) | mittel | gering (Inhalte von dir) | 4 |

---

## 7. Offene Fragen vor Phase 1

1. **Domain:** Wann wird the-court.com auf GitHub Pages umgestellt? Bis dahin zeigen alle Canonicals ins Leere. Ich lasse sie auf `the-court.com`, wie im Briefing vorgegeben.
2. **Anrede auf der Joint-Venture-Seite:** Laut Briefing bleibt dort „Sie wie bisher“. Seit dem 21.11. ist die Seite auf deinen Wunsch aber in Du-Form („Wir sind mit unseren Kunden per Du“). Ich lasse sie in Du-Form, außer du sagst etwas anderes.
3. **Löschen der Altlasten:** Darf ich die alten Kopien unter `/media/` (index.html, blog/, referenzen/, impressum/, datenschutz/, 404.html, robots.txt, sitemap.xml, README.md) und `media/media/` (28 MB) entfernen? Laut Prüfung verlinkt keine aktuelle Seite darauf.
4. **KI-Crawler:** GPTBot, CCBot, Google-Extended und Applebot-Extended sammeln auch **Trainingsdaten**, nicht nur Suchinhalte. Sollen alle ausdrücklich erlaubt werden, wie im Briefing, oder nur die Such-Crawler (OAI-SearchBot, PerplexityBot, Claude-SearchBot …)?
5. **Daten für JSON-LD und E-E-A-T** (sonst setze ich `[TODO]`):
   - Telefon für das Schema: +49 151 18175125 aus dem Impressum. Darf die Nummer rein?
   - Geokoordinaten der Adresse
   - URLs für `sameAs` (LinkedIn, Instagram, Northdata …)
   - Kurzprofile der Geschäftsführer Martin Gaffal und Stefan Möbius
6. **Lighthouse:** Für Vorher/Nachher-Werte brauche ich Node.js. Darf ich es installieren (winget, ca. 30 MB)? Alternativ messe ich nach dem Livegang mit PageSpeed Insights im Browser.
