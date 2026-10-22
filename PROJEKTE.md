# 7 Tage Flutter & Dart – Projektplan

**Zeitraum:** 23. Oktober – 30. Oktober
**Ordnerstruktur:** `flutter-learning-journey/flutter-learning-journey/tagX_ProjektName`

Die Projekte bauen aufeinander auf: Jedes Projekt nutzt die Konzepte der vorherigen Tage und fügt neue hinzu. Der 30. Oktober ist als Puffer- und Abschlusstag eingeplant.

Bei jedem Projekt gibt es **Pflicht-Features** (das Lernziel des Tages) und **Bonus-Features** (wenn Zeit übrig ist). Die Hinweise unter „Brücke zu deinem Wissen“ verbinden die neuen Konzepte mit Sprachen, die du schon kennst.

---

## Tag 1 – 23.10. – `tag1_Visitenkarte`

**Thema:** Dart-Grundlagen & erstes UI mit Stateless Widgets

### Idee
Eine digitale Visitenkarte / Profilseite von dir: Profilbild, Name, Berufsbezeichnung, Kontaktdaten (Telefon, E-Mail, GitHub) und eine kurze Liste deiner Skills.

### Vorbereitung (vormittags)
- Flutter SDK installieren, `flutter doctor` ausführen, Emulator oder Chrome als Zielgerät einrichten
- Eine kleine Dart-Konsolenübung (`dart create`), um die Sprache isoliert kennenzulernen: Variablen (`var`, `final`, `const`), Typen, Null-Safety, Funktionen, Klassen, Listen und Maps

### Pflicht-Features
- Profilbild (aus einem lokalen Asset)
- Name und Titel mit eigenem Text-Styling
- Kontaktzeilen mit Icons
- Saubere Abstände und Ausrichtung

### Bonus
- Eigene Schriftart (Google Fonts)
- Skills als „Chips“ darstellen
- Eigenes Widget für eine Kontaktzeile extrahieren und wiederverwenden

### Lernkonzepte
- Projektstruktur (`lib/`, `pubspec.yaml`, Assets registrieren)
- `main()`, `runApp`, `MaterialApp`, `Scaffold`
- Widget-Baum-Denken: alles ist ein Widget
- Layout: `Column`, `Row`, `Container`, `Padding`, `SizedBox`, `Expanded`
- `StatelessWidget` und das Prinzip der Komposition
- Hot Reload

### Brücke zu deinem Wissen
Der Widget-Baum ähnelt dem DOM in HTML, Layout-Widgets verhalten sich ähnlich wie Flexbox in CSS. Dart selbst fühlt sich syntaktisch wie eine Mischung aus C# und JS an.

### Fertig, wenn …
… die Karte auf dem Emulator / im Browser gut aussieht und du erklären kannst, warum `const` bei Widgets sinnvoll ist.

---

## Tag 2 – 24.10. – `tag2_Punktezaehler`

**Thema:** Zustand (State) & Interaktion

### Idee
Ein Punktezähler für Brett- oder Kartenspiele. Mehrere Spieler, jeder hat einen Punktestand, der per Button erhöht oder verringert werden kann. Dazu ein Würfel-Button, der eine Zufallszahl anzeigt.

### Pflicht-Features
- Mindestens 2 Spieler mit Namen und Punktestand
- Plus- / Minus-Buttons pro Spieler
- „Zurücksetzen“-Button für alle Punkte
- Würfel mit zufälligem Ergebnis (1–6), optisch dargestellt

### Bonus
- Spieler dynamisch hinzufügen / entfernen
- Führenden Spieler farblich hervorheben
- Langes Drücken auf einen Button erhöht um 10
- Kleine Animation beim Würfeln (`AnimatedSwitcher` oder `AnimatedContainer`)

### Lernkonzepte
- `StatefulWidget` vs. `StatelessWidget`
- `setState` und der Rebuild-Zyklus
- Lebenszyklus eines States (`initState`, `dispose`)
- Buttons und Gesten (`ElevatedButton`, `IconButton`, `GestureDetector`)
- Daten über Konstruktor an Kind-Widgets übergeben, Callbacks nach oben reichen
- Eigene Dart-Klasse als Datenmodell (z. B. `Spieler`)
- `dart:math` für Zufallszahlen

### Brücke zu deinem Wissen
Das Muster „Daten runter, Events (Callbacks) hoch“ ist dasselbe wie bei React-Props. `setState` ist vergleichbar mit Reacts `useState`, nur klassenbasiert.

