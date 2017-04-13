---
title: "Aktivera regeln för enhetsskydd | Microsoft Docs"
description: "Aktivera regeln för skydd mot mobila hot i enhetspolicyn för efterlevnad."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c951692d-6538-46c0-a9f0-d607ded189ae
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: d42fa20a3bc6b6f4a74dd0872aae25cfb33067b9
ms.openlocfilehash: 4e20ab540aa66be0c553b6e185bbdf755a1c5aa3
ms.lasthandoff: 03/21/2017


---

# <a name="create-lookout-device-compliance-policy-in-intune"></a>Skapa en efterlevnadsprincip för Lookout-enheten i Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Med Intune med Lookout Mobile Threat Defense kan du identifiera hot på mobila enheter och utvärdera risken på dessa enheter. Du kan skapa en regel för efterlevnadsprincip som bedömer risken för att avgöra om enheten är kompatibel. Du kan sedan använda den villkorliga åtkomstprincipen för att blockera åtkomst till tjänster utifrån enhetens efterlevnad.

Krav för efterlevnadsprincip med Lookout Mobile Threat Defense:

- [Konfigurera Lookout Mobile Threat Defense-prenumeration](set-up-your-subscription-with-lookout-mtp.md)
- [Aktivera anslutning till Lookout i Intune](enable-lookout-mtp-connection-in-intune.md)
- [Konfigurera och distribuera Lookout for Work-appen](configure-and-deploy-lookout-for-work-apps.md)

Som en del av installationen för Lookout Mobile Threat Defense har du skapat en princip i [Lookout-konsolen](https://aad.lookout.com) som klassificerar olika hot som hög, medel och låg. I efterlevnadsprincipen för Intune ställer du in den maximalt tillåtna hotnivån.

1. I [Intune-administratörskonsolen](https://manage.microsoft.com) går du till sidan **Efterlevnadsprinciper**. Du kan antingen använda en befintlig efterlevnadsprincip eller skapa en ny. Gå till **Enhetens hälsotillstånd** och aktivera **Enhetsskydd**.
  ![skärmbild som visar regeln för skydd mot enhetshot i ](../media/mtp/mtp-compliance-policy-rule.png)

2. Välj **Högsta tillåtna hotnivå**:
  * **Ingen (skyddad)**: Det här är det säkraste alternativet.  Enheten får inte ha några förekommande hot och ska ha tillgång till företagsresurser.  Om något hot identifieras på enheten kommer den att utvärderas som icke-kompatibel.  
  * **Låg**: Enheten är kompatibel om det bara finns hot på den låga nivån på enheten. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.
  * **Medel**: Enheten är kompatibel om hoten som hittas på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen icke-kompatibel.
  * **Hög**: Det här alternativet är minst säkert. Detta tillåter alla hotnivåer och använder Lookout mobilt skydd endast för rapportering.

![skärmbild som visar alternativet för hotnivåer för regeln för skydd mot enhetshot](../media/mtp/mtp-compliance-policy-setting.png)

Om du skapar principer för villkorlig åtkomst till Office 365 eller andra tjänster kommer denna utvärdering av efterlevnad att bedömas och icke-kompatibla enheter kommer inte att få åtkomst till dessa tjänster förrän hotet har lösts.

## <a name="monitor-device-threats"></a>Övervaka enhetshot
Om du vill se kompatibilitetstillståndet för en enhet kan du gå till [Intune-administratörskonsolen](https://manage.microsoft.com) och visa **Alla enheter**.

![skärmbild som visar enhetssidan i Intune-administratörskonsolen som visar kompatibilitetstillståndet för en enhet](../media/mtp/mtp-device-status-intune-console.png)

## <a name="next-steps"></a>Nästa steg
* Skapa princip för villkorlig åtkomst
  * [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  * [Exchange On-premises](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  * [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  * [Skype för företag – Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
  * [Dynamics CRM](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)
