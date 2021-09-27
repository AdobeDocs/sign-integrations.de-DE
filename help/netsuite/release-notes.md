---
title: Adobe Sign für NetSuite – Versionshinweise
description: 'Erfahren Sie mehr über die neuen Funktionen und Änderungen, die in der aktuellen Version der Adobe Sign-Integration für NetSuite enthalten sind.  '
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
source-git-commit: 924813403d8e13f816347dd548a68a16d78d866e
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 71%

---


# Adobe Sign für NetSuite – Versionshinweise

## Update auf Paket Version 4.0.4

4.0.4 ist vollständig auf die Verwendung kontenspezifischer Domänen für den gesamten neu generierten Datenverkehr angepasst.

Das Adobe Sign-Symbol wurde auf die neue Grafik aktualisiert.

## Frühere Versionen

### Adobe Sign für NetSuite 4.0.4

4.0.4 ist vollständig auf die Verwendung kontenspezifischer Domänen für den gesamten neu generierten Datenverkehr angepasst.

Das Adobe Sign-Symbol wurde auf die neue Grafik aktualisiert.

### Adobe Sign für NetSuite 4.0.2

Umbenannt in **Adobe Sign** (von *Adobe Document Cloud eSign-Dienste*)\
Sie sehen *Adobe Sign*, wo Sie zuvor *Adobe eSign-Dienste* als Beleg für das Rebranding gesehen haben.

### Adobe Sign für NetSuite 4.0.1

Aufgrund eines API-Regressionsfehlers, der beim Ausführen der Plattformaktualisierung von NetSuite aufgetreten ist, wurde ein neues Paket (v4.0.1) veröffentlicht.

Kunden wird empfohlen, eine Aktualisierung auf das neueste Paket durchzuführen.

### Adobe Sign für NetSuite 4.0

**Die automatische Bereitstellung von Benutzern über NetSuite wurde hinzugefügt.**

Für v4.0 wurde eine neue benutzerspezifische Voreinstellung hinzugefügt. Ist diese aktiviert, wird für Benutzer, die Vereinbarungen in NetSuite senden, automatisch ein Benutzerkonto für die Adobe Document Cloud eSign-Dienste bereitgestellt.

**Zertifiziert mit &quot;Built for NetSuite&quot;**

Diese Version enthält die Zertifizierung „Built for NetSuite“ und erfüllt alle aktuellen Design-Best-Practices für NetSuite.

**Umbenannt in Adobe Document Cloud eSign-Dienste (von EchoSign)**

Als Nachweis für die Umbenennung werden Sie Adobe Document Cloud eSign-Dienste (oder kurz Adobe eSign-Dienste) dort lesen, wo zuvor Adobe EchoSign stand.

**Implementierung einer erweiterten Sicherheit mit OAuth**

Zur Verbesserung der Datensicherheit verwenden die eSign-Dienste nun OAuth 2.0 für die Authentifizierung des Adobe Document Cloud eSign-Dienstkontos in NetSuite. Mithilfe dieses neuen Protokolls kann NetSuite mit eSign-Diensten kommunizieren, ohne Ihr eSign-Dienstkennwort anzufordern. Da vertrauliche Informationen nicht direkt zwischen den Anwendungen ausgetauscht werden, ist die Wahrscheinlichkeit geringer, dass Ihr Konto unerlaubt benutzt wird. Diese Verbesserung wirkt sich nicht auf Ihre Implementierung aus. Sie müssen jedoch ein einmaliges Setup durchführen, um Ihr NetSuite-Paket für die Kommunikation mit Adobe Document Cloud zu autorisieren. Dies geschieht während des Installationsprozesses. Für Kunden, die ein Upgrade von einer früheren Version des Pakets (v3.5.9 und früher) durchführen, wird der zuvor verwendete API-Schlüssel durch ein OAuth-Token ersetzt, das während des Autorisierungsprozesses generiert wurde.

**Migration der eSign-Dienste von SOAP-APIs in REST-APIs**

Um Effizienz, Flexibilität und Verarbeitungsgeschwindigkeit zu verbessern, wurden die Adobe Document Cloud eSign-Dienste und damit die NetSuite v4.0-Integration von SOAP-basierten zu REST-basierten APIs migriert.

### Adobe Sign für NetSuite 3.0

**Erweiterte Teilnehmerrollen – Genehmiger**

