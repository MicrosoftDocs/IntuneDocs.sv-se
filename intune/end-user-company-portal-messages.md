---
title: "Företagsportal, meddelanden som användare kan se på Android"
description: "Beskriver meddelanden i företagsportalen som kan visas för slutanvändare av Intune."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3df993aa-48c5-4799-b68d-c85fe4f7b02c
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: ae0bd848413fc82f68f2ce6e6ac55fe92b9cb989
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="help-end-users-understand-company-portal-app-messages"></a>Hjälpa slutanvändarna att förstå meddelanden i företagsportalappen

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

> [!NOTE]
> Följande information gäller endast på enheter med Android 6.0+.

Vid olika tidpunkter i registreringsprocessen ser slutanvändare två olika meddelanden som kan orsaka problem.

- __Tillåt att företagsportalen kan ringa och hantera telefonsamtal?__
- __Tillåt att företagsportalen kommer åt foton, media och filer på enheten?__

## <a name="allow-company-portal-to-make-and-manage-phone-calls"></a>Tillåt att företagsportalen kan ringa och hantera telefonsamtal?

### <a name="where-it-appears"></a>Var det visas
Meddelandet är **Tillåt att företagsportalen kan ringa och hantera telefonsamtal?** och visas när användare trycker på **Registrera** i företagsportalen för första gången för att börja registrera sin enhet.

### <a name="what-it-means"></a>Betydelse
Genom att acceptera varningen kan användarna låta telefonnummer och IMEI-nummer för deras enhet skickas till tjänsten Intune. Dessa visas i administrationskonsolen på sidan __Maskinvara__.

> [!NOTE]
> **Företagsportalappen ringer eller hanterar aldrig telefonsamtal!** Meddelandetexten styrs av Google och kan inte ändras.

Öppna sidan **Maskinvara** genom att gå till **Grupper** > **Alla mobila enheter** > **Enheter**. Välj användarens enhet och gå till **Visa egenskaper** > **Maskinvara**.

### <a name="what-happens-if-users-deny-access"></a>Vad händer om användarna nekar åtkomst
Om användarna nekar åtkomst kan de fortsätta att använda programmet för företagsportalen och registrera sina enheter. Enhetens telefonnummer och IMEI saknar data på sidan __Maskinvara__ i administrationskonsolen. Den andra gången användarna loggar in på företagsportalappen efter att de nekat åtkomst visas kryssrutan **Fråga inte igen** som de kan markera så att meddelandet inte visas igen.

Om användare tillåter men senare nekar åtkomst visas meddelandet nästa gång användaren loggar in på företagsportalappen efter registreringen.

Om användare senare bestämmer sig för att tillåta åtkomst kan de gå till **Inställningar** > **Appar** > **Företagsportal** > **Behörigheter** > **Telefon** och aktivera den.

### <a name="how-to-explain-this-to-your-users"></a>Så här förklarar du detta till dina användare
Hänvisa dina användare till [Registrera Android-enhet i Intune](/intune-user-help/enroll-your-device-in-intune-android) för mer information.

## <a name="allow-company-portal-to-access-your-contacts"></a>Tillåta att företagsportalappen får åtkomst till dina kontakter?

### <a name="where-it-appears"></a>Var det visas
Meddelandet är **Allow Company Portal to access your contacts?** (Tillåt att företagsportalen får åtkomst till dina kontakter?) och visas när användare trycker på **Registrera** i företagsportalen för första gången för att börja registrera sin enhet.

### <a name="what-it-means"></a>Betydelse
Meddelandet uppmanar användarna att låta Intune skapa ett arbetskonto och hantera den Azure Active Directory-identitet som har registrerats för användaren på enheten.

> [!NOTE]
> **Microsoft bereder sig aldrig åtkomst till dina kontakter!** Meddelandetexten styrs av Google och kan inte ändras.

### <a name="what-happens-if-users-deny-access"></a>Vad händer om användarna nekar åtkomst
Om användarna nekar åtkomst kommer enheten inte att registreras i Intune och kan inte hanteras. Den andra gången användarna loggar in på företagsportalappen efter att de nekat åtkomst visas kryssrutan **Fråga inte igen** som de kan markera så att meddelandet inte visas igen.

Om användare tillåter men senare nekar åtkomst visas meddelandet nästa gång användaren loggar in på företagsportalappen efter registreringen.

Om användare senare bestämmer sig för att tillåta åtkomst kan de gå till **Inställningar** > **Appar** > **Företagsportal** > **Behörigheter** > **Telefon** och aktivera den.

### <a name="how-to-explain-this-to-your-users"></a>Så här förklarar du detta till dina användare
Hänvisa dina användare till [Registrera Android-enhet i Intune](/intune-user-help/enroll-your-device-in-intune-android) för mer information.

## <a name="allow-company-portal-to-access-photos-media-and-files-on-your-device"></a>Tillåt att företagsportalen kommer åt foton, media och filer på enheten?

### <a name="where-it-appears"></a>Var det visas
Meddelandet **Tillåt att företagsportalen kommer åt foton, media och filer på enheten?** visas när användarna trycker på **Skicka Data** för att skicka dataloggar till sin IT-administratör.

### <a name="what-it-means"></a>Betydelse
När användarna accepterar meddelandet kan deras enheter skriva dataloggar till enhetens SD-kort och tillåta att loggarna flyttas med hjälp av en USB-kabel.   

> [!NOTE]
> **Företagsportalappen bereder sig aldrig åtkomst till användarnas foton, media och filer!** Meddelandetexten styrs av Google och kan inte ändras.

### <a name="what-happens-if-users-deny-access"></a>Vad händer om användarna nekar åtkomst
Om användarna nekar åtkomst kan de fortfarande skicka loggar via e-post, men loggarna kopieras inte till enhetens SD-kort.

Den andra gången användarna loggar in på företagsportalappen efter att de nekat åtkomst visas kryssrutan **Fråga inte igen** som de kan markera så att meddelandet inte visas igen. Om användare tillåter men senare nekar åtkomst visas meddelandet nästa gång användaren försöker skicka loggar. Om användare senare bestämmer sig för att tillåta åtkomst kan de gå till **Inställningar** > **Appar** > **Företagsportal** > **Behörigheter** > **Lagring** och aktivera behörigheten.


### <a name="how-to-explain-this-to-your-users"></a>Så här förklarar du detta till dina användare
Hänvisa dina användare till [Skicka loggar till IT-administratören via e-post](/intune-user-help/send-logs-to-your-it-admin-by-email-android). Du kan även hänvisa dem till [Skicka loggar till IT-administratören via kabel](/intune-user-help/send-logs-to-your-it-admin-by-cable-android) om du vill att de jämför de två metoderna.


### <a name="see-also"></a>Se även
[Vad du ska berätta för slutanvändare om att använda Intune](/intune-classic/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)