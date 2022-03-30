---
title: Installation der Workday-Testversion
description: Workday-Installationshandbuch für Testkonto in Adobe Sign
uuid: 0c51f329-b7c1-44a2-88a3-670be7673747
products: Adobe Sign
topic-tags: EchoSign/Integrations
content-type: reference
discoiquuid: 63ed2d5b-9d82-4f87-97e1-2dde23501e89
locnotes: All languages; screenshots for Tier 1 and 2 only (see the currently published localized page for guidance)
type: Documentation
solution: Acrobat Sign
role: User, Developer
topic: Integrations
exl-id: beafe6c0-262f-4f5b-9315-a023a4eef4a2
source-git-commit: 4d73ff36408283805386bd3266b683bc187d6031
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 31%

---

# [!DNL Workday] Testinstallation{#workday-trial-installation}

## Übersicht {#overview}

Dieses Dokument soll Ihnen helfen, [!DNL Workday] Kunden erfahren, wie sie ein Testkonto mit Adobe Sign aktivieren und dann in [!DNL Workday] Mandant. So verwenden Sie Adobe Sign in [!DNL Workday], Sie müssen wissen, wie Sie [!DNL Workday] Elemente wie:

* Rahmen für Geschäftsprozesse
* Einrichtung und Konfiguration der Mandanten
* Berichterstattung und [!DNL Workday] Integration mit Adobe Studio

**Hinweis**: Wenn Sie bereits über ein Adobe Sign-Konto verfügen, müssen Sie keine Testversion starten. Sie können sich an Ihren Client Success Manager wenden, um [!DNL Workday] Integration.

Die Schritte auf oberster Ebene zur Integration sind folgende:

* Aktiveren des Testkontos für Adobe Sign
* Erstellen eines Integrationsschlüssels in Adobe Sign
* Installieren Sie den Integrationsschlüssel im [!DNL Workday] Mandant

## Adobe Sign-Testkonto aktivieren {#activate-sign-trial-account}

