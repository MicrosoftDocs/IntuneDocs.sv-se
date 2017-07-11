---
title: Skydda appar och data
description: "I det här avsnittet beskrivs de olika Intune-funktionerna och hur du kan skydda företagets appar och data."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5c46e188-87eb-4ce2-b184-24809e8bf783
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 09b7a1d4901a52845719e8d7094f665b12b91ab4
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="protect-apps-and-data-with-microsoft-intune"></a>Skydda data och appar med Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune skyddar företagets data via flera tekniklager. I identitetslagret skyddas åtkomsten till tjänster med villkorlig åtkomst som endast tillåter åtkomst från hanterade och godkända enheter. I klientprogramlagret skyddar MAM (Mobile App Management) mot dataförlust genom att förhindra att data flyttas till appar eller lagringsplatser som inte är skyddade, och genom att rensa data om en enhet blir borttappad eller stulen. Vi rekommenderar att dessa två skyddslager används tillsammans för att bidra till dataskydet samtidigt som den mobila arbetsstyrkans produktivitet bibehålls.

Ett viktigt första steg för att skydda företagets data är att implementera villkorlig åtkomst. Du kan göra detta genom att se till att enheter som används för att komma åt dessa data använder säkerhetsskydd som starka lösenord och kryptering, och inte är upplåsta. I Intune kan du ange villkor som enheterna måste uppfylla innan de får tillgång till företagets e-post och data.

[Villkorlig åtkomst](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) baseras på två typer av principer som du kan konfigurera i Intune:
- Du använder [efterlevnadsprinciper](introduction-to-device-compliance-policies-in-microsoft-intune.md) när du vill fastställa en enhets efterlevnad. De utvärderar inställningar och villkor som:
  - PIN-koder och lösenord: Du kan skapa regler som kräver lösenord för att en enhet ska låsas upp, ställer krav på lösenordets komplexitet och används för andra lösenordsinställningar.
  - Kryptering: IT-administratören kan begränsa åtkomsten till enheter som är krypterade.
  - När en enhet varken är jailbrokad eller rotad: Intune kan känna av om en registrerad enhet är jailbrokad. Du kan konfigurera principen så att den blockerar åtkomst på sådana enheter.
- Du konfigurerar [principer för villkorlig åtkomst](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) för en viss tjänst, t.ex. Exchange Online eller SharePoint Online. För varje tjänst kan du definiera vilka grupper av användare som dessa principer ska gälla för. Du kan till exempel bestämma att anställda på personalavdelningen bara ska kunna komma åt företagets e-post från registrerade enheter som uppfyller efterlevnadskraven.

Att skydda åtkomsten till företagets resurser är bara det första steget i att skydda företagets data. Du måste fortfarande kunna skydda data efter det att användaren har fått åtkomst till den på enheten. Nu kan informationen kopieras, flyttas och sparas till en annan plats eller delas. I Intune kan du komma runt det här problemet genom att begränsa eller förhindra dataflyttning med en uppsättning regler som:
- Förhindrar kopiering och inklistring eller dataöverföring utanför arbetskontexten.
- Förhindrar säkerhetskopiering till personlig molnlagring, spärrar Spara som osv.
- Skyddar åtkomsten till appar genom att kräva PIN-kod/lösenord eller företagsautentiseringsuppgifter.
- Tvingar alla länkar att öppnas i Intune Managed Browser.

Den här uppsättningen regler kallas för [hanteringsprinciper för mobila appar (MAM)](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md). Du kan använda MAM-principerna för appar som körs på enheter som hanteras eller inte hanteras av dig.  

Du kan skydda företagets data genom att använda MAM-principer för enheter som är **registrerade i Intune**, enheter som är **registrerade och som hanteras i en MDM-lösning från tredje part** eller enheter som **inte är registrerade i någon MDM-lösning**, t.ex. personalägda enheter.

Om du vill associera en app med en MAM-princip måste Microsoft Intune App Software Development Kit (SDK) ingå i appen, eller så kan du använda appomslutningsverktyget.

I appar som Microsoft Office-apparna är Intune App-SDK:n inbyggd. Du kan visa en fullständig lista över appar som stöds i [Microsoft Intune-galleriet för mobilprogram](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) på sidan för Microsoft Intune-programpartner. Välj appen om du vill se vilka scenarier och plattformar som stöds och huruvida appen stöder flera identiteter.

Du kan också [aktivera dina egna anpassade affärsappar](/intune/apps-prepare-mobile-application-management) så att de kan användas med MAM-principer.

Förutom att du kan förhindra eller begränsa dataflyttning om en enhet blir stulen eller borttappad eller om användaren inte längre arbetar på ditt företag kan du [rensa företagsdata selektivt](wipe-managed-company-app-data-with-microsoft-intune.md), så att bara personliga data finns kvar.