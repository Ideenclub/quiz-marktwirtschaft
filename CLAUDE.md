# Regeln für dieses Repository

- **Fester Ort für alle Quizzes:** Das Repository `ideenclub/quiz-marktwirtschaft` ist der einzige Ort für alle Unterrichtsquizzes. Für Quizzes wird nie ein neues Repository angelegt.
- **Ein Angebot = ein Unterordner:** Gilt für Quizzes und Lernstrecken. **Bestehende Ordner nie umbenennen** (für die Live-Adressen gibt es gedruckte QR-Codes). Ein älteres Angebot im selben Ordner wird mit `git mv` in einen Unterordner verschoben (z. B. `<ordner>/quiz/`) und verlinkt.
- **Ein Quiz = ein Unterordner:** `<thema-in-kleinbuchstaben-mit-bindestrichen>/index.html` (keine Umlaute). Das Quiz ist eine einzige Datei: HTML, CSS und Vanilla-JavaScript inline, keine externen Abhängigkeiten (keine CDNs, Frameworks, Tracker, Cookies), Systemschrift, nur relative Pfade, Link „Alle Quizzes“ nach `../`.
- **Bei jedem neuen Quiz ergänzen:** die Übersichtsseite `index.html` im Hauptverzeichnis (Kachel fest im HTML, neuestes Quiz oben: Titel aus dem `<title>`, Klassenstufe, Datum) und die `README.md` (Liste mit Live-Links). `.nojekyll` bleibt im Hauptverzeichnis.
- **Live-URL-Schema:** `https://ideenclub.github.io/quiz-marktwirtschaft/<ordner>/`
- **Veröffentlichung immer so:** Branch → Pull Request → Squash-Merge in `main` → Pages-Check.
  1. Änderungen auf einem eigenen Branch committen und pushen.
  2. Pull Request gegen `main` erstellen und per Squash mergen (Branch danach löschen).
  3. GitHub Pages prüfen (`repos/ideenclub/quiz-marktwirtschaft/pages`): Quelle muss Branch `main`, Pfad `/` sein. Bei 404 aktivieren, bei falscher Quelle per PUT korrigieren.
  4. Bis zu 10 Minuten alle 30 Sekunden die Live-URL abfragen, bis sie 200 liefert und der Quiz-Titel im HTML steht; danach die Übersichtsseite prüfen.
  5. Live-Seiten einmal mit Playwright im iPad-Format öffnen und auf Konsolenfehler prüfen.
  - Hinweis für Cloud-Sitzungen: Ist `gh` nicht angemeldet, Pull Request und Merge über die GitHub-MCP-Werkzeuge erledigen. `*.github.io` kann dort vom Netzwerk gesperrt sein; dann `has_pages` über `https://api.github.com/repos/ideenclub/quiz-marktwirtschaft` und die Actions-Läufe „pages build and deployment“ prüfen.
- **Fotos:** liegen als JPEG in `<ordner>/img/` (max. 1600 px breit, max. ca. 350 KB). Sind Bild-Server aus der Sitzung gesperrt, die Quelle in `<ordner>/img/quellen.txt` eintragen (`dateiname.jpg URL`) und pushen: Der Workflow `.github/workflows/bilder-laden.yml` lädt, verkleinert und committet die Fotos in den Branch. Bildnachweise auf einer eigenen Seite und auf der Lehrkraftseite. Keine Buchmaterialien (Texte, Grafiken, Karikaturen) übernehmen, nur Seite und Materialnummer nennen.
- **Lehrkraftseite:** `<ordner>/lehrkraft.html`, von der Schülerseite nicht verlinkt (Ablauf, Codes, Lösungen, Erwartungshorizonte, Lehrplanbezug, Bildnachweise).
- **Vor dem Veröffentlichen testen (Pflicht):** lokal `python3 -m http.server` im Hauptverzeichnis, Playwright (Chromium) im iPad-Format 820×1180 (hochkant) und 1180×820 (quer): keine Konsolenfehler, kein horizontales Scrollen, automatischer Komplettdurchlauf (einmal alles richtig, einmal alles falsch inkl. Nochmal-Runde und Neustart), Prüfung, dass jede Aufgabe genau eine eindeutige Lösung hat, Screenshot je Aufgabentyp ansehen.
- **Zielgruppe:** Gesamtschule NRW, Lerngruppen eher leistungsschwach (kurze Sätze, Fachbegriffe erklären, Du-Form, keine Emojis). Spielgerät: iPad (Safari), alles per Tippen, kein Drag-and-drop, Tippflächen mindestens 52 px, Schrift mindestens 18 px.
- **Inhalte:** nur geprüfte Fakten und die von der Lehrkraft vorgegebenen Zahlen verwenden, nichts erfinden.
