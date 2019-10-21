---
title: Microsoft Intune-principer för att tillåta/blockera appar för Samsung Knox
titleSuffix: ''
description: Skapa en anpassad profil för att tillåta och blockera appar för Samsung Knox Standard-enheter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: afaee427b593cfaed957279b520765242a1aacd3
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506648"
---
# <a name="use-custom-policies-in-microsoft-intune-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>Använd anpassade principer för att tillåta och blockera appar för Samsung Knox Standard-enheter i Microsoft Intune 

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

I den här artikeln anges hur du skapar en anpassad princip för Microsoft Intune som skapar något av följande:

- En lista över appar som blockeras från att köras på enheten. Appar i den här listan blockeras från att köras även om de redan är installerade när principen tillämpas.
- En lista över appar som enhetens användare tillåts att installera från Google Play Store. Endast de appar som du tar med i listan kan installeras. Inga andra appar kan installeras från butiken.

De här inställningarna kan endast användas av enheter som kör Samsung Knox Standard.

## <a name="create-an-allowed-or-blocked-app-list"></a>Skapa en lista med tillåtna eller blockerade appar

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. I fönstret **Intune** väljer du **Enhetskonfiguration**.
2. I fönstret **Enhetskonfiguration** väljer du **Hantera** > **Profiler**.
2. Välj **Skapa profil** i fönstret med profillistan.
3. Ange **Namn** och en valfri **Beskrivning** för denna enhetsprofil i fönstret **Skapa profil**.
2. Välj en **Plattform** för **Android** och **profiltypen** **Anpassad**.
3. Klicka på **Inställningar**.
3. I fönstret **Anpassade OMA-URI-inställningar** väljer du **Lägg till**.
4. I dialogrutan **Lägg till eller redigera OMA-URI-inställning** anger du följande inställningar:

   För en lista över appar som blockeras från att köras på enheten:

   - **Namn** – Ange **PreventStartPackages**.
   - **Beskrivning** – Ange en valfri beskrivning, till exempel ”lista över appar som har blockerats från att köras.”
   - **Datatyp** – Välj **Sträng** i listrutan.
   - **OMA-URI** – Ange **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**
   - **Värde** – Ange en lista över de appaketnamn som du vill tillåta. Du kan använda **; : ,** eller **|** som avgränsare. (Exempel: paket1;paket2;)

   För en lista över appar som användare tillåts att installera från Google Play (alla andra appar exkluderas):
   - **Namn** – Ange **AllowInstallPackages**.
   - **Beskrivning** – Ange en beskrivning (valfritt), till exempel ”lista över appar som användare kan installera från Google Play.”
   - **Datatyp** – Välj **Sträng** i listrutan.
   - **OMA-URI** – Ange **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**
   - **Värde** – Ange en lista över de appaketnamn som du vill tillåta. Du kan använda **; : ,** eller **|** som avgränsare. (Exempel: paket1;paket2;)

4. Klicka på **OK** och klicka sedan på fönstret **Skapa profil** och välj **Skapa**.

>[!TIP]
> Du kan hitta paket-ID:et för en app genom att gå till appen i Google Play. Paket-ID finns i webbadressen på appens sida. Paket-ID för Microsoft Word-appen är till exempel **com.microsoft.office.word**.

Appinställningarna tillämpas nästa gång en målenhet checkar in.


<!---## Assign the custom profile--->