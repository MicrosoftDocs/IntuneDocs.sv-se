---
title: "VPN-inställningar i Intune för macOS-enheter"
titleSuffix: Intune on Azure
description: "Lär dig mer om de Intune-inställningar som du kan använda för att konfigurera VPN-anslutningar på macOS-enheter.”"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d203a70d-37df-4195-85f7-ad5ef14ac2a1
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 83e3776aacbddc37e5e7586d8fd7580143dead64
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="vpn-settings-for-macos-devices-in-microsoft-intune"></a>VPN-inställningar för macOS-enheter i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Beroende på vilka inställningar du väljer, är inte alla värden i listan nedan konfigurerbara.

## <a name="base-vpn-settings"></a>**Grundläggande VPN-inställningar**

**Anslutningsnamn** – Ange ett namn på anslutningen. Slutanvändarna ser det här namnet när de bläddrar på enheten i listan över tillgängliga VPN-anslutningar.
- **IP-adress eller FQDN** – Ange IP-adress eller fullständigt domännamn för den VPN-server som enheterna ska ansluta till. Exempel: **192.168.1.1**, **vpn.contoso.com**.
- **Autentiseringsmetod** – Välj hur enheter ska autentiseras mot VPN-servern från:
    - **Certifikat** – Under **Autentiseringscertifikat** väljer du den SCEP- eller PKCS-certifikatprofil som du skapade tidigare för att autentisera anslutningen. Mer information om certifikatprofiler finns i [Så här konfigurerar du certifikat](certificates-configure.md).
    - **Användarnamn och lösenord** – Slutanvändare måste ange ett användarnamn och lösenord för att logga in på VPN-servern.
- **Anslutningstyp** – Välj VPN-anslutningstyp från leverantörslistan nedan:
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **Anpassat VPN**
- **Delade tunnlar** - **Aktivera** eller **Inaktivera** detta alternativ för att låta enheterna bestämma vilken anslutning som ska användas beroende på trafiken. En användare på ett hotell kan till exempel använda VPN-anslutningen för att komma åt arbetsfiler, men använda hotellets standardnätverk för vanlig webbsurfning.

<!--- **Per-app VPN** - Select this option if you want to associate this VPN connection with an iOS or macOS app so that the connection will be opened when the app is run. You can associate the VPN profile with an app when you assign the software. For more information, see [How to assign and monitor apps](apps-deploy.md). --->

## <a name="custom-vpn-settings"></a>Anpassade VPN-inställningar

Om du har valt **Anpassat VPN** kan du konfigurera inställningarna ytterligare:

- **VPN-ID** Detta är en identifierare för VPN-appen som du använder och den tillhandahålls av VPN-leverantören.
- **Ange nyckel/värdepar för de anpassade VPN-attributen** Lägg till eller importera **Nycklar** och **Värden** som anpassar VPN-anslutningen. Även dessa värden tillhandahålls vanligtvis av VPN-leverantören.


## <a name="proxy-settings"></a>Proxyinställningar

- **Skript för automatisk konfigurering** – Använd en fil för att konfigurera proxyservern. Ange den **webbadress till proxyserver** (till exempel **http://proxy.contoso.com**) som innehåller konfigurationsfilen.
- **Adress** – Ange proxyns serveradress (som en IP-adress).
- **Portnummer** – Ange det portnummer som är kopplat till proxyservern.