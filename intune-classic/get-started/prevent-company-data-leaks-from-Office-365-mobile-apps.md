---
title: "Förhindra företagsdataläckor från Office 365-mobilappar"
description: "Använd Intune för att skydda din organisations data med MAM-principer för hantering av mobilappar som förhindrar läckage av företagsdata från Office 365-mobilappar eller andra affärsappar (LOB)."
keywords: 
author: jeffgilb
ms.author: jeffgilb
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 19be3de7-539c-49f5-8c46-5363b987fef9
ms.reviewer: pchacon
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 3f35dcb7168e9c76a8286a1425a26306914cfdb3
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="quick-start-guide-prevent-company-data-leaks-from-office-365-mobile-apps"></a>Snabbstartsguide: Förhindra företagsdataläckor från Office 365-mobilappar

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Med Microsoft Intune kan du skydda organisationens data med hanteringsprinciper för mobilprogram (MAM) som skyddar mot företagsdataläckor från Office 365-mobilappar eller andra verksamhetsspecifika appar. Du kan också använda Intune MAM-principer utan att användarna registrerar sina enheter i Intunes hantering av mobilenheter (MDM). Om du har användare som inte vill registrera sin iOS- eller Android-enhet i en Microsoft MDM-lösning (Intune, Configuration Manager eller EAS), om du vill skydda företagsdata utan att hantera användarnas enheter eller om du redan använder en annan lösning än Microsoft MDM, kan Intune ändå hjälpa dig att öka datasäkerheten i ditt företag.   

## <a name="is-this-quick-start-guide-right-for-me"></a>Är den här snabbstartsguiden rätt för mig?
Vill du ge användarna åtkomst till data i Office 365 och verksamhetsspecifika appar på deras iOS- och Android-enheter utan att kräva enhetsregistrering i en MDM-lösning, men ändå ha kontroll över vad de kan och inte kan göra med dessa data (till exempel kopiera och klistra in data i egna appar)?

I så fall kan du ange MAM-principer för Office 365-mobilappar på iOS- och Android-enheter med Microsoft Intune, till exempel ange begränsningar för att klippa ut, kopiera och klistra in data, förhindra ”spara som” och ange PIN-kodskrav. Du kan också fjärrensa MAM-skyddade data.  På så sätt kan du skydda företagsdata utan att kräva att användarna registrerar sina enheter i en MDM-lösning. Och får samtidigt en bra användarupplevelse i Office-mobilapparna.

## <a name="how-do-i-do-it"></a>Hur gör jag?
1.  Läs grundläggande information om [hur Intunes hantering av mobilprogram (MAM)](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) fungerar.
2.  Ta reda på [vad du behöver göra innan du kan skapa MAM-principer](/intune-classic/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune) i Azure Portal.
3.  [Skapa och distribuera MAM-principer](/intune-classic/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune) med Intune.

### <a name="additional-information"></a>Ytterligare information:
- [Slutanvändarupplevelse](/intune-classic/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune) med MAM-aktiverade appar.
- [Förbereda verksamhetsspecifika appar för MAM med Intune](/intune/apps-prepare-mobile-application-management)
- <a href="https://www.microsoft.com/cloud-platform/microsoft-intune-partners" target="_blank"> Lista över Microsoft Intune-partner &rarr;</a> som tillhandahåller MAM-aktiverade appar.

## <a name="what-should-i-do-next"></a>Vad ska jag göra sedan?
[Migrera från en annan lösning än Microsoft MDM till Microsoft Intune](/intune-classic/deploy-use/migrate-to-intune)

[Registrera enheter i Intune MDM](/intune-classic/deploy-use/enroll-devices-in-microsoft-intune)