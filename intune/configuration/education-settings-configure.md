---
title: Lägg till eller konfigurera utbildningsinställningar i Microsoft Intune – Azure | Microsoft Docs
description: Använd appen Gör ett prov i konfigurationsprofilen på Windows 10 och senare enheter i Microsoft Intune. Skapa en konfigurationsprofil med Education-inställningar och ange en URL för testappen, välj hur användare loggar in, övervaka skärmen under provet och tillåt eller förhindra textförslag under provet.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/10/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3fc42193b461b8a0364e4ef2a2c34fe3e446ada3
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724015"
---
# <a name="use-the-take-a-test-app-on-windows-10-devices-in-microsoft-intune"></a>Använd appen Gör ett prov på Windows 10-enheter i Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Utbildningsprofiler i Intune är utformade för elever som ska göra ett prov på enheter. Den här funktionen innehåller appen **Gör ett prov** och inställningar för att lägga till en test-URL, välja hur slutanvändare loggar in på provet och mycket mer. Den här funktionen har stöd för följande plattform:

- Windows 10 och senare

När användaren loggar in öppnas automatiskt appen Gör ett prov med det prov som du har angett. Inga andra appar kan köras på enheten medan provet pågår. [Gör prov i Windows 10](https://docs.microsoft.com/education/windows/take-tests-in-windows-10) innehåller mer information om appen Gör ett prov.

Artikeln visar stegen för att skapa en konfigurationsprofil för enheter i Microsoft Intune. Den innehåller även information om du vill läsa och lära dig mer om tillgängliga utbildningsinställningar för Windows 10-enheter.

## <a name="create-a-device-profile"></a>Skapa en enhetsprofil

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange följande egenskaper:

    - **Namn**: Ange ett beskrivande namn på den nya profilen.
    - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
    - **Plattform**: Välj **Windows 10 och senare**.
    - **Profil**: Välj **Utbildningsprofil**.

4. Ange vilka inställningar som du vill konfigurera:

    - [Windows 10 och senare](education-settings-windows.md)

5. Välj **OK** > **Skapa** för att spara ändringarna.

När du har angett dina inställningar och skapar profilen, visas din profil i profillistan. Härnäst [tilldela profilen till vissa grupper](device-profile-assign.md).

## <a name="next-steps"></a>Nästa steg

Se en lista över [utbildningsinställningarna för Windows 10](education-settings-windows.md) och deras beskrivningar.

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).