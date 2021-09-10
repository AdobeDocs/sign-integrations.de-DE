---
title: Produktversionen und Lebenszyklus von Adobe Sign Integrationen
description: Erfahren Sie mehr über Adobe Sign Integrationsversionen und Support-Lebenszyklus
audience: External
products: Adobe Sign
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: c1f22848-7951-4066-84d4-f8cf6c2f3a6f
source-git-commit: 30cb79b6856c7b623dc5118b4aa40193bf749220
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 40%

---

# Produktversionen und Lebenszyklus {#version}

Die Adobe Sign Versionsverwaltungskonvention und der Support-Lebenszyklus für integrierte Adoben stimmen mit anderen Produkten überein, mit denen Sie vielleicht vertraut sind.

## Versionsnummern

Die Paketversion verwendet ein dreiteiliges Nummerierungssystem, um die fortlaufende Build-Nummer der freigegebenen Version und den relativen Import des Upgrades in Bezug auf neue oder sich ändernde Inhalte zu identifizieren.

Die Versionsnummer folgt diesem Muster: N.m.p

wobei N = Hauptversion; m = Nebenversion; p = Patched version.

Beispiel: Eine Integrationspaket-Version 23.2.1 gibt folgenden Status an:

* Hauptversion: 23
* Nebenversion: 2
* Patch-Version: 1

Wenn Ingenieure neue &quot;Builds&quot;des Pakets entwickeln, erhöhen sie die Versionsnummer entsprechend der Art der Aktualisierungen des Codes.

* Wichtige Versionsänderungen beinhalten eine wesentliche Erweiterung der Funktionen oder eine wichtige Änderung der Kernsysteme.
* Kleinere Versionsaktualisierungen beinhalten kleinere Funktionsaktualisierungen und Sicherheits-Patches. Adobe Sign kann ein Upgrade auf die neueste gepatchte Version bei Sicherheitsupdates oder zur Behebung eines gemeldeten Artikels verlangen.
* Patch-Versionen sind fast ausschließlich Fehlerbehebungen und Anpassungen der Benutzeroberfläche.

>[!NOTE]
>
>Alle Versionen werden nicht veröffentlicht, da sich das Produkt in der Entwicklung befindet. Es kann also zwischen den Releases zu erheblichen Fortschritten in der Patch-Version kommen.

Die Administratoren müssen ihre Version auf dem neuesten Stand halten, um sicherzustellen, dass das Konto vollen Zugriff auf alle Funktionen hat und alle bekannten Sicherheitsprobleme gepatcht werden. Adobe Sign kann bei Sicherheitsbedenken oder zur Behebung eines kritischen Systemproblems ein Upgrade auf die neueste gepatchte Version verlangen.

## Lebenszyklus der Versionsunterstützung

Der Versionsunterstützungslebenszyklus eines Adobe Sign-Integrationsprodukts wird basierend auf der Hauptversion des Pakets definiert und gibt den Zeitrahmen an, in dem Adobe Sign die Einzelversion der Integration aktiv unterstützt.

Adobe Sign unterstützt die aktuelle Version eines Pakets und die beiden vorherigen Hauptversionen (einschließlich aller zugehörigen Nebenversionen und Patch-Updates). Hauptversionen werden wie folgt ausgedrückt:

* Aktuelle Version (N): Die neueste Hauptversion des Pakets
* Vorherige Version (N-1): Eine Hauptversion hinter der neuesten Version
* Letzte unterstützte Version (N-2): Zwei Hauptversionen hinter der aktuellen Version

Wenn beispielsweise die aktuelle verfügbare Version des Pakets 23.2.1 lautet, dann:

* Die aktuelle Hauptversion (N) ist 23.
* Die vorherige Hauptversion (N-1) dieses Pakets ist 22.
* Die letzte unterstützte Hauptversion (N-2) dieses Pakets ist 21.
* Alle Version vor 21.0.0 werden nicht unterstützt.

![Versionsübersicht](images/version_chart.png)

## Lebenszyklus des Versionsdienstes

Die Support-Dauer für Dienste definiert, wie lange der Dienst verwendet werden kann. Die Zeitleiste entspricht der Support-Dauer für Versionen mit einer zusätzlichen Toleranzperiode von 90 Tagen, die es Kunden ermöglicht, ein Upgrade abzuschließen.

* Während der Toleranzperiode einer nicht unterstützten Version wird nur das Upgrade auf eine neuere Version unterstützt.
* Nach Ablauf der Nachfrist wird die Version nicht mehr verwendet

* Adobe Sign akzeptiert keine Anfragen von abgelaufenen Versionen.
* Sobald die Integration auf die aktuelle Version aktualisiert wurde, wird die Kommunikation zwischen Adobe Sign und der Integration normal fortgesetzt.

![Abschaltzeit](images/shutdown_period.png)

Wenden Sie sich bei Fragen an Ihren Händler oder an den Support.
