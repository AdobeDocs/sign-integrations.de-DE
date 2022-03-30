---
title: Adobe EchoSign für SugarCRM
description: Installationshandbuch für die Aktivierung der Adobe Sign-Integration in SugarCRM
product: Adobe Sign
content-type: reference
type: Documentation
solution: Acrobat Sign
role: User, Developer
topic: Integrations
exl-id: 0512f616-568a-4b96-9bd1-48e67bc3536b
source-git-commit: 4d73ff36408283805386bd3266b683bc187d6031
workflow-type: tm+mt
source-wordcount: '2354'
ht-degree: 2%

---


# [!DNL SugarCRM] Installationshandbuch {#sugarcrm-install-guide}

[Kontaktaufnahme mit der Kundenunterstützung](https://adobe.com/go/adobesign-support-center_de)

Adobe [!DNL EchoSign] für [!DNL SugarCRM] ist eine führende Lösung für elektronische Unterschriften und Web-basierte Vertragsabwicklung, die elektronische Unterschriften in [!DNL SugarCRM] für E-Signaturen und Faxsignaturen. Benutzer können Verträge direkt aus SugarCRM senden, den Vertragsverlauf anzeigen und eSignierte Verträge mit zugehörigen Konten, Kontakten, Angeboten und mehr speichern.
Adobe [!DNL EchoSign] für [!DNL SugarCRM] ist für alle unterstützten Versionen von SugarCRM verfügbar, einschließlich 6.3 - 6.7 für On-Demand- oder On-Premise-Lösungen.

Dieses Dokument ist eine Anleitung für [!DNL SugarCRM] Administratoren erfahren, wie sie Adobe installieren und konfigurieren [!DNL EchoSign] für [!DNL SugarCRM] -Plug-In.

## Dieses Plug-in installieren {#install-plugin}

1. Adobe herunterladen [!DNL EchoSign] für [!DNL SugarCRM]  -Archivdatei aus der [SugarExchange-Liste](http://www.sugarexchange.com/product_details.php?product=1123).
1. Anmelden bei [!DNL SugarCRM] mit Ihrem Administratorkonto.
1. Wechseln zu **[!UICONTROL Administration]** > **[!UICONTROL Modullader]**.

   ![Bild](images/module-loader.png)

1. So laden Sie die Archivdatei der Adobe hoch [!DNL EchoSign] für [!DNL SugarCRM] Plug-in, wählen Sie **[!UICONTROL Durchsuchen]**, wählen Sie dann die Archivdatei aus, und wählen Sie dann **[!UICONTROL Hochladen]**.
1. Nachdem die Archivdatei hochgeladen wurde, wählen Sie **[!UICONTROL Installieren]** , um die Installation zu starten.
1. Überprüfen Sie die Nutzungsbedingungen und wählen Sie dann **[!UICONTROL Akzeptieren]** > **[!UICONTROL Commit]**.
1. Wenn das Plug-in erfolgreich installiert wurde, zeigt die Fortschrittsleiste 100 % Erfolg an.  Wenn der Fortschrittsbalken nicht 100 % erreicht, wählen Sie **[!UICONTROL Protokoll anzeigen]** , um den Fehler von SugarCRM anzuzeigen.

   ![Bild](images/display-log.png)

1. Wechseln Sie nach der Installation zu **[!UICONTROL Administration > Reparatur]** und wählen Sie **[!UICONTROL Schnelle Reparatur und Wiederherstellung]**.

>[!NOTE]
>
>Wenn Sie das Plug-in auf der [!DNL SugarCRM] OnDemand, reichen Sie ein Support-Ticket bei [!DNL SugarCRM] , um die Einschränkungen des Paketinspektors für OnDemand vorübergehend zu entfernen, damit das Paket installiert werden kann. Dies ist Teil des Standardprozesses.

## Plug-in aktualisieren {#upgrade-plugin}

Wenn Sie die Adobe aktualisieren [!DNL EchoSign] für [!DNL SugarCRM] einer neueren Version installieren, sollten Sie das Plug-in installieren, ohne die vorherige Version zu deinstallieren.
Wechseln Sie nach dem Upgrade des Plug-ins zu **[!UICONTROL Administration]** > **[!UICONTROL Reparieren]** und wählen Sie **[!UICONTROL Schnelle Reparatur und Wiederherstellung]**.

**Hinweis:** Wenn Sie ein früheres Plug-in deinstallieren, entfernen Sie die Tabellen nicht während der Deinstallation. Andernfalls verlieren Sie möglicherweise die [!DNL EchoSign] Vereinbarungsdaten.

## Plug-in konfigurieren {#configure-plugin}

1. Wenn Sie bereits Adobe sind [!DNL EchoSign] zu Schritt 2.

   Wenn Sie kein [!DNL EchoSign] Konto [abonnieren Sie eine KOSTENLOSE 14-Tage-Testversion](https://sugarcrmintegration.echosign.com/public/login) und befolgen Sie die Online-Registrierungsschritte, um Ihre Adobe zu aktivieren [!DNL EchoSign] Konto.
1. Anmelden bei [Echo Sign-Konto](http://www.echosign.com) und führen Sie die folgenden Schritte aus:
   1. Auswählen **[!UICONTROL Konto]** &quot; ändern.
   1. Auswählen **[!UICONTROL EchoSign-API]** unten links.
   1. Auswählen **[!UICONTROL API-Zugriff aktivieren]** und rufen Sie Ihren API-Schlüssel von der Seite ab.

   ![Bild](images/enable-api-access.png)

1. Wechseln Sie in SugarCRM zu **[!UICONTROL Administration]** > **[!UICONTROL Adobe EchoSign Settings]** und geben Sie den API-Schlüssel in das Feld mit der Bezeichnung **[!UICONTROL EchoSign-API-Schlüssel]**.
1. Optional können Sie das Plug-in mit den folgenden Einstellungen konfigurieren:

   1. Hängen Sie beim Erstellen einer Vereinbarung aus einem Angebot automatisch eine PDF an: Wählen Sie aus, ob eine PDF des Angebots automatisch angehängt werden soll, wenn ein [!DNL SugarCRM] Benutzer erstellt eine EchoSign-Vereinbarung aus dem Anführungszeichen-Modul.
   1. Empfängerliste verwalten: Wählen Sie aus, welche Module im Unterfenster Empfänger im Fenster &quot; [!DNL EchoSign] Vereinbarungsmodul. Dadurch wird auch das [!DNL EchoSign] Unterbereich &quot;Vereinbarungen&quot; für diese Module.
   1. Fügen Sie die Senden-Schaltflächen zu diesen Modulen hinzu: Wählen Sie zum Erstellen des Dialogfelds [!DNL EchoSign] Vereinbarungsschaltfläche/Aktion, die in die primären Aktionen des Angebotsmoduls aufgenommen werden soll.
   1. Auswählen **[!UICONTROL Speichern]** , um Ihre Einstellungen zu speichern.

**Hinweis:** Die Adobe [!DNL EchoSign] für [!DNL SugarCRM] erfordert das [PHP SOAP-Erweiterung](http://www.php.net/manual/en/book.soap.php). Um die SOAP-Unterstützung zu aktivieren, konfigurieren Sie PHP mit enable-soap.

## Vereinbarungsaktualisierungen abrufen (für [!DNL SugarCRM] Versionen 6.3 oder höher) {#get-agreement-updates}

Für Version 6.3 und höher können Sie die folgenden beiden Optionen verwenden, um Vereinbarungsaktualisierungen zu erhalten. In früheren Versionen von SugarCRM bietet das Plug-In standardmäßig nur die Rückrufmethode (Option 1).

### Option 1: Einrichten der Rückrufmethode zum Übertragen von Updates an EchoSign

Wenn Ihre Website öffentlich ist, können Sie Adobe EchoSign pingen lassen [!DNL SugarCRM] -Instanz jedes Mal, wenn ein neues Ereignis eintritt. [!DNL SugarCRM] aktualisiert dann automatisch und in Echtzeit den Vereinbarungsstatus und Ereignisse und lädt das signierte Dokument (sofern signiert) herunter. (Wenn Sie sich hinter einer Firewall befinden, müssen Sie die [!DNL EchoSign] Server-IP-Adressen oder verwenden Sie die Methode Geplanter Auftrag zum Aktualisieren von EchoSign-Vereinbarungen, die im nächsten Abschnitt dieses Handbuchs beschrieben wird).

1. Wechseln zu **[!UICONTROL Administration]** > **[!UICONTROL Adobe EchoSign Settings]**.
1. Aktivieren Sie das Kontrollkästchen. **[!UICONTROL EchoSign-Rückrufmethode verwenden]** , um Ereignisse und Status von Vereinbarungen zu aktualisieren.
1. Auswählen **[!UICONTROL Speichern]**.

### Option 2: Geplanten Auftrag einrichten für [!DNL SugarCRM] Instanzen hinter einer Firewall

Die [!DNL EchoSign] für [!DNL SugarCRM] kann auch einen geplanten Auftrag verwenden, um eine Abfrage durchzuführen [!DNL EchoSign] für Aktualisierungen von Vereinbarungen, die zur Signatur gesendet wurden. Die Abfragemethode für geplante Aufträge kann verwendet werden, wenn Sie über eine lokale [!DNL SugarCRM] -Installation befindet sich hinter einer Firewall.

Einrichten:

1. Wechseln zu **[!UICONTROL Administration]** > **[!UICONTROL Scheduler]**.
1. Wählen Sie im Dropdown-Menü Registerkarte die Option **[!UICONTROL Planer erstellen]**.
1. Geben Sie einen Auftragsnamen ein.
1. Wählen Sie für das Feld Job die Option **[!UICONTROL Adobe EchoSign Status Updater]**.
1. Legen Sie fest, dass der Auftrag so häufig wie erforderlich ausgeführt wird. Wir empfehlen, die Ausführung alle 10 Minuten vorzunehmen. Nachdem eine Vereinbarung geöffnet, gelesen oder unterzeichnet wurde, kann dies bis zu 10 Minuten dauern. [!DNL SugarCRM] mit diesen Informationen zu aktualisieren.

   **Hinweis:** Wenn Sie viele Vereinbarungen zur Signatur haben, kann diese Ausführung zu häufig dazu führen, dass Ihr System langsamer wird.

   ![Bild](images/echosign-status-updater.png)

1. Wechseln zu **[!UICONTROL Administration]** > **[!UICONTROL Adobe EchoSign Settings]**.
1. Deaktivieren Sie das Kontrollkästchen. **[!UICONTROL EchoSign-Rückrufmethode verwenden]** , um Ereignisse und Status von Vereinbarungen zu aktualisieren.
1. Auswählen **[!UICONTROL Speichern]**.
Hinweis: Zeitplaner aktivieren in [!DNL SugarCRM] damit das funktioniert.

So fügen Sie EchoSign-Vereinbarungen anderen [!DNL SugarCRM] Module:

1. Wechseln zu **[!UICONTROL Administration]** > **[!UICONTROL Studio]**.
1. Wählen Sie in der linken Ordnerstruktur das Modul zum Hinzufügen von [!DNL EchoSign] Vereinbarungen.
1. Auswählen **[!UICONTROL Beziehungen]**> **[!UICONTROL Beziehungen hinzufügen]**.
1. Wählen Sie im Dropdown-Menü Typ als **[!UICONTROL 1:n]** und Modul als **[!UICONTROL EchoSign-Vereinbarungen]**.
1. Auswählen **[!UICONTROL Speichern und Bereitstellen]**.

   ![Bild](images/save-and-deploy.png)

   [!DNL EchoSign] Vereinbarungen werden jetzt im Modul angezeigt und können dort erstellt und verfolgt werden.

   ![Bild](images/echosign-agreements.png)

**Weitere Konfigurationsschritte**

* **Ausblenden [!DNL EchoSign] Module**: Sie können die [!DNL EchoSign] Empfänger und [!DNL EchoSign] Veranstaltungsmodule über &quot;Administration&quot; > Register und Unterfenster des Anzeigemoduls anzeigen und in die ausgeblendete Spalte verschieben.
* **Deaktivieren von packageScan**: Wenn Sie packageScan auf Ihrem eigenen System aktiviert haben, müssen Sie es während der Installation deaktivieren. Wenn Sie [!DNL SugarCRM] On-Demand, Kontakt [!DNL SugarCRM] , um packageScan für Sie zu deaktivieren.

## Plug-in deinstallieren {#uninstall-plugin}

1. Anmelden bei [!DNL SugarCRM] mit Ihrem Administratorkonto.
1. Wechseln zu **[!UICONTROL Administration]** > **[!UICONTROL Modullader]**.
1. Auswählen **[!UICONTROL Deinstallieren]** neben dem [!UICONTROL EchoSign für SugarCRM-Plug-in].
1. Auswählen **[!UICONTROL Commit]** , um die Deinstallation zu starten. Sie können auch die für das Plug-In erstellten Datenbanktabellen entfernen.

   ![Bild](images/uninstall-plugin.png)

   Wenn das Plug-in erfolgreich deinstalliert wurde, zeigt die Fortschrittsleiste 100 % Erfolg an. Wenn der Fortschrittsbalken nicht 100 % erreicht, wählen Sie [!UICONTROL Protokoll anzeigen] , um den Fehler von SugarCRM anzuzeigen.

   ![Bild](images/uninstall-display-log.png)

## Adobe verwenden [!DNL EchoSign] für [!DNL SugarCRM] {#use-echosign-for-sugarcrm}

Sie können eine Adobe erstellen [!DNL EchoSign] Vereinbarung, die mit einem Konto, Kontakt, Angebot oder anderen [!DNL SugarCRM] Modulen. Sie können Dateien anhängen, Empfänger angeben und zum Unterschreiben senden. Adobe [!DNL EchoSign] Updates [!DNL SugarCRM] mit dem aktuellen Status der Vereinbarung und speichert den unterzeichneten Vertrag in [!DNL SugarCRM] wenn sie vollständig ausgeführt wurde.

### Erstellen und Bearbeiten von Adoben [!DNL EchoSign] Vertrag {#create-edit-agreements}

Sie können Vereinbarungen über die [!DNL EchoSign] Vereinbarungsmodul oder über Module, die von einem [!DNL SugarCRM] Administrator.

1. Im Fenster &quot; [!UICONTROL Aktionen] in der [!UICONTROL EchoSign-Vereinbarungen] &quot; die Option **[!UICONTROL EchoSign-Vereinbarung erstellen]**.
1. Im Hauptabschnitt der [!DNL EchoSign] Vereinbarung die folgenden Informationen ein oder wählen Sie aus verschiedenen Vereinbarungsoptionen aus:

   1. **[!UICONTROL Name:]** Geben Sie einen Namen für die Vereinbarung ein.
   1. **[!UICONTROL Signaturtyp:]** Wählen Sie den Signaturtyp aus, der für das Dokument akzeptiert wird. Die Optionen sind E-Signatur und Faxsignatur.
   1. **[!UICONTROL Ich muss diese Vereinbarung auch unterzeichnen:]** Geben Sie an, ob der Absender auch die Vereinbarung unterzeichnen muss.
   1. **[!UICONTROL Signaturreihenfolge:]** Wenn die vorherige Option Ich muss diese Vereinbarung auch unterzeichnen aktiviert ist, wählen Sie auch die Reihenfolge aus, in der der Absender und die Empfänger unterschreiben sollen.
   1. **[!UICONTROL Empfänger an Unterschrift erinnern:]** Legen Sie fest, wie oft Empfänger daran erinnert werden sollen, ein Dokument zu unterschreiben. Die Optionen sind Täglich oder Wöchentlich.
   1. **[!UICONTROL Tage bis zum Ablauf der Signaturfrist:]** Geben Sie die Anzahl der Tage an, bis die Vereinbarung unterzeichnet werden muss.
   1. **[!UICONTROL Vorschau anz., Signatur platzieren od. Formularfelder hinzufüg.:]**  Wählen Sie diese Option aus, um eine Vorschau der Vereinbarung anzuzeigen, bevor sie gesendet wird, oder ziehen Sie Signaturfelder, Initialenfelder oder andere Formularfelder per Drag-and-Drop in die Vereinbarung, bevor sie an Empfänger gesendet wird. Nachdem Sie das Dokument in der Vorschau angezeigt oder die gewünschten Felder in das Dokument gezogen haben, wählen Sie die Schaltfläche Senden aus, um die Vereinbarung an den Empfänger zu senden.
   1. **[!UICONTROL Hostsignatur für ersten Unterzeichner:]** Geben Sie an, ob der Absender die Vereinbarung hosten möchte, die persönlich signiert.
      * **[!UICONTROL Meldung:]** Fügen Sie eine Nachricht für den Empfänger hinzu.
      * **[!UICONTROL Konto, Opportunity, Angebot:]** Wählen oder ändern Sie das Konto, die Opportunity oder das Angebot, das bzw. das mit dieser Vereinbarung verknüpft ist.
      * **[!UICONTROL Sprache:]** Geben Sie die Sprache an, in der die Signaturseite und E-Mail-Benachrichtigungen den Empfängern angezeigt werden.

      ![Bild](images/create-agreements.png)


1. Im Dialogfeld [!UICONTROL Sicherheitsoptionen] Abschnitt des [!UICONTROL EchoSign-Vereinbarung]die folgenden Informationen ein:

   a) **[!UICONTROL Zum Unterschreiben erforderliches Kennwort:]** Geben Sie an, ob ein Kennwort eingegeben werden muss, bevor ein Empfänger ein Dokument signieren kann.
b) **[!UICONTROL Kennwort zum Öffnen erforderlich:]** Geben Sie an, ob ein Kennwort eingegeben werden muss, bevor ein Empfänger eine PDF der Vereinbarung oder der unterzeichneten Vereinbarung öffnen kann c) **[!UICONTROL Kennwort:]** Geben Sie das Kennwort zum Signieren oder Öffnen eines Dokuments an.
d) **[!UICONTROL Kennwort bestätigen:]** Bestätigen Sie das Kennwort zum Signieren oder Öffnen eines Dokuments.

1. Im Abschnitt &quot;Andere&quot; der [!DNL EchoSign] Vereinbarung geben Sie die folgenden Informationen ein:

   a) **[!UICONTROL Benutzer:]** Geben Sie einen [!DNL SugarCRM] Benutzer. Standardmäßig ist der Benutzer im System angemeldet.
