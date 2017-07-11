---
title: Samla in enhetsloggar
description: "Lär dig hur du samlar in loggar från dina hanterade enheter."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 02/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b15e4b7fa0c650a85a080c42d00cd75cb8783c62
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="device-logs"></a>Enhetsloggar

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Som en del av ditt arbete med felsökning vill du kanske samla in loggar från användarenheter. Anvisningar om att samla in dessa loggar finns här. I normala fall behöver du åtkomst till enheten för att få tillgång till dessa loggar, eller så kan du skicka en begäran till användaren om att samla in loggarna och skicka dem till dig.

### <a name="android-logs"></a>Android-loggar
Android-loggar finns i *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*.

Ibland visas filerna inte, särskilt på nyare Android-enheter. Om detta händer så låt dina användare öppna företagsportalsappen för Android. De bör då välja **Inställningar**>**Kopiera loggar** och starta om enheten.

Mer information om hur dina användare kan skicka dataloggar till dig finns i följande artiklar:

- [Hjälp din IT-administratör med att åtgärda enhetsproblem genom att använda utförlig loggning](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android): Beskriver hur användarna kan aktivera utförlig loggning, varvid alla deras dataloggar skickas till dig automatiskt. Utförlig loggning är aktiverat som standard.

- [Send Android diagnostic data logs to your IT admin using email](/intune-user-help/send-logs-to-your-it-admin-by-email-android) (Skicka loggar med diagnostikdata för Android till din IT-administratör med e-post)

- [Skicka loggar med diagnostikdata till din IT-administratör via USB-kabel](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)

### <a name="ios-logs"></a>iOS-loggar

Användare kan skicka registreringsfelen till dig enligt beskrivningen i [Skicka iOS-registreringsfel till IT-administratören](/intune-user-help/send-errors-to-your-it-admin-ios).

Användarna kan skicka enhetsloggar. Mer information finns i avsnittet om hur du [skickar iOS-enhetsloggar](/intune-user-help/send-logs-to-microsoft-ios).

### <a name="mac-os-x-logs"></a>Mac OS X-loggar

1. Öppna appen **Konsol**.
2. Välj **system.log** under **FILES**.
3. Välj **Arkiv** > **Spara en kopia som…** i menyfältet högst upp. Spara sedan filen.

### <a name="windows-phone"></a>Windows Phone

I Windows Phone-företagsportalsappen öppnar användarna menyn genom att klicka på de tre punkterna (**…**) och väljer sedan **Skicka loggar**. Det här alternativet är tillgängligt både före och efter inloggning till företagsportalappen.

### <a name="windows"></a>Windows

Loggarna för Windows-företagsportalen finns i *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*.