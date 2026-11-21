# GEO-Empfehlungen THE COURT

Stand: 21.11.2026 · Branch `seo-geo-optimierung`

GEO (Generative Engine Optimization) bedeutet: KI-Assistenten wie ChatGPT, Perplexity, Claude, Gemini, Copilot und die Google AI Overviews sollen THE COURT bei Fragen rund um Padelanlagen finden, richtig beschreiben und als Quelle verlinken.

## 1. Was auf der Website umgesetzt ist (Phase 1–4)

| Maßnahme | Wo | Wirkung |
|---|---|---|
| KI-Crawler ausdrücklich erlaubt | `robots.txt` | OpenAI, Perplexity, Anthropic, Google-Extended, Applebot-Extended, Bingbot und CCBot dürfen alle Seiten lesen |
| Kurzfassung für Sprachmodelle | `/llms.txt` | Definition, Eckdaten und alle wichtigen URLs mit Beschreibung |
| Volltext für Sprachmodelle | `/llms-full.txt` | Alle Hauptseiten, FAQ, Ratgeber und Blogartikel als Text (ca. 73.000 Zeichen) |
| Einheitliche Definition | Startseite, JSON-LD, llms.txt | „THE COURT ist ein Projektentwickler für Padel-, Pickleball- und Tennisanlagen in Deutschland, Österreich und der Schweiz …“ |
| Kurzfassung unter jeder H1 | Start, Courts, Automaten, Referenzen, Events, Blog (Motions hatte sie schon) | Der erste Absatz nennt THE COURT und beantwortet „Was ist das?“ |
| FAQ mit direkten Antworten | 6 Hauptseiten, 37 Fragen | Frage-Antwort-Paare, die KI-Systeme direkt zitieren können |
| Ratgeber mit Tabellen | 2 Pillar-Seiten | Vergleichbare Zahlen in Tabellenform, mit Stand-Datum |
| Stand-Daten | Automaten (10/2026), Courts (11/2026), Ratgeber (November 2026) | Aktualität ist erkennbar |
| JSON-LD-Graph | alle Seiten | Organisation, Personen, Leistungen, Preise, Artikel, Event, FAQ |
| Statische Inhalte | alle Seiten | Inhalte stehen ohne JavaScript im HTML (Blog, Referenzen, FAQ) |

### Bewusst nicht geändert

- **Frage-Überschriften auf den Hauptseiten:** Die H2-Headlines wie „Drei Varianten. Eine Entscheidung.“ gehören zum Markenauftritt und bleiben. Fragen als Überschriften stehen in den FAQ-Blöcken und in den Ratgebern. Wenn du willst, kann ich einzelne H2 umformulieren, z. B. „Welcher Padel-Court passt zu dir?“. Das wäre aber eine sichtbare Textänderung.
- **Personenprofile (E-E-A-T):** Ohne geprüfte Angaben schreibe ich keine Bios. Was fehlt, steht in Abschnitt 3.

## 2. Off-Page-Maßnahmen (außerhalb der Website)

KI-Systeme vertrauen Quellen, die an mehreren Stellen übereinstimmend genannt werden. Wichtig ist deshalb, was andere über THE COURT schreiben.

| Prio | Maßnahme | Details |
|---|---|---|
| 1 | **Google-Unternehmensprofil** anlegen bzw. pflegen | Name „THE COURT GmbH“, Adresse Unterföhring, Kategorie Sportanlagenbau/Projektentwicklung, Link auf the-court.com, Fotos echter Projekte. Bewertungen nur von echten Kunden, nie gekauft. |
| 1 | **LinkedIn-Unternehmensseite** + Profile der Geschäftsführer | Dieselbe Definition im „Info“-Text verwenden, Link auf the-court.com. Danach die URLs in `sameAs` im JSON-LD ergänzen. |
| 1 | **Bing Places + Bing Webmaster Tools** | Bing speist Copilot und teilweise ChatGPT. Sitemap einreichen. |
| 1 | **Google Search Console** | Domain verifizieren, Sitemap einreichen, Indexierung prüfen. |
| 2 | **Verbände und Partner** | Eintrag bzw. Verlinkung beim Bayerischen Tennis-Verband, bei Herstellern (Padel Concept, Padel Factory, 100% Padel …), beim Motions Racket Club, bei Scheck Club und bei den Messepartnern MPM GmbH / Sports Connected. Jeweils mit Link auf die passende Unterseite. |
| 2 | **Referenzkunden** | Betreiber bitten, auf ihrer Website „Anlage geplant/gebaut von THE COURT“ mit Link zu nennen. Mit Freigabe kurze Zitate für die Referenzen sammeln. |
| 2 | **Fachpresse und regionale Presse** | Pressemitteilungen zu Eröffnungen (z. B. Memmingen, Stuttgart), zur Rafa Nadal Padel Tour und zur f.re.e 2027. Online-Artikel mit Link sind für KI-Systeme besonders wertvoll. |
| 2 | **Branchenverzeichnisse** | Einheitliche Angaben (Name, Adresse, Telefon, Website) in Verzeichnissen wie Gelbe Seiten, Wer liefert was, Cylex und Sportstättenbau-Verzeichnissen. Überall dieselbe Schreibweise „THE COURT GmbH“. |
| 3 | **Wikipedia / Wikidata** | Wikipedia erst bei ausreichender unabhängiger Berichterstattung. Ein Wikidata-Eintrag mit Basisdaten ist früher möglich. |
| 3 | **YouTube** | Das Projektvideo und Baustellen-Zeitraffer mit beschreibendem Titel und Link zur Website hochladen. Transkripte werden von KI-Systemen gelesen. |
| 3 | **Fragen-Plattformen** | Fachlich antworten, wo Vereine und Betreiber fragen (z. B. Foren, LinkedIn-Gruppen). Transparent als THE COURT auftreten, keine verdeckte Werbung. |

