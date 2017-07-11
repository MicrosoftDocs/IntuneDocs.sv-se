---
title: "Inställningar av begränsningar i Intune-enheter för Windows Phone 8.1"
titleSuffix: Intune on Azure
description: "Läs om de Intune-inställningar du kan använda för att styra inställningar och funktioner på Windows Phone 8.1-enheter.”"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c2d42714-49ca-43b3-b080-2e67a4268198
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e425b8a3c93c2f5dc73fbe9c75aa9adf49c5cdc8
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="windows-phone-81-device-restriction-settings-in-microsoft-intune"></a>Inställningar fö enhetsbegränsningar för Windows Phone 8.1-enheter i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="general"></a>Allmänt
-   **Använd alla inställningar endast för Windows Phone 8.1** – Detta är en inställning som du kan konfigurera i den klassiska Intune-portalen. Den här inställningen kan inte ändras i Azure-portalen. Om inställningen anges till **Konfigurerad**, tillämpas inställningar endast på Windows Phone 8.1-enheter. Om inställningen anges till **Inte konfigurerad**, gäller de här inställningarna även för Windows 10 Mobile-enheter.
-   **Kamera** – Tillåter eller blockerar kameran på enheten.
-   **Kopiera och klistra in** – Tillåter eller blockerar kopierings- och inklistringsfunktioner på enheter.
-   **Flyttbara lagringsmedia** – Tillåter att enheten använder flyttbara lagringsmedia, t.ex. SD-kort.
-   **Geoplats** – Gör att enheten använder platsinformation.
-   **Microsoft-konto** – Tillåter eller blockerar användaren från att länka ett Microsoft-konto till enheten.
-   **Skärmdump** – Låter användaren fånga innehållet på skärmen som en bildfil.
-   **Sändning av diagnostikdata** – Gör att enheten skickar diagnostikinformation till Microsoft.
-   **Synkronisering av anpassade e-postkonton** – Gör det möjligt för enheten att ansluta till andra e-postkonton än Microsoft-e-postkonton.

## <a name="password"></a>Lösenord
-   **Använd alla inställningar endast för Windows Phone 8.1** – Detta är en inställning som du kan konfigurera i den klassiska Intune-portalen. Den här inställningen kan inte ändras i Azure-portalen. Om inställningen anges till **Konfigurerad**, tillämpas inställningar endast på Windows Phone 8.1-enheter. Om inställningen anges till **Inte konfigurerad**, gäller de här inställningarna även för Windows 10 Mobile-enheter.
-   **Lösenord krävs** – Slutanvändaren måste ange ett lösenord för att få åtkomst till enheten.
    -   **Krav på lösenordstyp** – Anger vilken typ av lösenord som krävs, t.ex. enbart alfanumeriskt eller numeriskt.
    -   **Minsta längd på lösenord** – Anger det minsta antalet tecken som lösenordet måste innehålla.
    -   **Enkla lösenord** – Anger att enkla lösenord kan användas, t.ex. 0000 och 1234.
    -   **Antal felaktiga inloggningar innan enheten rensas** – Anger hur många gånger ett felaktigt lösenord kan anges innan enheten rensas.
    -   **Maximalt antal minuter av inaktivitet innan skärmen låses** – Anger hur lång tid en enhet måste vara i viloläge innan skärmen låses automatiskt.
    -   **Lösenordets giltighetstid (dagar)** – Anger antal dagar innan lösenordet för enheten måste ändras.
    -   **Förhindra återanvändning av tidigare lösenord** – Anger hur många tidigare använda lösenord som koms ihåg.
-   **Kryptering** – Kräver att data på mobila enheter som stöds krypteras.

## <a name="app-store"></a>Appbutik
-   **Använd alla inställningar endast för Windows Phone 8.1** – Detta är en inställning som du kan konfigurera i den klassiska Intune-portalen. Den här inställningen kan inte ändras i Azure-portalen. Om inställningen anges till **Konfigurerad**, tillämpas inställningar endast på Windows Phone 8.1-enheter. Om inställningen anges till **Inte konfigurerad**, gäller de här inställningarna även för Windows 10 Mobile-enheter.
-   **Appbutik** – Tillåter att användarna ansluter till appbutiken från enheten.