b) **[!UICONTROL Teams:]** Um die primäre Teamzuweisung zu ändern, geben Sie den Namen des neuen primären Teams ein. Um dem Datensatz weitere Teams zuzuweisen, klicken Sie auf **[!UICONTROL Auswählen]** und wählen Sie ein Team aus der Teamliste aus, oder wählen Sie **[!UICONTROL Hinzufügen zu]** , um Teamfelder hinzuzufügen und die Teamnamen einzugeben. Weitere Informationen finden Sie unter &quot;Zuweisen von Datensätzen zu Benutzern und Teams&quot; im Dialogfeld &quot; [!DNL SugarCRM] Anwendungshandbuch.

1. Auswählen **[!UICONTROL Speichern]**.

### [!DNL EchoSign] Detailansicht der Vereinbarung {#agreement-detail-view}

Nach einem [!DNL EchoSign] Die Vereinbarung wird gespeichert. Die Detailansicht der Vereinbarung enthält die folgenden Unterfenster:

* **[!UICONTROL Empfänger:]** Alle in diesem Unterfenster aufgeführten Kontakte erhalten die im Unterfenster Dokumente angegebenen Dokumente. Sie müssen einen oder mehrere Empfänger hinzufügen, bevor Sie die Vereinbarung senden.
* **[!UICONTROL Dokumente:]** Neues Dokument hochladen oder ein bereits hochgeladenes Dokument auswählen [!DNL SugarCRM] zum Unterschreiben senden.
* **[!UICONTROL Veranstaltungen:]** Alle Aktionen in Bezug auf die Vereinbarung, z. B. wenn die Vereinbarung zur Signatur gesendet, angezeigt oder signiert wurde, werden in diesem Unterfenster aufgeführt.
Um ein [!DNL EchoSign] Vereinbarung die Option [!UICONTROL Bearbeiten] auf der Registerkarte &quot; [!UICONTROL Detailansicht] des Abkommens.