### Fertig, wenn …
… du erklären kannst, *wo* der Zustand liegt und warum er genau dort liegen sollte („Lifting State Up“).

---

## Tag 3 – 25.10. – `tag3_TodoListe`

**Thema:** Listen, Eingaben, Navigation

### Idee
Eine klassische Todo-App mit mehreren Screens: Übersicht aller Aufgaben, Detail-/Bearbeitungsseite und ein Formular zum Anlegen neuer Aufgaben.

### Pflicht-Features
- Liste von Aufgaben mit Titel, Beschreibung und Erledigt-Status
- Neue Aufgabe über ein Formular anlegen (mit Validierung: Titel darf nicht leer sein)
- Aufgabe abhaken, bearbeiten und löschen
- Navigation zu einer Detail-Seite und zurück, inklusive Rückgabe von Daten
- Bestätigungsdialog vor dem Löschen

### Bonus
- Wischen zum Löschen (`Dismissible`) mit „Rückgängig“ in einer `SnackBar`
- Filter: Alle / Offen / Erledigt
- Prioritäten oder Fälligkeitsdatum (mit `DatePicker`)
- Sortieren per Drag & Drop (`ReorderableListView`)

### Lernkonzepte
- `ListView.builder` und warum er performant ist
- `TextField`, `TextEditingController`, `Form`, `TextFormField`, Validatoren
- `Navigator.push` / `pop`, Daten zwischen Screens übergeben (async/await bei Navigation)
- Dialoge (`showDialog`) und `SnackBar`
- `Key`s bei Listen und warum sie wichtig sind
- Unveränderliche Modelle und `copyWith`-Muster