## <a name="restricted-apps"></a>Begränsade appar

-   **Använd alla inställningar endast för Windows Phone 8.1** – Detta är en inställning som du kan konfigurera i den klassiska Intune-portalen. Den här inställningen kan inte ändras i Azure-portalen. Om inställningen anges till **Konfigurerad**, tillämpas inställningar endast på Windows Phone 8.1-enheter. Om inställningen anges till **Inte konfigurerad**, gäller de här inställningarna även för Windows 10 Mobile-enheter.

Du kan konfigurera en av följande listor i listan med begränsade appar:

Listan **Blockerade appar** – Ange de appar (som inte hanteras av Intune) som användarna inte får installera och köra.
Listan **Tillåtna appar** – Ange de appar som användare tillåts att installera. Appar som hanteras av Intune tillåts automatiskt.

Konfigurera listan genom att klicka på **Lägg till**, ange ett namn, t.ex. appens utgivare samt webbadressen till appen i appbutiken.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Så här anger du webbadressen till appen i butiken

Om du vill ange en app-URL i listan över tillåtna och blockerade appar använder du följande format:

Gå till sidan [Windows Phone Store](https://www.microsoft.com/store/apps/windows-phone) och sök efter den app du vill använda.

Öppna appens sida och kopiera webbadressen till Urklipp. Nu kan du använda den som webbadress i listan över tillåtna eller blockerade appar.

Exempel: Sök i butiken efter Skype-appen. Webbadressen som du använder är **http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51**.



### <a name="additional-options"></a>Ytterligare alternativ

Du kan också klicka på **Importera** för att fylla i listan från en csv-fil i formatet <*app-url*>, <*appnamn*>, <*appens utgivare*>, eller klicka på **Exportera** för att skapa en csv-fil med innehållet i listan över begränsade appar i samma format.


## <a name="browser"></a>Webbläsare
-   **Använd alla inställningar endast för Windows Phone 8.1** – Detta är en inställning som du kan konfigurera i den klassiska Intune-portalen. Den här inställningen kan inte ändras i Azure-portalen. Om inställningen anges till **Konfigurerad**, tillämpas inställningar endast på Windows Phone 8.1-enheter. Om inställningen anges till **Inte konfigurerad**, gäller de här inställningarna även för Windows 10 Mobile-enheter.
-   **Webbläsare** – Tillåter eller blockerar den inbyggda webbläsaren på enheter.

## <a name="cellular-and-connectivity"></a>Mobilnät och anslutning
-   **Använd alla inställningar endast för Windows Phone 8.1** – Detta är en inställning som du kan konfigurera i den klassiska Intune-portalen. Den här inställningen kan inte ändras i Azure-portalen. Om inställningen anges till **Konfigurerad**, tillämpas inställningar endast på Windows Phone 8.1-enheter. Om inställningen anges till **Inte konfigurerad**, gäller de här inställningarna även för Windows 10 Mobile-enheter.
-   **Wi-Fi** – Aktiverar eller inaktiverar Wi-Fi-funktioner på enheten.
-   **Trådlös Internetdelning** – Tillåter att trådlös Internetdelning används på enheten.
-   **Anslut automatiskt till trådlösa surfpunkter** – Gör att enheten ansluter automatiskt till kostnadsfria trådlösa surfpunkter och att den automatiskt godkänner användningsvillkoren.
-   **Rapportering om trådlösa surfzoner** – Skickar information om Wi-Fi-anslutningar så att användaren lättare kan upptäcka närliggande anslutningar.
-   **NFC** – Aktiverar eller inaktiverar åtgärder som använder närfältskommunikation på de enheter som stöds.
-   **Bluetooth** – Aktiverar eller inaktiverar Bluetooth-funktionen på enheten.