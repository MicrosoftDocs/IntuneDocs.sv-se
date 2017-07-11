---
title: "Grundläggande Intune-konfiguration"
description: "Syftet med den här artikeln är att tillhandahålla nödvändiga åtgärder för hur du konfigurerar Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 60cfa440-0723-4ea0-bacf-3c5d26f9a1d3
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: c3129b2a8d93e91493455da5f3e5fd1a59dd77bb
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="basic-setup"></a>Grundläggande konfiguration

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

När du utvärderat miljön är det dags att konfigurera Intune.

## <a name="external-dependencies-for-an-intune-deployment"></a>Externa beroenden för en Intune-distribution

### <a name="identity"></a>Identitet

Intune kräver Azure Active Directory (AAD) som leverantör av identitet och användargruppering.

-   Läs mer om [identitetskrav](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview).

-   Läs mer om [katalogsynkroniseringskrav](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements).

-   Läs mer om [krav för multifaktorautentisering](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements).

-   Läs mer om att [planera användar- och enhetsgrupper](/intune/users-permissions-add).

-   Läs om att [skapa användar- och enhetsgrupper](/intune/groups-get-started).

Om företaget redan använder Office 365 är det viktigt att Intune använder samma Azure Active Directory-miljö.

### <a name="pki-optional"></a>PKI (valfritt)

Om du planerar att använda certifikatbaserad autentisering för VPN-, Wi-Fi- eller e-postprofiler med Intune måste du kontrollera att du har en [PKI-infrastruktur på plats](/intune/certificates-configure) som stöds och är redo att skapa och distribuera certifikatprofiler.

Mer information om hur man konfigurerar certifikat i Intune finns nedan.

-   [Konfigurera certifikatinfrastruktur för SCEP](/intune/certificates-scep-configure).

-   [Konfigurera certifikatinfrastruktur för PFX](/intune/certficates-pfx-configure).


## <a name="task-list-for-an-intune-setup"></a>Uppgiftslista för en Intune-installation

### <a name="task-1-intune-subscription"></a>Uppgift 1: Intune-prenumeration

Innan du kan migrera till Intune måste du ha en Intune-prenumeration.

-   Du kan besöka [den här sidan](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0). Här får du anvisningar om hur du kan:

    -   Skapa en ny Intune-prenumeration som är länkad till en ny AAD-klient.

    -   Länka Intune-prenumerationen genom att logga in till en befintlig AAD-klient.

### <a name="task-2-assign-intune-user-licenses"></a>Steg 2: Tilldela Intune-användarlicenser

-   Lär dig [hur man tilldelar Intune-användarlicenser](licenses-assign.md).

-   Om du har skapat en ny Azure Active Directory-klient kan du läsa om [hur du kan skapa nya användare eller synkronisera användare från din lokala Active Directory (AD).](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)

### <a name="task-3-set-your-mdm-authority-to-intune"></a>Uppgift 3: Konfigurera Intune som utfärdare för hantering av mobilenheter

Du kan hantera Intune via Azure Portal eller konsolen Configuration Manager Current Branch. Såvida du inte behöver integrera Intune med en Configuration Manager Current Branch-distribution så rekommenderar vi att du hanterar Intune från [Azure Portal](https://portal.azure.com).

Aktivera Intune Azure Portal genom att ange **Intune** som utfärdare för hantering av mobilenheter. Genom att använda en annan utfärdare för hantering av mobilenheter kan du låta Intune överföra hanteringen av mobilenheter till alternativa Microsoft-hanteringskonsoler. Dessa fall är ovanliga.

> [!IMPORTANT]
> Om du överför hanteringen av mobila enheter till Intune för första gången måste du ange Intune som utfärdare för hantering av mobilenheter.

-   Lär dig hur [man anger utfärdare för hantering av mobilenheter](/intune/mdm-authority-set).

## <a name="next-step"></a>Nästa steg

[Konfigurera principer för enhets- och apphantering](migration-guide-configure-policies.md)