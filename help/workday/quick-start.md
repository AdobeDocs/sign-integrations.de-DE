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
source-git-commit: d462ccf41fa5483cfa02f5eaf154c23f26157a1e
workflow-type: tm+mt
source-wordcount: '1352'
ht-degree: 31%

---

# [!DNL Workday] Kurzanleitung{#workday-quick-start-guide}

[**Adobe Sign-Support kontaktieren**](https://adobe.com/go/adobesign-support-center_de)

## Übersicht {#overview}

Dieses Dokument soll [!DNL Workday]-Administratoren dabei helfen, die [!DNL Workday]-Geschäftsvorgänge so anzupassen, dass sie Adobe Sign zum Abrufen elektronischer Signaturen einschließen. Um Adobe Sign in [!DNL Workday] zu verwenden, müssen Sie wissen, wie [!DNL Workday]-Elemente erstellt und geändert werden, z. B.:

* Geschäftsprozess-Framework
* Einrichtung und Konfiguration des Mandanten
* Reporting und [!DNL Workday] Studio-Integration

## Aus heraus auf Adobe Sign zugreifen[!DNL Workday] {#access-adobe-sign}

Die elektronische Signaturfunktion der Adobe Sign wird als Aktion [!UICONTROL Schritt des Dokuments prüfen] innerhalb des Business Process Framework (BPF) und als Aufgabe &quot;Dokumente verteilen&quot;angezeigt.

## [!UICONTROL Der Schritt „Review Document“ (Dokument prüfen)] {#review-document-step}

Adobe Sign für [!DNL Workday] wird über den Schritt [!UICONTROL Dokument prüfen] bereitgestellt, den Sie zu über 400 Geschäftsvorgängen innerhalb von [!DNL Workday] hinzufügen können, einschließlich Angebot, Verteilen von Dokumenten und Aufgaben, Ausgleichsvorschlägen und mehr.

Sie können die [[!DNL Workday] Community-Artikel auf [!UICONTROL Schritt zum Überprüfen des Dokuments]](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg) lesen.

Es besteht eine 1:1-Beziehung zwischen [!UICONTROL [!UICONTROL Schritt &quot;Dokument prüfen&quot;und ]s]-Abrechnungstransaktionen mit Adobe Sign. Sie können mehrere Dokumente in einem einzigen [!UICONTROL Schritt Dokument prüfen] zusammenführen und sie werden als einzelnes Paket zur Signatur angezeigt.

**Hinweis**: Innerhalb eines bestimmten  ** Dokumentschritts [!UICONTROL  kann nur auf ein einzelnes ]dynamisches Dokument verwiesen werden.

So definieren Sie eine Funktion [!UICONTROL Schritt &quot;Dokument prüfen]&quot;:

1. Fügen Sie einen [!UICONTROL Schritt Dokument prüfen] ein.
1. Geben Sie die Gruppen (Rollen) an, die auf den Schritt [!UICONTROL Dokument prüfen] angewendet werden können.

![Die Schritte des Geschäftsvorgangs](images/insert-review-doc-steptornm-575.png)

So konfigurieren Sie den Schritt [!UICONTROL Dokument prüfen]:

1. Geben Sie den *[!UICONTROL eSignature Integration type]* als *[!UICONTROL eSign by Adobe]* an.

1. Fügen Sie dem Signaturraster Zeilen hinzu.

   * Die Signaturtabelle gibt die Reihenfolge an, in der das Dokument zur Unterzeichnung weitergeleitet wird. Jede Zeile enthält eine oder mehrere Rollen und stellt einen Schritt des Unterzeichnungsvorgangs dar..
   * Jedes Mitglied der Rolle innerhalb eines bestimmten Schritts wird benachrichtigt, dass ein Signaturereignis aussteht.
   * Sobald eine einzelne Person aus der Rolle signiert hat, wird der Zeilenschritt abgeschlossen und das Dokument wird in den nächsten Zeilenschritt verschoben.
   * Wenn alle Zeilen signiert wurden, ist der Schritt [!UICONTROL Dokument prüfen] abgeschlossen.

1. Geben Sie das zu signierende Dokument an. Wenn es sich um einen Geschäftsvorgang „Offer“ (Angebot) handelt, können Sie das Dokument aus einem Schritt „Generate Document“ (Dokument generieren) verwenden. Wählen Sie andernfalls ein vorhandenes Dokument oder einen vorhandenen Bericht.

1. Wiederholen Sie Schritt 3 für alle benötigten Dokumente..

   ![Den Schritt „Review Document“ (Dokument prüfen) konfigurieren](images/configure-rd-stepsmaller-575.png)

1. Fügen Sie optional einen &quot;Benutzer umleiten&quot;hinzu, um Aktionen mit der Einstellung &quot;Nicht unterschreiben&quot;zu erfassen. Wenn Benutzer ablehnen, leitet [!DNL Workday] die Dokumente zur Überprüfung in eine konfigurierte Sicherheitsgruppe um.

Wählen Sie im Menü &quot;Zugehörige Aktionen&quot;eines [!UICONTROL Schritt Dokument prüfen] **[!UICONTROL Geschäftsprozess]** > **[!UICONTROL Umleitung beibehalten]**. Wählen Sie als Nächstes eine der folgenden Optionen:

* **[!UICONTROL Zurücksenden]**: Damit Sicherheitsgruppenmitglieder einen Schritt zurück zu einem vorherigen Schritt im Geschäftsprozess senden können. Der Geschäftsprozess startet ab diesem Schritt neu.
* **[!UICONTROL Zum nächsten Schritt]** gehen: Damit Sicherheitsgruppenmitglieder einen Schritt zum nächsten Schritt im Geschäftsprozess weiterleiten können.
* **[!UICONTROL Sicherheitsgruppen]**: Schritte im Geschäftsablauf umleiten. Sicherheitsgruppen, die an dieser Eingabeaufforderung angezeigt werden, werden in der Geschäftsprozess-Sicherheitsrichtlinie im Abschnitt Umleitung ausgewählt.

## Schrittnotizen für Geschäftsvorgänge {#business-process-step-notes}

Der Rahmen für Geschäftsprozesse ist leistungsstark. Sie müssen jedoch sicherstellen, dass

* Jeder Geschäftsprozess muss einen Abschlussschritt haben, der idealerweise am Ende des Geschäftsprozesses steht.

* Ein Abschlussschritt wird im Menü &quot;Zugehörige Aktionen&quot;des Suchsymbols deaktiviert. Dies ist nur beim &quot;Anzeigen&quot;des Geschäftsvorgangs und nicht beim &quot;Bearbeiten&quot;des Geschäftsvorgangs möglich.

* Jeder Schritt des Geschäftsprozesses wird nacheinander ausgeführt.

   Sie können die Reihenfolge eines Schritts ändern, indem Sie den Bestellwert ändern. Um beispielsweise einen Schritt zwischen den Elementen &quot;c&quot;und &quot;d&quot;einzufügen, geben Sie ein neues Element als &quot;ca&quot;an.

### Beispiel: bieten {#example-offer}

Das Angebot BP ist ein Teilprozess des Job Application Dynamic BP, der konfiguriert werden muss, um das Angebot BP auszuführen. Er wird ausgelöst, wenn der Zustand von „Job Application“ (Bewerbung) in „Offer“ (Angebot) oder „Make Offer“ (Angebot machen) übergeht.

Im folgenden Beispiel verwendet ein [!UICONTROL Schritt Dokument prüfen] einen Schritt für ein dynamisches Dokument für Nordamerika und Japan.

![Beispiel für einen  [!DNL Workday] Geschäftsprozess](images/bp-for-offersmaller-575.png)

Dieser Geschäftsvorgang führt Folgendes durch:

* fordert den Initiator des Geschäftsvorgangs auf, eine Entschädigung für den Kandidaten vorzuschlagen (Schritt b).
* Verwendet eine Schrittbedingung, um zu prüfen, ob das aktuelle Land NICHT Japan ist.

   Wenn true, wird Schritt &quot;ba&quot;ausgeführt, der ein Dokument in englischer Sprache verwendet.

   Bei &quot;false&quot;wird Schritt &quot;bb&quot;ausgeführt, der ein Dokument in japanischer Sprache verwendet.

* Definiert den Signaturvorgang im Schritt [!UICONTROL Dokument prüfen] &quot;bc&quot;.
* Definiert den Entscheidungspunkt, um ein Angebot im erforderlichen Abschlussschritt &quot;d&quot;zu machen.

Das im Schritt „ba“ generierte dynamische Dokument hat den Namen [!UICONTROL Offer Letter] (Angebotsbrief). Es enthält einen einzigen Textblock mit dem Namen [!UICONTROL Rapid Offer] (Schnellangebot). Sie können bei Bedarf mehrere Textblöcke wie Kopfzeile, Anrede, Vergütung, Stock, Schließen, Begriffe und mehr hinzufügen.

![[!DNL Workday] Dokumentseite anzeigen](images/offer-letter-575.png)

Der folgende dynamische Angebotsbrief wird im Rich-Text-Editor [!DNL Workday] erstellt. Die unter *grau* hervorgehobenen Elemente sind [!DNL Workday] bereitgestellte Objekte, die auf Kontextdaten verweisen.

Bei den Elementen in {{geschweiften Klammern}} handelt es sich um [Adobe-Text-Tags](https://adobe.com/go/adobesign_text_tag_guide_de).

![Dynamisches Beispielformular](images/script.png)

Im Schritt [!UICONTROL Dokument prüfen] wird das dynamische Dokument aus dem vorherigen Schritt referenziert und definiert den sequenziellen Signaturvorgang über zwei Signaturgruppen.

Mit dem unten gezeigten Verhalten wird das dynamisch generierte Dokument zuerst an den Personalmanager und dann an den Bewerber weitergeleitet.

![[!DNL Workday] Signaturgruppen werden definiert](images/configure-rd-stepsmaller-575.png)

### Beispiel: Dokumente verteilen {#example-distribute-documents}

Die Aufgabe &quot;Dokumente oder Aufgaben massenhaft verteilen&quot;wurde in [!DNL Workday] 30 eingeführt und kann verwendet werden, um ein einzelnes Dokument an eine große Gruppe (&lt; 20 KB) einzelner Unterzeichner zu senden. Es gilt eine Begrenzung auf eine Unterschrift pro Dokument. Die Erstellung einer Distribution erfolgt durch Zugriff auf die Aktion &quot;[!UICONTROL Verteilen von Dokumenten oder Aufgaben erstellen]&quot;in der Suchleiste.

Beispiel: Senden Sie ein Auswahlformular zur Mitarbeitergleichstellung an alle Manager bei Global Modern Services. Sie können sie bei Bedarf weiter auf einzelne Manager filtern.

Sie können auch auf den Bericht **Dokumente verteilen anzeigen oder Aufgaben** anzeigen, um den Verteilungsfortschritt zu verfolgen.

![](images/create-distributedocumentsortasks.png)

### Beispiel: Berichterstellung {#example-reporting}

[!DNL Workday] verfügt über eine umfassende Berichterstellungs-Infrastruktur. Wenn Sie Einblick in die Details des Adobe Sign-Vorgangs erhalten möchten, untersuchen Sie die Elemente des Ereignisses *Review Document Event* (Dokument prüfen).

Nachfolgend finden Sie einen einfachen benutzerspezifischen Bericht, der Adobe Sign-Transaktionen und ihren Status über alle Geschäftsvorgänge ermitteln kann.

![Beispiel für einen  [!DNL Workday] benutzerdefinierten Bericht](images/review-document-eventsmaller-575.png)

Der folgende Bericht wurde unter Verwendung der Geschäftsvorgänge Offer (Angebot), Onboarding (Eingliederung) und Propose Compensation (Vergütung vorschlagen) innerhalb eines Implementierungsmandanten generiert.

Sie sehen folgende Elemente:

* die Dokumente zur Signatur
* den zugeordneten Schritt des Geschäftsvorgangs
* die nächste Person, die auf die Signatur wartet

![Beispiel für einen  [!DNL Workday] Bericht mit drei Objekten](images/workday-reportsmaller-575.png)

## Signierte Dokumente {#signed-documents}

Der Signaturzyklus [!DNL Workday] unterdrückt alle E-Mail-Benachrichtigungen von Adobe Sign. Benutzer werden über ausstehende Aktionen in ihrem [!DNL Workday]-Posteingang informiert.

Sobald ein Dokument von allen Signaturgruppen signiert wurde, wird eine Kopie des signierten Dokuments per E-Mail an alle Mitglieder der Signaturgruppe verteilt.

Um dieses Verhalten zu unterdrücken, wenden Sie sich an Ihren Adobe Sign Success Manager oder das [Adobe Sign Support-Team](https://adobe.com/go/adobesign-support-center).

Innerhalb von [!DNL Workday] können Sie auf die signierten Dokumente im vollständigen Prozessdatensatz zugreifen. Sie finden folgende Informationen:

* Arbeitskräftedokumente im Arbeitnehmerprofil und
* Bewerberdokumente (Angebotsbriefe) im Profil &quot;Bewerber&quot;.

Das folgende Bild zeigt einen signierten Angebotsbrief für den Kandidaten Chris Foxx.

![Beispielangebotssbrief  [!DNL Workday] ](images/offer.png)

## Support {#support}

### [!DNL Workday] Support {#workday-support}

[!DNL Workday] ist der Integrationsverantwortliche, der Ihre erste Anlaufstelle bei Fragen zum Umfang der Integration, bei Funktionsanfragen oder Problemen bei der täglichen Arbeit mit der Integration sein sollte.

Die [!DNL Workday]-Community enthält mehrere gute Artikel, wie Sie die Integration beheben und Dokumente generieren:

* [Fehlersuche bei der eSignature-Integration](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/zhA~hYllD3Hv1wu0CvHH_g)
* [Der Schritt „Dokumente prüfen“](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg)
* [Dynamische Generierung von Dokumenten](https://community.workday.com/node/176443)
* [Konfigurationstipps für die Generierung von Angebotsunterlagen](https://community.workday.com/node/183242)

### Adobe Sign-Support {#adobe-sign-support}

Adobe Sign ist der Integrationspartner und sollte nur dann kontaktiert werden, wenn über die Integration keine Signaturen geliefert werden oder wenn die Benachrichtigung über ausstehende Signaturen fehlschlägt.

Adobe Sign-Kunden wenden sich bezüglich Support bitte an ihren Customer Success Manager (CSM). Alternativ kann der technische Support von Adobe telefonisch erreicht werden: 1-866-318-4100, auf die Produktliste warten und dann 4 und 2 eintippen (nach Aufforderung).

* [Hinzufügen von Adobe-Text-Tags zu Dokumenten](https://adobe.com/go/adobesign_text_tag_guide)

<!--
[Download PDF](images/adobe-sign-for-workday-quick-start-guide-2016.pdf)
-->
