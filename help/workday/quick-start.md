---
title: Workday-Kurzanleitung
description: Eine Kurzanleitung für Kunden, die Adobe Sign in ihren Workday-Umgebungen verwenden möchten.
uuid: 10bf8ee8-9075-44d1-a836-e454950e2d9a
products: Adobe Sign
content-type: reference
discoiquuid: 13135c88-4c39-4707-b7ba-63ff94769258
locnotes: All languages; screenshots to follow what's there already (seems there is a mix within a given language version of the article)
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 8b6fa8b4-e240-4ebe-ae2a-8807d75a6c69
source-git-commit: 5ac9dc27dcdb6cab19281e6aafd4ea0524cc01d6
workflow-type: tm+mt
source-wordcount: '1348'
ht-degree: 24%

---

# [!DNL Workday] Kurzanleitung{#workday-quick-start-guide}

[**Adobe Sign-Support kontaktieren**](https://www.adobe.com/go/adobesign-support-center)

## Übersicht {#overview}

Dieses Dokument soll Ihnen helfen [!DNL Workday] Administratoren wissen, wie Sie die [!DNL Workday] Geschäftsprozesse, die Adobe Sign zum Abrufen elektronischer Signaturen einschließen. Verwenden von Adobe Sign innerhalb von [!DNL Workday]müssen Sie wissen, wie Sie [!DNL Workday] Elemente wie:

* [!UICONTROL Geschäftsprozess-Framework]
* Einrichtung und Konfiguration des Mandanten
* Berichterstattung und [!DNL Workday] Studio-Integration

## Aus heraus auf Adobe Sign zugreifen[!DNL Workday] {#access-adobe-sign}

[!UICONTROL Adobe Sign-Funktion für elektronische Signaturen] wird als [!UICONTROL Schritt &quot;Dokument prüfen&quot;] innerhalb der [!UICONTROL Business Process Framework (BPF)] und als Aufgabe &quot;Dokumente verteilen&quot;.

## [!UICONTROL Der Schritt „Review Document“ (Dokument prüfen)] {#review-document-step}

Adobe Sign für [!DNL Workday] über die [!UICONTROL Schritt &quot;Dokument prüfen&quot;] , die Sie zu über 400 Geschäftsprozessen innerhalb von [!DNL Workday], einschließlich [!UICONTROL Angebot], [!UICONTROL Dokumente und Aufgaben verteilen], [!UICONTROL Ausgleichszahlungen vorschlagen]und mehr.

Sie können die [[!DNL Workday] Community-Artikel [!UICONTROL Schritt &quot;Dokument prüfen&quot;]](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg).

Es besteht eine 1:1-Beziehung zwischen [!UICONTROL [!UICONTROL Schritt &quot;Dokument prüfen&quot;]s] und abrechenbaren Transaktionen mit Adobe Sign. Sie können mehrere Dokumente in einem [!UICONTROL Schritt &quot;Dokument prüfen&quot;] und sie werden als einzelnes Paket zur Signatur angezeigt.

**Hinweis**: Nur eine *Dynamisch* kann innerhalb eines bestimmten [!UICONTROL Schritt &quot;Dokument prüfen&quot;].

Definieren einer Funktion [!UICONTROL Schritt &quot;Dokument prüfen&quot;]:

1. Einfügen eines [!UICONTROL Schritt &quot;Dokument prüfen&quot;].
1. Geben Sie die Gruppen (Rollen) an, die auf die [!UICONTROL Schritt &quot;Dokument prüfen&quot;].

![Die Schritte des Geschäftsvorgangs](images/insert-review-doc-steptornm-575.png)

So konfigurieren Sie die [!UICONTROL Schritt &quot;Dokument prüfen&quot;]:

1. Geben Sie die *[!UICONTROL Integrationstyp eSignature]* als *[!UICONTROL eSign nach Adobe]*.

1. Fügen Sie dem Signaturraster Zeilen hinzu.

   * Die Signaturtabelle gibt die Reihenfolge an, in der das Dokument zur Unterzeichnung weitergeleitet wird. Jede Zeile enthält eine oder mehrere Rollen und stellt einen Schritt des Unterzeichnungsvorgangs dar..
   * Jedes Mitglied der Rolle innerhalb eines bestimmten Schritts wird benachrichtigt, dass ein Signaturereignis aussteht.
   * Sobald eine einzelne Person aus der Rolle signiert hat, wird der Zeilenschritt abgeschlossen und das Dokument wird in den nächsten Zeilenschritt verschoben.
   * Wenn alle Zeilen signiert wurden, wird die [!UICONTROL Schritt &quot;Dokument prüfen&quot;] ist abgeschlossen.

1. Geben Sie das zu signierende Dokument an. Wenn das Dokument ein [!UICONTROL Angebot BP]können Sie sie in einem Schritt Dokument generieren verwenden. Wählen Sie andernfalls ein vorhandenes Dokument oder einen vorhandenen Bericht.

1. Wiederholen Sie Schritt 3 für alle benötigten Dokumente..

   ![Den Schritt „Review Document“ (Dokument prüfen) konfigurieren](images/configure-rd-stepsmaller-575.png)

1. Fügen Sie optional einen &quot;Benutzer umleiten&quot;hinzu, um Aktionen mit der Einstellung &quot;Nicht unterschreiben&quot;zu erfassen. Wenn Benutzer ablehnen, [!DNL Workday] leitet die Dokumente zur Überprüfung in eine konfigurierte Sicherheitsgruppe um.

Über das Menü &quot;Zugehörige Aktionen&quot;eines [!UICONTROL Schritt &quot;Dokument prüfen&quot;], wählen Sie **[!UICONTROL Geschäftsprozess]** > **[!UICONTROL Umleitung beibehalten]**. Wählen Sie als Nächstes eine der folgenden Optionen:

* **[!UICONTROL Zurück]**: Damit Sicherheitsgruppenmitglieder einen Schritt zurück zu einem vorherigen Schritt im Geschäftsprozess senden können. Der Geschäftsprozess startet ab diesem Schritt neu.
* **[!UICONTROL Zum nächsten Schritt gehen]**: Damit Sicherheitsgruppenmitglieder einen Schritt zum nächsten Schritt im Geschäftsprozess weiterleiten können.
* **[!UICONTROL Sicherheitsgruppen]**: Schritte im Geschäftsablauf umleiten. Sicherheitsgruppen, die an dieser Eingabeaufforderung angezeigt werden, werden in der Geschäftsprozess-Sicherheitsrichtlinie im Abschnitt Umleitung ausgewählt.

## Schrittnotizen für Geschäftsvorgänge {#business-process-step-notes}

[!UICONTROL Rahmen für Geschäftsprozesse] leistungsstark ist; Sie müssen jedoch sicherstellen, dass

* Jeder Geschäftsprozess muss einen Abschlussschritt haben, der idealerweise am Ende des Geschäftsprozesses steht.

* Ein Abschlussschritt wird im Menü &quot;Zugehörige Aktionen&quot;des Suchsymbols festgelegt. Dies ist nur beim &quot;Anzeigen&quot;des Geschäftsvorgangs und nicht beim &quot;Bearbeiten&quot;des Geschäftsvorgangs möglich.

* Jeder Schritt des Geschäftsprozesses wird nacheinander ausgeführt.

   Sie können die Reihenfolge eines Schritts ändern, indem Sie den Bestellwert ändern. Um beispielsweise einen Schritt zwischen den Elementen &quot;c&quot;und &quot;d&quot;einzufügen, geben Sie ein neues Element als &quot;ca&quot;an.

### Beispiel: bieten {#example-offer}

Das Angebot BP ist ein Teilprozess des [!UICONTROL Dynamischer BP für Auftragsanwendung] die konfiguriert werden müssen, um das Angebot BP auszuführen. Sie wird ausgelöst, wenn der Status der Jobanwendung in &quot;[!UICONTROL Angebot]&quot; oder &quot;[!UICONTROL Angebot erstellen]&quot;.

Im folgenden Beispiel wird ein [!UICONTROL Schritt &quot;Dokument prüfen&quot;] verwendet sowohl für Nordamerika als auch für Japan den Schritt &quot;Dynamisches Dokument&quot;.

![Beispiel eines [!DNL Workday] Geschäftsprozess](images/bp-for-offersmaller-575.png)

Dieser Geschäftsvorgang führt Folgendes durch:

* fordert den Initiator des Geschäftsvorgangs auf, eine Entschädigung für den Kandidaten vorzuschlagen (Schritt b).
* Verwendet eine Schrittbedingung, um zu prüfen, ob das aktuelle Land NICHT Japan ist.

   Wenn true, wird Schritt &quot;ba&quot;ausgeführt, der ein Dokument in englischer Sprache verwendet.

   Bei &quot;false&quot;wird Schritt &quot;bb&quot;ausgeführt, der ein Dokument in japanischer Sprache verwendet.

* Definiert den Signaturvorgang im [!UICONTROL Schritt &quot;Dokument prüfen&quot;] &quot;bc&quot;.
* Definiert den Entscheidungspunkt, um ein Angebot im erforderlichen Abschlussschritt &quot;d&quot;zu machen.

Das im Schritt „ba“ generierte dynamische Dokument hat den Namen [!UICONTROL Offer Letter] (Angebotsbrief). Es enthält einen einzigen Textblock mit dem Namen [!UICONTROL Rapid Offer] (Schnellangebot). Sie können bei Bedarf mehrere Textblöcke wie Kopfzeile, Anrede, Vergütung, Stock, Schließen, Begriffe und mehr hinzufügen.

![[!DNL Workday] Dokumentseite anzeigen](images/offer-letter-575.png)

Der folgende dynamische Angebotsbrief wird im [!DNL Workday] Rich-Text-Editor. Die in *grau* sind [!DNL Workday] bereitgestellte Objekte, die auf Kontextdaten verweisen.

Bei den Elementen in {{geschweiften Klammern}} handelt es sich um [Adobe-Text-Tags](https://adobe.com/go/adobesign_text_tag_guide_de).

![Dynamisches Beispielformular](images/script.png)

Innerhalb der [!UICONTROL Schritt &quot;Dokument prüfen&quot;]wird das dynamische Dokument aus dem vorherigen Schritt referenziert und definiert den sequenziellen Signaturvorgang über zwei Signaturgruppen.

Das unten dargestellte Verhalten leitet das dynamisch generierte Dokument zunächst an den Personalmanager und dann an den Bewerber weiter.

![[!DNL Workday] Signaturgruppen werden definiert](images/configure-rd-stepsmaller-575.png)

### Beispiel: Dokumente verteilen {#example-distribute-documents}

Neu in [!DNL Workday] 30, kann die Aufgabe &quot;Dokumente oder Aufgaben massenhaft verteilen&quot;verwendet werden, um ein einzelnes Dokument an eine große Gruppe (&lt; 20 KB) einzelner Unterzeichner zu senden. Es gilt eine Begrenzung auf eine Unterschrift pro Dokument. Die Erstellung einer Distribution erfolgt durch Zugriff auf das[!UICONTROL Verteilen von Dokumenten oder Aufgaben erstellen]-Aktion aus der Suchleiste.

Beispiel: Senden Sie ein Auswahlformular für Mitarbeiterbeteiligungen an alle Manager mit [!UICONTROL Globale moderne Dienstleistungen]. Sie können sie bei Bedarf weiter auf einzelne Manager filtern.

Sie können auch auf die **Dokumente oder Aufgaben verteilen anzeigen** , um den Fortschritt der Verteilung zu verfolgen.

![](images/create-distributedocumentsortasks.png)

### Beispiel: Berichterstellung {#example-reporting}

[!DNL Workday] verfügt über eine umfassende Berichterstellungs-Infrastruktur. Wenn Sie Einblick in die Details des Adobe Sign-Vorgangs erhalten möchten, untersuchen Sie die Elemente des Ereignisses *Review Document Event* (Dokument prüfen).

Nachfolgend finden Sie einen einfachen benutzerspezifischen Bericht, der Adobe Sign-Transaktionen und ihren Status über alle Geschäftsvorgänge ermitteln kann.

![Beispiel eines [!DNL Workday] Benutzerdefinierter Bericht](images/review-document-eventsmaller-575.png)

Der folgende Bericht wurde unter Verwendung der Geschäftsvorgänge Offer (Angebot), Onboarding (Eingliederung) und Propose Compensation (Vergütung vorschlagen) innerhalb eines Implementierungsmandanten generiert.

Sie sehen folgende Elemente:

* die Dokumente zur Signatur
* den zugeordneten Schritt des Geschäftsvorgangs
* die nächste Person, die auf die Signatur wartet

![Beispiel eines [!DNL Workday] Bericht mit drei Objekten](images/workday-reportsmaller-575.png)

## Signierte Dokumente {#signed-documents}

Die [!DNL Workday] Signaturzyklus unterdrückt alle E-Mail-Benachrichtigungen von Adobe Sign. Die Benutzer werden über anhängige Aktionen in ihrem [!DNL Workday] Posteingang.

Sobald ein Dokument von allen Signaturgruppen signiert wurde, wird eine Kopie des signierten Dokuments per E-Mail an alle Mitglieder der Signaturgruppe verteilt.

Um dieses Verhalten zu unterdrücken, wenden Sie sich an Ihren [!UICONTROL Adobe Sign Success Manager] oder [Adobe Sign Support Team](https://adobe.com/go/adobesign-support-center).

Innerhalb [!DNL Workday]können Sie auf die signierten Dokumente im vollständigen Prozessdatensatz zugreifen. Sie finden folgende Informationen:

* Arbeitskräftedokumente im Arbeitnehmerprofil und
* Bewerberdokumente (Angebotsbriefe) im Profil &quot;Bewerber&quot;.

Das folgende Bild zeigt einen signierten Angebotsbrief für den Kandidaten Chris Foxx.

![Beispiel [!DNL Workday] Angebotsbrief](images/offer.png)

## Support {#support}

### [!DNL Workday] Support {#workday-support}

[!DNL Workday] ist der Integrationsverantwortliche, der Ihre erste Anlaufstelle bei Fragen zum Umfang der Integration, bei Funktionsanfragen oder Problemen bei der täglichen Arbeit mit der Integration sein sollte.

Die [!DNL Workday] Community enthält mehrere gute Artikel, wie Sie die Integration beheben und Dokumente generieren können:

* [Fehlersuche bei der eSignature-Integration](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/zhA~hYllD3Hv1wu0CvHH_g)
* [Der Schritt „Dokumente prüfen“](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg)
* [Dynamische Generierung von Dokumenten](https://community.workday.com/node/176443)
* [Konfigurationstipps für die Generierung von Angebotsunterlagen](https://community.workday.com/node/183242)

### Adobe Sign-Support {#adobe-sign-support}

Adobe Sign ist der Integrationspartner und sollte nur dann kontaktiert werden, wenn über die Integration keine Signaturen geliefert werden oder wenn die Benachrichtigung über ausstehende Signaturen fehlschlägt.

Adobe Sign-Kunden sollten sich an ihren Customer Success Manager wenden, um Unterstützung zu erhalten. Alternativ [!UICONTROL Technischer Support für Adobe] Telefonisch erreichbar: 1-866-318-4100, warten Sie auf die Produktliste und geben Sie Folgendes ein: 4 und dann 2 (nach Aufforderung).

* [Hinzufügen von Adobe-Text-Tags zu Dokumenten](https://www.adobe.com/go/adobesign_text_tag_guide)

<!--
[Download PDF](images/adobe-sign-for-workday-quick-start-guide-2016.pdf)
-->