* Ein oder mehrere Empfänger können in einer Vereinbarung als Genehmiger markiert werden
* Genehmiger müssen das Dokument überprüfen und genehmigen
* Vor der Genehmigung müssen Genehmiger möglicherweise auch Daten in die Vereinbarung eintragen

**Vor dem Senden Dokument in der Vorschau anzeigen oder Formularfelder per Drag &amp; Drop verschieben**

Vorschau der Vereinbarung anzeigen oder Formularfelder per Drag &amp; Drop zum Unterschreiben senden

**Erinnerung an aktuellen Unterzeichner senden**

Sofortige Erinnerung an aktuellen Unterzeichner senden

**Erweiterte Richtlinien für die Unterzeichnerauthentifizierung**

* **Wissensbasierte Authentifizierung:Fragen zur Bestätigung der Unterzeichneridentität** beantworten
   * Unterzeichner müssen ihre Identität durch die Beantwortung von Fragen nachweisen, die aus mehreren hundert öffentlichen und kommerziellen Datenbanken entnommen wurden
   * Der Name auf der Signatur wird dem authentifizierten Namen des Benutzers entnommen und kann zum Zeitpunkt der Unterzeichnung nicht geändert werden
   * Powered by RSA
   * Die KBA-Nutzung ist pro Konto und pro Monat beschränkt. Wenden Sie sich für weitere Informationen an den Vertrieb.

* **Webidentität:** Melden Sie sich vor dem Signieren mit Facebook, LinkedIn, Google oder einem anderen Webdienst von Drittanbietern an.

   * Der Unterzeichner kann die Signatur erst vornehmen, nachdem seine Identität mithilfe eines Drittanbieter-Webdiensts überprüft wurde.
   * Der Name auf der Signatur wird dem Webdienstprofil des Benutzers entnommen und kann zum Zeitpunkt der Unterzeichnung nicht geändert werden
   * Audit-Protokoll erfasst Identitätsüberprüfungsdetails

* **Einmaliges Kennwort**
   * Wenden Sie Authentifizierungsmethoden für interne oder externe Unterzeichner oder alle Unterzeichner an. Externe Unterzeichner müssen ein Kennwort verwenden oder die wissensbasierte Authentifizierung verwenden, während interne Unterzeichner nicht

**Zusätzliche benutzerdefinierte Voreinstellungen**

* Signierte PDF-Datei als Link zur &quot;!le&quot;-URL oder als in NetSuite gehostete Anlage hinzufügen
* Fügen Sie das Audit-Protokoll der Vereinbarung nach dem Signieren der Vereinbarung hinzu
* Verwenden Sie anstelle der Kunden-E-Mail standardmäßig den Geschäftskontakt als ersten Unterzeichner
* Gewähren Sie Absendern die Möglichkeit, Empfänger als Genehmiger zu kennzeichnen

**Transaktionsdateien**

Sie können Dateien auswählen, die aus der aktuellen Transaktion angehängt werden sollen, indem Sie die neue Dropdownliste &quot;Transaktionsdateien&quot;verwenden.

**Adobe PDF-Zertifizierung für alle EchoSign-Dokumente**

* Alle PDF-Dateien, die von EchoSign gesendet oder heruntergeladen wurden, werden mit einem Adobe EchoSign Digital Certificate zertifiziert
* Acrobat oder Reader wird die Zertifizierung anzeigen, die gewährleistet, dass das Dokument nicht manipuliert wurde, um mehr Vertrauen und Ruhe zu schaffen

**Sammeln Sie unterstützende Dokumente.**

* Absender können während des Signierens zusätzliche Begleitdokumente von Unterzeichnern erfassen (z. B. Führerschein, Gewerbenachweis)
* Erfasste Dokumente werden Teil des offiziellen Datensatzes der signierten Vereinbarung

**Bedingte Datenfelder**

* Definieren Sie eine konditionelle Logik für Vereinbarungsfelder
* Bedingungen können auf Werten für ein oder mehrere Felder in der Vereinbarung basieren
* Bedingungen können über die Authoring-UI der Drag &amp; Drop-Formulare oder über Text-Tags definiert werden
* Dem Unterzeichner werden die entsprechenden Felder angezeigt, wenn er ein Dokument basierend auf den De!ned-Bedingungen signiert.

**Weitere Verbesserungen an EchoSign-Formularfeldern**

* Dropdown-Menüs
* Feldmaskierung
* Optionsfelder
* Erstellen Sie kürzere Text-Tags, um die Dokumentstruktur beizubehalten