Wenn Sie eine 30-Tage-Testversion von Adobe Sign anfordern möchten, müssen Sie diese [Anmeldeformular](https://land.echosign.com/esign-trial-workday-registration.html).

**Hinweis**: Es wird dringend empfohlen, zum Erstellen der Testversion eine gültige funktionale E-Mail-Adresse zu verwenden und keine temporäre E-Mail. Sie müssen auf diese E-Mail zugreifen, um das Konto zu bestätigen, daher muss die Adresse gültig sein.

![Das Anforderungsformular für den Test](images/trial-land.png)

Innerhalb eines Werktages stellt ein Adobe Sign-Onboarding-Spezialist Ihr Konto (in Adobe Sign) für [!DNL Workday]. Sobald der Vorgang abgeschlossen ist, erhalten Sie wie unten gezeigt eine Bestätigungs-E-Mail.

![Die Begrüßungs-E-Mail von Adobe Sign](images/welcome-email-2020.png)

So initialisieren Sie Ihr Konto und greifen auf Ihre Adobe Sign zu [!UICONTROL Startseite] &quot; den Anweisungen in der E-Mail .

![Das Adobe Sign-Dashboard](images/classic-home.png)

## Integrationsschlüssel generieren {#generate-an-integration-key}

Bei neuen Installationen müssen Sie in Adobe Sign einen Integrationsschlüssel generieren und diesen dann in [!DNL Workday]. Dieser Schlüssel authentifiziert die Adobe Sign und [!DNL Workday] Umgebungen, um sich gegenseitig zu vertrauen und Inhalte freizugeben.

So erstellen Sie in Adobe Sign einen Integrationsschlüssel:

1. Melden Sie sich in Adobe Sign mit Ihrem Administratorkonto an..
1. Navigieren Sie zu **[!UICONTROL **Account]** > **[!UICONTROL Persönliche Vorgaben]** > **[!UICONTROL Zugriffstoken**]**.
1. Klicken Sie auf **eingekreistes Pluszeichen** auf der rechten Seite des Fensters.

   Das Dialogfeld &quot; [!UICONTROL Integrationsschlüssel erstellen] Schnittstelle.

   ![Bild der Navigation zur Zugriffstoken-Seite](images/navigate-to-group-accesstokens.png)

1. Geben Sie einen intuitiven Namen für den Schlüssel ein, z. B. [!DNL Workday].

   Für den Integrationsschlüssel müssen folgende Elemente aktiviert sein:

   * agreement_read
   * agreement_write
   * agreement_send
   * widget_read
   * library_read

   ![Das Feld „Integrationsschlüssel erstellen“](images/create-integration-key-575.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

   Die Seite [!UICONTROL Zugriffstoken] mit den in Ihrem Konto erstellten Schlüsseln wird angezeigt.

1. Klicken Sie auf die Schlüsseldefinition, die für [!DNL Workday].

   Die [!UICONTROL Integrationsschlüssel] am oberen Rand der Definition angezeigt.

1. Klicken Sie auf **[!UICONTROL Integrationsschlüssel]** Link.

   Der Integrationsschlüssel wird angezeigt.

   ![Der Link „Integrationsschlüssel“](images/integration-key.png)

1. Kopieren Sie diesen Schlüssel und speichern Sie ihn für den nächsten Schritt an einem sicheren Ort.
1. Klicken Sie auf **[!UICONTROL OK]**.

   ![Das Feld „Integrationsschlüssel“](images/copy-the-key-575.png)

## Konfigurieren Sie die [!DNL Workday] Mieter {#configuring-the-workday-tenant}

### Integrationsschlüssel installieren {#install-the-integration-key}

Installieren des Integrationsschlüssels im [!DNL Workday] Mandant richtet die Vertrauensbeziehung zu Adobe Sign ein. Sobald diese Beziehung besteht, kann für jeden Geschäftsvorgang eine [!UICONTROL Schritt &quot;Dokument prüfen&quot;] hinzugefügt, der den Signaturprozess aktiviert.

**Hinweis**: Adobe Sign wird im gesamten [!DNL Workday] Umgebung.

So installieren Sie den Integrationsschlüssel:

1. Anmelden bei [!DNL Workday] als Kontoadministrator registrieren.
1. Suchen Sie nach dem **[!UICONTROL Einrichtung der Mandanten bearbeiten - Geschäftsvorgänge]** angezeigt.

1. Geben Sie Informationen zu den folgenden vier Feldern ein:

   * **[!UICONTROL Adobe Document Cloud-Bestätigung]**: Eine feste Textbestätigung der Integration.

   * **[!UICONTROL Adobe Document Cloud API-Schlüssel]**: Speicherort des Integrationsschlüssels

   * **[!UICONTROL Adobe Document Cloud-Absender-E-Mail-Adresse]**: Die E-Mail-Adresse des Administrators auf Gruppenebene in Adobe Sign

   * **[!UICONTROL Dokumente entfernen, die auf eine E-Signatur warten, wenn das Dokument abgebrochen wird]**: Eine optionale Konfiguration, bei der Dokumente aus dem Signaturzyklus entfernt werden, wenn ein Dokument in [!DNL Workday].

   ![Die Felder für den Adobe Sign-Integrationsschlüssel](images/bp-filled-torn2-575.png)

1. Führen Sie anschließend die Installation durch:

   1. Fügen Sie Ihren Integrationsschlüssel in das Feld [!UICONTROL Adobe Sign API-Integrationsschlüssel] ein.
   1. Geben Sie die E-Mail-Adresse des Adobe Sign-Administrators in das Feld [!UICONTROL Adobe Document Cloud-Absender-E-Mail-Adresse] ein.
   1. Klicken Sie auf **[!UICONTROL OK]**.

   ![Die Felder für den Integrationsschlüssel und das Feld für die E-Mail-Adresse des Schlüsselbesitzers](images/bp-filled-small.png)

Adobe Sign-Funktionen können jetzt zu jedem Geschäftsvorgang hinzugefügt werden, indem ein [!UICONTROL Schritt &quot;Dokument prüfen&quot;] und Konfiguration für die Verwendung **[!UICONTROL eSign nach Adobe]** als E-Signaturtyp.

### Den Schritt &quot;Dokument prüfen&quot; konfigurieren {#configure-the-review-document-step}

Das Dokument für den Schritt Dokument prüfen kann ein statisches Dokument sein. ein Dokument, das mit dem Schritt &quot;Dokument generieren&quot; innerhalb desselben Geschäftsvorgangs erstellt wurde; oder einen formatierten Bericht, der mit dem [!DNL Workday] Berichts-Designer. Alle diese Dokumente können mit [Adobe-Text-Tags](https://adobe.com/go/adobesign_text_tag_guide_de) versehen werden, um das Aussehen und die Position der spezifischen Komponenten von Adobe Sign zu steuern. Die Quelle des Dokuments muss innerhalb der Definition des Geschäftsvorgangs angegeben werden. Es ist nicht möglich, ein Ad-hoc-Dokument hochzuladen, während der Geschäftsprozess ausgeführt wird.

Die Möglichkeit, Unterzeichnergruppen mit Seriennummer zu versehen, ist eine Besonderheit von Adobe Sign mit dem Schritt &quot;Dokument prüfen&quot;. Mit Unterzeichnergruppen können Sie rollenbasierte Gruppen angeben, die nacheinander signieren. Adobe Sign unterstützt keine parallelen Signaturgruppen.

Hilfe zum Schritt Dokument prüfen finden Sie im [Kurzanleitung](https://adobe.com//go/adobesign_workday_quick_start){target=&quot;_blank&quot;}.

## Support {#support}

### [!DNL Workday] unterstützen {#workday-support}

[!DNL Workday] ist der Integrationsverantwortliche, der Ihre erste Anlaufstelle bei Fragen zum Umfang der Integration, bei Funktionsanfragen oder Problemen bei der täglichen Arbeit mit der Integration sein sollte.

Die [!DNL Workday] Community hat mehrere gute Artikel zur Fehlerbehebung bei der Integration und zum Generieren von Dokumenten:

* [Fehlersuche bei der eSignature-Integration](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/zhA~hYllD3Hv1wu0CvHH_g)
* [Der Schritt „Dokumente prüfen“](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg)
* [Dynamische Generierung von Dokumenten](https://community.workday.com/node/176443)

* [Konfigurationstipps für die Generierung von Angebotsunterlagen](https://community.workday.com/node/183242)

### Unterstützung für Adobe Sign {#adobe-sign-support}

Adobe Sign ist der Integrationspartner und sollte nur dann kontaktiert werden, wenn über die Integration keine Signaturen geliefert werden oder wenn die Benachrichtigung über ausstehende Signaturen fehlschlägt.

Adobe Sign-Kunden wenden sich bezüglich Support bitte an ihren Customer Success Manager (CSM). Alternativ ist der technische Support von Adobe telefonisch erreichbar: 1-866-318-4100; auf die Produktliste warten und dann Folgendes eingeben: 4 und dann 2 (nach Aufforderung).

* [Hinzufügen von Adobe-Text-Tags zu Dokumenten](https://adobe.com/go/adobesign_text_tag_guide)

* [Konfiguration und Beispiele für &quot;Dokument prüfen&quot;](https://www.adobe.com//go/adobesign_workday_quick_start){target=&quot;_blank&quot;}

[**Adobe Sign-Support kontaktieren**](https://www.adobe.com/go/adobesign-support-center)
