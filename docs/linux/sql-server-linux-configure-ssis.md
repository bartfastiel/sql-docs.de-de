---
title: Konfigurieren von SSIS unter Linux mit Ssis-Conf | Microsoft Docs
description: In diesem Artikel wird das Konfigurieren von SQL Server Integration Services unter Linux mit dem Ssis-Conf-Dienstprogramm veranschaulicht.
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.date: 09/26/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 46327772e8c22f76770bc51f72817ceedffae469
ms.contentlocale: de-de
ms.lasthandoff: 09/27/2017

---
# <a name="configure-sql-server-integration-services-on-linux-with-ssis-conf"></a>Konfigurieren von SQL Server Integration Services unter Linux mit Ssis-conf

`ssis-conf`ist ein Konfigurationsskript, die bei Installation von SQL Server Integration Services (SSIS) für Red Hat Enterprise Linux und Ubuntu. Sie können dieses Hilfsprogramm verwenden, so konfigurieren Sie die folgenden Eigenschaften:

| Befehl | Description |
|-------------|---------------------------------------------------------------------|
| Set-edition | Legen Sie die Edition von SQL Server                                       |
| Telemetrie   | Aktivieren Sie oder deaktivieren Sie der telemetriedienst für SQL Server Integration Services |
| Setup       | Initialisieren und Einrichten von Microsoft SQL Server Integration Services      |
|||

## <a name="how-to-run-ssis-conf"></a>Zum Ausführen von Ssis-conf

In den Beispielen in diesem Artikel ausführen `ssis-conf` durch den vollständigen Pfad angeben: `/opt/ssis/bin/ssis-conf`. Wenn Sie zu, dass der Pfad navigieren, vor dem Ausführen von `ssis-conf`, führen Sie das Hilfsprogramm im Kontext des aktuellen Verzeichnisses: `./ssis-conf`.

Stellen Sie sicher, dass Sie die Befehle in diesem Artikel mit Root-Berechtigung beschrieben ausführen. Führen Sie z. B. `sudo /opt/ssis/bin/ssis-conf setup` und nicht `/opt/ssis/bin/ssis-conf setup`.

Führen Sie diese Befehle mit Abfragen in der Sprache, die Sie lieber können Sie ein Gebietsschema angeben. Führen Sie z. B. aufforderungen Chinesisch erhalten den folgenden Befehl ein:

`sudo LC_ALL=zh_CN.UTF-8 /opt/ssis/bin/ssis-conf setup`.

## <a name="use-set-edition-to-set-the-edition-of-sql-server-integration-services"></a>Verwenden Sie Set-Edition, um die Edition von SQL Server Integration Services festzulegen

Die Edition von SSIS wird mit der Edition von SQL Server ausgerichtet.

Geben Sie den folgenden Befehl ein:

`$ sudo /opt/ssis/bin/ssis-conf set-edition`

Nachdem Sie den Befehl eingegeben haben, wird die folgende Meldung angezeigt:

```
Choose an edition of SQL Server:

1) Evaluation (free, no production use rights, 180-day limit)

2) Developer (free, no production use rights)

3) Express (free)

4) Web (PAID)

5) Standard (PAID)

6) Enterprise (PAID)

7) Enterprise Core (PAID)

8) I bought a license through a retail sales channel and have a product key to enter.

Details about editions can be found at

https://go.microsoft.com/fwlink/?LinkId=852748&clcid=0x409

Use of PAID editions of this software requires separate licensing through a

Microsoft Volume Licensing program.

By choosing a PAID edition, you are verifying that you have the appropriate

number of licenses in place to install and run this software.

Enter your edition(1-8):
```

Wenn geben Sie einen Wert zwischen 1 und 7, das System konfiguriert eine Edition kostenlose oder bezahlte. Wenn Sie auf "8" eingeben, fordert das Dienstprogramm Sie den Product Key eingeben, den Sie gekauft haben:

```
Enter the 25-character product key:
```

## <a name="use-telemetry-to-configure-customer-feedback"></a>Verwenden Sie Telemetrie, um Kundenfeedback zu konfigurieren

Die `telemetry` Befehl wird bestimmt, ob SSIS Feedback an Microsoft sendet.

Für kostenlose Editionen (d. h. Express, Developer und Evaluation-Editionen) ist der telemetriedienst immer aktiviert. Wenn Sie eine kostenlose Edition haben, können keine der `telemetry` Befehl zum Deaktivieren der Telemetrie.

Geben Sie den folgenden Befehl ein:

`$ sudo /opt/ssis/bin/ssis-conf telemetry`

Nachdem Sie den Befehl eingegeben haben, sehen Sie für kostenpflichtige Edition die folgende Meldung angezeigt:

```
Send feature usage data to Microsoft. Feature usage data includes information
about your hardware configuration and how you use SQL Server Integration Services.

[Yes/No]:
```

Wenn wählen **Ja**, der telemetriedienst aktiviert ist und ausgeführt wird. Der Dienst automatisch-startet nach jedem Startvorgang. Wenn wählen **keine**, der telemetriedienst beendet und ist deaktiviert.

## <a name="use-setup-to-initialize-and-set-up-microsoft-sql-server-integration-services"></a>Mithilfe von Setup initialisieren und Einrichten von Microsoft SQL Server Integration Services

Verwenden der `setup` Befehl jedes Mal, wenn Sie SSIS installieren.

Geben Sie den folgenden Befehl ein:

`sudo /opt/ssis/bin/ssis-conf setup`

Das Dienstprogramm fordert Sie zu bestätigen oder geben Sie Werte für die folgenden Elemente:
-   Produktlizenz
-   Endbenutzer-Lizenzvertrag
-   Telemetriedienst
-   Die von Integration Services verwendete Sprache

Zum Ausführen der `setup` Befehl mit den Anweisungen in der Sprache, mit dem Sie es vorziehen, können Sie ein Gebietsschema angeben. Angenommen, um aufforderungen Chinesisch anzuzeigen, führen den folgenden Befehl: `sudo LC_ALL=zh_CN.UTF-8 /opt/ssis/bin/ssis-conf setup`.

## <a name="ssisconf-format"></a>SSIS.conf-format

Die folgenden `/var/opt/ssis/ssis.conf` Datei bietet ein Beispiel für jede Einstellung.

Für SQL Server, können Sie Systemeinstellungen ändern, indem die Werte in der `mssql.conf` Datei. Für SSIS die Sie **kann nicht** Systemeinstellungen ändern, indem Sie die Werte in der `ssis.conf` Datei. Die `ssis.conf` Datei zeigt nur die Ergebnisse des Setups. Wenn Sie die Einstellungen für SSIS ändern möchten, können Sie löschen die `ssis.conf` , und führen Sie die `setup` erneut aus.

Hier ist ein Beispiel für `ssis.conf` Datei. Jedes Feld entspricht das Ergebnis des einschrittigen Installation.

```
[LICENSE]
                       
registered = Y        
                       
pid = enterprisecore  
                       
[EULA]
                       
accepteula = Y        
                       
[TELEMETRY]
                       
enabled = Y           
                       
[language]
                       
lcid = 2052
```