# 🎸 ChordWanze - Mobile App

ChordWanze Web App (PWA) für Gitarristen zum Anzeigen von Song-Lyrics mit Akkorden. 

## ✨ Neue Features

### 🎵 Vollständige Chromatische Akkord-Bibliothek (200+ Akkorde)
Alle 12 Halbtöne für jede Akkordart:

**Dur-Akkorde (Alle Halbtöne):**
- Natürlich: C, D, E, F, G, A, B
- Kreuz (#): C#, D#, F#, G#, A#
- Be (♭): Db, Eb, Gb, Ab, Bb

**Moll-Akkorde (Alle Halbtöne):**
- Cm, C#m/Dbm, Dm, D#m/Ebm, Em, Fm, F#m/Gbm, Gm, G#m/Abm, Am, A#m/Bbm, Bm

**Septakkorde (Alle Halbtöne):**
- C7, C#7/Db7, D7, D#7/Eb7, E7, F7, F#7/Gb7, G7, G#7/Ab7, A7, A#7/Bb7, B7

**Major 7 (Alle Halbtöne):**
- Cmaj7, C#maj7/Dbmaj7, Dmaj7, D#maj7/Ebmaj7, Emaj7, usw.

**Minor 7 (Alle Halbtöne):**
- Cm7, C#m7/Dbm7, Dm7, D#m7/Ebm7, Em7, usw.

**Power Chords (Alle Halbtöne):**
- C5, C#5/Db5, D5, D#5/Eb5, E5, F5, F#5/Gb5, G5, G#5/Ab5, A5, A#5/Bb5, B5

**Plus:**
- **Suspended**: sus2, sus4 (für verschiedene Grundtöne)
- **Diminished**: dim (alle 12 Halbtöne)
- **Augmented**: aug (alle 12 Halbtöne)
- **Add9**: add9 (alle 12 Halbtöne)

**Insgesamt über 200 Akkorde!** Jetzt kannst du Songs in jeder Tonart spielen.

### 🌐 Übersetzungsfunktion
- Übersetze Song-Texte zwischen Deutsch und Englisch
- Einfacher Sprach-Swap mit einem Klick
- Integration vorbereitet für DeepL oder Google Translate API

### 📱 Vollständige PWA-Funktionalität
- **Installierbar** auf iOS und Android Homescreen
- **Offline-Fähig** - funktioniert ohne Internetverbindung
- **Native App-Feeling** - keine Browser-Leiste
- **Optimiert** für mobile Geräte

### 📚 Akkord-Bibliothek
- Alle verfügbaren Akkorde auf einen Blick
- Nach Kategorien sortiert
- Übersichtliche Darstellung mit Gitarrengriffen

## 🚀 Installation

### Für iOS (iPhone/iPad):

1. Öffne die App in **Safari** (wichtig!)
2. Tippe auf das **Teilen-Symbol** (□↑) unten in der Mitte
3. Scrolle und wähle **"Zum Home-Bildschirm"**
4. Tippe auf **"Hinzufügen"**
5. Die App erscheint jetzt auf deinem Homescreen! 🎉

### Für Android:

#### Option 1: Chrome
1. Öffne die App in **Chrome**
2. Tippe auf die **drei Punkte** (⋮) oben rechts
3. Wähle **"Zum Startbildschirm hinzufügen"** oder **"App installieren"**
4. Bestätige mit **"Installieren"**

#### Option 2: Automatischer Installationsprompt
1. Beim ersten Besuch erscheint ein Banner mit **"App installieren"**
2. Tippe auf **"Installieren"**

### Für Desktop (optional):

1. Öffne die App in **Chrome** oder **Edge**
2. Klicke auf das **Install-Symbol** (⊕) in der Adressleiste
3. Oder: **Drei Punkte → App installieren**

## 📖 Nutzung

### Editor-Tab:
1. Gib deinen Song-Text ein
2. Füge Akkorde als einzelne Wörter ein (z.B. "C Am F G")
3. Nutze die **Sprache-zu-Text-Funktion** (🎤) deiner Tastatur
4. Klicke auf **"Akkorde anzeigen"**
5. Die App zeigt alle Akkorde mit Gitarrengriffen an!

**Beispiel:**
```
C Das ist ein Test Am
Die F# Sonne G scheint C5 hell
Eb Refrain Bbm7 hier D#maj7 yeah
```

### Übersetzer-Tab:
1. Wähle die Quell- und Zielsprache
2. Gib deinen Text ein
3. Klicke auf **"Übersetzen"**
4. Die Übersetzung erscheint unten

**Hinweis:** Für Produktivnutzung integriere eine echte Übersetzungs-API (siehe unten).

### Akkorde-Tab:
- Durchsuche alle verfügbaren Akkorde
- Sortiert nach Kategorien
- Perfekt als Nachschlagewerk

## 🔧 Für Entwickler

### Dateien:
- `index.html` - Haupt-App-Datei
- `manifest.json` - PWA-Manifest für Installation
- `sw.js` - Service Worker für Offline-Funktionalität
- `icon-192.png` & `icon-512.png` - App-Icons (müssen erstellt werden)

### Icons erstellen:

Erstelle zwei Icons:
- **192x192 px** für normale Auflösung
- **512x512 px** für hohe Auflösung

Empfohlene Tools:
- [Favicon.io](https://favicon.io/)
- [RealFaviconGenerator](https://realfavicongenerator.net/)
- Canva
- Figma

**Design-Tipp:** Verwende ein Gitarren-Symbol, Notenschlüssel oder Akkord-Diagramm als Motiv.

### Übersetzungs-API integrieren:

Die App ist vorbereitet für eine echte Übersetzungs-API. Ersetze die `simulateTranslation`-Funktion:

#### DeepL API:
```javascript
async function translateText() {
    const apiKey = 'DEIN_DEEPL_API_KEY';
    const response = await fetch('https://api-free.deepl.com/v2/translate', {
        method: 'POST',
        headers: {
            'Authorization': `DeepL-Auth-Key ${apiKey}`,
            'Content-Type': 'application/json'
        },
        body: JSON.stringify({
            text: [sourceText],
            source_lang: sourceLang.toUpperCase(),
            target_lang: targetLang.toUpperCase()
        })
    });
    const data = await response.json();
    return data.translations[0].text;
}
```

#### Google Translate API:
```javascript
async function translateText() {
    const apiKey = 'DEIN_GOOGLE_API_KEY';
    const response = await fetch(
        `https://translation.googleapis.com/language/translate/v2?key=${apiKey}`,
        {
            method: 'POST',
            headers: {'Content-Type': 'application/json'},
            body: JSON.stringify({
                q: sourceText,
                source: sourceLang,
                target: targetLang
            })
        }
    );
    const data = await response.json();
    return data.data.translations[0].translatedText;
}
```

### Lokales Testen:

```bash
# Python 3
python -m http.server 8000

# Node.js
npx http-server

# PHP
php -S localhost:8000
```

Dann öffne: `http://localhost:8000`

### Hosting:

Kostenlose Hosting-Optionen:
- **GitHub Pages** (empfohlen für statische Apps)
- **Netlify** (automatische Deployments)
- **Vercel** (schnell und einfach)
- **Firebase Hosting** (Google)

## 🎯 Features im Detail

### Akkord-Erkennung:
- Automatische Erkennung von 60+ Akkorden
- Intelligente Wort-Trennung
- Erhält Original-Text zwischen Akkorden

### Visuelle Darstellung:
- Fretboard-Diagramme für jeden Akkord
- Farbcodierte Markierungen:
  - 🔴 Finger-Positionen
  - ❌ Gedämpfte Saiten
  - ⭕ Leere Saiten

### Mobile Optimierung:
- Touch-optimierte Buttons
- Responsive Layout
- Große, gut lesbare Schrift
- Safe-Area-Insets für iPhone notch

## 🆕 Weitere Akkorde hinzufügen

Um eigene Akkorde hinzuzufügen, erweitere das `chords`-Objekt in `index.html`:

```javascript
const chords = {
    // Bestehende Akkorde...
    
    // Deine neuen Akkorde:
    'Csus2': [-1, 3, 0, 0, 1, 3],
    'F#m': [2, 4, 4, 2, 2, 2],
    // [Saite 6, 5, 4, 3, 2, 1]
    // -1 = gedämpft, 0 = leer, 1-4 = Bund
};
```

**Saiten-Reihenfolge:** E A D G B E (von dick nach dünn)

### 🎼 Enharmonische Äquivalente

Beachte: Kreuz (#) und Be (♭) Akkorde sind enharmonisch äquivalent:
- C# = Db
- D# = Eb
- F# = Gb
- G# = Ab
- A# = Bb

Du kannst beide Schreibweisen nutzen - sie erzeugen dieselben Griffbilder!

## 📱 Browser-Kompatibilität

- ✅ iOS Safari 11.3+
- ✅ Android Chrome 67+
- ✅ Samsung Internet 8+
- ✅ Desktop Chrome, Firefox, Edge, Safari

## 🐛 Bekannte Einschränkungen

1. **iOS Safari:** PWA-Installation nur über Safari möglich (nicht Chrome/Firefox)
2. **Offline-Übersetzung:** Erfordert API-Integration für echte Übersetzungen
3. **Icons:** Platzhalter-Icons müssen durch echte Icons ersetzt werden

## 💡 Tipps

- **Spracherkennung nutzen:** Verwende das Mikrofon-Symbol deiner Tastatur zum Diktieren
- **Akkorde kopieren:** Lange auf einen Akkord tippen zum Kopieren (iOS)
- **Offline arbeiten:** Nach der Installation funktioniert die App ohne Internet
- **Aktualisieren:** Wische von oben nach unten zum Aktualisieren

## 🤝 Beitragen

Verbesserungsvorschläge? Features gewünscht? 

1. Forke das Projekt
2. Erstelle einen Feature Branch
3. Committe deine Änderungen
4. Push zum Branch
5. Erstelle einen Pull Request

## 📝 Lizenz

Dieses Projekt steht unter der MIT-Lizenz - siehe LICENSE-Datei für Details.


**Viel Spaß beim Musizieren! 🎸🎵**