![Bild](images/agreement-detail-view.png)

**Hinweis:** Nachdem eine Vereinbarung zum Signieren gesendet wurde, zeigt der Katalog [!UICONTROL Bearbeiten] wird aus der Detailansicht entfernt, um den Ereignisdatensatz beizubehalten. Sie können jedoch die Schaltfläche Bearbeiten aktivieren. Gehen Sie dazu zu [!UICONTROL Administrator] > [!UICONTROL Adobe EchoSign Settings] und deaktivieren Sie die Option *[!UICONTROL Nachdem eine Vereinbarung zum Signieren gesendet wurde, deaktivieren Sie die Möglichkeit zum Bearbeiten oder Löschen.]*.

### Dokument zu einem [!DNL EchoSign] Vertrag {#add-document}

[!DNL SugarCRM] Benutzer können ein neues Dokument hochladen oder ein bereits hochgeladenes Dokument auswählen. [!DNL SugarCRM] mithilfe des Unterfensters Dokumente eines EchoSign-Vereinbarungsdatensatzes.
Um ein Dokument hochzuladen, wählen Sie **[!UICONTROL Dokument hochladen]** in der [!UICONTROL Dokumente] Unterfenster.

Weitere Informationen finden Sie im Abschnitt &quot;Dokumentenmodul&quot; des [!DNL SugarCRM] Bewerbungshandbuch , um weitere Informationen zu den einzelnen Feldern dieses Formulars zu erhalten.

