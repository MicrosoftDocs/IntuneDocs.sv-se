---
title: Hantera enheter med Microsoft Intune – Azure | Microsoft Docs
description: Granska de enheter du hanterar med Microsoft Intune. Du kan exportera en enhetslista i csv-format, visa dina Azure Active Directory-anslutna enheter, granska en ändringslogg över åtgärder på enheten, använda TeamViewer-anslutningsprogrammet så att IT-administratörer via fjärranslutning kan felsöka Android-enheter samt visa alla åtgärder som du kan köra på dina enheter.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/19/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: cd1d99e0c3853a7bf607dd2f64046c503068566d
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728630"
---
# <a name="what-is-microsoft-intune-device-management"></a>Vad är enhetshantering i Microsoft Intune?

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Som IT-administratör måste du se till att hanterade enheter tillhandahåller de resurser som användarna behöver för att utföra sitt arbete, samtidigt som du måste skydda dessa data så att de inte utsätts för risk.

Arbetsbelastningen **Enheter** ger dig insikter om de enheter du hanterar och låter dig utföra fjärråtgärder på dessa enheter.

## <a name="get-to-your-devices"></a>Kom åt dina enheter

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Välj **Enheter**. Den här vyn visar detaljerad information om enskilda enheter och vad du kan göra med dem, inklusive:

   - **Översikt** visar en visuell ögonblicksbild av de registrerade enheterna och visar även hur många enheter som använder olika plattformar, inklusive Android, iOS och mycket mer.
   - **Alla enheter** visar en lista över de registrerade enheter du hanterar.

     Använd funktionen **Exportera** för att skapa en .csv-lista över alla enheter i steg om 10 000 (Internet Explorer) eller 30 000 (Microsoft Edge, Chrome).

     Välj valfri enhet för att [visa ytterligare information om enheten](device-inventory.md), inklusive information om maskinvara, installerade appar, status för policy för efterlevnad och mycket mer.

   - **Azure AD-enheter** visar en lista över de enheter som registrerats för eller anslutits till Azure Active Directory (Azure AD). Läs mer om [Azure AD-enhetshantering](https://docs.microsoft.com/azure/active-directory/device-management-introduction).
   - **Enhetsåtgärder** omfattar en historik över de fjärråtgärder som körts på olika enheter, inklusive åtgärden, dess status, vem som initierade åtgärden och när den utfördes.

     ![Skärmbild som visar när enhetsåtgärder övervakas](./media/device-management/monitor-device-actions.png)

   - **Granskningsloggar** är en post med aktiviteter som genererar en ändring i Intune. [Granskningsloggar](../fundamentals/monitor-audit-logs.md) innehåller mer information.
   - **TeamViewer-anslutningsprogram** är en tjänst som gör att användare av Intune-hanterade Android-enheter kan få fjärrhjälp från sin IT-administratör. Läs mer om [TeamViewer](teamviewer-support.md).
   - **Hjälp och Support** innehåller en genväg till felsökningstips, att begära support eller kontrollera status för Intune.

## <a name="available-device-actions"></a>Tillgängliga enhetsåtgärder
Vilka åtgärder som är tillgängliga beror på enhetsplattformen och enhetens konfiguration.

- [Visa enhetsinventeringen](device-inventory.md)
- Kör åtgärder för fjärransluten enhet:
  - [Pensionera](devices-wipe.md#retire)
  - [Rensning](devices-wipe.md#wipe)
  - [Fjärrlåsning](device-remote-lock.md)
  - [Återställ lösenord](device-passcode-reset.md)
  - [Kringgå aktiveringslås](device-activation-lock-bypass.md) (Endast iOS)
  - [Börja om på nytt](device-fresh-start.md) (Endast Windows)
  - [Borttappat läge](device-lost-mode.md) (Endast iOS)
  - [Hitta enhet](device-locate.md) (Endast iOS)
  - [Starta om](device-restart.md) (Endast Windows)
  - [Återställning av Windows 10-PIN](device-windows-pin-reset.md)
  - [Fjärrstyrning för Android](teamviewer-support.md)
  - [Synkronisera enhet](device-sync.md)
  - [Skicka anpassade meddelanden](custom-notifications.md#send-a-custom-notification-to-a-single-device) (Android, iOS)

## <a name="next-steps"></a>Nästa steg

- Välj en enhet för att visa mer information om den här enheten i **Alla enheter**.
- Välj **Enhetsåtgärder** för att se status för de åtgärder som vidtas på enheter som du hanterar.