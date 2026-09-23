# ZClone

ZClone ist ein vollständig portabler Dual-Pane-Dateimanager für Windows
10/11, geschrieben in C#/.NET 8 (Windows Forms). Er kombiniert eine klassische
Zwei-Fenster-Explorer-Ansicht mit einer Anbindung an
[rclone](https://github.com/rclone/rclone) ([rclone.org](https://rclone.org/)),
sodass Cloud-Speicher (Google Drive, WebDAV, S3-kompatible Anbieter usw.)
genauso durchsucht, kopiert und verwaltet werden kann wie lokale Ordner.

Keine Installation, keine Registry-Einträge, keine Änderungen am
Betriebssystem - alle Pfade werden relativ zum Programmordner aufgebaut.

## Download

Dieses Repository enthält ausschließlich fertig gebaute Beta-Versionen von
ZClone (eine einzelne, portable `ZClone.exe` als ZIP) zum direkten Download -
**kein Quellcode**. Aktuelle Beta: siehe [Releases](../../releases).

Der Quellcode liegt im separaten Haupt-Repository
[Temkina/ZClone](https://github.com/Temkina/ZClone).

## Lizenz

ZClone ist proprietäre, kostenlose Software - alle Rechte vorbehalten.
Lizenztext: [`ZClone-LICENSE.txt`](https://github.com/Temkina/ZClone/blob/master/Dokumentation/Lizenzen/ZClone-LICENSE.txt)
(liegt identisch auch in der heruntergeladenen ZIP unter
`Dokumentation\Lizenzen\` und ist aus der App heraus über "Optionen" &gt;
"ZClone" verlinkt).

Diese Lizenz gilt ausschließlich für den von Temkina selbst erstellten
Quellcode/die Anwendung ZClone (`src\`, siehe Haupt-Repository). Sie gilt
**nicht** für die mitgelieferten Drittanbieter-Komponenten - siehe nächster
Abschnitt.

## Drittanbieter-Komponenten

ZClone bindet folgende fertige Drittanbieter-Werkzeuge portabel mit ein -
bereits enthalten in der ZIP, kein separater Download nötig. Diese stehen
unter ihrer jeweils eigenen, unveränderten Originallizenz - **nicht** unter
der proprietären ZClone-Lizenz oben:

| Komponente | Datei (in der ZIP) | Lizenz | Lizenztext |
|---|---|---|---|
| [rclone](https://rclone.org/) (genauer: [rclone-extra](https://github.com/gulp79/rclone-extra)) | `Programme\Rclone\rclone.exe` | MIT | [`Rclone-LICENSE.txt`](https://github.com/Temkina/ZClone/blob/master/Dokumentation/Lizenzen/Rclone-LICENSE.txt) |
| [7-Zip](https://www.7-zip.org/) (`7za.exe`) | `Programme\7-Zip\7za.exe` | LGPL | [`7-Zip-LICENSE.txt`](https://github.com/Temkina/ZClone/blob/master/Dokumentation/Lizenzen/7-Zip-LICENSE.txt) |
| [Rufus](https://rufus.ie/) (`rufus.exe`) | `Programme\Rufus\rufus.exe` | GPLv3 | [`Rufus-LICENSE.txt`](https://github.com/Temkina/ZClone/blob/master/Dokumentation/Lizenzen/Rufus-LICENSE.txt) |

Diese Werkzeuge werden unverändert (bei rclone: als vom jeweiligen
Maintainer bereitgestellte Binaries) weitergegeben - siehe die Abschnitte
"Rclone", "7-Zip" und "Rufus" unten für Details zur jeweils verwendeten
Variante.

## Voraussetzungen

- Windows 10 oder 11
- Keine .NET-Installation nötig - die `ZClone.exe` in der ZIP ist
  self-contained und läuft direkt

Für das Rettungsmedium (Reiter "Rettungsmedium") ist **keine** zusätzliche
Installation nötig - Kernel, Bootloader und alle weiteren Bausteine des
eigenen, minimalen Linux-Live-Systems sind bereits fertig in der ZIP unter
`Programme\Bootdateien` enthalten.

## Rclone

`Programme\Rclone\rclone.exe` liegt bereits in der ZIP bei - nach dem
Entpacken ist rclone also sofort vorhanden, ohne separaten Download.

Verwendet wird dabei nicht das offizielle rclone von rclone.org, sondern das
von [gulp79](https://github.com/gulp79) gepflegte
[rclone-extra](https://github.com/gulp79/rclone-extra/releases/tag/v1.75.0-extra)
- ein Community-Fork, der zusätzliche Backends mitbringt, die im offiziellen
rclone (noch) nicht enthalten sind (u. a. Uloz.to und Teldrive, siehe die
entsprechenden Provider im Provider-Dialog).

`Konfiguration\` (Zugangsdaten/Remotes) ist nicht Teil der ZIP - Provider
müssen nach dem ersten Start jeweils selbst angelegt werden.

Lizenztext von rclone (MIT): [`Rclone-LICENSE.txt`](https://github.com/Temkina/ZClone/blob/master/Dokumentation/Lizenzen/Rclone-LICENSE.txt).

## 7-Zip

Für die optionale Passwort-Verschlüsselung (AES-256) fertiger Sicherungen
(Reiter "Sichern") wird das portable, standalone `7za.exe` genutzt - liegt
analog zu rclone bereits unter `Programme\7-Zip\7za.exe` in der ZIP bei,
kein separater Download nötig.

Lizenztext von 7-Zip (LGPL): [`7-Zip-LICENSE.txt`](https://github.com/Temkina/ZClone/blob/master/Dokumentation/Lizenzen/7-Zip-LICENSE.txt).

## Rufus

Im Reiter "Rettungsmedium" gibt es neben "Als ISO-Datei erstellen …" und
"Direkt auf USB-Stick schreiben …" (UEFI-only) einen dritten Knopf "Rufus
starten (ISO auf Stick schreiben) …" - startet das portable, unverändert
mitgelieferte `Programme\Rufus\rufus.exe`, mit dem sich eine zuvor erstellte
ZClone-ISO auch BIOS/Legacy-startfähig auf einen Stick schreiben lässt
(für Geräte ohne UEFI bzw. mit eingeschränkter SecureBoot-Firmware). Ist
`rufus.exe` ausnahmsweise nicht vorhanden, öffnet der Knopf ersatzweise
[rufus.ie](https://rufus.ie/) im Standardbrowser. ZClone greift dabei selbst
zu keinem Zeitpunkt auf einen Datenträger zu - das eigentliche Schreiben
übernimmt ausschließlich Rufus.

Lizenztext von Rufus (GPLv3): [`Rufus-LICENSE.txt`](https://github.com/Temkina/ZClone/blob/master/Dokumentation/Lizenzen/Rufus-LICENSE.txt).

## Funktionsumfang

- Dual-Pane-Explorer: Ordnerbaum links über die volle Höhe (inkl. Rclone-
  Remotes), rechts Adressleiste/Liste/Buttonleiste/Status.
- Kopieren/Verschieben/Löschen/Umbenennen/Neuer Ordner/Alle markieren, per
  Button und per Rechtsklick-Kontextmenü - auch zu/von Rclone-Remotes, mit
  laufendem Fortschritt und Abbrechen-Option.
- Drag &amp; Drop von Dateien/Ordnern zwischen den beiden Panes (Strg gedrückt
  halten für Kopieren statt Verschieben).
- Rclone-Anbindung: Provider anlegen/bearbeiten/löschen (inkl. Rohdaten-
  Bearbeitung), Mounten als Windows-Laufwerk (auch automatisch beim
  Programmstart), Konfigurationsverschlüsselung.
- Windows-Explorer-Kontextmenü-Integration ("ZClone: Hochladen",
  verschlüsselt/unverschlüsselt, nur für den aktuellen Benutzer).
- Sicherung (Reiter "Sichern"): eigenes Sektor-Abbildformat (`.zdi`) für
  ganze Datenträger oder einzeln ausgewählte Partitionen (inkl. optionaler
  Bootloader-Partitionen für Bare-Metal-Restore), auf Wunsch nur der
  tatsächlich belegte Speicherplatz, konsistentes Lesen offener Laufwerke
  per Schattenkopie (VSS), Größenschätzung/Warnung bei zu wenig Zielplatz
  sowie eine eigene Integritätsprüfung für bestehende `.zdi`-Dateien.
- Wiederherstellung (Reiter "Wiederherstellen"): Rückspielen einzelner
  Nicht-System-Laufwerke direkt aus ZClone heraus.
- Rettungsmedium (Reiter "Rettungsmedium"): eigenes, minimales
  Linux-Live-System (Kernel + Busybox, kein Windows ADK nötig) als
  bootfähige ISO (BIOS **und** UEFI im selben Hybrid-Medium) oder direkt
  auf einen USB-Stick geschrieben (UEFI; für BIOS/Legacy-Sticks alternativ
  über den mitgelieferten Rufus, siehe oben) - für die Wiederherstellung
  der aktiven Systemplatte, die aus einem laufenden Windows heraus nicht
  überschrieben werden kann. Bootet automatisch in das mitgelieferte
  `ZRestore` (Textoberfläche) mit drei Wiederherstellungswegen: lokaler
  Pfad, SMB-Netzwerkfreigabe oder Cloud über ein im Medium eingebettetes
  rclone. BitLocker-verschlüsselte Datenträger lassen sich per
  Wiederherstellungsschlüssel/-passwort oder per externer `.bek`-
  Schlüsseldatei entsperren (wird auf angeschlossenen Laufwerken
  automatisch gesucht) - eine TPM+PIN-Entsperrung ist von einem externen
  Medium aus grundsätzlich nicht möglich (siehe `Dokumentation/
  Rettungsmedium.md` im Haupt-Repository für die technische Begründung).
  UEFI SecureBoot wird über einen von Microsoft signierten Shim plus ein
  selbst gebautes, selbst signiertes GRUB unterstützt - beim ersten
  SecureBoot-Start ist einmalig ein manuelles Zertifikats-Enrollment über
  Shims MokManager nötig (Details siehe dort). Per Hyper-V-VM-Boot-Test
  verifiziert (BIOS- und UEFI-Pfad booten beide bis zur ZRestore-Oberfläche
  durch); ein erster echter Hardware-Boot (BIOS/Legacy per Rufus) gelang
  ebenfalls, ein Test gegen ein echtes BitLocker-Volume sowie ein
  erfolgreiches SecureBoot-Enrollment auf funktionierender Hardware stehen
  noch aus.
- Enterprise-Funktionen (Reiter "Enterprise"): optionales Rollback-Journal
  für die Wiederherstellung - sichert vor jedem Schreibvorgang die alten
  Sektoren und rollt bei einem Fehler automatisch zurück.
- Hell/Dunkel-Design (auch per Schnellwechsel im Menü "Ansicht"),
  natürliche/numerische Sortierung, gekürzte Dateinamen, Toast-
  Benachrichtigungen, Windows-typische Datei-/Ordner-/Laufwerkssymbole,
  Einzelinstanz-Sicherung u. v. m.
- Protokolle als ZIP exportieren (Optionen &gt; Logging) - für die Weitergabe
  an den Entwickler bei Problemen, bewusst ohne Konfiguration/Zugangsdaten.
- Sponsor-Tab in den Optionen mit Links zu GitHub, Telegram, PayPal und
  Stripe für freiwillige Unterstützung des Projekts.
