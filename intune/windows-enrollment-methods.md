---
title: Intune-registreringsmetoder för Windows-enheter
titleSuffix: Microsoft Intune
description: Lär dig de olika sätten att registrera Windows-enheter i Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/02/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: ''
ms.openlocfilehash: 346b74871b7519e03ca3e68061f690ef1a4e6d6a
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61514794"
---
# <a name="intune-enrollment-methods-for-windows-devices"></a>Intune-registreringsmetoder för Windows-enheter

För att enheter ska hanteras i Intune måste de först registreras i Intune-tjänsten. Både personligt ägda och företagsägda enheter kan registreras för Intune-hantering. 

Det finns två sätt att hämta enheter som registrerats i Intune:
- Användare kan registrera sina Windows-datorer på egen hand 
- Administratörer kan konfigurera principer för att framtvinga automatisk registrering utan inblandning av användare

## <a name="user-self-enrollment-in-intune"></a>Självregistrering i Intune av användare

Användare kan själva registrera sina Windows-enheter med hjälp av någon av dessa metoder:

- [BYOD (Bring Your Own Device)](https://docs.microsoft.com/intune-user-help/enroll-windows-10-device): Användarna registrerar sina personligt ägda enheter genom att välja att ansluta ett **arbets- och skolkonto** från enhetens **inställningar**. Den här processen:
    - Registrerar enheten med Azure Active Directory för att få åtkomst till företagsresurser såsom e-post.
    - Registrerar enheten i Intune som en personligt ägd enhet (BYOD).
Om en administratör har konfigurerat automatisk registrering (tillgängligt med Azure AD Premium-prenumerationer) behöver användaren bara ange sina autentiseringsuppgifter en gång. Annars behöver användaren registrera separat via registrering med endast MDM och ange autentiseringsuppgifterna på nytt.  
- **Registrering med endast MDM** gör att användarna kan registrera en befintlig arbetsgrupp, Active Directory eller Azure Active Directory-ansluten dator till Intune. Användare registrerar från inställningarna på den befintliga Windows-datorn. Den här metoden rekommenderas inte eftersom den inte registrerar enheten till Azure Active Directory. Den förhindrar även användningen av funktioner som villkorsstyrd åtkomst.
- [Azure Active Directory-anslutning (Azure AD)](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network) – ansluter enheten till Azure Active Directory och gör att användarna kan logga in på Windows med sina Azure AD-autentiseringsuppgifter. Om automatisk registrering har aktiverats registreras enheten automatiskt i Intune. Fördelen med automatisk registrering är att användarna får en enstegsprocess. Annars behöver användaren registrera separat via registrering med endast MDM och ange autentiseringsuppgifterna på nytt. Användarna registrerar på det här sättet antingen under det inledande Windows-välkomstprogrammet (OOBE) eller från Inställningar. Enheten har markerats som en företagsägd enhet i Intune.
- [Autopilot](enrollment-autopilot.md) – automatiserar Azure AD-anslutning och registrerar nya företagsägda enheter till Intune. Den här metoden förenklar välkomstprogrammet och eliminerar behovet av att tillämpa anpassade operativsystemavbildningar på enheterna. När administratörer använder Intune för att hantera Autopilot-enheter kan de hantera principer, profiler, appar med mera när de har registrerats.  Det finns två typer av Autopilot-distributioner: [Självdistribuerande läge ](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying) (för kiosker, digital signering eller en delad enhet) och [Användarläge](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) (för traditionella användare). 

## <a name="administrator-based-enrollment-in-intune"></a>Administratörbaserad registrering i Intune

Administratörer kan konfigurera följande metoder för registrering som inte kräver användarinteraktion:

- [Azure AD-hybridanslutning](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy) gör att administratörer kan konfigurera Active Directory-grupprincip till att automatiskt registrera enheter som är Azure AD-hybridanslutna. 
- [Configuration Manager-samhantering](https://docs.microsoft.com/sccm/comanage/overview) gör att administratörer kan registrera sina befintliga hanterade Configuration Manager-enheter till Intune för att få de dubbla fördelarna med Intune och Configuration Manager. 
- [Hanterare av enhetsregistrering](device-enrollment-manager-enroll.md) (DEM) är ett särskilt tjänstkonto. DEM-konton behörigheter som gör att behöriga användare kan registrera och hantera flera företagsägda enheter. Dessa typer av enheter är till exempel bra för verktygs- eller kassaappar (Point-of-Sale), men inte för användare som behöver åtkomst till e-post eller företagsresurser. Den här metoden låter heller inte användning av funktioner såsom villkorsstyrd åtkomst. 
- [Massregistrering](windows-bulk-enroll.md) gör att en behörig användare kan ansluta ett stort antal nya företagsägda enheter till Azure Active Directory och Intune. Du skapar ett etableringspaket med hjälp av appen Windows Configuration Designer (WCD). Sedan använder du en USB-enhet under det inledande Windows-välkomstprogrammet (OOBE) eller från en befintlig Windows-dator för att installera etableringspaketet till att automatiskt registrera enheterna till Intune. 

## <a name="next-steps"></a>Nästa steg

[Lär dig mer om funktionerna i Windows-registreringsmetoderna](enrollment-method-capab.md)