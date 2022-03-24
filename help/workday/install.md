---
title: Workday-Installationshandbuch
description: Installationshandbuch für die Aktivierung der Integration von Adobe Sign in Workday
uuid: 56478222-fe66-4fa5-aac3-0ecdf2863197
product: Adobe Sign
topic-tags: EchoSign/Integrations
content-type: reference
discoiquuid: 29d55a25-6e2f-4c59-ae7c-c21bb82cecba
locnotes: All languages; screenshots for Tier 1 and 2 only (see the currently published localized page for guidance)
type: Documentation
solution: Acrobat Sign, Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 8f12b524-2123-45d4-98d5-b2b23580a5ea
source-git-commit: b326a9afa2c16333d390cac3b30a2c7c741a4360
workflow-type: tm+mt
source-wordcount: '1133'
ht-degree: 21%

---

# [!DNL Workday] Installationshandbuch{#workday-installation-guide}

[**Adobe Sign-Support kontaktieren**](https://adobe.com/go/adobesign-support-center_de)

## Übersicht {#overview}

In diesem Dokument wird erläutert, wie Sie Adobe Sign in Ihre [!DNL Workday] Mandant. So verwenden Sie Adobe Sign in [!DNL Workday], Sie müssen wissen, wie Sie [!DNL Workday] Elemente wie:

* Rahmen für Geschäftsprozesse
* Einrichtung und Konfiguration der Mandanten
* Berichterstattung und [!DNL Workday] Studiointegration

Die allgemeinen Schritte zum Abschließen der Integration sind:

* Administratorkonto in Adobe Sign aktivieren (nur für neue Kunden)
* Konfigurieren Sie eine Gruppe in Adobe Sign für die [!DNL Workday] Integrationsbenutzer
* Stellen Sie die OAuth-Beziehung zwischen [!DNL Workday] und Adobe Sign

## Adobe Sign-Konto aktivieren {#activating-your-adobe-sign-account}

Bestehende Kunden mit bestehenden Konten können zur [Konfigurieren von Adobe Sign für [!DNL Workday]](#config) Thema.

Für Kunden, die Adobe Sign noch nicht kennen und noch nicht über eine bestehende Anmeldung verfügen, stellt ein Einstiegsspezialist für die Adobe Ihr Konto (in Adobe Sign) für [!DNL Workday]. Sobald der Vorgang abgeschlossen ist, erhalten Sie wie unten gezeigt eine Bestätigungs-E-Mail.

![Bild der Begrüßungs-E-Mail von Adobe Sign](images/welcome-email-2020.png)

Sie müssen die Anweisungen in der E-Mail befolgen, um Ihr Konto zu initialisieren und auf Ihre Adobe Sign zuzugreifen [!UICONTROL Startseite] angezeigt.

![Die Adobe Sign-Dashboard-Seite](images/classic-home.png)

## Konfigurieren von Adobe Sign für [!DNL Workday] {#config}

So konfigurieren Sie Adobe Sign für [!DNL Workday]müssen Sie die folgenden zwei dedizierten Objekte im Adobe Sign-System generieren:

* **A [!DNL Workday] Gruppe**: [!DNL Workday] erfordert eine dedizierte &quot;Gruppe&quot; innerhalb des Adobe Sign-Kontos, um die Integrationsfunktion zu aktivieren. Mit der Gruppe Adobe Sign wird nur die [!DNL Workday] Nutzung von Adobe Sign. Andere Nutzungsmöglichkeiten wie Salesforce.com oder Arriba sind hiervon nicht betroffen. Die E-Mail-Benachrichtigungen werden unterdrückt in [!DNL Workday] , sodass die [!DNL Workday] erhalten Benutzer nur Benachrichtigungen innerhalb ihrer [!DNL Workday] Posteingang.

* **Einen authentifizierenden Benutzer, der den Integrationsschlüssel hält**: A [!DNL Workday] Gruppe darf nur über einen Administrator auf Gruppenebene verfügen, der der maßgebliche Inhaber des Integrationsschlüssels ist. Wir empfehlen dem Administrator, eine funktionale E-Mail-Adresse zu verwenden, z. B. `HR@MyDomain.com` anstatt eine persönliche E-Mail, um das Risiko zu verringern, dass der Benutzer in Zukunft deaktiviert wird und somit die Integration deaktiviert wird.

### Erstellen von Benutzern und Gruppen in Adobe Sign {#create-a-user-and-group-in-adobe-sign}

So erstellen Sie in Adobe Sign einen Benutzer:

1. Melden Sie sich bei Adobe Sign als Konto-Administrator an..
1. Navigieren Sie zu **[!UICONTROL Konto]** > **[!UICONTROL Benutzer]**.
1. Klicken Sie auf ![Plus-Symbolbild](images/icon_plus.png) , um einen neuen Benutzer zu erstellen.

   ![Bild des Navigationspfads zum Erstellen eines neuen Benutzers](images/navigate-to-group-unbranded.png)

1. Geben Sie im daraufhin geöffneten Dialogfeld die neuen Benutzerdetails ein:

   * Geben Sie eine funktionierende E-Mail an, auf die Sie zugreifen können.
   * Geben Sie einen geeigneten Vor- und Nachnamen ein.
   * Auswählen **[!UICONTROL Neue Gruppe für diesen Benutzer erstellen]** aus der Benutzergruppe aus.
   * Geben Sie den **[!UICONTROL Neuer Gruppenname]** mit einem intuitiven Namen wie *[!DNL Workday]*.

   ![Das Feld „Benutzer erstellen“](images/create-user.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

   Damit gelangen Sie zurück zur [!UICONTROL Benutzer] , die den neuen Benutzer mit einem **[!UICONTROL ERSTELLT]** Status.

   ![Eine Ansicht des neu erstellten Benutzers](images/post-user-creation.png)

So überprüfen Sie die E-Mail-Adresse des Benutzers mit dem Status &quot;Erstellt&quot;:

1. Melden Sie sich als E-Mail-Adresse des neuen Benutzers an.
2. Suchen Sie die E-Mail &quot;Willkommen bei Adobe Sign&quot;.
3. Klicken Sie auf die Textstelle **[!UICONTROL Klicken Sie hier, um Ihr Kennwort festzulegen]**.
4. Legen Sie das Kennwort fest.

Sobald Sie die E-Mail-Adresse bestätigt haben, ändert sich der Status des Benutzers von [!UICONTROL ERSTELLT] bis [!UICONTROL AKTIV].

![Bild des neu aktivierten Benutzers](images/actived-users-575.png)

### Authentifizierenden Benutzer definieren {#define-the-authenticating-user}

Um den neuen Benutzer im [!DNL Workday] Gruppe:

1. Navigieren Sie zur Registerkarte [!UICONTROL Benutzer] -Seite (falls nicht bereits vorhanden).
2. Doppelklicken Sie auf den Benutzer im [!DNL Workday] Gruppe.

   Dadurch wird eine [!UICONTROL Bearbeiten] für die Benutzerberechtigungen.

3. Überprüfen Sie die **[!UICONTROL Gruppenadministrator]**.
4. Klicken Sie auf **[!UICONTROL Speichern]**.

![](images/user-permissions-edit1-575.png)

## Konfigurieren Sie die [!DNL Workday] Mieter {#configure-workday}

Um die Verbindung zwischen dem [!DNL Workday] Mandant und Adobe Sign verwenden, müssen wir eine vertrauenswürdige Beziehung zwischen den Services herstellen. Anschließend können wir einen Schritt Dokument prüfen hinzufügen, der den Signaturprozess über Adobe Sign ermöglicht.

>[!NOTE]
>
>Adobe Sign wird im gesamten [!DNL Workday] Umgebung.

So stellen Sie eine vertrauenswürdige Beziehung her:

1. Anmelden bei [!DNL Workday] als Kontoadministrator registrieren.
1. Öffnen Sie die **[!UICONTROL Einrichtung der Mandanten bearbeiten - Geschäftsvorgänge]** angezeigt.
1. Suchen Sie den Abschnitt [!UICONTROL Konfiguration der eSignatur]:

   ![](images/esignature_configurations.png)

1. Klicken **[!UICONTROL Mit Adobe authentifizieren]**.

   Dadurch wird die OAuth2.0-Authentifizierungssequenz gestartet.

1. Wenn Sie dazu aufgefordert werden, geben Sie die Anmeldeinformationen für den Adobe Sign-Gruppenadministrator ein, den Sie zuvor erstellt haben.
1. Genehmigen Sie den Zugriff auf Adobe Sign.

>[!NOTE]
>
>Stellen Sie sicher, dass Sie sich vollständig von jeder anderen Adobe Sign-Instanz abmelden, bevor Sie fortfahren.

Sobald die Verbindung hergestellt ist, wird das Kontrollkästchen Adobe-Konfiguration aktiviert und Sie können Adobe Sign mit [!DNL Workday].

### Den Schritt &quot;Dokument prüfen&quot; konfigurieren {#configure-review}

Das Dokument für den Schritt &quot;Dokument prüfen&quot; kann eine der folgenden Optionen haben:

* Ein statisches Dokument
* Ein Dokument, das mit dem Schritt &quot;Dokument generieren&quot; innerhalb desselben Geschäftsvorgangs generiert wurde
* Ein formatierter Bericht, der mit dem [!DNL Workday] Berichts-Designer

Sie können jedes dieser Dokumente mit [Adobe-Text-Tags](https://adobe.com/go/adobesign_text_tag_guide_de) , um das Aussehen und die Position der Adobe zu steuern. Die Quelle des Dokuments muss innerhalb der Definition des Geschäftsvorgangs angegeben werden. Es ist nicht möglich, während der Durchführung des Geschäftsvorgangs ein Ad-hoc-Dokument hochzuladen.

Die Möglichkeit, Unterzeichnergruppen mit Seriennummer zu versehen, ist eine Besonderheit von Adobe Sign mit dem Schritt &quot;Dokument prüfen&quot;. Auf diese Weise können Sie rollenbasierte Gruppen angeben, die nacheinander signieren. Adobe Sign unterstützt keine parallelen Signaturgruppen.

Hilfe zum Schritt Dokument prüfen finden Sie im [Kurzanleitung](https://adobe.com//go/adobesign_workday_quick_start){target=&quot;_blank&quot;}.

## Support {#support}

### [!DNL Workday] unterstützen {#workday-support}

[!DNL Workday] ist der Integrationsverantwortliche, der Ihre erste Anlaufstelle bei Fragen zum Umfang der Integration, bei Funktionsanfragen oder Problemen bei der täglichen Arbeit mit der Integration sein sollte.

Weitere Informationen finden Sie unter [!DNL Workday] Community-Artikel zur Fehlerbehebung bei der Integration und zum Generieren von Dokumenten:

* [Fehlerbehebung bei der Integration von E-Signaturen](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/zhA~hYllD3Hv1wu0CvHH_g)
* [Schritt &quot;Dokumente prüfen&quot;](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg)
* [Dynamische Dokumenterstellung](https://community.workday.com/saml/login?destination=/articles/176443)
* [Tipps zur Erstellung von Angebotsunterlagen](https://community.workday.com/node/183242)

### Unterstützung für Adobe Sign {#adobe-sign-support}

Adobe Sign ist der Integrationspartner und sollte nur dann kontaktiert werden, wenn über die Integration keine Signaturen geliefert werden oder wenn die Benachrichtigung über ausstehende Signaturen fehlschlägt.

Adobe Sign-Kunden wenden sich bezüglich Support bitte an ihren Customer Success Manager (CSM). Alternativ kann der technische Support von Adobe telefonisch erreicht werden: 1-866-318-4100, auf die Produktliste warten und dann 4 und 2 eintippen (nach Aufforderung).

* [Hinzufügen von Adobe-Text-Tags zu Dokumenten](https://adobe.com/go/adobesign_text_tag_guide)
* [Konfiguration und Beispiele für Review-Dokumente](https://www.adobe.com//go/adobesign_workday_quick_start)

## Häufig gestellte Fragen {#faq}

### Warum wird der Status nicht aktualisiert in [!DNL Workday] selbst wenn das Dokument vollständig unterzeichnet ist? {#why-is-the-status-not-being-updated-within-workday-even-the-document-is-fully-signed}

Der Dokumentstatus in [!DNL Workday] wird möglicherweise nicht angezeigt, wenn der Bewerber nicht auf das Symbol &quot;[!UICONTROL Senden]&#39; nach der Anmeldung bei Adobe Sign.

Gemäß [!DNL Workday] Aufgabe Signaturstatus der eSignatur überprüfen: Um den Prozess zu starten, kann der Benutzer die zugeordnete Posteingangsaufgabe senden.

Gemäß [!DNL Workday] Entwicklung: Die ursprüngliche Signatur schließt den Vorgang nur ab, wenn der Benutzer die Posteingangsaufgabe nach der Signatur des Dokuments übermittelt. Nach dem Signieren wird der iframe geschlossen und der Benutzer wird zu derselben Aufgabe umgeleitet, wo er auf die Schaltfläche [!UICONTROL Senden] , um den Vorgang abzuschließen.