Um ein Dokument auszuwählen, klicken Sie auf **[!UICONTROL Auswählen]** im Unterfenster Dokumente . Informationen zum Anzeigen und Verwalten von Datensatzinformationen finden Sie im [!DNL SugarCRM] Anwendungshandbuch für weitere Informationen zum Verwalten zugehöriger Informationen in Unterfenstern.

![Bild](images/add-document-to-agreement.png)

### Geben Sie einen Empfänger für ein [!DNL EchoSign] Vertrag {#specify-recipient}

1. Im Fenster &quot; [!UICONTROL Empfänger] Unterfenster eines [!DNL EchoSign] Vereinbarung, wählen Sie **[!UICONTROL Empfänger hinzufügen]**.
1. Geben Sie die folgenden Informationen ein: a) [!UICONTROL Empfänger:] Wählen Sie den Empfängertyp aus dem Dropdown-Menü aus. Geben Sie den Namen oder die E-Mail-Adresse des Empfängers in das Textfeld ein. [!DNL SugarCRM] sucht den Namen während der Eingabe und bietet eine Auswahlliste an. Wählen Sie einen Namen, wenn eine Übereinstimmung gefunden wird. Sie können auch das Pfeilsymbol auswählen, um einen Namen aus einem Popup-Fenster auszuwählen. Um den Namen aus dem Feld zu löschen, wählen Sie die Option **[!UICONTROL X]** Symbol.
b) [!UICONTROL Rolle:] Wählen Sie im Dropdown-Menü eine Rolle aus. Die Optionen sind Unterzeichner und CC und Genehmiger. Ein Genehmiger muss das Dokument nicht signieren.
1. Wählen Sie Speichern.

