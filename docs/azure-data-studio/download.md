---
title: Zur Installation herunterladen können Sie
titleSuffix: Azure Data Studio
description: Herunterladen und installieren Sie Azure Data Studio für Windows, MacOS oder Linux
ms.custom: seodec18
ms.date: 01/10/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d7e9cd2130487a0ac50d6aa55a8a2e0f9cf9e80c
ms.sourcegitcommit: 96032813f6bf1cba680b5e46d82ae1f0f2da3d11
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54298717"
---
# <a name="download-and-install-azure-data-studio"></a>Herunterladen und Installieren von Azure Data Studio

  > [!div class="nextstepaction"]
  > [Teilen Sie uns Ihr Feedback zu SQL-Dokumentation des Inhaltsverzeichnisses!](https://aka.ms/sqldocsurvey)

[!INCLUDE[name-sos](../includes/name-sos.md)] auf Windows, MacOS und Linux ausgeführt wird.


Herunterladen und installieren die neueste Version der *Release von Januar*:

> [!NOTE]
> Wenn Sie über SQL Operations Studio aktualisieren und Ihre Einstellungen, Tastenkombinationen in Visual Studio oder Codeausschnitte beibehalten möchten, finden Sie unter [verschieben benutzereinstellungen](#move-user-settings).

|Platform|Herunterladen|Veröffentlichungsdatum| Version |
|:---|:---|:---|:---|
|Windows|[Installationsprogramm für Benutzer (empfohlen)](https://go.microsoft.com/fwlink/?linkid=2049972)<br>[System-Installer](https://go.microsoft.com/fwlink/?linkid=2049975)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=2050146)|09 Januar 2019 |1.3.8|
|macOS|[.zip](https://go.microsoft.com/fwlink/?linkid=2049981)|09 Januar 2019 |1.3.8|
|Linux|[.deb](https://go.microsoft.com/fwlink/?linkid=2050157)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=2049989)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=2049986)|09 Januar 2019 |1.3.8|

Weitere Informationen über die neueste Version finden Sie unter den [Anmerkungen zu dieser Version](release-notes.md).

## <a name="get-azure-data-studio-for-windows"></a>Azure Data-Studio für Windows herunterladen

Diese Version von [!INCLUDE[name-sos](../includes/name-sos-short.md)] enthält eine standardmäßige Windows Installer-Erfahrung und ZIP-Datei:

**Installationsprogramm Benutzer** (empfohlen)

Das Installationsprogramm für Benutzer wird empfohlen, da es keine Administratorrechte verfügt, benötigt wird, die sowohl Installationen und Upgrades vereinfacht.

1. Herunterladen und Ausführen der [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] *Benutzer* Installer für Windows](https://go.microsoft.com/fwlink/?linkid=2049972).
2. Starten Sie den [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] app.

**System-Installer**

1. Herunterladen und Ausführen der [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] *System* Installer für Windows](https://go.microsoft.com/fwlink/?linkid=2049975).
2. Starten Sie den [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] app.


**zip-Datei**

1. Herunterladen [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] ZIP für Windows](https://go.microsoft.com/fwlink/?linkid=2050146).
2. Suchen Sie die heruntergeladene Datei, und extrahieren Sie sie.
3. Ausführen von `\azuredatastudio-windows\azuredatastudio.exe`


## <a name="get-azure-data-studio-for-macos"></a>Abrufen von Azure Data Studio für macOS

1. Herunterladen [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] für MacOS](https://go.microsoft.com/fwlink/?linkid=2049981).
2. Doppelklicken Sie darauf, um den Inhalt der ZIP-Datei zu erweitern.
3. Vornehmen [!INCLUDE[name-sos](../includes/name-sos-short.md)] zur Verfügung, in der *Launchpad*, ziehen Sie *Azure Daten Studio.app* auf die *Anwendungen* Ordner.


## <a name="get-azure-data-studio-for-linux"></a>Azure Data-Studio für Linux herunterladen

1. Herunterladen [!INCLUDE[name-sos](../includes/name-sos-short.md)] für Linux mithilfe eines der Installationsprogramme oder das Archiv für die ".TAR.gz":
    - [.deb](https://go.microsoft.com/fwlink/?linkid=2050157)
    - [.rpm](https://go.microsoft.com/fwlink/?linkid=2049989)
    - [.tar.gz](https://go.microsoft.com/fwlink/?linkid=2049986)
1. Extrahieren Sie die Datei, und starten Sie [!INCLUDE[name-sos](../includes/name-sos-short.md)], öffnen Sie ein neues Terminalfenster, und geben Sie die folgenden Befehle:

   **Debian-Installation:**
   ```bash
   cd ~
   sudo dpkg -i ./Downloads/azuredatastudio-linux-<version string>.deb

   azuredatastudio
   ```

   **u/Min Installation:**
   ```bash
   cd ~
   yum install ./Downloads/azuredatastudio-linux-<version string>.rpm

   azuredatastudio
   ```

   **.tar.gz Installation:**
   ```bash 
   cd ~ 
   cp ~/Downloads/azuredatastudio-linux-<version string>.tar.gz ~ 
   tar -xvf ~/azuredatastudio-linux-<version string>.tar.gz 
   echo 'export PATH="$PATH:~/azuredatastudio-linux-x64"' >> ~/.bashrc
   source ~/.bashrc 
   azuredatastudio 
   ``` 

   > [!NOTE]
   > Für Debian, Red hat und Ubuntu müssen Sie möglicherweise fehlende Abhängigkeiten. Verwenden Sie die folgenden Befehle aus, um diese Abhängigkeiten abhängig von Ihrer Version von Linux zu installieren:
   

   **Debian:** 
   ```bash
   sudo apt-get install libunwind8
   ```

   **Redhat:** 
   ```bash
   yum install libXScrnSaver
   ```

   **Ubuntu:** 
   ```bash
   sudo apt-get install libxss1

   sudo apt-get install libgconf-2-4

   sudo apt-get install libunwind8
   ```


## <a name="uninstall-azure-data-studio"></a>Deinstallieren Sie Azure Data Studio

Wenn Sie installiert [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] mit dem Windows-Installer, deinstallieren Sie die gleiche Weise, wie Sie eine Windows-Anwendung entfernen.

Wenn Sie installiert [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] mit ZIP-Datei oder andere archivieren, löschen Sie anschließend einfach die Dateien.

## <a name="supported-operating-systems"></a>Unterstützte Betriebssysteme

[!INCLUDE[name-sos](../includes/name-sos-short.md)] unter Windows, MacOS und Linux ausgeführt wird, und wird auf folgenden Plattformen unterstützt:

### <a name="windows"></a>Windows
- Windows 10 (64-Bit)
- Windows 8.1 (64-Bit)
- Windows 8 (64-Bit)
- Erfordert Windows 7 (SP1) (64-Bit) - [KB2533623](https://www.microsoft.com/download/details.aspx?id=26767)
- Windows Server 2016
- Windows Server 2012 R2 (64-Bit)
- Windows Server 2012 (64-Bit)
- Windows Server 2008 R2 (64-Bit)

### <a name="macos"></a>macOS
- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux"></a>Linux
- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="recommended-system-requirements"></a>Empfohlene Systemanforderungen
Verwenden Sie um eine optimale benutzererfahrung die empfohlenen Systemanforderungen.

|             | CPU-Kerne | Speicher/RAM |
|:-----------:|:---------:|:----------:|
| Empfohlen |     4     |      8     |
|   Minimum   |     2     |      4     |
|             |           |            |

## <a name="check-for-updates"></a>Nach Updates suchen
Um die neuesten Updates zu überprüfen, klicken Sie auf das Zahnradsymbol unten links des Fensters, und klicken Sie auf **nach Updates suchen**

## <a name="supported-sql-offerings"></a>Unterstützte SQL-Angebote

* Diese Version von Azure Data Studio funktioniert mit allen [unterstützten Versionen von SQL Server 2014 - [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] ](https://support.microsoft.com/lifecycle?C2=1044) und bietet Unterstützung für die Arbeit mit den neuesten cloudfeatures in Azure SQL-Datenbank und Azure SQL Data Warehouse. Azure Data Studio bietet auch vorschauunterstützung für verwaltete Azure SQL-Instanz.

## <a name="upgrade-from-sql-operations-studio"></a>Upgrade von SQL Operations Studio

Wenn Sie SQL Operations Studio weiterhin verwenden möchten, müssen Sie ein Upgrade auf Azure Data Studio durchführen. SQL Operations Studio war die Preview-Namen und die Preview-Version von Azure Data Studio. Im September 2018 wir [den Namen in Azure Data Studio geändert](https://cloudblogs.microsoft.com/sqlserver/2018/09/25/azure-data-studio-for-sql-server/) und der allgemeinen Verfügbarkeit (GA) Version veröffentlicht. Da SQL Operations Studio ist nicht mehr aktualisiert oder unterstützt, bitten wir alle SQL Operations Studio-Benutzer von Azure Data Studio, um die neuesten Features, Sicherheitsupdates, erhalten die neueste Version herunterladen und Korrekturen.
 
Beim Upgrade von der alten Vorschauversion auf die neuesten Studio für Azure Data verlieren Sie Ihre aktuellen Einstellungen und Erweiterungen. Um Ihre Einstellungen zu verschieben, folgen Sie die Anweisungen in der folgenden *verschieben benutzereinstellungen* Abschnitt:


## <a name="move-user-settings"></a>Verschieben von benutzereinstellungen

Wenn Sie Ihre benutzerdefinierten Einstellungen, Tastenkombinationen in Visual Studio oder Codeausschnitte verschieben möchten, führen Sie die folgenden Schritte aus. Dies ist wichtig, wenn Sie SQL Operations Studio-Version auf Azure Data Studio aktualisieren.

*Wenn Sie bereits über Azure Data Studio verfügen oder Sie nicht installiert oder SQL Operations Studio angepasst haben, können Sie diesen Abschnitt ignorieren.*


1. Öffnen Sie Einstellungen, indem Sie auf das Zahnradsymbol auf der linken unteren und auf **Einstellungen.**

   ![open-settings](./media/download/open-settings.png)

2. Mit der rechten Maustaste die **Benutzereinstellungen** Registerkarte im Vordergrund, und klicken Sie auf **im Explorer anzeigen**

   ![Anzeigen-in-explorer](./media/download/reveal-in-explorer.png)

3. Kopieren Sie alle Dateien in diesem Ordner, und speichern Sie in einem übersichtlichen Ort auf dem lokalen Laufwerk, z. B. Ihren Dokumentordner finden.

   ![Einstellungen kopieren](./media/download/copy-settings.png)

4. Führen Sie die Schritte, die 1-2, wählen Sie unter Schritt 3 Fügen Sie den Inhalt, die Sie gespeichert, aufgerufen werden, in den Ordner, in Ihrer neuen Version von Azure Data Studio. Sie können auch manuell über die Einstellungen, Keybindings oder Codeausschnitte in ihren entsprechenden Speicherorten kopieren.

5. Wenn eine vorhandene Installation außer Kraft gesetzt werden, löschen Sie das alte Installationsverzeichnis vor der Installation zur Vermeidung von Fehlern, die mit Ihrem Azure-Konto für den Ressourcen-Explorer.

## <a name="next-steps"></a>Nächste Schritte

Finden Sie in der folgenden schnellstartanleitungen für den Einstieg:
- [Verbinden und Abfragen von SQLServer](quickstart-sql-server.md)
- [Verbinden und Abfragen von Azure SQL-Datenbank](quickstart-sql-database.md)
- [Verbinden und Abfragen von Azure Datawarehouse](quickstart-sql-dw.md)

Mitwirken an [!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/azuredatastudio](https://github.com/Microsoft/azuredatastudio) 

[Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=521839) und [Sammlung von Verwendungsdaten](usage-data-collection.md).
