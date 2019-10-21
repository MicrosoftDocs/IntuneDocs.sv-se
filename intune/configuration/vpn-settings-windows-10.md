---
title: Windows 10 VPN-inställningar i Microsoft Intune – Azure | Microsoft Docs
description: Läs om alla tillgängliga VPN-inställningar i Microsoft Intune, vad de används till och vad de gör, inklusive trafikregler, villkorlig åtkomst samt DNS- och proxyinställningar för Windows 10- och Windows Holographic for Business-enheter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.reviewer: tycast
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 122872eff92a37c8724fd4a853091e51a0a54c66
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506525"
---
# <a name="windows-10-and-windows-holographic-device-settings-to-add-vpn-connections-using-intune"></a>Inställningar för Windows 10- och Windows Holographic-enheter för att lägga till VPN-anslutningar med Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Du kan lägga till och konfigurera VPN-anslutningar för enheter med Microsoft Intune. Den här artikeln listar och beskriver vanliga inställningar och funktioner när virtuella privata nätverk (VPN) skapas. Dessa VPN-inställningar och -funktioner används i enhetskonfigurationsprofiler i Intune som skickas eller distribueras till enheter.

Som en del av din MDM-lösning (hantering av mobilenheter) använder du dessa inställningar till att tillåta eller inaktivera funktioner, till exempel att använda en VPN-leverantör, aktivera Alltid på, använda DNS, lägga till en proxy med mera.

Dessa inställningar gäller för enheter som kör:

- Windows 10
- Windows 10 Holographic for Business

Beroende på vilka inställningar du väljer, kanske inte alla värden är konfigurerbara.

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en VPN-enhetskonfigurationsprofil](vpn-settings-configure.md).

## <a name="base-vpn-settings"></a>Grundläggande VPN-inställningar

- **Anslutningsnamn**: Ange ett namn på anslutningen. Slutanvändarna ser det här namnet när de bläddrar på enheten i listan över tillgängliga VPN-anslutningar.
- **Servrar**: Lägg till en eller flera VPN-servrar som enheterna ska ansluta till. När du lägger till en server, anger du följande information:
  - **Beskrivning**: Ange ett beskrivande namn för servern, som t.ex. **Contoso VPN-server**
  - **IP-adress eller fullständigt domännamn**: Ange IP-adress eller fullständigt domännamn (FQDN) för den VPN-server som enheter ansluter till, exempelvis **192.168.1.1** eller **vpn.contoso.com**
  - **Standardserver**: Gör servern till den standardserver som enheterna använder för att upprätta anslutningen. Ange endast en server som standard.
  - **Importera**: Bläddra till en kommateckenavgränsad fil som innehåller en lista med servrar i formatet: beskrivning, IP-adress eller FQDN, samt standardserver. Välj **OK** för att importera dessa servrar till listan **Servrar**.
  - **Exportera**: Exporterar listan med servrar till en kommateckenavgränsad fil (csv)

- **Registrera IP-adresser med internt DNS**: Välj **Aktivera** om du vill konfigurera Windows 10 VPN-profilen för dynamisk registrering av IP-adresserna som tilldelats till VPN-gränssnittet med internt DNS. Välj **Inaktivera** om du inte vill registrera IP-adresserna dynamiskt.

- **Anslutningstyp**: Välj VPN-anslutningstypen från leverantörslistan nedan:

  - **Pulse Secure**
  - **F5 Edge Client**
  - **SonicWALL Mobile Connect**
  - **Check Point Capsule VPN**
  - **Citrix**
  - **Palo Alto Networks GlobalProtect**
  - **Automatiskt**
  - **IKEv2**
  - **L2TP**
  - **PPTP**

  När du väljer en VPN-anslutningstyp, kan du också efterfrågas om följande inställningar:  
  - **Always On**: Välj **Aktivera** för att automatiskt ansluta till VPN-anslutningen när följande händelser inträffar: 
    - Användarna loggar in på sina enheter
    - Nätverket på enheten ändras
    - Skärmen på enheten sätts på efter att ha varit avstängd 

  - **Autentiseringsmetod**: Välj hur du vill att användarna autentiseras mot VPN-servern. Med hjälp av **certifikat** får du utökade funktioner, t.ex. zero-touch-upplevelse, VPN på begäran och VPN per app.
  - **Spara autentiseringsuppgifter för varje inloggning**: välja att cachelagra autentiseringsuppgifterna.
  - **Anpassad XML**: Ange anpassade XML-kommandon som konfigurerar VPN-anslutningen.
  - **EAP XML**: Ange EAP XML-kommandon som konfigurerar VPN-anslutningen