![Bild](images/add-recipient-to-agreement.png)

### Vereinbarungen zum Unterschreiben senden {#send-for-signature}

Wenn Vereinbarungen zum Unterschreiben gesendet werden können, wählen Sie **[!UICONTROL Send for Signature]** aus dem Dropdown-Menü oben links auf der Seite. Die Empfänger erhalten dann eine E-Mail, in der sie über die Dokumente informiert werden, die auf ihre Signatur warten. Nachdem die Empfänger das Dokument unterzeichnet haben, erhält der Absender eine E-Mail-Benachrichtigung.
Wenn die Option [!UICONTROL Hostsignatur für ersten Unterzeichner] aktiviert ist, können Sie **[!UICONTROL Send for Signature]** , damit der Unterzeichner das Dokument in Anwesenheit des Absenders signieren kann.

![Bild](images/send-for-signature.png)

Neben dem Link [!UICONTROL Hostsignatur für ersten Unterzeichner] wird auch der Link **[!UICONTROL Hostsignatur für aktuellen Unterzeichner]** angezeigt, auf den zugegriffen werden kann, bis das Dokument signiert ist. Sie können diesen Link verwenden, um die Vereinbarungssignatur für mehrere Unterzeichner zu hosten oder das Popup-Fenster erneut zu öffnen, wenn es versehentlich geschlossen wurde.
Wenn [!UICONTROL Vorschau anz., Signatur platzieren od. Formularfelder hinzufüg.] aktiviert ist, wählen Sie **[!UICONTROL Send for Signature]** , damit der Absender eine Vorschau des Dokuments anzeigen oder Felder vor dem Senden in das Dokument ziehen kann. Sie müssen **[!UICONTROL Senden]** in diesem Fenster, um die Vereinbarung an den Empfänger zu senden.

