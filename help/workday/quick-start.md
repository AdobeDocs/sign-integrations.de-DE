---
title: Workday-Kurzanleitung
description: Eine Kurzanleitung für Kunden, die Adobe Sign in ihren Workday-Umgebungen verwenden möchten.
uuid: 10bf8ee8-9075-44d1-a836-e454950e2d9a
products: Adobe Sign
content-type: reference
discoiquuid: 13135c88-4c39-4707-b7ba-63ff94769258
locnotes: All languages; screenshots to follow what's there already (seems there is a mix within a given language version of the article)
type: Documentation
solution: Acrobat Sign, Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 8b6fa8b4-e240-4ebe-ae2a-8807d75a6c69
source-git-commit: b326a9afa2c16333d390cac3b30a2c7c741a4360
workflow-type: tm+mt
source-wordcount: '1348'
ht-degree: 24%

---

# [!DNL Workday] Kurzanleitung{#workday-quick-start-guide}

[**Adobe Sign-Support kontaktieren**](https://www.adobe.com/go/adobesign-support-center)

## Übersicht {#overview}

Dieses Dokument soll Ihnen helfen, [!DNL Workday] Administratoren wissen, wie Sie die [!DNL Workday] Geschäftsprozesse mit Adobe Sign zum Einholen elektronischer Unterschriften. So verwenden Sie Adobe Sign in [!DNL Workday], Sie müssen wissen, wie Sie [!DNL Workday] Elemente wie:

* [!UICONTROL Rahmen für Geschäftsprozesse]
* Einrichtung und Konfiguration der Mandanten
* Berichterstattung und [!DNL Workday] Studio-Integration

## Aus heraus auf Adobe Sign zugreifen[!DNL Workday] {#access-adobe-sign}

[!UICONTROL Adobe Sign-Funktion für elektronische Unterschriften] wird als [!UICONTROL Schritt &quot;Dokument prüfen&quot;] im Rahmen der [!UICONTROL Business Process Framework (BPF)] und als Aufgabe &quot;Dokumente verteilen&quot;.

## [!UICONTROL Der Schritt „Review Document“ (Dokument prüfen)] {#review-document-step}

Adobe Sign für [!DNL Workday] wird über die [!UICONTROL Schritt &quot;Dokument prüfen&quot;] die Sie zu mehr als 400 Geschäftsvorgängen innerhalb von [!DNL Workday]einschließlich [!UICONTROL Angebot], [!UICONTROL Dokumente und Aufgaben verteilen], [!UICONTROL Ausgleichsvorschlag]und mehr.

Weitere Informationen finden Sie im [[!DNL Workday] Community-Artikel über [!UICONTROL Schritt &quot;Dokument prüfen&quot;]](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg).

Es gibt eine 1:1-Beziehung zwischen [!UICONTROL [!UICONTROL Schritt &quot;Dokument prüfen&quot;]s] und abrechenbare Transaktionen mit Adobe Sign. Sie können mehrere Dokumente in einem [!UICONTROL Schritt &quot;Dokument prüfen&quot;] und sie werden als ein Paket zur Unterzeichnung vorgelegt.

**Hinweis**: Nur eine einzelne *Dynamisch* Dokument kann in einem bestimmten [!UICONTROL Schritt &quot;Dokument prüfen&quot;].

So definieren Sie eine Funktion [!UICONTROL Schritt &quot;Dokument prüfen&quot;]:

1. Fügen Sie ein [!UICONTROL Schritt &quot;Dokument prüfen&quot;].
1. Geben Sie die Gruppen (Rollen) an, die für die [!UICONTROL Schritt &quot;Dokument prüfen&quot;].

![Die Schritte des Geschäftsvorgangs](images/insert-review-doc-steptornm-575.png)

So konfigurieren Sie die [!UICONTROL Schritt &quot;Dokument prüfen&quot;]:

1. Geben Sie die *[!UICONTROL Integrationstyp der eSignatur]* als *[!UICONTROL eSign nach Adobe]*.

1. Fügen Sie dem Signaturraster Zeilen hinzu.

   * Die Signaturtabelle gibt die Reihenfolge an, in der das Dokument zur Unterzeichnung weitergeleitet wird. Jede Zeile enthält eine oder mehrere Rollen und stellt einen Schritt des Unterzeichnungsvorgangs dar..
   * Jedes Mitglied der Rolle in einem bestimmten Schritt wird darüber informiert, dass ein Signaturereignis aussteht.
   * Sobald eine einzelne Person aus der Rolle signiert hat, wird der Zeilenschritt abgeschlossen und das Dokument wird zum nächsten Zeilenschritt verschoben.
   * Wenn alle Zeilen signiert wurden, zeigt der Katalog [!UICONTROL Schritt &quot;Dokument prüfen&quot;] abgeschlossen ist.

1. Geben Sie das zu signierende Dokument an. Wenn das Dokument ein [!UICONTROL Angebot BP]können Sie sie über den Schritt &quot;Dokument generieren&quot; verwenden. Wählen Sie andernfalls ein vorhandenes Dokument oder einen vorhandenen Bericht.

1. Wiederholen Sie Schritt 3 für alle benötigten Dokumente..

   ![Den Schritt „Review Document“ (Dokument prüfen) konfigurieren](images/configure-rd-stepsmaller-575.png)

1. Optional können Sie einen &quot;Benutzer umleiten&quot; hinzufügen, um die Aktionen &quot;Unterzeichnen ablehnen&quot; zu erfassen. Wenn Benutzer ablehnen, [!DNL Workday] leitet die Dokumente zur Überprüfung an eine konfigurierte Sicherheitsgruppe um.

Im Menü für zugehörige Aktionen eines [!UICONTROL Schritt &quot;Dokument prüfen&quot;]&quot; die Option **[!UICONTROL Geschäftsprozess]** > **[!UICONTROL Umleitung verwalten]**. Wählen Sie als Nächstes eine der folgenden Optionen aus:

* **[!UICONTROL Nach hinten]**: So können Sicherheitsgruppenmitglieder einen Schritt an einen vorherigen Schritt im Geschäftsprozess zurücksenden. Der Geschäftsprozess startet ab diesem Schritt neu.
* **[!UICONTROL Zum nächsten Schritt]**: So können Sicherheitsgruppenmitglieder einen Schritt an den nächsten Schritt im Geschäftsprozess weiterleiten.
* **[!UICONTROL Sicherheitsgruppen]**: So leiten Sie Schritte im Geschäftsprozessfluss um: Sicherheitsgruppen, die bei dieser Eingabeaufforderung angezeigt werden, werden in der Sicherheitsrichtlinie für Geschäftsprozesse im Abschnitt Umleiten ausgewählt.

## Hinweise zu Geschäftsprozessen {#business-process-step-notes}

[!UICONTROL Der Rahmen für Geschäftsprozesse] mächtig ist; Sie müssen jedoch sicherstellen, dass

* Jeder Geschäftsprozess muss einen Abschlussschritt haben, der idealerweise am Ende des Geschäftsprozesses liegt.

* Im Menü für zugehörige Aktionen des Suchsymbols wird ein Abschlussschritt angezeigt. Dies ist nur beim &quot;Anzeigen&quot; des Geschäftsvorgangs und nicht beim &quot;Bearbeiten&quot; des Geschäftsvorgangs möglich.

* Jeder Schritt des Geschäftsprozesses wird sequenziell ausgeführt.

   Sie können die Reihenfolge eines Schritts ändern, indem Sie den Bestellwert ändern. Wenn Sie beispielsweise einen Schritt zwischen den Elementen &quot;c&quot; und &quot;d&quot; einfügen möchten, geben Sie ein neues Element als &quot;ca&quot; an.

### Beispiel: anbieten {#example-offer}

Der Geschäftsvorgang des Angebots ist ein Unterprozess der [!UICONTROL Dynamisches Geschäftsverfahren für Stellenbewerbungen] die konfiguriert werden muss, um den Angebotsvorgang auszuführen. Er wird ausgelöst, wenn der Status der Stellenanwendung in &quot;&quot; verschoben wird.[!UICONTROL Angebot]&quot; oder &quot;[!UICONTROL Angebot unterbreiten]&quot;.

Im folgenden Beispiel wird ein [!UICONTROL Schritt &quot;Dokument prüfen&quot;] verwendet einen Schritt für dynamische Dokumente für Nordamerika und Japan.

![Beispiel einer [!DNL Workday] Geschäftsprozess](images/bp-for-offersmaller-575.png)

Dieser Geschäftsvorgang führt Folgendes durch:

* fordert den Initiator des BP auf, eine Entschädigung für den Bewerber vorzuschlagen (Schritt b).
* Verwendet eine Schrittbedingung, um zu testen, ob das aktuelle Land NICHT Japan ist.

   Wenn &quot;true&quot;, wird Schritt &quot;ba&quot; ausgeführt, der ein englischsprachiges Dokument verwendet.

   Wenn &quot;false&quot;, wird Schritt &quot;bb&quot; ausgeführt, der ein Dokument in japanischer Sprache verwendet.

* Definiert den Signaturprozess in der Datei [!UICONTROL Schritt &quot;Dokument prüfen&quot;] &quot;bc&quot;.
* Definiert den Entscheidungspunkt, ein Angebot im erforderlichen Abschlussschritt &quot;d&quot; abzugeben.

Das im Schritt „ba“ generierte dynamische Dokument hat den Namen [!UICONTROL Offer Letter] (Angebotsbrief). Es enthält einen einzigen Textblock mit dem Namen [!UICONTROL Rapid Offer] (Schnellangebot). Sie können bei Bedarf mehrere Textblöcke wie Kopfzeile, Anrede, Vergütung, Bestand, Abschluss, Bedingungen und mehr hinzufügen.

![[!DNL Workday] Dokumentseite anzeigen](images/offer-letter-575.png)

Der folgende dynamische Angebotsbrief wird im [!DNL Workday] Rich-Text-Editor. Die in *Grau* sind [!DNL Workday] Objekte bereitgestellt, die auf Kontextdaten verweisen.

Bei den Elementen in {{geschweiften Klammern}} handelt es sich um [Adobe-Text-Tags](https://adobe.com/go/adobesign_text_tag_guide_de).

![Dynamisches Beispielformular](images/script.png)

Innerhalb der [!UICONTROL Schritt &quot;Dokument prüfen&quot;]klicken, wird im vorherigen Schritt auf das dynamische Dokument verwiesen, das den sequenziellen Signaturprozess über zwei Signaturgruppen definiert.

Das unten abgebildete Verhalten leitet das dynamisch generierte Dokument zuerst an den Personalverantwortlichen und dann an den Bewerber weiter.

![[!DNL Workday] Unterzeichnergruppen werden definiert](images/configure-rd-stepsmaller-575.png)

### Beispiel: Verteilen von Dokumenten {#example-distribute-documents}

Eingeführt in [!DNL Workday] 30, kann die Aufgabe Dokumente oder Aufgaben global verteilen verwendet werden, um ein einzelnes Dokument an eine große Gruppe (&lt; 20.000) einzelner Unterzeichner zu senden. Es gilt eine Begrenzung auf eine Unterschrift pro Dokument. Die Erstellung einer Distribution erfolgt durch Zugriff auf das[!UICONTROL Erstellen von verteilten Dokumenten oder Aufgaben]’ Aktion in der Suchleiste.

Beispiel: Senden Sie ein Auswahlformular für die Mitarbeiterbeteiligung an alle Manager mit [!UICONTROL Global Modern Services]. Sie können sie bei Bedarf weiter nach einzelnen Managern filtern.

Sie können auch auf das Dialogfeld &quot; **Ansicht > Dokumente oder Aufgaben verteilen** , um den Fortschritt der Verteilung zu verfolgen.

![](images/create-distributedocumentsortasks.png)

### Beispiel: Berichterstellung {#example-reporting}

[!DNL Workday] verfügt über eine umfassende Berichterstellungs-Infrastruktur. Wenn Sie Einblick in die Details des Adobe Sign-Vorgangs erhalten möchten, untersuchen Sie die Elemente des Ereignisses *Review Document Event* (Dokument prüfen).

Nachfolgend finden Sie einen einfachen benutzerspezifischen Bericht, der Adobe Sign-Transaktionen und ihren Status über alle Geschäftsvorgänge ermitteln kann.

![Beispiel einer [!DNL Workday] Benutzerdefinierter Bericht](images/review-document-eventsmaller-575.png)

Der folgende Bericht wurde unter Verwendung der Geschäftsvorgänge Offer (Angebot), Onboarding (Eingliederung) und Propose Compensation (Vergütung vorschlagen) innerhalb eines Implementierungsmandanten generiert.

Sie sehen folgende Elemente:

* die Dokumente zur Signatur
* den zugeordneten Schritt des Geschäftsvorgangs
* die nächste Person, die auf die Signatur wartet

![Beispiel einer [!DNL Workday] Bericht mit drei Objekten](images/workday-reportsmaller-575.png)

## Signierte Dokumente {#signed-documents}

Die [!DNL Workday] Der Signaturzyklus unterdrückt alle E-Mail-Benachrichtigungen von Adobe Sign. Benutzer werden über ausstehende Aktionen in ihren [!DNL Workday] Posteingang.

Sobald ein Dokument von allen Signaturgruppen signiert wurde, wird eine Kopie des signierten Dokuments per E-Mail an alle Mitglieder der Signaturgruppe verteilt.

Um dieses Verhalten zu unterdrücken, können Sie sich an Ihren [!UICONTROL Adobe Sign Success Manager] oder der &quot; [Adobe Sign Support-Team](https://adobe.com/go/adobesign-support-center).

Innerhalb [!DNL Workday]können Sie im vollständigen Prozessdatensatz auf die signierten Dokumente zugreifen. Sie finden hier:

* Arbeitskräftedokumente im Arbeitsprofil und
* Bewerberdokumente (Angebotsschreiben) im Bewerberprofil.

Die folgende Abbildung zeigt einen unterzeichneten Angebotsbrief für den Kandidaten Chris Foxx.

![Beispiel [!DNL Workday] Angebotsschreiben](images/offer.png)

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

Adobe Sign-Kunden sollten sich an ihren Customer Success Manager wenden, um Unterstützung zu erhalten. Alternativ können Sie [!UICONTROL Technischer Support für Adobe] telefonisch erreichbar: 1-866-318-4100, warten Sie auf die Produktliste und geben Sie dann Folgendes ein: 4 und dann 2 (nach Aufforderung).

* [Hinzufügen von Adobe-Text-Tags zu Dokumenten](https://www.adobe.com/go/adobesign_text_tag_guide)

<!--
[Download PDF](images/adobe-sign-for-workday-quick-start-guide-2016.pdf)
-->
