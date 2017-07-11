---
title: Vilka enhetsprofiler finns i Microsoft Intune? | Microsoft Docs
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Mer information om enhetsprofiler i Intune och hur de kan hjälpa dig att hantera och skydda enheter i företaget."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/16/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 54b20d405613a67e54e9d22df45a3055f093fafa
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="what-are-microsoft-intune-device-profiles"></a>Vad är enhetsprofiler i Microsoft Intune?

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Använd arbetsbelastningen **Enhetskonfiguration** i Microsoft Intune för att hantera inställningar och funktioner på alla enheter som du hanterar. Du kommer mest att använda den här arbetsbelastningen för att skapa enhetsprofiler som låter dig hantera och kontrollera en rad olika funktioner på enheter som du hanterar.

När du öppnar den här arbetsbelastningen ser du följande alternativ:

- **Översikt** – På den här sidan kan du se status och rapporter som hjälper dig övervaka enhetskonfigurationer som du har tilldelat till användare och enheter.
- **Hantera profiler** – Det här avsnittet används för att skapa konfigurationsprofiler för enheten. Nedan finns en lista med alla profiltyper som du kan skapa.
- **Konfigurera certifikatutfärdare** – Arbetsflödet vägleder dig genom de steg som krävs för att konfigurera certifikat. Du måste göra detta om du vill använda Intunes certifikatprofiler.

## <a name="getting-started"></a>Komma igång

Arbetsflödet för att skapa enhetsprofiler är likadant för alla profiler. Läs [Så här skapar du enhetskonfigurationsprofiler i Microsoft Intune](device-profile-create.md) för information om hur du skapar profiler. Läs vidare för specifik information om att skapa inställningar för varje profiltyp.

Du kan hantera följande funktioner på dina enheter:

## <a name="device-features"></a>Enhetsfunktioner

Med enhetsfunktioner kan du styra funktioner på iOS- och macOS-enheter, som t.ex. AirPrint, meddelanden och delade enhetskonfigurationer.
Mer information finns i [Så här konfigurerar du inställningar för enhetsfunktioner](device-features-configure.md) Har stöd för: iOS och macOS.

## <a name="device-restrictions"></a>Enhetsbegränsningar
Med enhetsbegränsningar kan du styra en mängd olika inställningar för enheter som du hanterar i flera kategorier, bland annat säkerhet, webbläsare, maskinvara och datadelning. Du kan till exempel skapa en profil för enhetsbegränsningar som förhindrar användare av iOS-enheter från att komma åt kameran på enheten.
Mer information finns i [Så här konfigurerar du inställningar för enhetsbegränsningar](device-restrictions-configure.md) Stöder: Android, iOS, macOS, Windows 10 och Windows 10 Team.

## <a name="email"></a>E-post
Med e-postprofiler kan du skapa, tilldela och övervaka e-postinställningarna för Exchange ActiveSync på enheterna som du hanterar. Genom att tilldela inställningarna uppnår du konsekvens, minskar supportsamtalen och ger slutanvändarna åtkomst till företagets e-post på sina personliga enheter utan de behöver konfigurera något själva.
Mer information finns i [Så här konfigurerar du e-postinställningar](email-settings-configure.md) Stöder: Android, iOS, Windows 8.1 och Windows 10.

## <a name="wi-fi"></a>Wi-Fi
Använd trådlösa profiler för att tilldela trådlösa nätverksinställningar till användare och enheter i din organisation. När du tilldelar en Wi-Fi-profil får användarna åtkomst till ditt företags trådlösa nätverk utan att de behöver göra några inställningar själva.
Mer information finns i [Så här konfigurerar du trådlösa inställningar](wi-fi-settings-configure.md) Stöder: Android, iOS, macOS och Windows 8.1 (endast import).

## <a name="vpn"></a>VPN
Virtuella privata nätverk (VPN, Virtual Private Networks) ger användarna säker fjärråtkomst till företagets nätverk. Enheterna använder en profil för VPN-anslutning för att initiera en anslutning till VPN-servern. Använd VPN-profiler för att tilldela VPN-inställningar till användare och enheter i din organisation, så att de enkelt och säkert kan ansluta till nätverket.
Mer information finns i [Så här konfigurerar du VPN-inställningar](vpn-settings-configure.md).
Stöder: Android, iOS, macOS, Windows Phone 8.1, Windows 8.1 och Windows 10.

## <a name="education"></a>Utbildning
Konfigurera alternativ för Windows Gör ett prov-app. När du konfigurerar dessa alternativ kan inga andra appar köras på enheten förrän provet har slutförts.
Mer information finns i [Så här konfigurerar du utbildningsinställningar](education-settings-configure.md)

## <a name="certificates"></a>Certifikat
Med den här profiltypen kan du konfigurera betrodda, SCEP- och PKCS-certifikat som kan tilldelas till enheter och användas för att autentisera trådlösa profiler, VPN- och e-postprofiler.
Mer information finns i [Så här konfigurerar du certifikat](certificates-configure.md) Stöder: Android, iOS, Windows Phone 8.1, Windows 8.1 och Windows 10.

## <a name="edition-upgrade"></a>Versionsuppgradering
Med den här profiltypen kan du automatiskt uppgradera enheter som kör vissa versioner av Windows 10 till en nyare version. För mer information, se [Så här konfigurerar du Windows 10-uppgraderingar](edition-upgrade-configure-windows-10.md) Stöder: endast Windows 10.

## <a name="windows-information-protection"></a>Windows informationsskydd
Windows informationsskydd bidrar till att skydda mot dataläckage utan att störa medarbetarnas användning. Informationsskyddet skyddar även företagsappar och företagsdata mot oavsiktliga dataläckage i företagsägda enheter och personliga enheter som medarbetarna tar med sig till jobbet utan att det behövs några ändringar i miljön eller andra appar.
Mer information finns i [Så här konfigurerar du Windows informationsskydd](windows-information-protection-configure.md) Stöder: endast Windows 10.

## <a name="custom"></a>Anpassad
Med anpassade inställningar kan du tilldela enhetsinställningar som inte är inbyggda i Intune. Du kan till exempel ange OMA-URI-värden som konfigurerar Android-enheter. På iOS-enheter kan du importera en konfigurationsfil som du har skapat i Apple Configurator.
Mer information finns i [Så här konfigurerar du anpassade inställningar](custom-settings-configure.md) Stöder: Android, iOS, macOS och Windows Phone 8.1.