### <a name="pulse-secure-example"></a>Pulse Secure-exempel

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

### <a name="f5-edge-client-example"></a>F5 Edge Client-exempel

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

### <a name="sonicwall-mobile-connect-example"></a>SonicWall Mobile Connect-exempel
**Inloggningsgrupp eller domän**: Den här egenskapen kan inte anges i VPN-profilen. I stället parsar Mobile Connect värdet när användarnamn och domän har angetts i formatet `username@domain` eller `DOMAIN\username`.

Exempel:

```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

### <a name="checkpoint-mobile-vpn-example"></a>Kontrollpunkt för mobilt VPN-exempel

```
<CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

### <a name="writing-custom-xml"></a>Skriva anpassad XML
Mer information om hur du skriver anpassade XML-kommandon finns i varje tillverkares VPN-dokumentation.

Läs mer om att skapa anpassade EAP XML-filer i informationen om [EAP-konfiguration](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration).

## <a name="apps-and-traffic-rules"></a>Regler för appar och trafik

- **Associera PIA eller appar med denna VPN**: Aktivera den här inställningen om du endast vill att vissa appar ska använda VPN-anslutningen. Alternativen är:

  - **Associera en PIA med den här anslutningen**: Ange en **PIA-domän för den här anslutningen**
  - **Associera appar med den här anslutningen**: Du kan **Begränsa VPN-anslutning för dessa appar** och sedan lägga till **Associerade appar**. De appar som du anger använder automatiskt VPN-anslutningen. Appidentifieraren beror på typen av app. För en universell app anger du paketfamiljenamnet. För en skrivbordsapp anger du appens filsökväg.
  >[!IMPORTANT]
  >Vi rekommenderar att du skyddar alla applistor som skapas för VPN:er per app. Om en obehörig användare ändrar listan och du importerar den till applistan med VPN:er per app, finns risken att du tillåter VPN-åtkomst till appar som inte ska ha åtkomst. Ett sätt att skydda applistor på är att använda en åtkomstkontrollista (ACL).

- **Nätverkstrafikregler för den här VPN-anslutningen**: Välj vilka protokoll, vilka lokala portar och fjärrportar, samt vilka adressintervall som ska aktiveras för VPN-anslutningen. Om du inte skapar någon regel för nätverkstrafik aktiveras alla protokoll, portar och adressintervall. När du har skapat en regel använder VPN-anslutningen bara de protokoll, portar och adressintervall som du har angett i regeln.

## <a name="conditional-access"></a>Villkorlig åtkomst

- **Villkorlig åtkomst för den här VPN-anslutningen**: Aktiverar enhetskompatibilitetsflöde från klienten. När den här inställningen är aktiverad kommunicerar VPN-klienten med Azure Active Directory (AD) för att få ett certifikat för autentisering. VPN-klienten måste vara inställd på användning av certifikatautentisering och VPN-servern måste lita på den server som returneras av Azure Active Directory.

- **Enkel inloggning (SSO) med alternativt certifikat**: Använd ett annat certifikat än VPN-autentiseringscertifikatet vid Kerberos-autentisering för att uppnå enhetskompatibilitet. Ange certifikatet med följande inställningar:

  - **Namn**: Namn för förbättrad nyckelanvändning (EKU)
  - **Objektidentifierare**: Objektidentifierare vid förbättrad nyckelanvändning
  - **Utfärdarhash**: Tumavtryck för SSO-certifikat

## <a name="dns-settings"></a>DNS-inställningar

- **Söklista för DNS-suffix**: I **DNS-suffix** anger du ett DNS-suffix och klickar sedan på **Lägg till**. Du kan lägga till många suffix.

  När du använder DNS-suffix, kan du söka efter en nätverksresurs med dess korta namn i stället för det fullständiga domännamnet (FQDN). När du söker med hjälp av det korta namnet bestäms suffixet automatiskt av DNS-servern. Till exempel finns `utah.contoso.com` med i listan över DNS-suffix. Du pingar `DEV-comp`. I det här scenariot matchas det till `DEV-comp.utah.contoso.com`.

  DNS-suffix matchas i den angivna ordningen, och ordningen kan ändras. Till exempel finns `colorado.contoso.com` och `utah.contoso.com` i DNS-suffixlistan och båda har en resurs med namnet `DEV-comp`. Eftersom `colorado.contoso.com` är först i listan matchas det som `DEV-comp.colorado.contoso.com`.
  
  Om du vill ändra ordningen klickar du på punkterna till vänster om DNS-suffixet och drar sedan suffixet längst upp:

  ![Välj de tre punkterna och klicka och dra för att flytta DNS-suffixet](./media/vpn-settings-windows-10/vpn-settings-windows10-move-dns-suffix.png)

