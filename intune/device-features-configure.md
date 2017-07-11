---
title: "Konfigurera funktionsinställningar för Intune-enheten"
titleSuffix: Intune on Azure
description: "Läs hur du använder Intune till att konfigurera funktioner på enheter som du hanterar.”"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f286119019bb26d8851c766a9d88ad818d7e600b
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-configure-device-feature-settings-in-microsoft-intune"></a>Så här konfigurerar du enhetens funktionsinställningar i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Med enhetsbegränsningar kan du styra funktioner på iOS- och macOS-enheter, som t.ex. AirPrint, meddelanden och delade enhetskonfigurationer.

Använd informationen i det här avsnittet om du vill lära dig grunderna för hur du konfigurerar profiler för enhetsfunktioner. Läs sedan de specifika avsnitten om respektive plattform om du vill veta mer.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Skapa en enhetsprofil med inställningar för enhetsbegränsningar

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enhetskonfiguration** på **Intune**-bladet.
2. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
3. Välj **Skapa profil** på profilbladet.
4. På bladet **Skapa profil** anger du ett **Namn** och en **Beskrivning** för enhetens funktionsprofil.
5. Välj den enhetsplattform som du vill tillämpa inställningarna på i listrutan **Plattform**. För närvarande kan du välja någon av följande plattformar för enhetsfunktioner:
    - **iOS**
    - **macOS**
6. I listrutan **Profiltyp** väljer du **Enhetsfunktioner**. 
7. Beroende på vilken plattform du har valt så varierar de inställningar som du kan konfigurera. Gå till något av följande avsnitt om du vill ha detaljerad information om respektive plattform:
    - [AirPrint-inställningar för iOS och MacOS](air-print-settings-ios-macos.md)
    - [AirPlay-inställningar för iOS](airplay-settings-ios.md)
    - [Layoutinställningar för iOS-startskärm](home-screen-settings-ios.md)
    - [Appaviseringsinställningar för iOS](app-notification-settings-ios.md)
    - [Konfigurationsinställningar för delade enheter för iOS](shared-device-settings-ios.md)
    - [Inställningar för webbinnehållsfilter för iOS](web-content-filter-settings-ios.md)

8. När du är klar går du tillbaka till bladet **Skapa profil** och trycker på **Skapa**.

Profilen skapas och visas på bladet med profillistan.
Om du vill gå vidare och tilldela den här profilen till grupper, kan du läsa mer i [Tilldela enhetsprofiler](device-profile-assign.md).


