---
title: "Direktregistrering för iOS-enheter"
description: "Använd verktyget Apple Configurator för att registrera företagsägda iOS-enheter direkt med en fördefinierade princip genom att ansluta dem via USB till en Mac-dator."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 01/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a692b90c-72ae-47d1-ba9c-67a2e2576cc2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9909e1dd4f9891a2efb47383242ed7765d3f0291
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="directly-enroll-ios-devices-by-using-apple-configurator"></a>Registrera iOS-enheter direkt med hjälp av Apple Configurator

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune stöder registrering av företagsägda iOS-enheter via [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) på en Mac-dator. Den här processen fabriksåterställer inte enheten och registrerar enheten med en fördefinierad princip. Den här metoden gäller för enheter som **inte har någon användartillhörighet** och kräver att du utför företagsregistreringen genom att ansluta iOS-enheten till en Mac-dator via en USB-anslutning.

När du registrerar iOS-enheter direkt kan du registrera dem utan att hämta enhetens serienummer. Du kan också namnge enheten i identifieringssyfte innan Intune samlar in enhetens namn under registreringen. Företagsportalappen stöds inte för direktregistrerade enheter. Den här vägledningen förutsätter att du använder Apple Configurator 2.0 på en Mac-dator.

>[!NOTE]
>Den här registreringsmetoden kan inte användas med metoden [hanterare av enhetsregistrering](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).

1.  Om du inte redan har gjort det skapar du en registreringsprofil för iOS-enheter som registreras via Apple Configurator. En enhets registreringsprofil definierar inställningarna som tillämpas på enheter.

    1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) går du till **Princip** &gt; **Företagsägda enheter** och väljer sedan **Lägg till**.

        ![Skapa sida för mobilenhetsregistrering](../media/pol-sa-corp-enroll.png)

    2.  Ange information om enhetsprofilerna:

        -   **Namn**: Namnet på enhetens registreringsprofil. Inte synligt för användarna.

        -   **Beskrivning**: Beskrivning av enhetens registreringsprofil. Inte synligt för användarna.

        -   **Användartillhörighet**: Anger hur enheterna registreras. För direktregistrering väljer du **Ingen användartillhörighet**.

        -   **Förtilldelning av enhetsgrupp**: Alla enheter med den här profilen hör ursprungligen till den här gruppen. Du kan tilldela enheter på nytt efter registreringen.

            [!INCLUDE[groups deprecated](../includes/group-deprecation.md)]

    3.  Välj **Spara profil** för att lägga till profilen.

5.  Exportera en profil som .mobileconfig för distribution till iOS-enheter:

    1.   Välj den enhetsprofil som du skapat.

    2.   Välj **Exportera** i Aktivitetsfältet.

    3.   Välj **Hämta profil** och spara den nedladdade .mobileconfig-filen.

6.  Flytta filen genom att kopiera den nedladdade .mobileconfig-filen till en Mac-dator.
    > [!NOTE]
    > Registreringsprofilens URL är giltig i två veckor från tidpunkten för exporten. Efter två veckor måste du exportera en ny registreringsprofils-URL för att kunna registrera iOS-enheter med installationsassistenten.

7.  Förbered enheten med Apple Configurator. iOS-enheter är anslutna till Mac-datorn och registreras för hantering av mobila enheter.

    1.  På en Mac-dator öppnar du **Apple Configurator 2.0**.

    2.  Anslut iOS-enheten till Mac-datorn med en USB-kabel. Stäng **Foton**, **iTunes** och andra appar som öppnas för enheten när enheten identifieras.

    3.  I Apple Configurator väljer du den anslutna iOS-enheten och väljer sedan knappen **Lägg till**. Alternativ som kan läggas till för enheten visas i den nedrullningsbara listan. Välj **Profiler**.

    4.  Använd filväljaren och välj den .mobileconfig-fil som du exporterade från Intune och välj sedan **Lägg till**. Profilen läggs till för enheten.  Om enheten är **obevakad** kräver installationen godkännande på enheten.

8.  Du är redo att installera profilen på iOS-enheten. Installationsassistenten måste ha slutförts på enheten och enheten måste vara redo att användas. Om registreringen medför appdistributioner måste enheten ha ett konfigurerat Apple-ID eftersom appdistributioner kräver att du har ett Apple-ID för App Store.

    1.  Lås upp iOS-enheten.

    2.  Välj **Installera** för **Management profile** (Hanteringsprofil) i dialogrutan **Installera profil**.

    3.  Ange **enhetens lösenord** eller **Apple-ID** om det behövs.

    4.  Acceptera **varningen** och välj **Installera**.

    5.  Acceptera **fjärrvarningen** och välj **Förtroende**.

    6.  När rutan **Profilen har installerats** bekräftar att profilen har **installerats** väljer du **Klar**.

9.  På iOS-enheten öppnar du **Inställningar** och går till **Allmänt** &gt; **Enhetshantering** &gt; **Management Profile** (Hanteringsprofil). Bekräfta att profilinstallationen visas och kontrollera iOS-principbegränsningarna och installerade appar. Det kan ta upp till tio minuter innan principbegränsningar och appar visas på enheten.

10.  Distribuera enheter. Nu är iOS-enheten registrerad med Intune och hanteras.