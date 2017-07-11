---
title: "Kringgå iOS-aktiveringslås med Intune"
titleSuffix: Intune on Azure
description: "Lär dig hur du använder Intune för att kringgå iOS-aktiveringslås och få åtkomst till låsta enheter.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9ca3b0ba-e41c-45fb-af28-119dff47c59f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0b92949efca2e4dac5836755e2f32b0527d4762d
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2017
---
# <a name="bypass-activation-lock-on-supervised-ios-devices-with-intune"></a>Kringgå aktiveringslåset på övervakade iOS-enheter med Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune kan hjälpa dig att hantera iOS-aktiveringslåset, en funktion i Hitta min iPhone-appen för enheter med iOS 8.0 och senare. Aktiveringslås aktiveras automatiskt när en användare öppnar appen Hitta min iPhone på en enhet. När den har aktiverats måste användarens Apple-ID och lösenord anges innan någon kan:

- Inaktivera Hitta Min iPhone
- Rensa enheten
- Återaktivera enheten

## <a name="how-activation-lock-affects-you"></a>Hur du påverkas av aktiveringslås

Även om aktiveringslås hjälper till att skydda iOS-enheter och förbättra chansen att få tillbaka en borttappad eller stulen enhet, så gör den här funktionen att du som IT-administratör står inför ett antal utmaningar. Exempel:

- En användare ställer in aktiveringslås på en enhet. Användaren lämnar sen företaget och lämnar tillbaks enheten. Utan användarens Apple-ID och lösenord går det inte att återaktivera enheten.
- Du behöver en rapport med alla enheter som har aktiveringslås aktiverat.
- Du vill omtilldela några enheter till en annan avdelning under en enhetsuppdatering i organisationen. Du kan bara omtilldela enheter som inte har aktiveringslås aktiverat.

För att hjälpa att lösa de här problemen, så introducerade Apple med iOS 7.1 funktionen Kringgå Aktiveringslås. Den låter dig ta bort aktiveringslås från övervakade enheter utan att ha användarens Apple-ID och lösenord. Övervakade enheter kan generera en enhetsspecifik kod för att kringgå aktiveringslåset, vilken lagras på Apples aktiveringsserver.

>[!TIP]
>Övervakat läge för iOS-enheter gör att du kan använda Apple Configurator för att låsa en enhet och begränsa funktionerna till specifika företagsändamål. Övervakat läge är generellt sett bara till för företagsägda enheter.

Du kan läsa mer om aktiveringslåset på [Apples webbplats](https://support.apple.com/HT201365).

## <a name="how-intune-helps-you-manage-activation-lock"></a>Hur Intune hjälper dig att hantera aktiveringslås
Intune kan begära status för aktiveringslåset för övervakade enheter som kör iOS 8.0 och senare. Enbart för övervakade enheter kan Intune hämta koden för att kringgå aktiveringslåset och skicka den direkt till enheten. Om enheten har rensats kan du få åtkomst till den direkt genom att använda ett tomt användarnamn och koden som lösenord.

**Företagets fördelar med detta är att:**

- Användaren får säkerhetsfördelarna i Hitta Min iPhone-appen.
- Du kan låta användarna sköta sitt arbete och samtidigt vara säker på att du kan avaktivera eller låsa upp en enhet när den behöver återanvändas.

## <a name="before-you-start"></a>Innan du börjar
Innan du kan kringgå aktiveringslåset på enheter måste du först aktivera det. Gör så här:

1. Konfigurera en Intune-begränsningsprofil för iOS med hjälp av informationen i [Så här konfigurerar du inställningar för enhetsbegränsning](/intune-azure/configure-devices/how-to-configure-device-restrictions).
2. Aktivera inställningen **Helskärmsläge** **Aktiveringslås**.
3. Spara profilen och tilldela den till de enheter som du vill hantera kringgåendet av aktiveringslåset för.


## <a name="how-to-use-activation-lock-bypass"></a>Så här kringgår du aktiveringslås

>[!IMPORTANT]
>När du kringgått aktiveringslåset på en enhet aktiveras ett nytt aktiveringslås automatiskt om appen Hitta min iPhone öppnas. Därför **bör du ha fysisk tillgång till enheten innan du följer den här proceduren**.

Intunes fjärråtgärd **Kringgå aktiveringslås** tar bort aktiveringslåset från en iOS-enhet utan användarens Apple-ID och lösenord. När du har kringgått aktiveringslåset aktiverar enheten aktiveringslåset igen när appen Hitta Min iPhone startar. Kringgå bara aktiveringslåset om du har fysisk åtkomst till enheten.

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.
4. På bladet **Enheter och grupper** väljer du **Alla enheter**.
5. I listan med enheter som du hanterar väljer du en övervakad iOS-enhet och sedan fjärråtgärden **Kringgå aktiveringslås**.

Du kan kontrollera status för upplåsningsbegärandet på informationssidan för enheten i arbetsbelastningen **Hantera enheter**.