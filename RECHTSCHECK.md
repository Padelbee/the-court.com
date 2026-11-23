# Rechtscheck the-court.com

Stand: 23.11.2026 · geprüft gegen den Leitfaden „Deine KI-Website – 10 Punkte“ (Stand 18.11.2026)

> Das ist keine Rechtsberatung, sondern eine technische Prüfung der Website gegen die Checkliste. Punkte mit „an Anwalt“ bitte in eine Beratung mitnehmen.

| # | Punkt | Status | Fundstelle / Nachweis |
|---|---|---|---|
| 1 | Impressum vollständig | **erfüllt** | `/impressum/`: Firma und Anschrift (keine Postfachadresse), Rechtsform GmbH, Vertretung durch beide Geschäftsführer, E-Mail und Telefon, Amtsgericht München HRB 314787, USt-IdNr. DE464043497, Verantwortlicher nach § 18 Abs. 2 MStV. Auf allen 62 Seiten (DE, EN, 404) mit einem Klick im Footer erreichbar. Gilt ausdrücklich auch für `/en/`. |
| 2 | Datenschutzerklärung mit jedem Tool | **erfüllt** | `/datenschutz/` nennt alle Datenverarbeitungen: Hosting (GitHub Pages), E-Mail (Microsoft 365), den Wechsel zu padelbee.de über die Anfrage-Buttons und externe Links. Es gibt keine weiteren Tools. Gilt ausdrücklich auch für `/en/`. **Bei jedem neuen Tool (Formular, Statistik, Karte, Video-Einbettung) muss die Erklärung ergänzt werden.** |
| 3 | Schriften vom eigenen Server | **erfüllt** | Inter und Caladea liegen unter `media/fonts/`. Keine Treffer für `fonts.googleapis.com` / `fonts.gstatic.com` in HTML, CSS und JS. |
| 4 | Cookie-Banner mit „Alles ablehnen“ | **nicht nötig** | Die Website setzt keine Cookies und nutzt weder localStorage noch sessionStorage. Es gibt kein Tracking und keine Inhalte von Drittservern (geprüft: alle `src`/`href`/`url()` in HTML, CSS und JS). Ohne Einwilligungspflicht nach § 25 TDDDG braucht es kein Banner. Kommt später Statistik oder Marketing dazu, wird ein Banner mit gleichwertigem „Alles ablehnen“ Pflicht. |
| 5 | Uploads privat | **nicht relevant** | Es gibt keine Upload-Funktion und kein Formular. Alle Dateien unter `media/` sind bewusst öffentliche Website-Inhalte. |
| 6 | Barrierefrei beim Online-Verkauf | **nicht verpflichtend, trotzdem erfüllt** | Das BFSG greift nicht, weil es keinen Online-Verkauf und keine Buchung für Verbraucher gibt (Angebot ausschließlich für Unternehmen, Vereine, öffentliche Hand). Trotzdem gilt: alle Bilder haben Alt-Texte (62 Seiten geprüft), Lighthouse „Barrierefreiheit“ 100 auf den gemessenen Seiten, Menüs, FAQ (`<details>`) und Buttons sind per Tastatur bedienbar. |
| 7 | Bilder nur mit Lizenz | **erfüllt** (Angaben der Geschäftsführung) | Bildnachweise im Impressum: eigene Fotos (Startseite, Rafa Nadal Padel Tour), Projektfotos eigene bzw. von den Betreibern freigegeben, Hersteller- und Produktbilder (Padel Factory, 100% Padel, Padel Concept, Sportogo, Pure Vending, Zuply), Hallenfotos Haltec, Partnerlogos mit Freigabe. Herstellerbilder sind auf `/courts/` zusätzlich als „Herstellerreferenzen, keine Projekte von THE COURT“ gekennzeichnet. **Die Freigaben von Herstellern, Betreibern und Partnern solltet ihr schriftlich ablegen.** |
| 8 | Keine erfundenen Bewertungen | **erfüllt** | Keine Sterne, Kundenstimmen oder Bewertungen auf der Seite, kein `aggregateRating` im JSON-LD. Alle Zahlen und Referenzen stammen aus euren Angaben. |
| 9 | Widerrufsbelehrung und Widerrufsbutton | **nicht relevant** | Kein Online-Verkauf an Verbraucher. Preise sind Richtpreise, Verträge entstehen über ein schriftliches Angebot. |
| 10 | Kündigungsbutton bei Abos | **nicht relevant** | Keine online abschließbaren Abos oder Dauerschuldverhältnisse für Verbraucher. Die monatlichen Grundgebühren der Automaten werden B2B über Angebot und Vertrag vereinbart. |

## An Anwalt (zur Absicherung)

- Formulierung der Partnerschaft „Offizieller Padel-Infrastrukturpartner des Bayerischen Tennis-Verbands“ (Werbeaussage, Wortlaut mit dem BTV abstimmen).
- Herstellerangaben wie Garantiezeiten und Windlasten sind mit „lt. Hersteller“ gekennzeichnet. Bitte prüfen, ob das als Abgrenzung reicht.
- Englische Seiten verweisen auf das deutsche Impressum und die deutsche Datenschutzerklärung. Bitte prüfen, ob für eure Zielgruppen eine englische Fassung gewünscht ist.

## Bei Änderungen erneut prüfen

Diese Checkliste gilt für den aktuellen Stand. Neu prüfen, sobald dazukommt: Kontaktformular, Newsletter, Statistik/Tracking, eingebettete Karten oder Videos (Google Maps, YouTube, Instagram), Online-Buchung oder Online-Shop.
