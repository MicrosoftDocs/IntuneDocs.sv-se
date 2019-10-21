---
title: Lägg till inbyggda appar på mobila enheter med Microsoft Intune
titleSuffix: ''
description: Så här använder du Intune för att underlätta installation av inbyggda appar på mobila enheter.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0ec8de66-5a0f-4c8d-afbf-c2becc7d6eec
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2a94542311bc5ff4a25b2f9c6229898b1d891c6c
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725315"
---
# <a name="add-built-in-apps-to-microsoft-intune"></a>Lägg till inbyggda appar i Microsoft Intune

Den *inbyggda* apptypen gör det enkelt att tilldela granskade och hanterade appar som till exempel Office 365-appar till iOS- och Android-enheter. Du kan tilldela specifika appar för den här apptypen, till exempel Excel, OneDrive, Outlook, Skype med mera. När du lagt till en app visas apptypen antingen som *Inbyggd iOS-app* eller *Inbyggd Android-app*. Du kan välja vilken av dessa appar du vill publicera till enhetsanvändare genom att använda den inbyggda apptypen.

I tidigare versioner av Intune-konsolen tillhandahöll Intune flera hanterade Office 365-appar som standard, till exempel Outlook och OneDrive. Apptyperna för dessa hanterade appar har taggats som *Hanterad iOS Store-app* eller *Hanterad Android-app*. Istället för att använda dessa apptyper, rekommenderar vi att du använder den inbyggda apptypen. Genom att använda den inbyggda apptypen får du extra flexibilitet för att redigera och ta bort Office 365-appar.

>[!NOTE]
>Standard-Office 365-appar som taggats som *Hanterad iOS Store* och *Hanterad Android-app* tas bort från listan över appar när alla tilldelningar har tagits bort.

## <a name="add-a-built-in-app"></a>Lägg till en inbyggd app

För att lägga till en inbyggd app till dina tillgängliga appar i Microsoft Intune, gör följande:
1. Logga in på Azure-portalen.
2. För att visa Microsoft Intune-fönstret väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Klientappar** i **Intune**-fönstret.
4. I fönstret **Klientappar** väljer du **Appar** under **Hantera**.
5. Välj **Lägg till**.
6. I appfönstret **Lägg till** i listan **Apptyp** väljer du **Inbyggd app**.
7. Välj **Välj app**.
8. I fönstret **Inbyggd app** väljer du de appar som du vill inkludera.
9. I fönstret **Lägg till app** väljer du **Lägg till**.


## <a name="configure-app-information"></a>Konfigurera appinformation

Du kan modifiera informationen om den inbyggda appen. Den här informationen hjälper dig att identifiera appen i Intune och hjälper användarna att hitta appen i företagsportalen.
1. I fönstret **Klientappar – Appar** väljer du den inbyggda app som du vill ändra.  
    Ett fönster för den inbyggda appen visas.
2. Under **Hantera**, välj alternativet **Egenskaper**.
3. Välj alternativet **Konfigurera** för att ändra informationen om den inbyggda appen.
4. I fönstret **Appinformation** kan du ändra följande information:
    - **Namn**: Ange namnet på den inbyggda appen så som det visas i företagsportalen. Kontrollera att alla namn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna för användarna på företagsportalen.
    - **Beskrivning**: Ange en beskrivning för appen. 
    - **Utgivare**: Ange namnet på appens utgivare.
    - **Kategori**: Valfritt – välj en eller fler av de inbyggda appkategorierna. Om du konfigurerar det här alternativet blir det lättare för användarna att hitta appen när de söker på företagsportalen.
    - **Visa denna som en aktuell app i företagsportalen**: Visa appen tydligt på huvudsidan för företagsportalen när användare söker efter appar.
    - **Webbadress till information**: Du kan välja att ange en webbadress till en webbplats som innehåller information om den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Sekretesswebbadress**: Du kan välja att ange en webbadress till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Utvecklare**: Alternativt kan du ange apputvecklarens namn.
    - **Ägare**: Alternativt kan du ange ett namn på appens ägare (till exempel *HR-avdelningen*).
    - **Kommentarer**: Ange eventuella kommentarer som du vill koppla till den här appen.
    - **Ladda upp ikon**: Ladda upp en ikon som visas med appen när användare söker i företagsportalen.
4. Välj **OK**.
5. I fönstret **Egenskaper** väljer du **Spara**.

## <a name="next-steps"></a>Nästa steg

- Nu kan du tilldela apparna till de grupper som du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).