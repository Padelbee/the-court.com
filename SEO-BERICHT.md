# SEO- & GEO-Bericht – the-court.com

Stand: 21.11.2026 · Branch `seo-geo-optimierung` (8 Commits, nicht gepusht) · Vergleichsbasis: `main` = Commit `d00393b`

Ausgangslage und Befunde stehen in [SEO-AUDIT.md](SEO-AUDIT.md), der Redaktionsplan in [CONTENT-PLAN.md](CONTENT-PLAN.md) und die Maßnahmen außerhalb der Website in [GEO-EMPFEHLUNGEN.md](GEO-EMPFEHLUNGEN.md).

---

## 1. Ergebnis in Kürze

- **Crawler sehen jetzt alles.** Blogtexte, Blog-Übersicht, Referenzen, Projektkarte und FAQ stehen im statischen HTML. Vorher sah ein Crawler ohne JavaScript auf jeder Beitragsseite 67 Wörter und eine leere H1.
- **Seiten sind 4- bis 14-mal kleiner.** Das HTML schrumpft von 274–290 KB auf 21–73 KB. CSS, JS und Logos liegen jetzt als Dateien vor, die der Browser cacht.
- **Ein zusammenhängender JSON-LD-Graph auf allen 31 Seiten:** Organisation, Geschäftsführer, Leistungen, Preise (netto), Artikel, Event und FAQ. Er ist intern und mit validator.schema.org geprüft: 0 Fehler, 0 Warnungen.
- **Neue Inhalte für Suche und KI:** 37 FAQ-Antworten, 2 Ratgeber mit Tabellen, `llms.txt`, `llms-full.txt` und eine ausdrückliche Freigabe der KI-Crawler.
- **Design unverändert.** Bis zu den neuen Abschnitten ist jede Seite auf Desktop und Mobil pixelgleich gemessen. Geändert hat sich nur Text an vereinbarten Stellen: Einleitungen unter den H1, die Dachzeile auf Referenzen und das Stand-Datum.

---

## 2. Was umgesetzt wurde

| Phase | Commit | Inhalt |
|---|---|---|
| 0 | `a158023` | Audit (SEO-AUDIT.md) |
| 1 | `e9b8a37` | Gemeinsames CSS/JS und Logos als Dateien; Titles ≤ 60 und Descriptions 140–155 Zeichen; Canonical, Open Graph, Twitter; eigene og:images (1200 × 630) |
| 1 | `39a9fed` | Genau eine H1 pro Seite mit Suchbegriff; Blog und Referenzen statisch im HTML; eigene Snippets je Blogartikel |
| 1 | `00523d1` | Bildgrößen (width/height), WebP mit srcset, Preloads, Video-Preload; echte 404-Seite; Sitemap; Altlasten unter `/media/` gelöscht (u. a. 28 MB Duplikat) |
| 1 | `5baf693` | Kürzere Dachzeile auf Referenzen (mobil kein Umbruch); Blog-Script überschreibt Beitragstitel nicht mehr |
| 2 | `0c54a32` | JSON-LD-Graph über `@id` (Organization, WebSite, Person, Service, WebPage, BreadcrumbList, Product/Offer, BlogPosting, Blog, Event) |
| 3 | `4bf8ef3` | FAQ auf 6 Seiten + FAQPage-Schema; Ratgeber „Padelanlage bauen“ und „Padel im Tennisverein“; interne Verlinkung; CONTENT-PLAN.md |
| 4 | `42332c7` | robots.txt mit KI-Crawlern; llms.txt, llms-full.txt; Kurzfassungen unter den H1; Stand-Datum; GEO-EMPFEHLUNGEN.md |
| 5 | *dieser Commit* | QA: Referenzkarten valides HTML (`<article>` statt `<button>`); Kartenbilder auf /referenzen/ laden erst beim Scrollen; SEO-BERICHT.md |

---

## 3. Qualitätsprüfung (Phase 5)

### Lighthouse vorher/nachher

**Mobil** (vorher → nachher)

| Seite | Performance | Barrierefreiheit | Best Practices | SEO | LCP | CLS | Übertragung |
|---|---|---|---|---|---|---|---|
| Start | 73 → **85** | 100 → 100 | 100 → 100 | 100 → 100 | 5,7 s → **4,3 s** | 0,000 → 0,000 | 4,2 MB → 4,0 MB |
| Courts | 73 → **87** | 100 → 100 | 100 → 100 | 100 → 100 | 6,2 s → **3,8 s** | 0,000 → 0,000 | 1,1 MB → 539 KB |
| Automaten | 84 → **92** | 98 → **100** | 100 → 100 | 100 → 100 | 3,8 s → **3,2 s** | 0,012 → **0,000** | 578 KB → 413 KB |
| Referenzen | 86 → **96** | 100 → 100 | 100 → 100 | 100 → 100 | 3,4 s → **2,6 s** | 0,016 → **0,000** | 1,3 MB → 298 KB |
| Blogartikel | 75 → **92** | 100 → 100 | 100 → 100 | 100 → 100 | 5,3 s → **3,3 s** | 0,100 → **0,000** | 791 KB → 391 KB |

