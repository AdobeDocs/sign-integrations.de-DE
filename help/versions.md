---
title: Produktversionen und Lebenszyklus von Adobe Sign-Integrationen
description: Erfahren Sie mehr über die Versionen der Adobe Sign-Integration und die Support-Dauer
audience: External
products: Adobe Sign
type: Documentation
solution: Acrobat Sign
role: User, Developer
topic: Integrations
exl-id: c1f22848-7951-4066-84d4-f8cf6c2f3a6f
source-git-commit: 4d73ff36408283805386bd3266b683bc187d6031
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 40%

---

# Produktversionen und Lebenszyklus {#version}

Die Adobe Sign-Versionierungskonvention und die Support-Dauer für integrierte Services entsprechen anderen Adobe-Produkten, mit denen Sie möglicherweise vertraut sind.

## Versionsnummern

Die Paketversion verwendet ein dreiteiliges Nummerierungssystem, um die fortlaufende Build-Nummer der freigegebenen Version und den relativen Import des Upgrades in Bezug auf neue oder sich ändernde Inhalte zu identifizieren.

Die Versionsnummer folgt diesem Muster: N.m.p.

wobei n = Hauptversion; m = Nebenversion; p = Patch-Version.

Beispiel: Ein Integrationspaket der Version 23.2.1 gibt den folgenden Versionsstatus an:

* Hauptversion: 23
* Nebenversion: 2
* Patch-Version: 1

Wenn Ingenieure neue &quot;Builds&quot; des Pakets entwickeln, erhöhen sie die Versionsnummer entsprechend der Art der Codeaktualisierungen.

* Hauptversionsänderungen beinhalten eine erhebliche Erweiterung der Funktionen oder eine wichtige Änderung der Kernsysteme.
* Nebenversionsupdates umfassen kleinere Funktionsupdates und Sicherheits-Patches. Möglicherweise ist auch ein Upgrade auf die neueste gepatchte Version von Adobe Sign erforderlich, wenn Sicherheitsupdates durchgeführt werden oder ein gemeldetes Problem behoben werden muss.
* Patch-Versionen sind fast ausschließlich Fehlerbehebungen und Anpassungen der Benutzeroberfläche.

>[!NOTE]
>
>Nicht alle Versionen werden für die Öffentlichkeit freigegeben, wenn das Produkt die Entwicklung durchläuft. Es kann also zu erheblichen Sprüngen in der Patch-Version zwischen den Releases kommen.

Die Administratoren müssen ihre Version auf dem neuesten Stand halten, um sicherzustellen, dass das Konto vollen Zugriff auf alle Funktionen hat und für alle bekannten Sicherheitsprobleme ein Patch aufgespielt wurde. Möglicherweise ist auch ein Upgrade auf die neueste gepatchte Version von Adobe Sign erforderlich, wenn ein Sicherheitsrisiko besteht oder ein kritisches Systemproblem behoben werden muss.

## Support-Dauer für Versionen

Die Support-Dauer für Versionen eines Adobe Sign-Integrationsprodukts basiert auf der Hauptversion des Pakets und gibt den Zeitrahmen an, in dem Adobe Sign die individuelle Version der Integration aktiv unterstützt.

Adobe Sign unterstützt die aktuelle Version eines Pakets sowie die beiden vorherigen Hauptversionen (einschließlich aller zugehörigen Nebenversions- und Patch-Updates). Hauptversionen werden wie folgt ausgedrückt:

* Aktuelle Version (N): Die neueste Hauptversion des Pakets
* Vorherige Version (N-1): Eine Hauptversion hinter der neuesten Version
* Letzte unterstützte Version (N-2): Zwei Hauptversionen hinter der aktuellen Version

Wenn die aktuelle verfügbare Version des Pakets beispielsweise 23.2.1 ist, dann gilt Folgendes:

* Die aktuelle Hauptversion (N) ist 23.
* Die vorherige Hauptversion (N-1) dieses Pakets ist 22.
* Die letzte unterstützte Hauptversion (N-2) dieses Pakets ist 21.
* Alle Version vor 21.0.0 werden nicht unterstützt.

![Versionsübersicht](images/version_chart.png)

## Lebenszyklus des Versionsdiensts

Die Support-Dauer für Dienste definiert, wie lange der Dienst verwendet werden kann. Die Zeitleiste entspricht der Support-Dauer für Versionen mit einer zusätzlichen Toleranzperiode von 90 Tagen, die es Kunden ermöglicht, ein Upgrade abzuschließen.

* Während der Toleranzperiode einer nicht unterstützten Version wird nur das Upgrade auf eine neuere Version unterstützt.
* Nach Ablauf der Kulanzzeit ist die Version nicht mehr verfügbar.

* Adobe Sign akzeptiert keine Anfragen von abgelaufenen Versionen.
* Sobald die Integration auf die aktuelle Version aktualisiert wurde, wird die Kommunikation zwischen Adobe Sign und der Integration normal fortgesetzt.

![Abschaltzeit](images/shutdown_period.png)

Wenden Sie sich bei Fragen an Ihren Händler oder an den Support.
