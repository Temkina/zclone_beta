# ZClone

ZClone ist ein vollstaendig portabler Dual-Pane-Dateimanager fuer Windows
10/11, geschrieben in C#/.NET 8 (Windows Forms). Er kombiniert eine klassische
Zwei-Fenster-Explorer-Ansicht mit einer Anbindung an
[rclone](https://github.com/rclone/rclone) ([rclone.org](https://rclone.org/)),
sodass Cloud-Speicher (Google Drive, WebDAV, S3-kompatible Anbieter usw.)
genauso durchsucht, kopiert und verwaltet werden kann wie lokale Ordner.

Keine Installation, keine Registry-Eintraege, keine Aenderungen am
Betriebssystem - alle Pfade werden relativ zum Programmordner aufgebaut.

## Download

Dieses Repository enthaelt ausschliesslich fertig gebaute Beta-Versionen von
ZClone (eine einzelne, portable `ZClone.exe` als ZIP) zum direkten Download -
**kein Quellcode**. Aktuelle Beta: siehe [Releases](../../releases).

Der Quellcode liegt im separaten Haupt-Repository
[Temkina/ZClone](https://github.com/Temkina/ZClone).

## Lizenz

ZClone ist proprietaere, kostenlose Software - alle Rechte vorbehalten.
Lizenztext: [`ZClone-LICENSE.txt`](https://github.com/Temkina/ZClone/blob/master/Dokumentation/Lizenzen/ZClone-LICENSE.txt)
(liegt identisch auch in der heruntergeladenen ZIP unter
`Dokumentation\Lizenzen\` und ist aus der App heraus ueber "Optionen" &gt;
"ZClone" verlinkt).

Diese Lizenz gilt ausschliesslich fuer den von Temkina selbst erstellten
Quellcode/die Anwendung ZClone (`src\`, siehe Haupt-Repository). Sie gilt
**nicht** fuer die mitgelieferten Drittanbieter-Komponenten - siehe naechster
Abschnitt.

## Drittanbieter-Komponenten

ZClone bindet folgende fertige Drittanbieter-Werkzeuge portabel mit ein -
bereits enthalten in der ZIP, kein separater Download noetig. Diese stehen
unter ihrer jeweils eigenen, unveraenderten Originallizenz - **nicht** unter
der proprietaeren ZClone-Lizenz oben:

| Komponente | Datei (in der ZIP) | Lizenz | Lizenztext |
|---|---|---|---|
| [rclone](https://rclone.org/) (genauer: [rclone-extra](https://github.com/gulp79/rclone-extra)) | `Programme\Rclone\rclone.exe` | MIT | [`Rclone-LICENSE.txt`](https://github.com/Temkina/ZClone/blob/master/Dokumentation/Lizenzen/Rclone-LICENSE.txt) |
| [7-Zip](https://www.7-zip.org/) (`7za.exe`) | `Programme\7-Zip\7za.exe` | LGPL | [`7-Zip-LICENSE.txt`](https://github.com/Temkina/ZClone/blob/master/Dokumentation/Lizenzen/7-Zip-LICENSE.txt) |
| [Rufus](https://rufus.ie/) (`rufus.exe`) | `Programme\Rufus\rufus.exe` | GPLv3 | [`Rufus-LICENSE.txt`](https://github.com/Temkina/ZClone/blob/master/Dokumentation/Lizenzen/Rufus-LICENSE.txt) |

Diese Werkzeuge werden unveraendert (bei rclone: als vom jeweiligen
Maintainer bereitgestellte Binaries) weitergegeben - siehe die Abschnitte
"Rclone", "7-Zip" und "Rufus" unten fuer Details zur jeweils verwendeten
Variante.

## Voraussetzungen

- Windows 10 oder 11
- Keine .NET-Installation noetig - die `ZClone.exe` in der ZIP ist
  self-contained und laeuft direkt

Fuer das Rettungsmedium (Reiter "Rettungsmedium") ist **keine** zusaetzliche
Installation noetig - Kernel, Bootloader und alle weiteren Bausteine des
eigenen, minimalen Linux-Live-Systems sind bereits fertig in der ZIP unter
`Programme\Bootdateien` enthalten.

## Rclone

`Programme\Rclone\rclone.exe` liegt bereits in der ZIP bei - nach dem
Entpacken ist rclone also sofort vorhanden, ohne separaten Download.

Verwendet wird dabei nicht das offizielle rclone von rclone.org, sondern das
von [gulp79](https://github.com/gulp79) gepflegte
[rclone-extra](https://github.com/gulp79/rclone-extra/releases/tag/v1.75.0-extra)
- ein Community-Fork, der zusaetzliche Backends mitbringt, die im offiziellen
rclone (noch) nicht enthalten sind (u. a. Uloz.to und Teldrive, siehe die
entsprechenden Provider im Provider-Dialog).

`Konfiguration\` (Zugangsdaten/Remotes) ist nicht Teil der ZIP - Provider
muessen nach dem ersten Start jeweils selbst angelegt werden.

Lizenztext von rclone (MIT): [`Rclone-LICENSE.txt`](https://github.com/Temkina/ZClone/blob/master/Dokumentation/Lizenzen/Rclone-LICENSE.txt).

## 7-Zip

Fuer die optionale Passwort-Verschluesselung (AES-256) fertiger Sicherungen
(Reiter "Sichern") wird das portable, standalone `7za.exe` genutzt - liegt
analog zu rclone bereits unter `Programme\7-Zip\7za.exe` in der ZIP bei,
kein separater Download noetig.

Lizenztext von 7-Zip (LGPL): [`7-Zip-LICENSE.txt`](https://github.com/Temkina/ZClone/blob/master/Dokumentation/Lizenzen/7-Zip-LICENSE.txt).

## Rufus

Im Reiter "Rettungsmedium" gibt es neben "Als ISO-Datei erstellen …" und
"Direkt auf USB-Stick schreiben …" (UEFI-only) einen dritten Knopf "Rufus
starten (ISO auf Stick schreiben) …" - startet das portable, unveraendert
mitgelieferte `Programme\Rufus\rufus.exe`, mit dem sich eine zuvor erstellte
ZClone-ISO auch BIOS/Legacy-startfaehig auf einen Stick schreiben laesst
(fuer Geraete ohne UEFI bzw. mit eingeschraenkter SecureBoot-Firmware). Ist
`rufus.exe` ausnahmsweise nicht vorhanden, oeffnet der Knopf ersatzweise
[rufus.ie](https://rufus.ie/) im Standardbrowser. ZClone greift dabei selbst
zu keinem Zeitpunkt auf einen Datentraeger zu - das eigentliche Schreiben
uebernimmt ausschliesslich Rufus.

Lizenztext von Rufus (GPLv3): [`Rufus-LICENSE.txt`](https://github.com/Temkina/ZClone/blob/master/Dokumentation/Lizenzen/Rufus-LICENSE.txt).

## Funktionsumfang

- Dual-Pane-Explorer: Ordnerbaum links ueber die volle Hoehe (inkl. Rclone-
  Remotes), rechts Adressleiste/Liste/Buttonleiste/Status.
- Kopieren/Verschieben/Löschen/Umbenennen/Neuer Ordner/Alle markieren, per
  Button und per Rechtsklick-Kontextmenue - auch zu/von Rclone-Remotes, mit
  laufendem Fortschritt und Abbrechen-Option.
- Drag &amp; Drop von Dateien/Ordnern zwischen den beiden Panes (Strg gedrueckt
  halten fuer Kopieren statt Verschieben).
- Rclone-Anbindung: Provider anlegen/bearbeiten/loeschen (inkl. Rohdaten-
  Bearbeitung), Mounten als Windows-Laufwerk (auch automatisch beim
  Programmstart), Konfigurationsverschluesselung.
- Windows-Explorer-Kontextmenue-Integration ("ZClone: Hochladen",
  verschluesselt/unverschluesselt, nur fuer den aktuellen Benutzer).
- Sicherung (Reiter "Sichern"): eigenes Sektor-Abbildformat (`.zdi`) fuer
  ganze Datentraeger oder einzeln ausgewaehlte Partitionen (inkl. optionaler
  Bootloader-Partitionen fuer Bare-Metal-Restore), auf Wunsch nur der
  tatsaechlich belegte Speicherplatz, konsistentes Lesen offener Laufwerke
  per Schattenkopie (VSS), Groessenschaetzung/Warnung bei zu wenig Zielplatz
  sowie eine eigene Integritaetspruefung fuer bestehende `.zdi`-Dateien.
- Wiederherstellung (Reiter "Wiederherstellen"): Rueckspielen einzelner
  Nicht-System-Laufwerke direkt aus ZClone heraus.
- Rettungsmedium (Reiter "Rettungsmedium"): eigenes, minimales
  Linux-Live-System (Kernel + Busybox, kein Windows ADK noetig) als
  bootfaehige ISO (BIOS **und** UEFI im selben Hybrid-Medium) oder direkt
  auf einen USB-Stick geschrieben (UEFI; fuer BIOS/Legacy-Sticks alternativ
  ueber den mitgelieferten Rufus, siehe oben) - fuer die Wiederherstellung
  der aktiven Systemplatte, die aus einem laufenden Windows heraus nicht
  ueberschrieben werden kann. Bootet automatisch in das mitgelieferte
  `ZRestore` (Textoberflaeche) mit drei Wiederherstellungswegen: lokaler
  Pfad, SMB-Netzwerkfreigabe oder Cloud ueber ein im Medium eingebettetes
  rclone. BitLocker-verschluesselte Datentraeger lassen sich per
  Wiederherstellungsschluessel/-passwort oder per externer `.bek`-
  Schluesseldatei entsperren (wird auf angeschlossenen Laufwerken
  automatisch gesucht) - eine TPM+PIN-Entsperrung ist von einem externen
  Medium aus grundsaetzlich nicht moeglich (siehe `Dokumentation/
  Rettungsmedium.md` im Haupt-Repository fuer die technische Begruendung).
  UEFI SecureBoot wird ueber einen von Microsoft signierten Shim plus ein
  selbst gebautes, selbst signiertes GRUB unterstuetzt - beim ersten
  SecureBoot-Start ist einmalig ein manuelles Zertifikats-Enrollment ueber
  Shims MokManager noetig (Details siehe dort). Per Hyper-V-VM-Boot-Test
  verifiziert (BIOS- und UEFI-Pfad booten beide bis zur ZRestore-Oberflaeche
  durch); ein erster echter Hardware-Boot (BIOS/Legacy per Rufus) gelang
  ebenfalls, ein Test gegen ein echtes BitLocker-Volume sowie ein
  erfolgreiches SecureBoot-Enrollment auf funktionierender Hardware stehen
  noch aus.
- Enterprise-Funktionen (Reiter "Enterprise"): optionales Rollback-Journal
  fuer die Wiederherstellung - sichert vor jedem Schreibvorgang die alten
  Sektoren und rollt bei einem Fehler automatisch zurueck.
- Hell/Dunkel-Design (auch per Schnellwechsel im Menue "Ansicht"),
  natuerliche/numerische Sortierung, gekuerzte Dateinamen, Toast-
  Benachrichtigungen, Windows-typische Datei-/Ordner-/Laufwerkssymbole,
  Einzelinstanz-Sicherung u. v. m.
- Protokolle als ZIP exportieren (Optionen &gt; Logging) - fuer die Weitergabe
  an den Entwickler bei Problemen, bewusst ohne Konfiguration/Zugangsdaten.
- Sponsor-Tab in den Optionen mit Links zu GitHub, Telegram, PayPal und
  Stripe fuer freiwillige Unterstuetzung des Projekts.
