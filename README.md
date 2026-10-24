# ZClone (Windows)

**ZClone** ist ein vollständig portabler Dateimanager mit zwei Fenstern für Windows 10 und 11. Er bindet
Cloud-Speicher („Provider“) so ein, dass du sie wie lokale Ordner nutzt. ZClone kann:

- Dateien und Ordner kopieren, verschieben, löschen und umbenennen – auch zwischen PC und Cloud,
- Ordner einmalig oder automatisch abgleichen (einseitig oder in beide Richtungen),
- Provider als Windows-Laufwerk einbinden,
- aus dem Windows-Explorer per Rechtsklick hochladen, auf Wunsch verschlüsselt.

Unter der Haube arbeitet **rclone-extra** – dasselbe wie in der Android-App
[ZClone Provider](https://github.com/Temkina/zclone-provider-beta). Damit gehen u. a. Google Drive, OneDrive,
Dropbox, Mega, Terabox, WebDAV (Telekom, Nextcloud …), S3-kompatible Speicher und verschlüsselte crypt-Provider.

| | |
|---|---|
| **Windows** | Windows 10 und 11, 64 Bit |
| **Installation** | keine – entpacken und starten; keine .NET-Installation nötig |
| **Sprachen** | Deutsch und Englisch (*Optionen → Einstellungen → Reiter „ZClone“*) |
| **Download** | [Releases auf zclone_beta](https://github.com/Temkina/zclone_beta/releases/latest), Datei `ZClone.zip` |
| **Konto** | Ein Konto bei uns ist nicht nötig. |

Dieses Repository enthält nur die fertigen Versionen, keinen Quellcode.

*English summary at the end of this file.*

---

## Inhalt

- [Installation und erste Schritte](#installation-und-erste-schritte)
- [Bedienung](#bedienung)
- [Funktionen](#funktionen)
- [Einstellungen](#einstellungen)
- [Was ZClone am System ändert](#was-zclone-am-system-ändert)
- [Datenschutz und Sicherheit](#datenschutz-und-sicherheit)
- [Zusammenspiel mit ZClone Provider (Android)](#zusammenspiel-mit-zclone-provider-android)
- [Grenzen](#grenzen)
- [Hilfe und Support](#hilfe-und-support)
- [Lizenzen](#lizenzen)
- [English summary](#english-summary)

---

## Installation und erste Schritte

1. **Herunterladen:** Im [neuesten Release](https://github.com/Temkina/zclone_beta/releases/latest) die Datei
   `ZClone.zip` laden.
2. **Entpacken:** an einen beliebigen Ort, z. B. nach `C:\` oder auf einen USB-Stick. Es entsteht der Ordner
   `ZClone` mit `ZClone.exe`, `Programme` (rclone), `Sprachen` und `Dokumentation`.
3. **Starten:** `ZClone.exe` öffnen. Einstellungen, Protokolle und Zugangsdaten entstehen in diesem Ordner.
   Liegt die exe einmal lose zwischen anderen Dateien, legt sie sich beim Start selbst einen Unterordner
   `ZClone` an und startet von dort neu.
4. **Provider einrichten (optional):** *ZClone → Rclone Provider → Neu…*, Anbieter wählen, Felder ausfüllen.
   Unten links **Hilfe** öffnet die Anleitung genau für diesen Anbieter. Bei Anbietern mit Browser-Anmeldung
   (Google Drive, OneDrive, Dropbox …) meldest du dich im Browser an.
5. **Synchronisation (optional):** *Synchronisation → Neuer Job…* für wiederkehrende Abgleiche.

Das Handbuch in der App (*Optionen → Handbuch*) erklärt jeden Schritt.

---

## Bedienung

- **Zwei Fenster (Panes):** links der Ordnerbaum über die volle Höhe mit Laufwerken, Schnellzugriff und
  Providern, rechts Adressleiste, Liste, Buttonleiste und Status. Beide Panes navigieren unabhängig.
- **Adressleiste:** zeigt den Pfad als anklickbare Abschnitte wie im Windows-Explorer; ein Klick auf die
  freie Fläche daneben erlaubt die Eingabe eines Pfads.
- **Mittelleiste** zwischen den Panes: Richtung wählen (→, ←, ↔), Vorschau der Unterschiede (⚖),
  sofort abgleichen (⟳) und neuen Sync-Job anlegen (⊕).
- **Aufträge-Liste:** alle gespeicherten Sync-Jobs mit Starten, Stoppen, Bearbeiten und Sortieren.
- **Menüs:** *ZClone* (u. a. Rclone Provider), *Synchronisation*, *Ansicht* (Hell/Dunkel, Ausblenden),
  *Partitionierung* und *Optionen* (Einstellungen, Handbuch, Updates).

---

## Funktionen

### Dateien

- **Kopieren, Verschieben, Löschen, Umbenennen, Neuer Ordner, Alle markieren** – per Buttonleiste oder
  Rechtsklick, auch zum anderen Pane und zu oder von Providern. Der Fortschritt steht in der Menüleiste,
  mit *Abbrechen*.
- **Drag & Drop** zwischen den Panes: verschiebt, mit gedrückter Strg-Taste wird kopiert.
- **Schnellzugriff:** häufige Ordner oben im Baum anheften (Rechtsklick → *Zum Schnellzugriff hinzufügen*),
  per Drag & Drop sortierbar.
- **Sortierung** per Klick auf die Spaltenüberschrift, natürlich sortiert (z. B. „Bild 2“ vor „Bild 10“).
- **Ausblenden:** Elemente aus der Anzeige nehmen, ohne sie zu löschen; *Ansicht → Ausgeblendete Elemente
  verwalten…* holt sie zurück. Systemdateien und versteckte Dateien sind standardmäßig ausgeblendet.

### Provider (Cloud-Speicher)

*ZClone → Rclone Provider*, Rechtsklick auf einen Provider im Ordnerbaum oder Systray-Menü → *Provider hinzufügen*

- **Neu, Bearbeiten, Umbenennen, Löschen, Testen.** Häufige Provider lassen sich mit ★ anheften. Die
  *Erweiterte Ansicht* zeigt alle rclone-Parameter mit Hilfe je Feld.
- **Umbenennen zieht alles nach:** abhängige verschlüsselte Provider, Sync-Jobs, Schnellzugriff,
  Kontextmenü-Ziele, Mounts und den Standard-Startpfad.
- **Löschen** entfernt nur die Einstellung in ZClone, nie die Daten in der Cloud. Was betroffen ist, zeigt
  ZClone vorher an.
- **Verbinden erst bei Bedarf:** Ein Provider verbindet sich, wenn du ihn anklickst. Rechtsklick auf den
  Knoten *Provider* → *Alle Provider verbinden* bzw. *Alle Provider trennen*.
- **Standard-Startpfad:** Rechtsklick → *Als Standard setzen* lässt das rechte Pane bei jedem Start dort beginnen.

### Verschlüsselte Provider (crypt)

- **Bequem:** Beim Anlegen *Gleichzeitig auch einen verschlüsselten Provider dafür erstellen* ankreuzen –
  für den ganzen Provider oder nur einen Unterordner, mit eigenem oder zufällig erzeugtem Passwort.
- **Von Hand:** *Neu* → Anbieter *crypt*, als Ziel z. B. `MeinProvider:Verschlüsselt`.
- Dateinamen und Inhalte liegen in der Cloud nur verschlüsselt. **Das Passwort gut aufbewahren** – ohne es
  sind die Daten nicht mehr lesbar.

### Als Windows-Laufwerk einbinden

*Optionen → Einstellungen → Reiter „Mounten“*

- Jedem Provider einen Laufwerksbuchstaben geben, auf Wunsch automatisch beim Start einbinden und beim
  Beenden wieder aushängen.
- Dafür braucht Windows **WinFsp** (einmalig installieren). Fehlt es, weist ZClone darauf hin.

### Synchronisation

- **Schnell, zwei Ordner:** Quelle in einem Pane, Ziel im anderen öffnen, in der Mittelleiste die Richtung
  wählen, mit ⚖ die Unterschiede ansehen und mit ⟳ abgleichen. Angekreuzte Elemente schränken den Abgleich ein.
- **Sync-Jobs (wiederkehrend):** *Synchronisation → Neuer Job…* mit mehreren Quellen und Zielen.
  - **Auslöser:** Echtzeit (sofort bei Änderungen), Geplant (alle X Minuten) oder nur manuell.
  - **Verhalten:** ob vorhandene Dateien überschrieben, fehlende gelöscht oder vor dem Löschen als
    Sicherungskopie behalten werden.
- **Konflikte** (z. B. beide Seiten geändert) entscheidest du in der Vorschau je Zeile.
- **Ausschlüsse:** in der Vorschau per Rechtsklick eine Datei oder ein Muster dauerhaft ausschließen.
  Systemdateien (z. B. `desktop.ini`) und versteckte Dateien sind standardmäßig ausgeschlossen, je Auftrag
  abweichend einstellbar.
- **Eine Übertragung nach der anderen:** Standardmäßig läuft immer nur eine rclone-Übertragung; mehrere
  Provider parallel lassen sich einschalten. Hängende Übertragungen werden beendet und neu gestartet.

### Hochladen aus dem Windows-Explorer

*Optionen → Einstellungen → Reiter „Kontextmenü“*

- *Rechtsklick-Kontextmenü „ZClone: Hochladen“ aktivieren* ankreuzen und Ziele anlegen (Provider und Ordner),
  getrennt nach verschlüsselt und unverschlüsselt.
- Danach im Explorer Rechtsklick auf Dateien oder Ordner → *ZClone* → Ziel wählen.
- Eine Sperrdatei verhindert, dass sich zwei Uploads zum selben Ziel überschneiden.

### Systray und Hintergrund

- Auf Wunsch legt sich ZClone beim Schließen oder Minimieren ins Systray neben der Uhr. **Autostart** lässt
  ZClone ab der nächsten Windows-Anmeldung unsichtbar mitlaufen.
- Echtzeit- und geplante Jobs sowie eingebundene Laufwerke laufen dann ohne offenes Fenster weiter.
- Das Rechtsklick-Menü des Symbols bietet *ZClone öffnen*, *Einstellungen*, *Neuer Job…*,
  *Provider hinzufügen* und *Beenden* (beendet auch alle Hintergrundaufgaben).

### Weiteres

- **Hell/Dunkel** ohne Neustart (*Ansicht* oder *Optionen → Reiter „ZClone“*).
- **Partitionierung:** *Partitionierung → Windows-Datenträgerverwaltung öffnen…* startet die
  Datenträgerverwaltung von Windows. Eine eigene Sicherung oder Partitionierung bringt ZClone nicht mit.
- **Updates:** *Optionen → Nach Updates suchen…* prüft dieses Repository. ZClone lädt die neue Version,
  ersetzt nur die Programmdateien und startet neu – Einstellungen, Zugangsdaten und Protokolle bleiben.
- **Mega über MEGAcmd (optional):** Statt des eingebauten Mega-Zugangs geht auch die WebDAV-Brücke von
  MEGAcmd, wenn MEGAcmd installiert ist.

---

## Einstellungen

*Optionen → Einstellungen*

| Reiter | Inhalt |
|---|---|
| **Datei** | Rückfragen (z. B. vor Löschen/Überschreiben), Meldungen, Fenster- und Spaltenlayout merken |
| **Synchronisation** | System- und versteckte Dateien ausschließen, mehrere Provider parallel |
| **Logging** | Protokollstufen, Aufräumen nach Alter oder Größe, Protokolle als ZIP exportieren |
| **Kontextmenü** | *ZClone: Hochladen* im Windows-Explorer ein/aus, Ziele, Rückfragen dieses Wegs |
| **Mounten** | Laufwerksbuchstaben je Provider, automatisch einbinden und aushängen |
| **Provider** | Provider-Liste der Adressleiste alphabetisch sortieren |
| **Sicherheit** | Konfiguration mit Passwort verschlüsseln |
| **ZClone** | Rückfrage beim Beenden, Design, Sprache, Systray und Autostart |
| **Sponsor** | GitHub, Telegram, PayPal und Stripe |

---

## Was ZClone am System ändert

Grundsätzlich nichts: keine Installation, keine Dienste, alle Daten im Programmordner. Nur diese
Funktionen schreiben außerhalb davon – jeweils erst, wenn du sie einschaltest, und nur für deinen Benutzer:

| Funktion | Änderung |
|---|---|
| **Autostart** (Hintergrund, Mounts) | Verknüpfung im persönlichen Autostart-Ordner von Windows |
| **Explorer-Kontextmenü** | Einträge unter `HKEY_CURRENT_USER` (ein Rechtsklick-Menü geht unter Windows nur über die Registry); beim Ausschalten werden sie wieder entfernt |
| **Als Laufwerk einbinden** | braucht WinFsp, das du selbst installierst |
| **Datenträgerverwaltung** | Windows fragt eventuell nach Administratorrechten |

---

## Datenschutz und Sicherheit

- **Keine Konten, keine Statistik.** ZClone spricht nur mit
  - deinen Providern,
  - `api.github.com` und `github.com`, nur für die Update-Suche und den Download,
  - `graph.microsoft.com`, nur beim Einrichten von OneDrive, um das richtige Laufwerk zu finden.
- **Zugangsdaten** liegen im Ordner `Konfiguration` neben der `ZClone.exe`. **Diesen Ordner nie weitergeben
  oder veröffentlichen.** Mit *Optionen → Einstellungen → Reiter „Sicherheit“* lässt sich die
  rclone-Konfiguration mit einem Passwort verschlüsseln.
- **Protokolle** liegen im Ordner `Protokolle` (Datei `Z.log`). Der ZIP-Export enthält bewusst **nicht**
  den Ordner `Konfiguration`.

---

## Zusammenspiel mit ZClone Provider (Android)

- **Gleiches rclone:** Beide nutzen rclone-extra von gulp79, also auch dessen Zusatz-Provider, die das
  normale rclone nicht kennt.
- **Provider übertragen:** Die `rclone.conf` aus `Konfiguration\Rclone` lässt sich in der App importieren
  (mit Auswahl einzelner Provider); in der App exportierte lassen sich am PC dort ablegen.
- **Verschlüsselte Konfiguration:** Beide verstehen das Format von rclone.
- **Releases:** Die Android-App erscheint in einem eigenen Repository,
  [zclone-provider-beta](https://github.com/Temkina/zclone-provider-beta).

---

## Grenzen

- **Echtzeit und Geplant** laufen nur, solange ZClone geöffnet ist oder per Autostart im Systray mitläuft.
- **Laufwerke** gehen nur mit installiertem WinFsp.
- **Umbenennen eines Providers** geht nicht bei verschlüsselter Konfiguration (vorher die Verschlüsselung
  aufheben) und nicht, solange er als Laufwerk eingebunden ist.
- **crypt-Passwort vergessen:** Ohne Passwort sind verschlüsselte Daten verloren – auch der Anbieter kann
  sie nicht entschlüsseln.
- **Nur Windows** (10 und 11, 64 Bit).

---

## Hilfe und Support

- **Handbuch** in der App: *Optionen → Handbuch*.
- **Fragen, Probleme, Vorschläge:** Telegram-Supportforum [t.me/ZClone_N](https://t.me/ZClone_N).
- **Bei Problemen** die Protokolle über *Optionen → Einstellungen → Reiter „Logging“* als ZIP exportieren
  und mitschicken – ohne Zugangsdaten.

---

## Lizenzen

- **ZClone:** © 2026 Temkina, alle Rechte vorbehalten, eigene Lizenzvereinbarung
  (im ZIP unter `Dokumentation\Lizenzen\ZClone-LICENSE.txt`). Unterstützen kannst du das Projekt freiwillig
  über *Optionen → Einstellungen → Reiter „Sponsor“*.
- **rclone-extra** von [gulp79](https://github.com/gulp79/rclone-extra), basierend auf
  [rclone](https://rclone.org/) © Nick Craig-Wood (MIT), unverändert mitgeliefert unter
  `Programme\Rclone\rclone.exe` (Lizenztext unter `Dokumentation\Lizenzen\Rclone-LICENSE.txt`).

---

## English summary

**ZClone** is a fully portable dual-pane file manager for Windows 10/11 (64 bit) that works with cloud
storage (“providers”) just like with local folders:

- **Files:** copy, move, delete, rename and create folders – also between PC and cloud – with progress and
  cancel; drag & drop between the panes; quick access pins; natural sorting; hide items without deleting them.
- **Providers:** create, edit, rename (all references follow), delete (never deletes cloud data) and test;
  browser sign-in for Google Drive, OneDrive, Dropbox …; a help button opens the guide for each provider;
  encrypted crypt providers in one step.
- **Drives:** mount providers as Windows drives (needs WinFsp), optionally at startup.
- **Sync:** quick two-folder sync with preview and per-line conflict choice, and saved jobs triggered in
  real time, on a schedule or manually, with exclusions.
- **Explorer context menu:** upload from Windows Explorer, encrypted or not (per-user registry entries,
  only when you enable it).
- **Tray and background:** jobs and mounts keep running without an open window; optional autostart.
- **Everyday features:** light/dark theme, German and English, in-app updates that keep your settings,
  log export without credentials.

It uses the same **rclone-extra** build as the Android app ZClone Provider. No installation, no accounts,
no tracking; all data stays in the program folder.
Download: [zclone_beta releases](https://github.com/Temkina/zclone_beta/releases/latest) (`ZClone.zip`).
