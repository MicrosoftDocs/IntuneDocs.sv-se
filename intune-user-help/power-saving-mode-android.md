---
title: "Energioptimering förhindrar e-poståtkomst | Microsoft Docs"
description: "Ta reda på hur du stänger av energioptimering för Android så att du är säker på att du får din e-post."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 07/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ad713f18-40a9-421f-aa2b-f8c21028d57c
searchScope: User help
ROBOTS: 
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: d94e3a79af1951debc4dd04413efff8f4c716545
ms.sourcegitcommit: d2a4f4477b3bf90aac6a9db77d41747e64ad7df4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2017
---
# <a name="outlook-wont-sync-managed-email-when-battery-optimization-for-android-is-turned-on"></a>Outlook synkroniserar inte hanterad e-post när batterioptimering för Android är aktiverat

> [!IMPORTANT]
> Det här problemet dokumenteras här eftersom vi har fått in fler och fler kundrapporter om det. Om problemet kvarstår efter att du har utfört stegen nedan kontaktar du [din IT-administratör](https://portal.manage.microsoft.com) för ytterligare hjälp.

Genom att registrera din enhet i Intune får du åtkomst till företagsresurser. En av de vanligaste resurserna är åtkomst till e-post. Ett problem som vi har observerat med åtkomsten till e-post via Outlook för Android-enheter är när batterioptimering är aktiverat. Batterioptimering kan aktiveras automatiskt så att din enhet är strömförsörjd så länge som möjligt. Batterioptimering kan i viss mån hjälpa dig på detta sätt eftersom funktionen försöker stoppa automatiska e-posthämtningar.

Microsoft Intune-teamet arbetar aktivt med en lösning på problemet. Ett sätt att förhindra att enheten försätts i energisparläge är att se till att batteriet alltid är laddat till mer än 30 %. Om du vill förhindra att problemet uppstår när enheten försätts i energisparläge måste du ta bort Företagsportal och Outlook från listan med appar som påverkas av batterioptimerings- och energisparinställningar.

Det finns ett stort antal Android-enheter som tillverkas av många olika tillverkare. Vi kan inte dokumentera de exakta stegen på varje enhet. Kanske behöver du bara göra ändringarna i dina systeminställningar, eller kanske även i vissa tillverkarspecifika inställningar. Vi har dokumenterat några vanliga exempel på hur du kan lösa det här problemet på Android-enheter.

## <a name="unmodified-android-devices"></a>Omodifierade Android-enheter

Många tillverkare lägger till modifikationer till deras Android-enheter. Detta kan påverka hur du interagerar med enheten, t.ex. när det gäller teman och meddelanden. Google gör normalt inte dessa modifikationer på sina telefoner. På en Google Pixel-enhet med Android 7.0 eller senare följer du till exempel stegen nedan för att ta bort dessa appar från batterioptimering:

1. Öppna **Inställningar**.
2. Tryck på **Batteri** > **Mer** > **Batterioptimering**.
3. Tryck på nedpilen och sedan på **Inte optimerad**.
4. Välj apparna Företagsportal och Outlook och inaktivera batterioptimering.

## <a name="samsung-devices"></a>Samsung-enheter

För andra typer av Android-enheter, till exempel Samsung-enheter med Android 7.0 eller senare, utför du andra steg för att ta bort apparna Outlook och Företagsportal från batterioptimering.

1. Öppna **Inställningar**.
2. Tryck på **Meny (…)** > **Särskilt åtkomst** > **Optimera batterianvändning**.
3. Välj **Alla appar** i listrutan.
4. Inaktivera batterioptimering genom att dra växlingsknappen bredvid apparna Företagsportalen och Outlook till **Av**-läge.

Om du använder en Samsung-enhet som har en tidigare version av Android måste du även följa stegen nedan för att ta bort dessa appar från energisparläge.

1. Öppna **Inställningar**.
2. Tryck på **Enhetsunderhåll** > **Batteri** > **Oövervakade appar**.
3. Tryck på **Lägg till appar**.
4. Välj apparna Företagsportal och Outlook och tryck på **Klar**.

## <a name="oneplus-devices"></a>OnePlus-enheter

Ett annat sätt att hitta dessa inställningar är genom att söka i systeminställningarna. På en OnePlus 3-enhet med Android 7.1.1 följer du till exempel dessa steg: 

1. Öppna **Systeminställningar**. 
2. Tryck på **sökknappen**. Den ser ut som ett förstoringsglas och är placerad längst upp till höger på skärmen. 
3. Skriv **batterioptimering** i sökfältet och välj sedan alternativet **Batterioptimering** på skärmen **Inställningar** som visas. 
4. Tryck på **Batteri** > **Batterioptimering**.
5. Välj apparna Företagsportal och Outlook och välj sedan **Optimera inte**. Tap **Klar**.

<!--On a OnePlus 5 device with Android 7.1.1, you would follow these steps to remove these apps from battery optimization:
1. Open **Settings**.
2. Tap **Battery** > **Battery optimization**.
3. Select the Company Portal and Outlook apps, then select **Don’t optimize**. Tap **Done**.-->

Behöver du fortfarande hjälp? Kontakta IT-administratören. Titta efter kontaktuppgifter på [företagsportalens webbplats](http://portal.manage.microsoft.com).