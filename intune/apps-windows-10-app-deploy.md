---
title: Windows 10-appdistribution med hjälp av Microsoft Intune
titlesuffix: ''
description: Läs mer om Windows 10-appscenarier som är tillgängliga med Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: abebfb5e-054b-435a-903d-d1c31767bcf2
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0bffb0ab4003cc02ceddcd0199b951113ff1e4fd
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321852"
---
# <a name="windows-10-app-deployment-using-microsoft-intune"></a>Windows 10-appdistribution med hjälp av Microsoft Intune 

Microsoft Intune har för närvarande stöd för en mängd olika typer av appar och distributionsscenarier på Windows 10-enheter. När du har lagt till en app till Intune kan du tilldela appen till användare och enheter. Följande information innehåller mer detaljer om de Windows 10-scenarier som stöds. Dessutom innehåller följande information viktiga punkter att tänka på när du distribuerar appar till Windows. 

Verksamhetsspecifika appar (LOB) och Microsoft Store för företag-appar är de typer av appar som stöds på Windows 10-enheter. Filnamnstillägg för Windows-appar omfattar **.msi**, **.appx**, **.appxbundle**, **.msix** och **.msixbundle**.  

> [!Note]
> Den minsta nödvändiga Windows 10-uppdateringen för att distribuera appar i enhetssammanhang är [May 23, 2018—KB4100403 (OS Build 17134.81)](https://support.microsoft.com/en-us/help/4100403/windows-10-update-kb4100403).

## <a name="windows-10-line-of-business-apps"></a>Verksamhetsspecifika Windows 10-appar

Verksamhetsspecifika Windows 10-appar signeras och laddas upp till Intune-administratörskonsolen och kan innefatta både moderna appar, till exempel Universal Windows Platform-appar (UWP) och Windows-appaket (AppX), och Win 32-appar såsom enkla Microsoft Installer-paketfiler (MSI). Uppdateringar av verksamhetsspecifika appar måste laddas upp och distribueras manuellt varje gång av administratören. Uppdateringar som distribueras installeras automatiskt på slutanvändarenheter med appen installerad utan åtgärd från användaren. Användaren har ingen kontroll över uppdateringarna. 

## <a name="microsoft-store-for-business-apps"></a>Microsoft Store för företag-appar

Microsoft Store för företag-appar är moderna appar som har köpts från Microsoft Store för företag-adminportalen och sedan synkroniserats över till Microsoft Intune för hantering. Apparna kan antingen vara **onlinelicensierade** eller **offlinelicensierade**. Uppdateringar av Microsoft Store för företag-appar hanteras direkt av Microsoft Store utan att ytterligare åtgärd krävs av administratören. Administratören kan även förhindra uppdateringar till specifika appar med hjälp av anpassad URI (Uniform Resource Identifier). Mer information finns på sidan om [Enterprise-apphantering – förhindra automatiska uppdateringar för appen](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates). På enheten kan slutanvändaren även inaktivera uppdateringar för alla Microsoft Store för företag-appar på enheten. 

## <a name="installing-apps-on-windows-10-devices"></a>Installera appar på Windows 10-enheter
Beroende på apptypen kan appen installeras på en Windows 10-enhet på ett av två sätt:

- **Användarkontext**: När en app distribueras i användarkontext installeras den hanterade appen för den användaren på enheten när användaren loggar in på enheten. Observera att installationen av appen inte lyckas förrän användaren loggar in på enheten. 
    - Moderna verksamhetsspecifika appar och Microsoft Store för företag-appar (både online och offline) kan distribueras i användarkontext och stöder både avsikten Krävs och Tillgänglig.
- **Enhetskontext**: När en app distribueras i enhetskontext installeras den hanterade appen direkt till enheten av Intune.
    - Endast moderna verksamhetsspecifika appar och onlinelicensierade Microsoft Store för företag-appar kan distribueras i enhetskontext och stöder endast avsikten Krävs.

> [!Note]
> Distribuering av MSI över MDM i enhetskontext stöds ännu inte på Windows 10-enheter.

När en app distribueras i enhetskontext lyckas endast installationen när den riktas till en enhet som stöder enhetskontext. Dessutom stöder distribuering i enhetskontext dessutom följande villkor:
- Om en app distribueras i enhetskontext och riktas mot en användare kommer installationen att misslyckas med följande status och fel som visas i administratörskonsolen:
    - Status: Failed (Misslyckades).
    - Error: A user can’t be targeted with a Device context install. (Fel: En användare kan inte riktas till med en enhetskontextinstallation.)
- Om en app distribueras i enhetskontext men riktas mot en enhet som inte stöder enhetskontext kommer installationen att misslyckas med följande status och fel i administratörskonsolen:
    - Status: Failed (Misslyckades).
    - Error: This platform does not support device context installs. (Fel: Den här plattformen stöder inte enhetskontextinstallation.) 

> [!Note]
> När en apptilldelning sparas med en specifik distribution går det inte att ändra kontexten för den tilldelningen förutom för moderna appar. I fallet med moderna appar går det att ändra kontexten från användarkontext till enhetskontext. 

I händelse av att det finns en konflikt i principer på en enskild användare/enhet används följande principprioriteringar för att avgöra den slutliga principen:
- En enhetskontextprincip är en högre prioritet än en användarkontextprincip. 
- En installationsprincip är en högre prioritet än en avinstallationsprincip.

Mer information om hur du tilldelar appar med hjälp av Microsoft Intune finns i [Tilldela appar till grupper med Microsoft Intune](apps-deploy.md) och [Inkludera och exkludera apptilldelningar i Microsoft Intune](apps-inc-exl-assignments.md). Mer information om apptyper i Intune finns i [Lägg till appar i Microsoft Intune](apps-add.md).

## <a name="next-steps"></a>Nästa steg

- Mer information om hur du tilldelar appar till grupper finns i [Tilldela appar till grupper med Microsoft Intune](apps-deploy.md).
- Mer information om hur du övervakar apptilldelningar finns i [Hur du övervakar appar](apps-monitor.md).