**Desktop** (vorher → nachher)

| Seite | Performance | Barrierefreiheit | Best Practices | SEO | LCP | CLS | Übertragung |
|---|---|---|---|---|---|---|---|
| Start | 97 → **99** | 100 → 100 | 100 → 100 | 100 → 100 | 1,1 s → **0,9 s** | 0,000 → 0,000 | 4,2 MB → 4,0 MB |
| Courts | 95 → **100** | 100 → 100 | 100 → 100 | 100 → 100 | 1,5 s → **0,8 s** | 0,000 → 0,000 | 1,9 MB → 766 KB |
| Automaten | 99 → **100** | 98 → **100** | 100 → 100 | 100 → 100 | 0,8 s → 0,8 s | 0,000 → 0,000 | 813 KB → 544 KB |
| Referenzen | 100 → 100 | 100 → 100 | 100 → 100 | 100 → 100 | 0,7 s → **0,6 s** | 0,014 → **0,008** | 4,5 MB → 940 KB |
| Blogartikel | 97 → **100** | 100 → 100 | 100 → 100 | 100 → 100 | 1,0 s → **0,7 s** | 0,086 → **0,000** | 791 KB → 391 KB |

Gemessen am 21.11.2026 mit Lighthouse 12 (headless Chrome) gegen lokale Server: vorher = `main` (d00393b), nachher = dieser Branch. Mobil mit simulierter Drosselung (langsames 4G, Mittelklasse-Smartphone). Auf der Live-Domain (HTTPS, CDN von GitHub Pages) fallen die absoluten Werte anders aus; der Vergleich vorher/nachher ist aussagekräftig. Die Übertragung auf Start bleibt hoch, weil das Intro-Video (3,3 MB) beim Autoplay geladen wird.

**In Phase 5 behoben:** Auf /referenzen/ luden alle 14 Kartenbilder sofort (4,5 MB mobil). Sie laden jetzt erst kurz bevor sie ins Bild scrollen (IntersectionObserver); für Crawler ohne JavaScript stehen die Bilder der statischen Karten in `<noscript>`.

### HTML-Validierung (html-validate, Regelsatz „standard“)

| | vorher (`main`) | nachher |
|---|---|---|
| Geprüfte Seiten | 30 | 32 |
| Fehler | 22 | 2 |

- **Die 2 verbleibenden Fehler** sind leere Bildvorlagen (`<img id="baCover">` auf `/blog/`, `<img id="rdImg">` auf `/referenzen/`). Das Script füllt sie erst beim Öffnen eines Artikels bzw. einer Referenz. Ohne Auswirkung auf Darstellung und Indexierung.
- **Ein Fehler aus Phase 1 wurde in Phase 5 behoben:** Die statischen Referenzkarten standen in `<button>`-Elementen, die keine Bilder und Blöcke enthalten dürfen. Sie sind jetzt `<article>`. Mit JavaScript werden sie wie vorher als anklickbare Karten dargestellt.

### Links

- 32 Seiten mit 1.808 internen Links und Sprungmarken geprüft: **0 defekte Links**.

### Strukturierte Daten

- **Interne Prüfung** (`scripts/validate_jsonld.py`, 31 Seiten):
  - alle `@id`-Verweise aufgelöst
  - Pflichtfelder vorhanden
  - Breadcrumb-Ziele existieren
  - Produkte haben Preise
  - **Ergebnis: keine Probleme.**
- **Externe Prüfung (validator.schema.org):** Courts (Organization, WebPage, Product, Service), Blogartikel (BlogPosting, BreadcrumbList) und Motions (FAQPage, Service): jeweils **0 Fehler, 0 Warnungen**.

### Sichtprüfung

- **Pixelgleich:** Seitenhöhe bis zu den neuen Abschnitten auf Desktop (1440 px) und Mobil (375 px) gemessen. Start, Courts, Automaten, Referenzen, Events, Motions und Impressum sind gleich wie vorher (±2 px Rundung).
- **Neue Abschnitte:** FAQ-Bereiche, Ratgeber-Tabellen und Referenzkarten im Browser geprüft. Kein horizontales Scrollen, keine Konsolenfehler.
- **Einleitungen unter der H1:** Courts und Automaten haben auf dem Desktop eine Textzeile mehr. Das ist eine bewusste Textänderung.

---

## 4. Offene TODOs

**Von dir zu liefern / zu entscheiden**