Abbildung 5: Wählen Sie Send for Signature , um ein Dokument zur Signatur an einen Empfänger zu senden.

### Senden aus einem Angebotsdatensatz {#send-from-quote-record}

Adobe [!DNL EchoSign] hat eine direkte Integration mit Angeboten in [!DNL SugarCRM] , damit die PDF des Angebots automatisch generiert und an den Vereinbarungsdatensatz angehängt wird.
Wenn ein Angebot angezeigt wird, wählen Sie **[!UICONTROL EchoSign-Vereinbarung erstellen]** , um das Angebot zu erstellen und es automatisch an die Vereinbarung anzuhängen. Die neue Vereinbarung verknüpft auch automatisch alle zugehörigen Opportunity-, Konto- oder Angebotsoptionen.

![Bild](images/create-echosign-agreement.png)

Um das automatische Anhängen der PDF mit dem Angebot an die Vereinbarung zu deaktivieren, wechseln Sie zu **[!UICONTROL Administration]** > **[!UICONTROL Adobe EchoSign Settings]** und deaktivieren Sie das Kontrollkästchen *[!UICONTROL Automatisch PDF anhängen, wenn eine Vereinbarung aus einem Angebot erstellt wird]*.

### Eine Vereinbarung abbrechen {#cancel-agreement}

