---
title: "Tillåtna och blockerade appar för KNOX | Microsoft Intune"
description: "Anpassad profil för att skapa en lista över tillåtna och blockerade appar för KNOX."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/09/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbc8e0df-7bf3-494e-8bc4-dac59a98ab41
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 65d2c9c1f5d81dae33422bd4bf7c0e2e21bb96e4
ms.openlocfilehash: 937e291f193f61329598395baa63c24d7fefa25f



---
# Använda anpassade principer för att tillåta och blockera appar för Samsung KNOX-enheter

I det här avsnittet anges hur du skapar en anpassad princip för Microsoft Intune som skapar något av följande:

- En lista över appar som blockeras från att köras på enheten. Inga andra appar kommer att kunna köras. Appar i den här listan blockeras från att köras även om de redan är installerade när principen tillämpas.
- En lista över appar som enhetens användare tillåts att installera från Google Play Store. Endast de appar som du tar med i listan kan installeras. Inga andra appar kan installeras från butiken.

De här inställningarna kan endast användas av enheter som kör Samsung KNOX.

## Skapa en lista med tillåtna eller blockerade appar

1. Öppna [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com/) och välj **Princip** &gt; **Konfigurationsprinciper** &gt; **Lägg till**.
2. Expandera **Android** i dialogrutan **Skapa en ny princip**, välj **Anpassad konfiguration** och välj sedan **Skapa princip**.
3. Ange ett namn och en beskrivning (valfritt) för principen och välj sedan **Lägg till** i avsnittet **OMA-URI-inställningar**.
4. I dialogrutan **Lägg till eller redigera OMA-URI-inställning** anger du följande: För en lista över appar som blockeras från att köras på enheten:
    
    - **Inställningsnamn.** Ange **PreventStartPackages**.
    - **Beskrivning av inställning.** Ange en valfri beskrivning (valfritt), till exempel ”lista över appar som har blockerats från att köras”.
    -   **Datatyp.** Välj **Sträng** i listrutan.
    -   **OMA-URI.** Ange **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**
    -   **Värde.** Ange en lista över de appaketnamn som du vill tillåta. Du kan använda **; : ,** eller **|** som avgränsare. (Exempel: paket1;paket2;)

    För en lista över appar som användare tillåts att installera från Google Play (alla andra appar exkluderas):

    - **Inställningsnamn.** Ange **AllowInstallPackages**.
    - **Beskrivning av inställning.** Ange en beskrivning (valfritt), till exempel ”lista över appar som användare kan installera från Google Play”.
    - **Datatyp.** Välj **Sträng** i listrutan.
    - **OMA-URI.** Ange **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**
    - **Värde.** Ange en lista över de appaketnamn som du vill tillåta. Du kan använda **; : ,** eller **|** som avgränsare. (Exempel: paket1;paket2;)

4. Klicka på **OK** och sedan på **Spara princip**. 

>[TIPS] Du kan hitta paket-ID för en app genom att gå till appen i Google Play. Paket-ID finns i webbadressen på appens sida. Paket-ID för Microsoft Word-appen är till exempel **com.microsoft.office.word**.

Appinställningarna tillämpas nästa gång en målenhet checkar in.


## Distribuera principen

1.  Välj den princip på arbetsytan **Princip** som du vill distribuera och klicka sedan på **Hantera distribution**.

2.  I dialogrutan **Hantera distribution** väljer du en eller flera grupper som du vill distribuera principen till. Klicka sedan på **Lägg till** &gt; **OK**.

 
När du väljer en distribuerad princip visas ytterligare information om distributionen i den nedre delen av principlistan.

### Se även
[Inställningar för Android- och Samsung KNOX-principer i Microsoft Intune](android-policy-settings-in-microsoft-intune.md)



<!--HONumber=Aug16_HO3-->