### Brücke zu deinem Wissen
`Navigator` funktioniert wie ein Stack von Seiten – ähnlich der Browser-History. Ein `TextEditingController` erinnert an Two-Way-Binding, musst du aber selbst verwalten und freigeben (`dispose`, vergleichbar mit `IDisposable` in C#).

### Fertig, wenn …
… die App sich wie eine „echte“ App anfühlt, aber die Daten beim Neustart noch verloren gehen – das lösen wir morgen.

---

## Tag 4 – 26.10. – `tag4_GewohnheitsTracker`

**Thema:** Lokale Persistenz, JSON & Theming

### Idee
Ein Habit-Tracker: Du legst Gewohnheiten an (z. B. „Wasser trinken“, „30 Min. lernen“) und hakst sie täglich ab. Die App zeigt Streaks (wie viele Tage am Stück) an. Baut direkt auf den Listen- und Formular-Kenntnissen von Tag 3 auf.

### Pflicht-Features
- Gewohnheiten anlegen, bearbeiten, löschen (Wissen von Tag 3)
- Pro Tag abhaken; Streak-Berechnung
- Alle Daten werden lokal gespeichert und überleben einen App-Neustart
- Light- und Dark-Mode, umschaltbar in einem Einstellungsscreen; die Auswahl wird ebenfalls gespeichert
- Einheitliches App-Design über ein zentrales `ThemeData`

### Bonus
- Wochenübersicht als Raster (7 Kästchen pro Gewohnheit)
- Farbe / Icon pro Gewohnheit wählbar
- Benannte Routen oder das Paket `go_router`
- Bottom Navigation Bar (Heute / Statistik / Einstellungen)

### Lernkonzepte
- Pakete einbinden über `pubspec.yaml` (`shared_preferences`)
- JSON-Serialisierung: `toJson` / `fromJson` von Hand, `dart:convert`
- `Future`, `async` / `await` erste Berührung (Laden beim Start)
- Umgang mit `DateTime`
- `ThemeData`, `ColorScheme`, `Theme.of(context)`
- Was ist `BuildContext` eigentlich?

### Brücke zu deinem Wissen
`shared_preferences` ist das Pendant zu `localStorage` im Browser. Dart-`Future` entspricht einem JS-`Promise` bzw. einer C#-`Task`.

### Fertig, wenn …
… du die App schließt, neu startest und alle Gewohnheiten, Häkchen und das gewählte Theme noch da sind.

---

## Tag 5 – 27.10. – `tag5_WetterApp`

**Thema:** Netzwerk, asynchrone Programmierung & Fehlerbehandlung

### Idee
Eine Wetter-App, die echte Daten aus dem Internet lädt. Empfehlung: die kostenlose **Open-Meteo API** (kein API-Key nötig). Suche nach Städten, aktuelles Wetter und eine 7-Tage-Vorhersage.

### Pflicht-Features
- Stadtsuche (Geocoding-Endpunkt von Open-Meteo)
- Aktuelle Temperatur, Wetterzustand (mit passendem Icon), Wind
- 7-Tage-Vorhersage als horizontale oder vertikale Liste
- Sauberer Umgang mit drei Zuständen: **Laden**, **Erfolg**, **Fehler** (z. B. kein Internet)
- Pull-to-Refresh

### Bonus
- Favoriten-Städte speichern (Wissen von Tag 4)
- Standort des Geräts verwenden (`geolocator`)
- Hintergrundfarbe / Verlauf abhängig vom Wetter
- Stündliche Vorhersage als Diagramm

### Lernkonzepte
- Paket `http` (oder `dio`), HTTP-GET, Statuscodes
- JSON verschachtelt parsen und in eigene Modellklassen umwandeln
- `FutureBuilder` und seine Zustände (`ConnectionState`, `hasError`, `hasData`)
- Fehlerbehandlung mit `try` / `catch`, eigene Exception-Klassen
- Trennung von UI und Datenzugriff: eine eigene Service-Klasse für API-Aufrufe
- Debouncing bei der Sucheingabe (`Timer`)
- Bei Web als Ziel: CORS-Thematik verstehen

### Brücke zu deinem Wissen
Die Service-Klasse ist dasselbe Prinzip wie ein API-Client in C# oder ein `fetch`-Wrapper in JS. Neu ist vor allem, wie die UI deklarativ auf den Zustand eines Futures reagiert.

### Fertig, wenn …
… die App bei Flugmodus eine verständliche Fehlermeldung mit „Erneut versuchen“-Button zeigt statt abzustürzen.

---

## Tag 6 – 28.10. – `tag6_Rezeptbuch`

**Thema:** State Management & App-Architektur

### Idee
Eine Rezept-App auf Basis der kostenlosen **TheMealDB API**. Rezepte durchsuchen, nach Kategorien filtern, Details ansehen, Favoriten markieren und Zutaten auf eine Einkaufsliste setzen. Die Favoriten und die Einkaufsliste müssen auf **mehreren Screens gleichzeitig** aktuell sein – genau hier stößt `setState` an seine Grenzen.

### Pflicht-Features
- Kategorien-Übersicht als Raster (`GridView`) mit Bildern aus dem Netz
- Rezeptliste pro Kategorie und Suchfunktion
- Detailseite mit Bild, Zutaten und Anleitung
- Favoriten: Herz-Icon auf Liste *und* Detailseite, immer synchron
- Einkaufsliste: Zutaten aus einem Rezept hinzufügen, abhaken, löschen; Badge mit Anzahl in der Navigation
- Favoriten und Einkaufsliste werden persistent gespeichert (Tag 4)
- Bottom Navigation: Entdecken / Favoriten / Einkaufsliste

### Bonus
- `Hero`-Animation für das Rezeptbild beim Öffnen der Detailseite
- Bilder cachen (`cached_network_image`)
- Responsives Layout: auf breiten Bildschirmen Liste und Detail nebeneinander (`LayoutBuilder`)
- Zufälliges „Rezept des Tages“

### Lernkonzepte
- Warum State Management? Das Problem von „Prop Drilling“
- `InheritedWidget` kurz verstehen (Grundlage von allem)
- Ein State-Management-Paket: **Provider** (einsteigerfreundlich) oder **Riverpod** (moderner, empfehlenswert)
- `ChangeNotifier` bzw. `Notifier`, gezieltes Neuzeichnen nur betroffener Widgets
- Schichtenarchitektur: UI → State → Repository → API / lokaler Speicher
- Ordnerstruktur nach Features (`models/`, `services/`, `providers/`, `screens/`, `widgets/`)

### Brücke zu deinem Wissen
Provider/Riverpod lösen dasselbe Problem wie Redux / Context in React oder ein ViewModel mit `INotifyPropertyChanged` in C# (MVVM). Das Repository-Pattern kennst du vermutlich aus der C#-Welt.

### Fertig, wenn …
… du ein Rezept auf der Detailseite favorisierst, zurückgehst und das Herz in der Liste sofort gefüllt ist – ohne dass du Callbacks durch mehrere Ebenen gereicht hast.

---

## Tag 7 – 29.10. – `tag7_FinanzTracker`

**Thema:** Abschlussprojekt – Datenbank, Diagramme, Animationen & Tests

### Idee
Ein persönlicher Ausgaben- und Budget-Tracker. Er vereint alles aus der Woche: Formulare (Tag 3), Persistenz (Tag 4), asynchronen Code (Tag 5), State Management & Architektur (Tag 6) – und kommt mit einer richtigen Datenbank, Diagrammen und Tests auf Profi-Niveau.

### Pflicht-Features
- Einnahmen und Ausgaben erfassen: Betrag, Kategorie, Datum, Notiz
- Speicherung in einer lokalen Datenbank (**sqflite**, **drift** oder **Isar/Hive**)
- Übersicht pro Monat mit Saldo, Wechsel zwischen Monaten
- Kreisdiagramm nach Kategorien und Balkendiagramm über die Monate (**fl_chart**)
- Monatsbudget pro Kategorie mit Fortschrittsbalken und Warnung bei Überschreitung
- State Management wie an Tag 6
- **Tests:** mindestens einige Unit-Tests (z. B. Saldo- und Budgetberechnung) und ein Widget-Test (z. B. Formular-Validierung)

### Bonus
- Implizite und explizite Animationen (z. B. animierte Zahlen beim Saldo, animierte Diagramme)
- Export der Daten als CSV
- Wiederkehrende Buchungen (Miete, Abos)
- Mehrsprachigkeit (Deutsch / Englisch) mit `intl` und Währungs-/Datumsformatierung
- App als Web-Version bauen und z. B. über GitHub Pages veröffentlichen

### Lernkonzepte
- SQL-Datenbank in Flutter, Migrationen, Repository kapselt die Datenbank
- `Stream`s (z. B. Datenbank-Abfragen, die sich automatisch aktualisieren) und `StreamBuilder`
- Diagramme mit externen Paketen
- Animations-Grundlagen: `AnimatedFoo`-Widgets, `AnimationController`, `Tween`
- Testen: `flutter_test`, Unit-Tests, Widget-Tests, Abhängigkeiten mocken
- Build-Prozess: `flutter build apk` / `flutter build web`, Release vs. Debug

### Brücke zu deinem Wissen
`Stream` entspricht einem `IObservable` (Rx) in C# bzw. einem Observable in RxJS. drift ist konzeptionell ähnlich zu Entity Framework, aber mit generiertem Code (`build_runner`).

### Fertig, wenn …
… die App alle Daten in einer Datenbank hält, Diagramme korrekt reagieren, `flutter test` grün ist und du einen Release-Build erstellt hast.

---

## Tag 8 – 30.10. – Puffer & Abschluss

- Offene Pflicht-Features der Vorwoche nachholen
- Code aufräumen: `flutter analyze` ohne Warnungen, `dart format`
- Zu jedem Projekt eine kurze README mit Screenshot und „Was habe ich gelernt?“
- Rückblick: Welche Konzepte sitzen, welche nicht? Daraus eine Liste für die Zeit nach den 7 Tagen erstellen

---

## Übersicht: Wie die Projekte aufeinander aufbauen

| Tag | Projekt | Neu hinzu kommt | Baut auf |
|-----|---------|-----------------|----------|
| 1 | Visitenkarte | Dart-Basics, Widgets, Layout | – |
| 2 | Punktezähler | State, `setState`, Interaktion | 1 |
| 3 | Todo-Liste | Listen, Formulare, Navigation | 1–2 |
| 4 | Gewohnheits-Tracker | Persistenz, JSON, Theming, `Future` | 1–3 |
| 5 | Wetter-App | HTTP, async, Fehlerbehandlung, Service-Schicht | 1–4 |
| 6 | Rezeptbuch | State Management, Architektur, `GridView` | 1–5 |
| 7 | Finanz-Tracker | Datenbank, `Stream`, Diagramme, Animationen, Tests | 1–6 |

## Empfohlene Ressourcen

- Offizielle Doku: docs.flutter.dev und dart.dev (besonders „Dart language tour“)
- „Flutter for React developers“ / „Flutter for web developers“ in der offiziellen Doku – passt gut zu deinem JS-Hintergrund
- Flutter Widget of the Week (YouTube-Playlist des Flutter-Teams)
- pub.dev zum Finden von Paketen (auf „Flutter Favorite“ und Likes achten)
