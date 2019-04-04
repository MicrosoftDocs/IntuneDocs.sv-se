---
title: Utbildningsinställningar för Windows 10 i Microsoft Intune – Azure | Microsoft Docs
description: Se en lista över alla utbildningsinställningar för Windows 10-enheter. Använd de här inställningarna i en konfigurationsprofil för enheter med appen Gör ett prov, välj hur användare eller elever loggar in, övervaka skärmen under provet och mer i Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 206bc3276f3c175fe61852f235c722b835ad60b4
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57564864"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>Konfigurera appen Gör ett prov på Windows 10-enheter med Intune

Den här artikeln visar alla appinställningar för Gör ett test i Microsoft Intune som du kan konfigurera på enheter som kör Windows 10 och senare. Elever kan med appen logga in på en enhet och göra ett prov.

Dessa inställningar läggs till en profil för enhetskonfiguration som sedan tilldelas eller distribueras till dina enheter med Microsoft Intune.

[Appen Gör ett prov i Intune](education-settings-configure.md) har mer information om den här funktionen.

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en enhetskonfigurationsprofil](education-settings-configure.md#create-a-device-profile).

## <a name="take-a-test-settings"></a>Inställningar för Gör ett prov

- **Kontotyp**: Välj hur användare loggar in på provet. Alternativen är:
  - Azure AD-konto
  - Domänkonto
  - Lokalt konto
- **Kontoanvändarnamn**: Ange användarnamnet för det konto som används med appen Gör ett prov. Du kan ange konton i följande format:
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **Utvärderings-URL**: Ange URL:en till det prov som du vill att användarna ska göra. Mer information om hur du hämtar webbadressen finns i [dokumentationen för Gör ett prov](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).
- **Skärmövervakning**: Välj **Tillåt** för att övervaka skärmaktiviteten medan användarna gör provet. **Inte konfigurerad** förhindrar dig från att övervaka skärmen under provet.
- **Textförslag**: Välj **Tillåt** så kan provdeltagarna se textförslag. **Inte konfigurerat** blockerar textförslag medan användarna gör ett prov.

## <a name="next-steps"></a>Nästa steg

Profilen skapas, men den kanske inte gör något än. Kom ihåg att [tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).