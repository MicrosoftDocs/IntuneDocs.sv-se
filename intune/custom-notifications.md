---
title: Skicka anpassade meddelanden till användare med Microsoft Intune
titleSuffix: Microsoft Intune
description: Använda Intune för att skapa och skicka anpassade push-meddelanden till användare av iOS- och Android-enheter
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f938afb738e75789194db0c74fee56deb1476dbc
ms.sourcegitcommit: c715c93bb242f4fe44bbdf2fd585909854ed72b6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/30/2019
ms.locfileid: "68660387"
---
# <a name="send-custom-notifications-in-intune"></a>Skicka anpassade meddelanden i Intune  

Använd Microsoft Intune för att skicka anpassade meddelanden till användare av hanterade iOS- och Android-enheter. Dessa meddelanden visas som push-standardmeddelanden från appen Företagsportal på en användares enhet, precis som meddelanden från andra program på enheten visas. Anpassade Intune-meddelanden stöds inte av Windows-enheter.   

Anpassade meddelanden innehåller en kort rubrik och en meddelandetext på högst 500 tecken. Dessa meddelanden kan anpassas för valfritt kommunikationssyfte.

## <a name="common-scenarios-for-sending-custom-notifications"></a>Vanliga scenarier för att skicka anpassade meddelanden  

- Använd anpassade meddelanden för att avisera specifika användare om en ny app som är tillgänglig i appen Företagsportal.  
- Meddela alla anställda om en ändring i schemat, till exempel om nedstängning av en byggnad på grund av dåligt väder.  

## <a name="considerations-for-using-custom-notifications"></a>Att tänka på när du använder anpassade meddelanden  

**Enhetskonfiguration**:  
- Appen Företagsportal måste vara installerad på enheten innan användarna kan ta emot anpassade meddelanden. De måste också ha konfigurerade behörigheter som tillåter att appen Företagsportal kan skicka push-meddelanden. Appen Företagsportal uppmanar användarna att tillåta aviseringar.  
- Google Play Services är ett obligatoriskt beroende i Android.  

**Skapa meddelanden**:  
- Om du vill skapa ett meddelande använder du ett konto som har tilldelats en Intune-roll som har behörigheten **Uppdatera** för **Organisation**. Information om hur du tilldelar behörigheter till en användare finns i [Rolltilldelningar](role-based-access-control.md#role-assignments)  
- Anpassade meddelanden är begränsade till rubriker med högst 50 tecken och meddelanden med högst 500 tecken.  
- Intune sparar inte skickade meddelanden. Om du vill skicka ett meddelande igen måste du återskapa meddelandet.  
- Du kan bara skicka upp till 25 meddelanden i timmen. Den här begränsningen finns på klientnivån.  
- Varje meddelande kan vara direkt riktat till 25 grupper. Kapslade grupper räknas inte mot den här summan.  
- Grupper kan innehålla användare eller enheter, men meddelanden skickas endast till användare, och skickas till alla iOS- eller Android-enheter som användaren har registrerat.  

**Leverans**:  
- Intune försöker leverera i upp till en timme efter att ett meddelande har skickats.  
- Intune skickar meddelanden till användarnas Företagsportal-app, som sedan skapar push-meddelandet. Användarna behöver inte vara inloggade i appen för att meddelandet ska kunna push-överföras till enheten.  
- Intune och appen Företagsportal kan inte garantera leverans av ett anpassat meddelande. Anpassade meddelanden kan visas efter flera timmars fördröjning, eller kanske inte alls. Därför bör de inte användas för brådskande meddelanden.  
- Anpassade meddelanden från Intune visas på enheter som vanliga push-meddelanden. Om appen Företagsportal är öppen på en iOS-enhet när den tar emot meddelandet visas meddelandet i appen i stället för som ett push-meddelande.  
- Anpassade meddelanden kan visas på låsskärmar på både iOS- och Android-enheter, beroende på enhetsinställningarna.  
- Andra appar kan ha åtkomst till data i dina anpassade meddelanden på Android-enheter. Använd dem inte för känslig kommunikation.  
- Användare av en enhet som nyligen har avregistrerats eller användare som har tagits bort från en grupp kan fortfarande få ett anpassat meddelande som skickas till den gruppen.  Om du lägger till en användare i en grupp efter att ett anpassat meddelande har skickats till gruppen, kan den nyligen tillagda användaren på motsvarande sätt ta emot det meddelande som skickades tidigare.  

## <a name="send-a-custom-notification"></a>Skicka ett anpassat meddelande  

1. Logga in i [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) med ett konto som har behörighet att skapa och skicka meddelanden och gå till **Enheter** > **Skicka anpassade notiser**.  

2. På fliken Grundläggande anger du följande och väljer sedan **Nästa** för att fortsätta.  
   - **Rubrik** – Ange en rubrik för meddelandet. Rubriken får innehålla högst 50 tecken.  
   - **Brödtext** – Ange meddelandet. Meddelanden får innehålla högst 500 tecken

   ![Skapa ett anpassat meddelande](./media/custom-notifications/custom-notifications.png)  

3. På fliken **Tilldelningar** väljer du de grupper som du vill skicka det här anpassade meddelandet till och väljer sedan Nästa för att fortsätta.  

4. På fliken **Granska + skapa** granskar du informationen och när du vill skicka meddelandet väljer du **Skapa**.  

Intune bearbetar meddelanden som du skapar direkt. Den enda bekräftelsen på att meddelandet skickades är Intune-aviseringen som bekräftar att det anpassade meddelandet har skickats.  

![Bekräftelse av ett skickat meddelande](./media/custom-notifications/notification-sent.png)  

Intune spårar inte de anpassade meddelanden som du skickar, och enheterna loggar inte mottagandet utanför enhetens meddelandecenter.  

## <a name="receive-a-custom-notification"></a>Ta emot ett anpassat meddelande  

På en enhet ser användarna anpassade meddelanden som skickas av Intune som ett push-standardmeddelande från appen Företagsportal. Dessa meddelanden liknar de push-meddelanden som användarna tar emot från andra appar på enheten.  

Om appen Företagsportal är öppen när ett meddelande tas emot på en iOS-enhet visas meddelandet i appen i stället för som ett push-meddelande.  

Meddelandet är kvar tills användaren stänger det.  

## <a name="next-steps"></a>Nästa steg  
[Hantera enheter](device-management.md)