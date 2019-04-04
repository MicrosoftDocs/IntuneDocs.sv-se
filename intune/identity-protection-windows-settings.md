---
title: Inställningar i Windows Hello för företag i Microsoft Intune – Azure | Microsoft Docs
description: Se en lista med alla inställningar för PIN-kod, biometri och skydd mot förfalskning i en identitetsskyddsprofil som använder och konfigurerar Windows Hello för företag på Windows 10-enheter i Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/14/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: shpate
ms.openlocfilehash: 308a730737612f39863160952409ab92670f9153
ms.sourcegitcommit: fdc6261f4ed695986e06d18353c10660a4735362
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2019
ms.locfileid: "58069376"
---
# <a name="windows-10-device-settings-to-enable-windows-hello-for-business-in-intune"></a>Inställningar i enheter som kör Windows 10 för att aktivera Windows Hello för företag i Intune

Den här artikeln visar och beskriver inställningarna i Windows Hello för företag som du kan styra på Windows 10-enheter i Intune. Som Intune-administratör kan du konfigurera och tilldela dessa inställningar till Windows 10-enheter som en del av din lösning för hantering av mobila enheter. 

Du hittar mer information om de här inställningarna i [konfigurera Windows Hello för företag principinställningar](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings), i WIndows Hello-dokumentationen.


Mer information om Windows Hello för företag-profiler i Intune finns i [Konfigurera identitetsskydd](identity-protection-configure.md).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en konfigurationsprofil](identity-protection-configure.md#create-the-device-profile).

## <a name="windows-hello-for-business"></a>Windows Hello för företag

- **Konfigurera Windows Hello för företag**: Om du vill använda den här funktionen och konfigurera dess inställningar, Välj **aktivera**.
- **Minsta PIN-kodslängd**: Ange den minsta PIN-kodslängd som du vill tillåta på enheterna. Standardlängden för PIN-koder är sex tecken. Minimilängden för PIN-koder är fyra tecken.
- **Maximala PIN-kodslängd**: Ange den maximala PIN-kodslängd som du vill tillåta på enheterna. Standardlängden för PIN-koder är sex tecken. Den maximala längden för PIN-kod är 127 tecken.  
- **Gemener i PIN-koden**: Du kan tillämpa en starkare PIN-kod genom att kräva att slutanvändarna även använder små bokstäver. Alternativen är:

  - **Inte tillåtet** (standard): blockera användare från att använda gemener i PIN-koden. Denna inställning tillämpas även när inställningen inte har konfigurerats.
  - **Tillåtet**: Användarna får använda gemener i PIN-koden, men det krävs inte.
  - **Krävs**: Användarna måste inkludera minst en gemen i PIN-koden. Det är till exempel vanligt att man kräver minst en versal och ett specialtecken.

- **Versaler i PIN-koden**: Du kan tillämpa en starkare PIN-kod genom att kräva att slutanvändarna använder stora bokstäver. Alternativen är:

  - **Inte tillåtet** (standard): blockera användare från att använda versaler i PIN-koden. Denna inställning tillämpas även när inställningen inte har konfigurerats.
  - **Tillåtet**: Användarna får använda versaler i PIN-koden, men det krävs inte.
  - **Krävs**: Användarna måste inkludera minst en versal i PIN-koden. Det är till exempel vanligt att man kräver minst en versal och ett specialtecken.

- **Specialtecken i PIN-koden**: Du kan tillämpa en starkare PIN-kod genom att kräva att slutanvändarna använder specialtecken. Alternativen är:

  - **Inte tillåtet** (standard): blockera användare från att använda specialtecken i PIN-koden. Denna inställning tillämpas även när inställningen inte har konfigurerats.
    Exempel på specialtecken är: `! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~`
  - **Tillåtet**: Användarna får använda versaler i PIN-koden, men det krävs inte.
  - **Krävs**: Användarna måste inkludera minst en versal i PIN-koden. Det är till exempel vanligt att man kräver minst en versal och ett specialtecken.

- **PIN-kodens giltighetstid (dagar)**: Det tillhör god praxis att ange en giltighetstid för en PIN-kod varefter användarna måste ändra den. Standarden är 41 dagar.

- **Spara PIN-kodshistorik**: begränsar återanvändning av tidigare PIN-koder. Standardvärdet är att de 5 senaste PIN-koderna inte kan återanvändas.  
- **Aktivera återställning av PIN-kod**: Gör att användaren kan ändra sin PIN-kod med hjälp av tjänsten för återställning av PIN-kod i Windows Hello för företag.

       - **Enable**: The cloud service encrypts a PIN recovery secret to store on the device. The user can change their PIN if needed.  
       - **Not configured** (default): A PIN recovery secret is not created or stored. If the user's PIN is forgotten, the only way to get a new PIN is by deleting the existing PIN and creating a new one. The user will need to re-register with any services the old PIN provided access to.  

- **Använd en Trusted Platform Module (TPM)**: Ett TPM-chip ger ett ytterligare lager med datasäkerhet. Välj ett av följande värden:  
  - **Aktivera**: Endast enheter med en tillgänglig TPM kan etablera Windows Hello för företag.
  - **Inte konfigurerat**: Alla enheter kan etablera Windows Hello för företag, även om det inte finns någon användbar TPM. Enheterna försöker först använda TPM, men om ingen är tillgänglig kan enheterna använda programvarukryptering.  

- **Tillåt biometrisk autentisering**: Aktiverar biometrisk autentisering, t.ex. ansiktsigenkänning eller fingeravtryck, som ett alternativ till PIN-koden för Windows Hello för företag. Användarna måste ändå konfigurera en PIN-kod om den biometriska autentiseringen skulle misslyckas. Välj mellan:

  - **Aktivera**: Windows Hello för företag tillåter biometrisk autentisering.
  - **Inte konfigurerat** (standard): Windows Hello för företag förhindrar biometrisk autentisering (för alla kontotyper).

- **Använd utökat skydd mot förfalskning när det är tillgängligt**: Välj om skydd mot förfalskning funktionerna i Windows Hello används på enheter som stöds. Till exempel att identifiera ett foto av ett ansikte, i stället för ett riktigt ansikte.

  - **Aktivera**: Windows kräver att alla användare använder skydd mot förfalskning för ansiktsdrag när detta stöds.  
  - **Inte konfigurerad** (standard): Windows godkänner konfigurationerna som skydd mot förfalskning på enheten.

- **Certifikat för lokala resurser**: 

  - **Aktivera**: Tillåter att Windows Hello för företag använder certifikat för att autentisera mot resurser lokalt.
  - **Inte konfigurerad** (standard): Förhindrar att Windows Hello för företag använder certifikat för att autentisera mot resurser lokalt. Använd i stället enheter standardbeteendet för *nyckel-förtroende på lokal autentisering*. Mer information finns i [användarcertifikat för lokal autentisering](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings#use-certificate-for-on-premises-authentication) i Windows Hello-dokumentationen.  
## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).