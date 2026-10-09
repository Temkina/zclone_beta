# ZClone Beta

Fertig gebaute Beta-Versionen von **ZClone** - einem vollständig portablen
Dual-Pane-Dateimanager für Windows 10/11 mit rclone-Anbindung (Cloud-Speicher
wie Google Drive, WebDAV, S3-kompatible Anbieter u. v. m.), Synchronisation,
Datenträger-Sicherung (`.zdi`) und eigenem Linux-Rettungsmedium.

Dieses Repository enthält **keinen Quellcode**, sondern nur die Releases.

## Download

1. Unter [Releases](https://github.com/Temkina/zclone_beta/releases/latest) die Datei `ZClone.zip` der neuesten Version herunterladen.
2. ZIP in einen beliebigen Ordner entpacken (z. B. auf einen USB-Stick oder nach `C:\ZClone`).
3. `ZClone.exe` starten.

## Voraussetzungen

- Windows 10 oder Windows 11 (64 Bit)
- keine Installation, keine Registry-Einträge, keine Änderungen am Betriebssystem
- keine .NET-Installation nötig: `ZClone.exe` ist eine einzelne, eigenständige Datei
- rclone, 7-Zip und Rufus liegen im Ordner `Programme` bereits bei

Alle Einstellungen, Protokolle und Zugangsdaten bleiben im Programmordner.
Der Ordner `Konfiguration` enthält deine Provider-Zugangsdaten - bitte
niemals weitergeben oder veröffentlichen.

## Updates

In ZClone: Menü „Optionen“ → „Nach Updates suchen…“. Dabei wird die jeweils
neueste Version dieses Repositorys geprüft.

## Hilfe und Support

- Handbuch in der App: „Optionen“ → „Handbuch“
- Fragen, Probleme, Vorschläge: Telegram-Supportforum [t.me/ZClone_N](https://t.me/ZClone_N)
- Bei Problemen die Protokolle über „Optionen“ → „Einstellungen“ → Reiter „Logging“ als ZIP exportieren und mitschicken (enthält bewusst keine Zugangsdaten).

## Lizenz

ZClone ist proprietäre, kostenlose Software - alle Rechte vorbehalten.
Der Lizenztext liegt im ZIP unter `Dokumentation\Lizenzen\ZClone-LICENSE.txt`.

Die mitgelieferten Drittanbieter-Werkzeuge stehen unter ihren eigenen,
unveränderten Lizenzen (ebenfalls unter `Dokumentation\Lizenzen`):

| Komponente | Lizenz |
|---|---|
| [rclone](https://rclone.org/) (rclone-extra von [gulp79](https://github.com/gulp79/rclone-extra)) | MIT |
| [7-Zip](https://www.7-zip.org/) (`7za.exe`) | LGPL |
| [Rufus](https://rufus.ie/) (`rufus.exe`) | GPLv3 |
