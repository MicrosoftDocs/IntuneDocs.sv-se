---
title: Registrera din macOS-enhet som tillhandahålls av organisationen för hantering | Microsoft Docs
description: Beskriver hur du registrerar en macOS-enhet i Intune som har köpts och tillhandahålls av din organisation.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: japoehlm
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: a5808a0ac80390b76058827d2ca0870249b043b9
ms.sourcegitcommit: 11cad61c565c474a8d653181675cc1109d562626
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/29/2018
ms.locfileid: "43241838"
---
# <a name="enroll-your-organization-provided-macos-device-in-management"></a>Registrera din macOS-enhet som tillhandahålls av organisationen i hanteringen

Läs om hur du får en ny macOS-enhet hanterad i Intune.  

Enheter som tillhandahålls till dig av arbete eller skola är ofta förkonfigurerade innan du tar emot dem. Din organisation skickar dessa förkonfigurerade inställningar till enheten när du startar den och loggar in för första gången. När installationen är färdig får du tillgång till arbetets eller skolans resurser. 

Du påbörjar konfigureringen genom att starta din enhet och logga in med dina inloggningsuppgifter för arbetet eller skolan. Resten av den här artikeln beskriver stegen och de skärmar du kommer att se i installationsassistenten.   

## <a name="what-is-apple-dep"></a>Vad är Apple DEP?
Organisationen kanske har köpt sina enheter via något som kallas *Apples program för enhetsregistrering* (DEP). Apple DEP gör det möjligt för organisationer att köpa stora mängder iOS- eller macOS-enheter. Organisationer kan sedan konfigurera och hantera dessa enheter i önskad provider för hantering av mobila enheter, som Intune. Om du är administratör och vill ha mer information om Apple DEP kan du läsa [Automatisk registrering av macOS-enheter i Apples program för enhetsregistrering](https://docs.microsoft.com/intune/device-enrollment-program-enroll-macos).  

## <a name="set-up-your-macos-device"></a>Konfigurera din macOS-enhet  
Utför följande steg när du ska registrera din macOS-enhet för hantering. Om du använder en egen enhet i stället för en enhet som tillhandahålls av organisationen följer du de här stegen för [egna enheter](enroll-your-device-in-intune-macos-cp.md).  

1. Starta din macOS-enhet. 
2. Välj **Språk** och klicka på **Fortsätt**.  

   ![Skärmbild av startskärmen i installationsassistenten för macOS-enheter och en lista med språk att välja mellan.](./media/macos-dep-welcome-1808.png)   
3. Välj en tangentbordslayout. I listan visas ett eller flera alternativ som baseras på det valda språket. Om du vill se alla layoutalternativ, oavsett vilket språk du har valt, klickar du på **Visa alla**. När du är färdig klickar du på **Fortsätt**.  

   ![Skärmbild av skärmen för tangentbordslayout i installationsassistenten för macOS-enheter och en lista med tangentbordsspråk att välja från, ett avmarkerat Visa alla-alternativ samt knapparna Tillbaka och Fortsätt.](./media/macos-dep-keyboard-1808.png)  
4. Välj ditt Wi-Fi-nätverk. Du måste ha en internetanslutning för att fortsätta med installationen. Om du inte ser ditt nätverket, eller om du behöver ansluta via ett kabelanslutet nätverk, klickar du på **Andra nätverksalternativ**. När du är färdig klickar du på **Fortsätt**.  

   ![Skärmbild av Wi-Fi-nätverksskärmen i installationsassistenten för macOS-enheter och en lista med tillgängliga nätverk att välja bland. Dessutom visas knapparna Andra nätverksalternativ, Bakåt och Fortsätt.](./media/macos-dep-wifi-1808.png)  
5. När du har anslutit till Wi-Fi visas skärmen **Fjärrhantering**. Med fjärrhantering kan organisationens administratör konfigurera din enhet med de konton, inställningar, appar och nätverk som används. Läs igenom dokumentationen innan du fortsätter så att du förstår hur din enhet hanteras. Klicka sedan på **Fortsätt**.  

   ![Skärmbild av skärmen för fjärrhantering i installationsassistenten för macOS-enheter samt text som förklarar fjärrhantering och en länk till ytterligare dokumentation. Dessutom visas knapparna Bakåt och Fortsätt.](./media/macos-dep-remote-management-1-1808.png)  
6. När du uppmanas till det loggar du in med ditt arbets- eller skolkonto. När du är inloggad installeras en hanteringsprofil på enheten. Profilen konfigurerar och aktiverar din åtkomst till organisationens resurser.  
7. Läs mer om Apple-ikonen för data och sekretess så att du senare kan se när personlig information samlas in om dig. Klicka sedan på **Fortsätt**.  

   ![Skärmbild av skärmen för data och sekretess i installationsassistenten för macOS-enheter och en bild av två personer som skakar hand samt en beskrivning av hur Apple använder personlig information. Dessutom visas knapparna Bakåt och Fortsätt.](./media/macos-dep-apple-data-privacy-1808.png)  
8. När enheten har registrerats kan det finnas ytterligare steg att utföra. Vilka steg du ser beror på hur din organisation har anpassat konfigureringen. Du kan behöva göra följande:
    * logga in på ett Apple-konto
    * godkänna användarvillkoren
    * skapa ett datorkonto
    * gå igenom en snabbkonfiguration
    * konfigurera din Mac  
## <a name="get-the-company-portal-app"></a>hämta appen för företagsportalen.      
Gå till App Store och hämta appen Intune Företagsportal till enheten. Med den här appen kan du övervaka, synkronisera, lägga till och ta bort enheten från hanteringen samt installera appar.

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).