Sie können eine [!DNL EchoSign] Vereinbarung, nachdem sie zum Signieren gesendet wurde, wenn noch nicht alle Empfänger das Dokument signiert haben. A [!UICONTROL Vereinbarung abbrechen] wird in der Detailansicht einer Vereinbarung angezeigt, nachdem ein Dokument zur Signatur gesendet wurde. Auswählen **[!UICONTROL Vereinbarung abbrechen]** , um die Vereinbarung zu kündigen.

![Bild](images/cancel-agreement.png)

Hinweis: Wenn ein [!DNL EchoSign] Die Vereinbarung wird zur Signatur gesendet und der Datensatz wird gelöscht. Sie müssen die Vereinbarung abbrechen, bevor Sie sie löschen.

### Unterschriften verfolgen {#track-signatures}

Die [!UICONTROL Events] Unterfenster eines [!DNL EchoSign] Die Vereinbarung verfolgt den Status von Vereinbarungen, die zur Signatur gesendet werden. Um die neuesten Updates auf einer [!DNL EchoSign] Vereinbarung, wählen Sie **[!UICONTROL Status aktualisieren]**. Die [!UICONTROL Status aktualisieren] ist nur verfügbar, nachdem eine Vereinbarung zum Signieren gesendet wurde.

![Bild](images/update-cancel-status.png)

Nachdem eine Vereinbarung zum Signieren gesendet wurde, wählen Sie **[!UICONTROL Status aktualisieren]** , um den neuesten Status abzurufen.

![Bild](images/events-subpanel.png)

### Erinnerungen senden {#send-reminders}

Um nach dem Senden der Vereinbarung eine Erinnerung an den aktuellen Unterzeichner zu senden, wählen Sie **[!UICONTROL Erinnerung senden]**. Es sendet sofort eine E-Mail-Erinnerung an den aktuellen Unterzeichner über die Vereinbarung, die auf eine Signatur wartet.

![Bild](images/send-reminder.png)
