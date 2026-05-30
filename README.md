# ⚡ Elektro-Lernwerkstatt

Interaktive **Single-File-Lernsoftware** (Deutsch) für den Elektrotechnik-Unterricht am Berufskolleg.
Themen: **Stromstärke (I)**, **Spannung (U)**, **Widerstand (R)** und **Leistung (P)** – inklusive Arbeit/Energie (W) und Wirkungsgrad (η).

Lehrkräfte gestalten Aufgaben, Schüler:innen lösen sie interaktiv: **messen** (virtuelles Multimeter), **rechnen** und das Ergebnis **per Simulation und Musterlösung** kontrollieren.

🔗 **Live:** https://cmonebk.github.io/BK-E-Plan/

---

## Inhalt

- [Highlights](#highlights)
- [Schnellstart](#schnellstart)
- [Bedienung](#bedienung)
  - [Schülermodus](#schülermodus)
  - [Lehrkraftmodus](#lehrkraftmodus)
- [Aufgaben an Schüler:innen verteilen](#aufgaben-an-schülerinnen-verteilen)
- [Dateiformate](#dateiformate)
- [Technik](#technik)
- [Deployment](#deployment)
- [Lizenz & Credits](#lizenz--credits)

---

## Highlights

- **Eine einzige Datei** (`index.html`) – kein Server, kein Build, keine Installation. Funktioniert offline im Browser.
- **Vier Schaltungsarten:** Grundschaltung, Reihen-, Parallel- und gemischte Schaltung – mit **frei verschachtelbaren Gruppen**.
- **Physikalisch korrekte Simulation** über einen DC-Netzwerklöser (Modified Nodal Analysis). Offene Schalter, Auftrennstellen und parallele Zweige verhalten sich realistisch.
- **Virtuelles Multimeter:** Messspitzen selbst anlegen; zur Strommessung muss die Leitung selbst aufgetrennt werden – auch an „falschen" Stellen.
- **Animierter Stromfluss** im Schaltplan (Laufschrift-Effekt), Lampen leuchten bei Stromfluss.
- **Schritt-für-Schritt-Musterlösung** mit komplettem Rechenweg – auf Wunsch einblendbar.
- **Lösbarkeitsprüfung** im Editor: zeigt an, ob gesuchte Größen berechenbar (✓), nur messbar (🔧) oder nicht ermittelbar (✗) sind.
- **Freigabe-Gates:** Messen und Musterlösung können deaktiviert, zeitgesteuert oder nach erfolgreichen Teillösungen freigeschaltet werden.
- **Zufallsgenerator** für Widerstandswerte – optional beschränkt auf E24-Normwerte nach IEC 60062 (Farbcode).
- **Light- / Dark-Mode**, umschaltbar und gespeichert.
- **Verteilung an Schüler:innen** per Link, QR-Code, HTML-Datei oder E-Mail – mit gesperrtem Lehrkraftmodus.

---

## Schnellstart

1. `index.html` im Browser öffnen (Doppelklick genügt) **oder** die [Live-Version](https://cmonebk.github.io/BK-E-Plan/) aufrufen.
2. Oben rechts zwischen **Schüler** und **Lehrkraft** umschalten.
3. Im Lehrkraftmodus eine Aufgabe bauen → speichern → an Schüler:innen verteilen.

> Keine Abhängigkeiten, kein Internet nötig. Alle Daten bleiben lokal im Browser (`localStorage`).

---

## Bedienung

### Schülermodus

- **Aufgabe lesen** und den Schaltplan betrachten.
- **Messen:** Multimeter-Modus wählen (U / I / R) und die Messspitzen an geeignete Punkte des Schaltplans anlegen.
  Für die **Strommessung** muss die Leitung an der gewünschten Stelle selbst aufgetrennt werden.
- **Rechnen:** Die gesuchten Werte in die Eingabefelder eintragen. Die Formeln können von der Lehrkraft ein- oder ausgeblendet werden.
- **Kontrollieren:** „Antworten prüfen" wertet die Eingaben aus. Bei Bedarf die **Musterlösung** Schritt für Schritt einblenden (sofern freigegeben).
- **Pro-Frage-Hilfe** (💡) blendet die Lösung einer einzelnen Größe ein.

### Lehrkraftmodus

**Aufgaben-Builder:**
- Schaltungsart wählen (Grund/Reihe/Parallel/gemischt) oder automatisch erkennen lassen.
- **Bauteile** hinzufügen: Widerstand, Lampe, Motor, Heizelement, Signalgeber.
- **Schaltglieder:** Taster und Schalter (jeweils Schließer/Öffner) sowie Not-Aus.
- **Gruppen** beliebig verschachteln (Reihe/Parallel ineinander).
- Pro Bauteil festlegen, ob der **Widerstandswert angezeigt** wird.
- **🎲 Zufallswerte** pro Bauteil oder für alle – optional auf E24-Farbcode-Werte beschränkt.

**Aufgabenkonfiguration:**
- Gesamtspannung, Titel, Beschreibung, Zeitangabe (für Arbeit W) festlegen.
- **Gesuchte Größen** wählen – gesamt und pro Bauteil (U, I, R, P …).
- **Multimeter beschränken** auf erlaubte Messgrößen.
- **Formeln** in der Schüleransicht ein-/ausblenden.

**Freigabe-Gates** (für Messen und Musterlösung):
- `immer` / `deaktiviert`
- `nach Zeit` (einstellbare Bearbeitungszeit)
- `nach richtigen Teillösungen` (einstellbare Anzahl)
- `nach Zeit ODER Teillösungen`
- `nach Zeit UND Teillösungen`

**Werkzeuge:**
- **Lösbarkeitsprüfung:** zeigt, ob die gesuchten Größen aus den gegebenen/angezeigten Werten berechenbar sind (optional unter Berücksichtigung des Multimeters).
- **Musterlösungs-Vorschau:** zeigt den vollständigen Rechenweg für die gefragten Größen.

---

## Aufgaben an Schüler:innen verteilen

Im Lehrkraftmodus stehen mehrere Verteilwege bereit – jeweils mit **gesperrtem Lehrkraftmodus** auf Schülerseite:

- **Link** – die Aufgabe steckt im URL-Hash (`#elw=…&lock=1`).
- **QR-Code** – als Bild kopier- und herunterladbar (Rechtsklick).
- **HTML-Datei** – eigenständige Schülerversion mit eingebetteter Aufgabe.
- **E-Mail** – vorbereiteter Versandlink.

---

## Dateiformate

| Endung | Inhalt |
|---|---|
| `.bkeptask` | Eine einzelne Aufgabe (JSON) |
| `.bkepenvironment` | Die komplette Erstellumgebung / alle Aufgaben (ersetzend **oder** additiv ladbar) |

Beispielaufgabe: [`Messen-und-Berechnen.bkeptask`](Messen-und-Berechnen.bkeptask) – eine „Messen-dann-Rechnen"-Aufgabe (Spannungen messen, Leistung und Arbeit berechnen).

---

## Technik

- **Aufbau:** reines HTML + CSS + JavaScript in einer Datei, ohne externe Laufzeit-Abhängigkeiten.
- **Schaltungsmodell:** rekursiver Block-Baum (Reihe/Parallel/Blatt).
- **Zwei Löser:**
  - analytischer rekursiver Löser (`computeR` / `propagate`) für Design-Werte und Musterlösung,
  - allgemeiner **DC-Netzwerklöser** per *Modified Nodal Analysis* (`solveNetwork`, Gauß-Elimination) für beliebige Auftrennungen und offene Schalter.
- **Lösbarkeitsanalyse** über Constraint-Propagation (Fixpunkt aus Ohm'schem Gesetz + Reihen-/Parallelregeln).
- **Rendering:** SVG-Auto-Layout im VALIS-angelehnten Stil, CSS-Variablen-Theming, Marching-Ants-Stromfluss.
- **Persistenz:** `localStorage`; Export/Import als JSON.
- **QR-Codes:** eingebettete `qrcode-generator`-Bibliothek (MIT).
- **Zahlenformat:** deutsche Schreibweise, automatische Einheiten-Präfixe.

Schaltzeichen sind an das Projekt **VALIS** (Virtual Automation Logic and Industrial Simulator) angelehnt.

---

## Deployment

Gehostet über **GitHub Pages** (Repo `CmoneBK/BK-E-Plan`).

> ⚠️ Die Datei **muss** `index.html` heißen, damit GitHub Pages sie unter der Wurzel-URL ausliefert.

Änderungen committen und pushen genügt – Pages aktualisiert sich automatisch.

---

## Lizenz & Credits

- Eigenentwicklung für den Unterrichtseinsatz am Berufskolleg.
- Eingebettete QR-Code-Bibliothek: [`qrcode-generator`](https://github.com/kazuhikoarase/qrcode-generator) (MIT-Lizenz).
- Schaltzeichen-Vorlagen angelehnt an das VALIS-Projekt.
