---
title: "Välj hur du vill registrera iOS-enheter i Intune | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Läs om hur du konfigurerar registrering av iOS-enheter i Microsoft Intune."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 12/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6c0a430-1851-4108-812a-87e0fc2623b5
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: c228601451b33238d0f6929987dcdec3a5e56e8d


---

# <a name="choose-how-to-enroll-ios-devices"></a>Välj hur du vill registrera iOS-enheter

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

I det här avsnittet beskrivs de metoder som du kan använda för att registrera iOS-enheter och vilka krav som gäller för registrering.

Använd följande information när du ska bestämma vilken metod som ska användas för att registrera iOS-enheter. Alla av de följande metoderna, förutom BYOD, är avsedda för registrering av företagsägda enheter.

**Krav:** Ett [certifikat för Apple Push Notification Service](get-an-apple-mdm-push-certificate.md) krävs.

## <a name="user-owned-ios-devices-byod"></a>Användarägda iOS-enheter (BYOD)

Om användarna vill registrera sina personliga BYOD-enheter, så är den enda tillgängliga registreringsmetoden att användarna hämtar företagsportalappen för iOS från App Store och följer registreringsanvisningarna i appen. När registreringen är klar kan användarna ansluta till företagets nätverk, ansluta till domänen eller Azure Active Directory och få åtkomst till företagets resurser.

## <a name="apple-configurator"></a>Apple Configurator

Du kan registrera iOS-enheter genom att exportera en företagsregistreringsprofil och sedan ansluta de mobila enheterna till en Mac som kör [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017). Apple Configurator stöder två typer av registrering:

- **Registrering av installationsassistenten**: Återställer enheten till fabriksinställningarna och förbereder den för installation av enhetens nya användare. Den här metoden kräver att administratören ansluter iOS-enheten via USB till en Mac-dator som kör Apple Configurator så att registreringen kan förkonfigureras. Enheterna levereras sedan till de användare som kör installationsassistensprocessen. Den här processen konfigurerar enheten med användarnas autentiseringsuppgifter arbetet eller skolan och slutför registreringen. Mer information finns i [Registrera iOS-enheter med Apple Configurator och installationsassistenten](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md).

- **Direktregistrering**: Skapar en Apple Configurator-kompatibel fil som används vid förberedelse av enheten. Den registrerade enheten är inte fabriksåterställd, och den har ingen anknytning till användaren. För att kunna registrera enheter krävs det att administratören ansluter iOS-enheten via USB till en Mac-dator som kör Apple Configurator. Mer information finns i [Registrera iOS-enheter som använder direktregistrering i Apple Configurator](enroll-ios-devices-with-apple-configurator-and-direct-enrollment.md).

## <a name="use-the-device-enrollment-program-dep"></a>Använd enhetsregistreringsprogrammet (DEP)

DEP distribuerar en registreringsprofil trådlöst till enheter som köpts via DEP. Enheten registreras i Intune när användaren kör installationsassistenten på enheten. Enheter som har registrerats via DEP kan inte avregistreras av användarna. Mer information finns i [Registrera iOS-enheter med enhetsregistreringsprogrammet](enroll-ios-devices-using-device-enrollment-program.md).

## <a name="use-the-device-enrollment-manager-dem"></a>Använda enhetsregistreringshanteraren (DEM)
Enhetsregistreringshanteraren är en typ av användarkonto som kan registrera upp till 1 000 enheter. Du kan lägga till befintliga användare till DEM-kontot för att ge dem dessa funktioner. Varje enhet som DEM-användaren registrerar använder en enda Intune-licens. Mer information finns i [Registrera enheter med enhetsregistreringshanteraren](enroll-devices-using-device-enrollment-manager.md).



<!--HONumber=Feb17_HO1-->

