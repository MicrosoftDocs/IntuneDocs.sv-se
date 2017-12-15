---
title: Starta Windows Defender | Microsoft Docs
description: "Lär dig hur du aktiverar Windows Defender för att komma åt företagets resurser."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d16dd2de-3ed5-474f-a04b-36dcd350162c
searchScope: User help
ROBOTS: 
ms.reviewer: shburbid
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: d2a7cd5cc4c201a73570f73892563463cb0bdcc7
ms.sourcegitcommit: f2f147a1177d1cf5bbc8001701eb8f44dd833b7d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/12/2017
---
# <a name="turn-on-windows-defender-to-access-company-resources"></a>Aktivera Windows Defender för att komma åt företagets resurser

Ditt arbete eller din skola vill se till att enheter som kommer åt deras resurser är skyddade. De kan använda [Windows Defender](https://www.microsoft.com/safety/pc-security/windows-defender.aspx), Windows inbyggda skydd mot skadlig programvara, på olika sätt.

Det är några inställningar som du kan behöva ändra i Windows Defender för att åtgärda eventuella åtkomstproblem. De här stegen kan kräva att du går till ett par olika ställen på datorn.

## <a name="turn-on-windows-defender"></a>Starta Windows Defender

1. Gå till **Start** och öppna **Kontrollpanelen**.
2. Öppna **Administrativa verktyg** > **Redigera grupprincip**. Då öppnas **Redigeraren för lokala grupprinciper** i ett nytt fönster.
3. Öppna **Datorkonfiguration** > **Administrativa mallar** > **Windows-komponenter** > **Windows Defender Antivirus**. Inställningen **Inaktivera Windows Defender Antivirus** finns under mapparna med andra inställningar. 
4. Öppna **Inaktivera Windows Defender Antivirus** och kontrollera att det är inställt på **Inaktiverad** eller **Inte konfigurerad**.

## <a name="turn-on-real-time-protection"></a>Starta realtidsskydd

Kontrollera att realtidsskydd är aktiverat genom att gå till **Start** och söka efter **Windows Defender Säkerhetscenter**. Välj **Inställningar för skydd mot virus och hot** och bekräfta att både **Realtidsskydd** och **Molnlevererat skydd** är inställt på **På**. Om dessa alternativ inte visas gör du så här för att aktivera dem:

1. Gå till **Start** och öppna **Kontrollpanelen**.
2. Öppna **Administrativa verktyg** > **Redigera grupprincip**. Då öppnas **Redigeraren för lokala grupprinciper** i ett nytt fönster.
3. Öppna **Datorkonfiguration** > **Administrativa mallar** > **Windows-komponenter** > **Windows Defender Säkerhetscenter** > **Skydd mot virus & hot**.
4. Öppna inställningen för **området för skydd mot virus och hot** och ställ in den på **Inaktiverad**.

## <a name="update-your-antivirus-definitions"></a>Uppdatera antivirusdefinitionerna

Kontrollera att antivirusdefinitionerna är uppdaterade genom att gå till **Start** och söka efter **Windows Defender Säkerhetscenter**. Välj **Skyddsuppdateringar** och **Sök efter uppdateringar** för att se till att enheten har ett aktuellt skydd mot virus. Om det här alternativet inte visas följer du stegen i [Starta realtidsskydd](turn-on-defender-windows.md#turn-on-real-time-protection)

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter kontaktuppgifter på [företagsportalens webbplats](https://portal.manage.microsoft.com#HelpDeskDialog).