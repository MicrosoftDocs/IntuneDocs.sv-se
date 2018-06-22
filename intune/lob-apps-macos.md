---
title: Lägga till verksamhetsspecifika appar för macOS i Microsoft Intune
titlesuffix: ''
description: Läs mer om att lägga till verksamhetsspecifika appar för macOS i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ef8008ac-8b85-4bfc-86ac-1f9fcbd3db76
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0304d90384bb2f6a5a78dd14bcf289fc8eb03bd1
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34224372"
---
# <a name="how-to-add-macos-line-of-business-lob-apps-to-microsoft-intune"></a>Lägga till verksamhetsspecifika appar för macOS i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Informationen i den här artikeln visar hur du lägger till verksamhetsspecifika appar för macOS i Microsoft Intune. Du måste hämta ett externt verktyg för att förbearbeta dina *.pkg*-filer innan du kan ladda upp din verksamhetsspecifika fil till Microsoft Intune. Förbearbetningen av dina *.pkg*-filer måste ske på en macOS-enhet.

>[!NOTE]
>Användare av macOS-enheter kan ta bort några av de inbyggda macOS-apparna som Aktier och Kartor, men du kan inte använda Intune för att distribuera dessa appar igen. Om slutanvändarna tar bort dessa appar måste de gå till App Store och installera om dem manuellt.
>
>Endast *.pkg*-filer kan användas för att överföra verksamhetsspecifika macOS-appar till Microsoft Intune. 

## <a name="step-1---pre-process-your-software-setup-file"></a>Steg 1 – Förbearbeta programvarans installationsfil

Använd Intune App Wrapping-verktyget för Mac för att aktivera Mac-appar som ska hanteras av Microsoft Intune.

1. Hämta och kör [Intunes programhanteringsverktyg för Mac](https://github.com/msintuneappsdk/intune-app-wrapping-tool-mac).

    > [!NOTE]
    > **Intunes programhanteringsverktyg för Mac** måste köras på en macOS-dator.

2. Använd `IntuneAppUtil`-kommandot inom den **Intunes programhanteringsverktyg för Mac** för att omsluta den verksamhetsspecifika *.pkg*-filen från en *.intunemac*-fil.<br>

    Exempelkommandon att använda för Microsoft Intune programhanteringsverktyget för macOS:
    
    - `IntuneAppUtil -h`<br>
    Det här kommandot visar användningsinformation för verktyget.
    
    - `IntuneAppUtil -c <source_file> -o <output_file> [-v]`<br>
    Det här kommandot kommer att omsluta den verksamhetsspecifika *.pkg*-filen till en *.intunemac*-fil.
    
    - `IntuneAppUtil -r <filename.intunemac> [-v]`<br>
    Det här kommandot extraherar identifierade parametrar och version för den skapade *.intunemac*-filen.

## <a name="step-2---specify-the-software-setup-file"></a>Steg 2 – Ange platsen för programinstallationsfilen

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Mobilappar** i **Intune**-fönstret.
4. Välj **Hantera** > **appar** i arbetsbelastningen **Mobilappar**.
5. Välj **Lägg till** ovanför applistan.
6. I fönstret **Lägg till app** väljer du **Verksamhetsspecifik app**.

## <a name="step-3---configure-the-app-package-file"></a>Steg 3 – Konfigurera appaketfilen

1. I fönstret **Lägg till app** väljer du **Appaketfil**.
2. I fönstret **Appaketfil** klickar du på knappen Bläddra och väljer en macOS-installationsfil med filnamnstillägget *.intunemac*.
3. Välj **OK** när du är klar.


## <a name="step-4---configure-app-information"></a>Steg 4 – Konfigurera appinformation

1. Välj **Appinformation** i fönstret **Lägg till app**.
2. I fönstret **Appinformation** lägger du till information om appen. Beroende på vilken app du har valt kan det hända att några av värdena i det här fönstret har fyllts i automatiskt:
    - **Namn** – Ange namnet på appen som ska visas på företagsportalen. Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna för användare i företagsportalen.
    - **Beskrivning** – Ange en beskrivning av appen som ska visas för användare på företagsportalen.
    - **Utgivare** – Ange namnet på appens utgivare.
    - **Minsta operativsystem** – Välj den minsta operativsystemversion som appen kan installeras på. Om appen tilldelas till en enhet med ett äldre operativsystem installeras den inte.
    - **Kategori** – Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Det gör det lättare för användarna att hitta appen när de söker på företagsportalen.
    - **Visa den här som aktuell app på företagsportalen** – Visa appen på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    - **Informations-URL** – Du kan välja att ange webbadressen till en webbplats som innehåller information om den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Sekretess-URL (valfritt)** – Ange webbadressen till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Utvecklare (valfritt)** – Ange apputvecklarens namn.
    - **Ägare (valfritt)** – Ange ett namn på appägaren, t.ex. **Personalavdelningen**.
    - **Anteckningar** – Ge eventuella kommentarer som du vill koppla till den här appen.
    - **Logotyp** – Ladda upp en ikon som är associerad med appen. Den här ikonen visas med appen när användare söker på företagsportalen.
3. Välj **OK** när du är klar.

## <a name="step-5---finish-up"></a>Steg 5 – Slutför

1. I fönstret **Lägg till app** kontrollerar du att informationen för appen är korrekt.
2. Välj **Lägg till** för att överföra appen till Intune.

Appen som du har skapat visas i applistan där du kan tilldela den till de grupper du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).

> [!NOTE]
> Om *.pkg*-filen innehåller flera appar eller appinstallationsprogram kommer Microsoft Intune endast rapportera att *appen* har installerats korrekt när alla installerade appar har upptäckts på enheten.

## <a name="step-6---update-a-line-of-business-app"></a>Steg 6 – Uppdatera en verksamhetsspecifik app

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> För att Intune-tjänsten ska kunna distribuera en ny *.pkg*-fil till enheten, måste du öka paketet `version` och `CFBundleVersion`-strängen i *packageinfo*-filen i ditt *.pkg*-paket.

## <a name="next-steps"></a>Nästa steg

- Appen som du har skapat visas i applistan. Nu kan du tilldela den till de grupper som du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).

- Lär dig mer om hur du kan övervaka appens egenskaper och tilldelning. Mer information finns i [Så här övervakar du appinformation och tilldelningar](apps-monitor.md).

- Lär dig mer om kontexten för din app i Intune. Mer information finns i [Översikt över enhets- och applivscykler](introduction-device-app-lifecycles.md)