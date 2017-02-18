---
title: "Konfigurationsprincip för Android for Work-appen | Microsoft Docs"
description: "Använd konfigurationsprinciper för mobilappar i Intune om du vill definiera inställningar som kan krävas när användaren kör en Android for Work-app."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fc6b645a-e837-4b2a-a10f-144065cbd8dd
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 31e28514ab4bdb0f5af261a1f7c87633ca0bd4a6
ms.openlocfilehash: 58671d037c7f62e5fdaa56657737a4470c90bdb7


---

# <a name="configure-android-for-work-apps-with-mobile-app-configuration-policies-in-microsoft-intune"></a>Konfigurera Android for Work-appar med konfigurationsprinciper för mobilappar i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]

Använd konfigurationsprinciper för mobilappar i Microsoft Intune om du vill definiera inställningar som kan krävas när användaren kör en app. En app kan till exempel kräva att användarna anger:

-   Ett anpassat portnummer
-   Språkinställningar
-   Anpassade inställningar, t.ex. en företagslogotyp

Om användarna inte anger inställningarna på ett korrekt sätt kan det öka supportens arbetsbörda och ta längre tid att börja använda nya appar.

Med konfigurationsprinciper för mobilappar kan du distribuera dessa inställningar till enheterna innan användarna kör appen. Inställningarna distribueras automatiskt utan att användarna behöver göra något.

Om du vill använda konfigurationsprinciper för appar måste utvecklaren av appen ha gjort konfigurationer för företagsappar tillgängliga när de skapade den. Google Chrome gör till exempel inställningar som låter dig ange standardbokmärken, tillåtna respektive nekade platser och mycket annat tillgängliga. Kontakta apputvecklaren för att se om de här inställningarna stöds och hur du anger dem i principen.

Du kan distribuera appkonfigurationsprincipen till samma användare som du har distribuerat appen som du vill konfigurera till. Appinställningarna tillämpas när appen körs.

## <a name="configure-a-mobile-app-configuration-policy"></a>Konfigurera en konfigurationsprincip för mobilappar

1.  I [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com) väljer du **Princip** &gt; **Översikt** &gt; **Lägg till princip**.

2.  Expandera **Android for Work**i listan med principer, välj **Konfigurationprincip för mobilapp (Android for Work)**och välj sedan **Skapa princip**.

    > [!TIP]
    > Du kan bara konfigurera anpassade inställningar för den här principtypen. Rekommenderade inställningar är inte tillgängliga.

3.  Ange ett namn och en valfri beskrivning av konfigurationsprincipen för mobilappen under **Allmänt** på sidan **Skapa princip** .

4. I avsnittet **Konfigurationsprincip för mobilappar** på sidan anger du följande information:
    - **Paket-ID för programmet som konfigurationen avser** – Paket-ID:t finns i delen 'id=' i appens URL på dess Google Play-sida. Paket-ID:t för Microsoft Excel-appen är till exempel **com.microsoft.office.excel**.
    - I textrutan anger du data för de app-inställningar som du vill konfigurera. Du kan hämta dessa inställningar från appens leverantör. Inte alla appar har stöd för dessa inställningar.
5.  Bekräfta att datan som du angav har ett giltigt format i form av en egenskapslista genom att klicka på **Validera**.

    > [!IMPORTANT]
    > När du klickar på **Validera** kontrollerar Intune att konfigurationsdatan som du angett har rätt format. Intune kontrollerar inte om datan fungerar med den app som den är associerad med.

6.  När du är klar klickar du på **Spara princip**.

Den nya principen visas i noden **Konfigurationsprinciper** .


## <a name="deploy-the-app-configuration-policy"></a>Distribuera appkonfigurationsprincipen
När du har skapat en konfigurationsprincip för mobilappar så måste du distribuera den till samma användare som appen som inställningarna ska gälla för distribueras till.

Mer information om att distribuera principer finns i [distribuera en konfigurationsprincip](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#deploy-a-configuration-policy)

Information om hur du distribuerar appar till Android for Work-enheter finns i [How to deploy Android for Work apps with Intune](android-for-work-apps.md) (Så distribuerar du Android for Work-appar med Intune).

När den distribuerade appen körs på en enhet körs den med de inställningar som du konfigurerade i konfigurationsprincipen för mobilappar.

> [!TIP]
> Distribuera endast en princip för app-konfiguration för varje app till en användare.



<!--HONumber=Feb17_HO1-->

