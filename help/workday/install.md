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
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 8f12b524-2123-45d4-98d5-b2b23580a5ea
source-git-commit: d462ccf41fa5483cfa02f5eaf154c23f26157a1e
workflow-type: tm+mt
source-wordcount: '1137'
ht-degree: 21%

---

# [!DNL Workday] Installationshandbuch{#workday-installation-guide}

[**Adobe Sign-Support kontaktieren**](https://adobe.com/go/adobesign-support-center_de)

## Übersicht {#overview}

In diesem Dokument wird erläutert, wie Adobe Sign in Ihren [!DNL Workday]-Mandanten integriert wird. Um Adobe Sign in [!DNL Workday] zu verwenden, müssen Sie wissen, wie [!DNL Workday]-Elemente erstellt und geändert werden, z. B.:

* Geschäftsprozessrahmen
* Einrichtung und Konfiguration des Mandanten
* Reporting und [!DNL Workday] Studiointegration

Die wichtigsten Schritte zum Abschluss der Integration sind:

* Aktivieren Sie Ihr Administratorkonto in Adobe Sign (nur neue Kunden).
* Konfigurieren Sie eine Gruppe in Adobe Sign für den [!DNL Workday]-Integrationsbenutzer.
* Herstellen der OAuth-Beziehung zwischen [!DNL Workday] und Adobe Sign

## Adobe Sign-Konto aktivieren {#activating-your-adobe-sign-account}

Bestehende Kunden mit bestehenden Konten können zum Thema [Adobe Sign für [!DNL Workday]](#config) konfigurieren überspringen.

Für Kunden, die neu bei Adobe Sign sind und keine bereits vorhandene Anmeldung haben, stellt ein Spezialist für Adobe-Onboarding Ihr Konto (in Adobe Sign) für [!DNL Workday] bereit. Sobald Sie fertig sind, erhalten Sie eine Bestätigungs-E-Mail wie unten gezeigt.

![Bild der Begrüßungs-E-Mail von Adobe Sign](images/welcome-email-2020.png)

Sie müssen die Anweisungen in der E-Mail befolgen, um Ihr Konto zu initialisieren und auf Ihre Adobe Sign [!UICONTROL Home]-Seite zuzugreifen.

![Die Adobe Sign-Dashboard-Seite](images/classic-home.png)

## Adobe Sign für [!DNL Workday] konfigurieren {#config}

Um Adobe Sign für [!DNL Workday] zu konfigurieren, müssen Sie die folgenden zwei dedizierten Objekte im Adobe Sign-System generieren:

* **Eine  [!DNL Workday] Gruppe**:  [!DNL Workday] erfordert eine spezielle &quot;Gruppe&quot;innerhalb des Adobe Sign-Kontos, um Integrationsfunktionen zu aktivieren. Die Adobe Sign-Gruppe wird verwendet, um nur die [!DNL Workday]-Verwendung von Adobe Sign zu steuern. Eine andere mögliche Nutzung, wie Salesforce.com oder Arriba, wird nicht beeinträchtigt. Die E-Mail-Benachrichtigungen werden in der [!DNL Workday]-Gruppe unterdrückt, sodass [!DNL Workday]-Benutzer nur Benachrichtigungen innerhalb ihres [!DNL Workday]-Posteingangs erhalten.

* **Ein authentifizierender Benutzer, der den Integrationsschlüssel** enthält: Eine  [!DNL Workday] Gruppe darf nur einen Administrator auf Gruppenebene haben, der der maßgebliche Inhaber des Integrationsschlüssels ist. Wir empfehlen dem Administrator, anstelle einer persönlichen E-Mail-Adresse eine funktionale E-Mail-Adresse wie `HR@MyDomain.com` zu verwenden, um das Risiko zu verringern, dass der Benutzer in Zukunft deaktiviert wird und somit die Integration deaktiviert wird.

### Benutzer und Gruppe in Adobe Sign erstellen {#create-a-user-and-group-in-adobe-sign}

So erstellen Sie in Adobe Sign einen Benutzer:

1. Melden Sie sich bei Adobe Sign als Konto-Administrator an..
1. Navigieren Sie zu **[!UICONTROL Konto]** > **[!UICONTROL Benutzer]**.
1. Klicken Sie auf das Symbol ![plus](images/icon_plus.png), um einen neuen Benutzer zu erstellen.

   ![Bild des Navigationspfads zum Erstellen eines neuen Benutzers](images/navigate-to-group-unbranded.png)

1. Geben Sie im daraufhin geöffneten Dialogfeld die neuen Benutzerdetails an:

   * Stellen Sie eine funktionale E-Mail bereit, auf die Sie zugreifen können.
   * Geben Sie einen geeigneten Vor- und Nachnamen ein.
   * Wählen Sie in der Benutzergruppe **[!UICONTROL Neue Gruppe für diesen Benutzer erstellen]** aus.
   * Geben Sie dem **[!UICONTROL Neuen Gruppennamen]** einen intuitiven Namen wie *[!DNL Workday]*.

   ![Das Feld „Benutzer erstellen“](images/create-user.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

   Sie gelangen zurück zur Seite [!UICONTROL Benutzer], auf der der neue Benutzer mit dem Status **[!UICONTROL ERSTELLT]** aufgeführt wird.

   ![Ansicht des neu erstellten Benutzers](images/post-user-creation.png)

So überprüfen Sie die E-Mail-Adresse des Benutzers mit dem Status &quot;Erstellt&quot;wie folgt:

1. Melden Sie sich bei der E-Mail des neuen Benutzers an.
2. Suchen Sie die E-Mail &quot;Welcome to Adobe Sign&quot;.
3. Klicken Sie an die Stelle, an der **[!UICONTROL Klicken Sie hier, um Ihr Kennwort]** festzulegen.
4. Legen Sie das Kennwort fest.

Nachdem Sie die E-Mail-Adresse bestätigt haben, ändert sich der Status des Benutzers von [!UICONTROL CREATED] in [!UICONTROL ACTIVE].

![Bild des neuen aktivierten Benutzers](images/actived-users-575.png)

### Authentifizierungsbenutzer definieren {#define-the-authenticating-user}

So bewerben Sie den neuen Benutzer in der [!DNL Workday]-Gruppe:

1. Navigieren Sie zur Seite [!UICONTROL Benutzer] (falls nicht bereits vorhanden).
2. Doppelklicken Sie auf den Benutzer in der [!DNL Workday]-Gruppe.

   Dadurch wird eine Seite [!UICONTROL Bearbeiten] für die Benutzerberechtigungen geöffnet.

3. Aktivieren Sie die Option **[!UICONTROL Gruppenadministrator]**.
4. Klicken Sie auf **[!UICONTROL Speichern]**.

![](images/user-permissions-edit1-575.png)

## [!DNL Workday]-Mandanten konfigurieren {#configure-workday}

Um die Verbindung zwischen dem [!DNL Workday]-Mandanten und Adobe Sign abzuschließen, müssen wir eine vertrauenswürdige Verbindung zwischen den Diensten herstellen. Anschließend können wir einen Schritt Dokument prüfen hinzufügen, der den Signaturvorgang über Adobe Sign ermöglicht.

>[!NOTE]
>
>Adobe Sign wird in der [!DNL Workday]-Umgebung als Adobe Document Cloud gekennzeichnet.

So stellen Sie eine vertrauenswürdige Beziehung her:

1. Melden Sie sich bei [!DNL Workday] als Kontoadministrator an.
1. Öffnen Sie die Seite **[!UICONTROL Mandanteneinrichtung bearbeiten - Geschäftsprozesse]**.
1. Suchen Sie den Abschnitt [!UICONTROL Konfiguration der eSignatur]:

   ![](images/esignature_configurations.png)

1. Klicken Sie auf **[!UICONTROL Authentifizieren Sie sich mit Adobe]**.

   Dadurch wird die OAuth2.0-Authentifizierungssequenz gestartet.

1. Wenn Sie gefragt werden, geben Sie die Anmeldeinformationen für den zuvor erstellten Adobe Sign-Gruppenadministrator an.
1. Genehmigen Sie den Zugriff auf Adobe Sign.

>[!NOTE]
>
>Stellen Sie sicher, dass Sie sich bei jeder anderen Adobe Sign-Instanz vollständig abmelden, bevor Sie fortfahren.

Nachdem die Verbindung hergestellt wurde, ist das Kontrollkästchen Adobe-Konfiguration aktiviert und Sie können Adobe Sign mit [!DNL Workday] verwenden.

### Schritt &quot;Dokument prüfen&quot;konfigurieren {#configure-review}

Das Dokument für den Schritt &quot;Dokument prüfen&quot;kann eine der folgenden Aktionen ausführen:

* Ein statisches Dokument
* Ein Dokument, das durch einen Schritt Dokument generieren innerhalb desselben Geschäftsvorgangs generiert wurde
* Ein mit dem [!DNL Workday]-Berichtdesigner erstellter formatierter Bericht

Sie können eines dieser Dokumente mit [Adobe-Text-Tags](https://adobe.com/go/adobesign_text_tag_guide_de) hinzufügen, um das Aussehen und die Position der Adobe zu steuern Signieren bestimmter Komponenten. Die Quelle des Dokuments muss innerhalb der Definition des Geschäftsvorgangs angegeben werden. Es ist nicht möglich, während der Durchführung des Geschäftsvorgangs ein Ad-hoc-Dokument hochzuladen.

Einzigartig bei der Verwendung von Adobe Sign mit einem Schritt Dokument prüfen ist die Möglichkeit, serialisierte Unterzeichnergruppen zu haben. Auf diese Weise können Sie rollenbasierte Gruppen angeben, die nacheinander signieren. Adobe Sign unterstützt keine parallelen Signaturgruppen.

Hilfe zum Konfigurieren des Schritts &quot;Dokument prüfen&quot;finden Sie in der [Kurzanleitung](https://adobe.com//go/adobesign_workday_quick_start){target=&quot;_blank&quot;}.

## Support {#support}

### [!DNL Workday] Support {#workday-support}

[!DNL Workday] ist der Integrationsverantwortliche, der Ihre erste Anlaufstelle bei Fragen zum Umfang der Integration, bei Funktionsanfragen oder Problemen bei der täglichen Arbeit mit der Integration sein sollte.

In den folgenden [!DNL Workday]-Community-Artikeln erfahren Sie, wie Sie die Integration beheben und Dokumente generieren:

* [Fehlerbehebung bei eSignature-Integrationen](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/zhA~hYllD3Hv1wu0CvHH_g)
* [Schritt zum Überprüfen von Dokumenten](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg)
* [Dynamische Dokumenterstellung](https://community.workday.com/saml/login?destination=/articles/176443)
* [Tipps zur Dokumenterstellung](https://community.workday.com/node/183242)

### Adobe Sign-Support {#adobe-sign-support}

Adobe Sign ist der Integrationspartner und sollte nur dann kontaktiert werden, wenn über die Integration keine Signaturen geliefert werden oder wenn die Benachrichtigung über ausstehende Signaturen fehlschlägt.

Adobe Sign-Kunden wenden sich bezüglich Support bitte an ihren Customer Success Manager (CSM). Alternativ kann der technische Support von Adobe telefonisch erreicht werden: 1-866-318-4100, auf die Produktliste warten und dann 4 und 2 eintippen (nach Aufforderung).

* [Hinzufügen von Adobe-Text-Tags zu Dokumenten](https://adobe.com/go/adobesign_text_tag_guide)
* [Dokumentkonfiguration und Beispiele](https://experienceleague.adobe.com/docs/dc-sign-integrations/using/workday/quick-start.html?lang=en){target=&quot;_blank&quot;}

## Häufig gestellte Fragen {#faq}

### Warum wird der Status nicht innerhalb von [!DNL Workday] aktualisiert, selbst wenn das Dokument vollständig signiert ist? {#why-is-the-status-not-being-updated-within-workday-even-the-document-is-fully-signed}

Der Dokumentstatus in [!DNL Workday] wird möglicherweise nicht angezeigt, wenn der Bewerber nach der Anmeldung in Adobe Sign nicht auf die Schaltfläche &quot;[!UICONTROL Senden]&quot;klickt.

Gemäß [!DNL Workday] Aufgabe e-Signatur-Signaturstatus prüfen: Um den Prozess zu starten, kann der Benutzer die zugehörige Posteingangsaufgabe senden.

Entsprechend [!DNL Workday] Entwicklung: Die ursprüngliche Signatur schließt den Vorgang nur ab, wenn der Benutzer die Posteingangsaufgabe nach dem Signieren des Dokuments sendet. Nach der Signatur wird der iframe geschlossen und der Benutzer wird zu derselben Aufgabe weitergeleitet, bei der er auf die Schaltfläche [!UICONTROL Senden] klicken kann, um den Vorgang abzuschließen.