- **NRPT-regler**: regler för namn matchnings princip tabell (NRPT) anger hur DNS matchar namn när de är anslutna till VPN. När anslutningen har upprättats kan du välja vilka DNS-servrar som ska användas av VPN-anslutningen.

  Du kan lägga till regler i tabellen som innehåller domän, DNS-server, proxy och andra detaljer för att matcha domänen du anger. VPN-anslutningen använder dessa regler när användare ansluter till de domäner du anger.

  Välj **Lägg till** för att lägga till en ny regel. För varje server anger du:

  - **Domän**: Ange det fullständiga domännamnet (FQDN) eller ett DNS-suffix för att tillämpa regeln. Du kan även ange en punkt (.) i början av ett DNS-suffix. Ange till exempel `contoso.com` eller `.allcontososubdomains.com`.
  - **DNS-servrar**: Ange den IP-adress eller DNS-server som löser domänen. Ange till exempel `10.0.0.3` eller `vpn.contoso.com`.
  - **Proxy**: Ange en webbproxyserver som löser domänen. Ange till exempel `http://proxy.com`.
  - **Anslut automatiskt**: När det här är **Aktiverat** ansluter enheten automatiskt till VPN-anslutningen när en enhet ansluter till en domän som du anger, till exempel `contoso.com`. När **Inte konfigurerad** (standard) anges ansluter enheten inte automatiskt till VPN
  - **Persistent**: När det här är inställt på **Aktiverat** blir regeln kvar i namnmatchningsprinciptabellen (NRPT) tills regeln tas bort från enheten manuellt, även efter att VPN koppas från. När det är inställt på **Inte konfigurerad** (standard) tas NRPT-regler i VPN-profilen tas bort från enheten när VPN kopplas från.

## <a name="proxy-settings"></a>Proxyinställningar

- **Skript för automatisk konfiguration**: Använd en fil för att konfigurera proxyservern. Ange **URL:n för proxyservern**, t.ex. `http://proxy.contoso.com`, som innehåller konfigurationsfilen.
- **Adress**: Ange proxyserverns adress såsom en IP-adress eller `vpn.contoso.com`
- **Portnummer**: Ange TCP-portnumret som används av proxyservern
- **Kringgå proxy för lokala adresser**: Om du inte vill använda en proxyserver för lokala adresser, välj då Aktivera. Den här inställningen gäller om VPN-servern kräver en proxyserver för anslutningen.

## <a name="split-tunneling"></a>Delade tunnlar

- **Delade tunnlar**: **Aktivera** eller **Inaktivera** för att låta enheterna bestämma vilken anslutning som ska användas beroende på trafiken. En användare på ett hotell kan till exempel använda VPN-anslutningen för att komma åt arbetsfiler, men använda hotellets standardnätverk för vanlig webbsurfning.
- **Routning för delade tunnlar för den här VPN-anslutningen**: Lägg till valfria vägar för tredje parts VPN-leverantörer. Ange ett målprefix och en prefixstorlek för varje anslutning.

## <a name="trusted-network-detection"></a>Identifiering av betrott nätverk

**DNS-suffix för betrodda nätverk**: När användarna redan är anslutna till ett betrott nätverk kan du förhindra att enheter automatiskt ansluter till andra VPN-anslutningar.

I **DNS-suffix** anger du ett DNS-suffix som du vill lita på, till exempel contoso.com, och väljer **Lägg till**. Du kan lägga till så många suffix du vill.

Om en användare är ansluten till ett DNS-suffix i listan ansluts inte användaren automatiskt till en annan VPN-anslutning. Användaren fortsätter att använda den betrodda listan över DNS-suffix du anger. Det betrodda nätverket används fortfarande, även om autotriggers har angetts.

Om användaren till exempel redan är ansluten till ett betrott DNS-suffix ignoreras följande autotriggers. Mer specifikt avbryter DNS-suffixen i listan alla andra autotriggers för anslutningen, inklusive:

- Alltid på
- Appbaserad trigger
- DNS-autotrigger

## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. [Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Konfigurera VPN-inställningar på [Android](vpn-settings-android.md)-, [iOS](vpn-settings-ios.md)- och [macOS](vpn-settings-macos.md)-enheter.