- [ ] **Push-Freigabe** für den Branch `seo-geo-optimierung` bzw. Merge in `main`. Danach baue ich das Artifact neu.
- [ ] **Domain umstellen** (CNAME/DNS auf the-court.com, laut dir innerhalb von 10 Tagen). Bis dahin zeigen Canonicals und Sitemap auf eine Adresse, die noch nicht erreichbar ist.
- [ ] **sameAs-Profile:** URLs von LinkedIn, Instagram, Facebook und YouTube der THE COURT GmbH.
- [ ] **Geschäftsführer-Profile:** Kurzbio, Foto und LinkedIn von Martin Gaffal und Stefan Möbius, für E-E-A-T und Person-Schema.
- [ ] **„3 Länder“:** Auf der Projektkarte gibt es keinen Standort in der Schweiz. Welches ist das dritte Land, oder soll die Angabe angepasst werden?
- [ ] **„+14 Jahre Padel-Erfahrung im Team“:** wem zuordnen?
- [ ] **Bayerischer Tennis-Verband:** offiziellen Wortlaut der Partnerschaft prüfen, ggf. Link setzen.
- [ ] **Rafa Nadal Padel Tour:** Termine der drei Tourstopps und den offiziellen Namen prüfen. Mit Datum ergänze ich Event-Schema.
- [ ] **Active Connected:** Termin, sobald bekannt.
- [ ] **Bildrechte** prüfen: Herstellerbilder auf /courts/ und Fotos auf der Startseite (`hero_*`), die jetzt auch als Titelbilder der Ratgeber dienen.

**Technisch offen (bewusst nicht gemacht)**

- [ ] **Critical CSS inline:** Das CSS ist ausgelagert (61 KB), aber nicht in kritisch/unkritisch aufgeteilt. Das bringt etwas LCP und wäre der nächste Performance-Schritt.
- [ ] **site.js (75 KB) aufteilen:** Die Kartendaten werden nur auf Start und Referenzen gebraucht, laden aber auf jeder Seite.
- [ ] **Leere Bildvorlagen** (2 HTML-Fehler) durch ein Platzhalterbild ersetzen.
- [ ] **Frage-Überschriften auf Hauptseiten:** bewusst nicht umgesetzt, weil die Slogans zum Markenauftritt gehören. Auf Wunsch formuliere ich sie um.
- [ ] **Motions-Dachzeile:** Sie wurde in Phase 1 zu „Padel im Tennisverein · THE COURT × Motions Racket Club“ geändert. Bitte freigeben oder zurücknehmen.
- [ ] **Google zeigt FAQ-Snippets** seit 2023 fast nur noch bei Behörden- und Gesundheitsseiten. Das Schema bleibt trotzdem sinnvoll für Bing, KI-Systeme und das Seitenverständnis.

---

## 5. Die nächsten 10 Schritte

1. **Freigabe und Push:** Branch prüfen und nach `main` mergen. Danach das Artifact neu bauen.
2. **Domain umstellen** und prüfen, ob `https://the-court.com/` mit HTTPS erreichbar ist und `padelbee.github.io/the-court.com/` weiterleitet.
3. **Google Search Console und Bing Webmaster Tools:**
   - Domain verifizieren
   - `sitemap.xml` einreichen
   - Indexierung der 31 Seiten beobachten
4. **Google-Unternehmensprofil** für die THE COURT GmbH anlegen bzw. abgleichen (Name, Adresse, Website, echte Projektfotos).
5. **sameAs und Personenprofile** liefern, ich ergänze JSON-LD und eine kurze „Über uns“-Sektion.
6. **Testprompts:** Die 20 Testprompts aus GEO-EMPFEHLUNGEN.md einmal als Ausgangswert durchlaufen und dokumentieren. Danach monatlich wiederholen.
7. **Referenzkunden und Partner** um einen Link auf the-court.com bitten (Betreiber, Hersteller, MRC, BTV, Messepartner).
8. **Zwei Fallstudien** aus den Referenzen schreiben (z. B. H30 Memmingen und ein Tennisverein), mit Freigabe der Betreiber.
9. **Performance:** Critical CSS und eine schlankere site.js ohne Kartendaten auf Unterseiten. Danach Lighthouse erneut messen, idealerweise auf der Live-Domain.
10. **Quartalsweise Pflege:** Preise und Stand-Daten prüfen und anpassen auf Courts, Automaten, in den Ratgebern, in den FAQs und in `llms.txt`.

---

## 6. Pflege und Skripte

Die Skripte liegen außerhalb des Repos in `crawlPaddelFinder/scripts/` und werden aus dem Repo-Ordner gestartet.

**Reihenfolge nach Inhaltsänderungen:**

1. `add_blog_posts.py`
2. `render_referenzen.py`
3. `seo_faq.py`
4. `seo_geo.py`
5. `seo_images.py`
6. `seo_jsonld.py`
7. `validate_jsonld.py` (Prüfung)

**Wo die Inhalte stehen:**

- FAQ-Texte: `faq_content.py`
- Blogartikel und Ratgeber: `blog_posts.py`
- Titles und Descriptions: `seo_meta.py`
