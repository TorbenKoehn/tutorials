Ein NodeJS/NPM Projekt erstellen
================================

### Was benötige ich?

- NodeJS und NPM
  ([nodejs.org](https://nodejs.org/de));
- Text/Code-Editor oder IDE 
  (z.B. [Sublime Text](https://www.sublimetext.com/),
  [Visual Studio Code](https://code.visualstudio.com/) oder [WebStorm](https://www.jetbrains.com/webstorm/))
- Eine Shell (Windows CMD, PowerShell, Terminal)

Die erstellen Dateien und den Code findet ihr im `files`-Ordner direkt neben dieser `README.md`

### NPM Projekt erstellen

Öffnet eine Shell in einem Projektordner eurer Wahl. Anschließend führt ihr folgendes Kommando
zur Erstellung eines neuen NPM Projekts aus

```bash
npm init
```

Ihr werdet durch einen Installer geführt, den ihr mit Angaben zu eurem Projekt befüttern müsst. 
Das Ganze sieht in etwa so aus:

```text
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help json` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
package name: (files)
```

Als erstes wird die Eingabe eines Paketnamens von euch erwartet. Der Wert zwischen Klammern (`()`) ist der
Standardwert, wenn ihr keinen angebt. Wenn euer Projektname derselbe ist, wieder Name eures Ordners, braucht
ihr nichts eingeben.

Der Paketname sollte lediglich aus kleinen Buchstaben und Bindestrichen (`-`) bestehen.

Wir nennen unser Paket `mein-npm-projekt`

Bestätigt das Ganze mit `<Enter>`.

```text
package name: (files) mein-npm-projekt
version: (1.0.0) 
```

Die `version` könnt ihr bei 1.0.0 belassen (Einfach `<Enter>` drücken)

```text
version: (1.0.0) 
description:
```

Als `description` gebt ihr eine kleine, kurze Beschreibung eures Projekts an

```text
description: Dies ist mein NPM Projekt und es macht Dinge
entry point: (index.js) 
```

Der `entry point` ist die erste Datei, die in eurem JavaScript-Projekt geladen werden soll.

Dies ist (und so auch übersetzt) der Einstiegspunkt eures Programms.

Im besten Falle packt ihr diese in einen Unter-Ordner eures Projekts, in dem
später der gesamte Code enthalten sein wird.

Wir nennen diesen Ordner (auch im Zuge sämtlicher Tutorials hier) immer `src` ("sources")

Gebt also

```text
src/index.js
```

ein.

```text
entry point: (index.js) src/index.js
test command: 
```

Das `test command` spielt für euch anfangs eine geringe Rolle, drückt `<Enter>`

```text
test command: 
git repository: 
```

Falls ihr das Projekt mit Git verwaltet, könnt ihr hier die URL zum Projekt angeben. Ansonsten
drückt einfach `<Enter>`

```text
git repository: 
keywords: 
```

Keywords haben wenig Relevanz, wenn ihr eine Applikation schreibt. Schreibt ihr eine Bibliothek,
könnt ihr hier (mit Kommata getrennt) Keywords angeben, die euer Projekt ausmachen, damit es
leichter auf NPM gefunden werden kann.

```text
keywords: 
author: 
```

Der Author seid natürlich ihr!

```text
author: Torben Köhn
license: (ISC) 
```

Die Lizenz eures Projekts hat nur Auswirkungen, wenn ihr es veröffentlicht. Plant ihr dies
(oder liegt es auf einem öffentlichen Git Repository), solltet ihr eine auswählen.

Eine Übersicht über gängige Open Source Lizenzen findet ihr unter
[choosealicense.com](https://choosealicense.com/licenses/)

Ich persönlich nutze für meine Projekte die `MIT` Lizenz, wenn ich es veröffentliche
und den Wert `UNLICENSED`, wenn es ein privates Paket oder ein Projekt für einen Kunden ist.

```text
license: (ISC) MIT
About to write to /files/package.json:

{
  "name": "mein-npm-projekt",
  "version": "1.0.0",
  "description": "Dies ist mein NPM Projekt und es macht Dinge",
  "main": "src/index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Torben Köhn",
  "license": "MIT"
}


Is this OK? (yes) 
```

Das war der letzte Schritt. Betrachtet eure Konfiguration nun noch ein mal im JSON Format und prüft, das
alles korrekt angegeben wurde. Wenn das der Fall ist, drückt `<Enter>`

### package.json

NPM hat euch in eurem Ordner nun eine Datei namens `package.json` erstellt.

Diese Datei ist das Herz eures Projekts. Es bestimmt Grundinformationen wie den Ort
des Codes oder den Namen und es enthält eure Abhängigkeiten.

Diese Datei gehört immer zu eurem Projekt und sollte genau dort bleiben, wo sie ist.

Mit etwas Übung werdet ihr eine `package.json` schneller ohne `npm init` schreiben, als mit!

### Programm ausführen

Damit wir Code ausführen können, benötigen wir natürlich erst mal Code.

Das einfachste Beispiel ist hier das klassische `Hello World!` in JavaScript.

Erstellt dazu einen `src`-Ordner und darin eine `index.js`-Datei. 

Das Projekt sollte danach so aussehen:

```text
src/
  index.js
package.json
```

Öffnet die `src/index.js` in eurem Editor und gebt folgenden Code darin ein

```js
console.log('Hello World!');
```

Speichert die Datei.

Geht anschließend wieder in die Shell in euren Projekt-Ordner und führt euer Projekt mit NodeJS aus

```bash
node .
```

Folgende Ausgabe sollte erscheinen

```
Hello World!
```

### Abhängigkeiten installieren

NPM verfügt über eine [enorm große Bibliothek an vorhanden Paketen](https://www.npmjs.com/),
die ihr frei verwenden könnt.

Damit ihr seht, wie ihr diese verwendet, werden wir eines davon nutzen.

Ein sehr beliebtes Paket ist zum Beispiel `express`.

`express` ist ein kleines, minimales Web-Framework, mit dem ihr blitzschnell
eine Web-Applikation bereitstellen könnt.

Wir gehen mit der Shell wieder in den Projekt-Ordner und installieren `express` mit folgendem Befehl:

```bash
npm install express
```

Nach kurzem Rattern wird folgendes passiert sein:

**1. Es wurde ein `node_modules/` Ordner in eurem Projekt erstellt**

Dieser Ordner enthält eure installierten Abhängigkeiten.

**Ihr könnt diesen Ordner jederzeit löschen**

Ein einfaches Ausführen des Befehls

```bash
npm install
```

wird ihn jederzeit wieder für euch herstellen.

**2. Eure `package.json` hat sich verändert**

```diff
{
  "name": "mein-npm-projekt",
  "version": "1.0.0",
  "description": "Dies ist mein NPM Projekt und es macht Dinge",
  "main": "src/index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Torben Köhn",
  "license": "MIT",
+  "dependencies": {
+    "express": "^4.17.1"
+  }
}
```

Im Bereich `dependencies` sind die installierten Abhängigkeiten eures Projekts gespeichert, inklusive
der bevorzugten Version. In unserem Beispiel ist das eben gerade nur `express` in der 
Version `4.17.1` (und höhere `4.17.*` Versionen)


**3. Eine `package-lock.json` wurde erstellt**

Diese Datei fixiert die Versionen eurer Abhängigkeiten und deren Abhängigkeiten exakt.
Solange diese Datei vorhanden ist, wird `npm install` immer exakt dieselben Pakete wie
zuvor installieren.

Dies garantiert, dass eure Applikation weiter funktioniert, sollte eine Abhängigkeit einmal
die Versionierung brechen.

### Abhängigkeiten nutzen

Da wir `express` nun installiert haben, nutzen wir es.

Wie genau express funktioniert, entnehmen wir am besten der
[eigenen Dokumentation](https://www.npmjs.com/package/express)

Zurzeit lassen sich JavaScript-Pakete mithilfe des [CommonJS-Standards](https://requirejs.org/docs/commonjs.html) laden.

Dazu existiert die Funktion `require(<paketName>)` innerhalb von NodeJS.

Wir ändern nun unsere `src/index.js`.

Mit `require` laden wir `express` und speichern es in einer Konstante namens, hilfreicherweise, `express`.

Diese Konvention der Benennung eignet sich sehr gut für NPM Pakete.

```js
const express = require('express');
```

Dann nutzen wir `express()`, um uns eine Applikation zu erstellen und dieser mitzuteilen,
dass sie uns auf dem Port 3000, wenn wir die URL / abrufen, Hello World! ausgeben soll.

```js
const app = express();

app.get('/', (req, res) => {
    res.send('Hello World!')
});
 
app.listen(3000, () => console.log('Server listening...'));
```

Ihr könnt nun das Projekt wieder mit

```bash
node .
```

ausführen.

Sobald `Server listening...` in der Konsole ausgeben wurde könnt ihr

http://localhost:3000

im Browser aufrufen und ihr seht, wie `express` euch antwortet!