### Nicht empfohlen

- Gekaufte Bewertungen, gekaufte Links und Linktausch-Netzwerke
- Automatisch erzeugte Massen-Inhalte
- Versteckter Text für Crawler (Cloaking)

## 3. Offene Punkte (TODO)

- [ ] **sameAs-URLs:** LinkedIn, Instagram, Facebook, YouTube der THE COURT GmbH, für JSON-LD und Footer
- [ ] **Geschäftsführer-Profile:** Kurzbio für Martin Gaffal und Stefan Möbius (Werdegang, Padel-Erfahrung, Rolle), Foto, LinkedIn-URL. Damit kann ich eine „Über uns“-Sektion und Person-Schema mit Expertise ergänzen.
- [ ] **„3 Länder“ prüfen:** Auf der Projektkarte stehen Standorte in Deutschland und Österreich, aber keiner in der Schweiz. Welches ist das dritte Land? Falls es keins gibt, sollten wir „3 Länder“ anpassen.
- [ ] **„+14 Jahre Padel-Erfahrung im Team“:** Wer im Team bringt diese Erfahrung mit? Sinnvoll für die Personenprofile.
- [ ] **Bayerischer Tennis-Verband:** den offiziellen Wortlaut der Partnerschaft prüfen und, wenn vorhanden, einen Link auf die BTV-Seite setzen.
- [ ] **Rafa Nadal Padel Tour:** Termine der Tourstopps und den offiziellen Namen prüfen. Danach kann ich Event-Schema ergänzen.
- [ ] **Active Connected:** Termin ergänzen, sobald er feststeht.

## 4. 20 Testprompts

Diese Fragen stellst du einmal im Monat in ChatGPT (mit Suche), Perplexity, Claude, Gemini und Copilot. Notiere jeweils:

- Wird THE COURT oder Padelbee genannt?
- Wird the-court.com verlinkt?
- Stimmen die Fakten?

Eine Vorlage für die Notizen steht unter der Liste.

**Marke und Anbieter**
1. Was ist THE COURT by Padelbee?
2. Welche Firmen planen und bauen Padelanlagen in Deutschland?
3. Wer baut Padel-Courts in Bayern?
4. Gibt es einen Projektentwickler für Padelanlagen in der Nähe von München?

**Kosten und Planung**

5. Was kostet eine Padelanlage mit vier Courts?
6. Was kostet ein Padel-Court in Deutschland?
7. Wie viel Platz braucht eine Padelhalle für vier Courts?
8. Was kostet eine Padelhalle pro Quadratmeter?
9. Welches Fundament brauche ich für einen Padel-Court?
10. Was ist der Unterschied zwischen Standard-, Panorama- und Full-Panorama-Padel-Courts?

**Tennisverein**

11. Wie kann ein Tennisverein Padel-Courts bauen, ohne selbst zu investieren?
12. Wie viele Padel-Courts passen auf einen Tennisplatz?
13. Was ist der Motions Racket Club?
14. Lohnt es sich, einen ungenutzten Tennisplatz für Padel zu verpachten?

**Automaten und Betrieb**

15. Wie kann ich Padelschläger ohne Personal verleihen?
16. Was kostet ein Schläger-Verleihautomat für eine Padelanlage?
17. Wie funktioniert eine automatische Lichtsteuerung für Padel-Courts über das Buchungssystem?

**Hersteller, Events, Referenzen**

18. Welche Padel-Court-Hersteller sind empfehlenswert und wie unterscheiden sie sich?
19. Wo macht die Rafa Nadal Padel Tour 2026 in Deutschland Station?
20. Welche Padelanlagen gibt es in Memmingen oder Stuttgart und wer hat sie gebaut?

### Vorlage für die Auswertung

| Datum | Prompt-Nr. | Tool | THE COURT genannt? | Link? | Fakten korrekt? | Notiz |
|---|---|---|---|---|---|---|
| | | | | | | |

**Ziel nach 3 Monaten:** THE COURT wird bei den Prompts 1, 11, 13 und 19 in mindestens 3 von 5 Tools genannt, bei Prompt 5–10 in mindestens 2 von 5.
