---
title: Integrera Check Point SandBlast MTD
titleSuffix: Microsoft Intune
description: Konfigurera CheckPoint SandBlast Mobile Threat Defense (MTD) med Intune för att styra mobil enhetsåtkomst till företagets resurser.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1e9b1576-b239-48cc-a672-da6b5fb7be0a
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3c3c19c927618cec4b5cb55eb08f097ea21ebc47
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722832"
---
# <a name="integrate-check-point-sandblast-mobile-with-intune"></a>Integrera Check Point SandBlast Mobile med Intune

## <a name="before-you-begin"></a>Innan du börjar

> [!NOTE] 
> Stegen nedan måste utföras i [Check Point SandBlast Mobile MTD-konsolen](https://intune-4.eu1.locsec.net/).

Kontrollera att du har följande innan du börjar integrera Check Point SandBlast Mobile med Intune:

- Microsoft Intune-prenumeration

- Azure Active Directory-administratörsautentiseringsuppgifter som beviljar följande behörigheter:

  - Logga in och läsa användarprofil

  - Gå till katalogen som den inloggade användaren

  - Läs katalogdata

  - Skicka enhetsinformation till Intune

- Administratörsautentiseringsuppgifter för åtkomst till Check Point SandBlast Mobile MTD-konsolen.

### <a name="check-point-sandblast-app-authorization"></a>Check Point SandBlast-appauktorisering

Check Point SandBlast-appauktoriseringsprocessen består av följande steg:

- Tillåt att Check Point SandBlast Mobile-tjänsten kommunicerar information om enhetens hälsostatus till Intune.

- CheckPoint SandBlast Mobile fyller enhetens databas genom att synkronisera med Azure AD-registreringsgruppmedlemskap.

- Tillåt att Check Point SandBlast-administratörskonsolen använder enkel inloggning för Azure AD.

- Tillåt att Check Point SandBlast Mobile-appen loggar in med enkel inloggning för Azure AD.

## <a name="to-set-up-check-point-sandblast-mobile-integration"></a>Så här konfigurerar du Check Point SandBlast Mobile-integrationen

1. Gå till [Check Point SandBlast Mobile MTD-konsolen](https://intune-4.eu1.locsec.net/) och logga in med dina autentiseringsuppgifter.

2. Klicka på fliken **Inställningar**.

3. Välj **Enhetshantering** och sedan **Inställningar**.

4. Välj **Microsoft Intune** i listrutan **MDM Service** (MDM-tjänst).

5. När du har angett Microsoft Intune som MDM-tjänsten visas fönstret **Microsoft Intune Configuration** (Microsoft Intune-konfiguration). Välj **Add to my organization** (Lägg till i min organisation) för respektive enhetsplattform – iOS, Android och Windows – för att ge Check Point SandBlast Mobile tillstånd att kommunicera med Intune och Azure AD.

    ![Bild som visar Check Point MTD Intune-konfiguration](./media/checkpoint-sandblast-mobile-mtd-connector-integration/checkpoint-MTD-1.PNG)

    > [!IMPORTANT]
    > Du måste lägga till alla enhetsplattformar innan du kan fortsätta till nästa steg.

6. Välj **Acceptera** för att ge Check Point SandBlast Mobile-appen tillstånd att kommunicera med Intune och Azure Active Directory.

7. När du har aktiverat alla enhetsplattformar måste du ange Azure AD-säkerhetsgruppen.

8. Välj **Verifiera** och välj sedan **Spara** när Azure AD-säkerhetsgruppen har verifierats.

## <a name="next-steps"></a>Nästa steg

- [Konfigurera Check Point SandBlast Mobile-appar](mtd-apps-ios-app-configuration-policy-add-assign.md)