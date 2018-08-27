---
title: Wi-Fi-inställningar för Windows 10-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Lägg till eller skapa Wi-Fi-konfigurationsprofil med hjälp av Wi-Fi-inställningar för Windows 10-enheter och senare enheter i Microsoft Intune. Du kan konfigurera grundläggande inställningar och inställningar på företagsnivå.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f6532c63612b806f9824f5b9ca98f1ebbbc943f
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321848"
---
## <a name="wi-fi-settings-for-windows-10-and-later-devices-in-intune"></a>Wi-Fi-inställningar för Windows 10-enheter och senare enheter i Microsoft Intune

Wi-Fi-inställningar används i en konfigurationsprofil som tillämpas för enheter som kör Windows 10 och senare. Alternativen är:

- Grundläggande
- Företag

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en enhetsprofil](device-profile-create.md).

## <a name="settings-for-basic-and-enterprise-profiles"></a>Inställningar för grundläggande profiler och företagsprofiler

- **Wi-Fi-namn (SSID)**: Förkortning för nätverksnamn. Det här värdet är det verkliga namnet på det trådlösa nätverk som enheterna ansluter till. Användarna ser dock bara det **anslutningsnamn** som du konfigurerar när de väljer anslutningen.
- **Anslutningsnamn**: Ange ett användarvänligt för den här Wi-Fi-anslutningen. Den text som du anger är det namn som användarna ser när de bläddrar i tillgängliga anslutningar på sin enhet.
- **Connect automatically when in range** (Anslut automatiskt inom räckvidd): När det här är **Yes** (Ja) ansluter enheter automatiskt när de är inom räckvidden för det här nätverket. När det är **No** (Nej) ansluter enheter inte automatiskt.
  - **Connect to more preferred network if available** (Anslut till ett mer prioriterat nätverk om det är tillgängligt): Om enheterna är inom räckvidden för ett mer prioriterat nätverk väljer du **Yes** (Ja) för att använda det föredragna nätverket. Välj **No** (Nej) om du vill använda Wi-Fi-nätverket i den här konfigurationsprofilen.

    Exempelvis kan du skapa ett Wi-Fi-nätverk med namnet **ContosoCorp** och använda **ContosoCorp** i konfigurationsprofilen. Du har även ett **ContosoGuest**-Wi-Fi-nätverk inom räckvidd. När företagets enheter är inom räckvidd vill du att de automatiskt ska anslutas till **ContosoCorp**. I det här scenariot ställer du in egenskapen **Connect to more preferred network if available** (Anslut till ett mer prioriterat nätverk om det är tillgängligt) till **No** (Nej).

  - **Connect to this network, even when it is not broadcasting its SSID** (Anslut till det här nätverket även om det inte sänder sitt SSID): Välj **Yes** (Ja) för att konfigurationsprofilen automatiskt ska ansluta till nätverket, även om nätverket är dolt (det vill säga att dess SSID inte sänds offentligt). Välj **No** (Nej) om du inte vill att den här konfigurationsprofilen ska ansluta till ditt dolda nätverk.

- **Company Proxy settings** (Företagets proxyinställningar): Välj att använda proxyinställningarna i din organisation. Alternativen är:
  - **Inga**: Inga proxyinställningar konfigureras.
  - **Konfigurera manuellt**: Ange **proxyserverns IP-adress** och dess **portnummer**.
  - **Konfigurera automatiskt**: Ange den URL som pekar till ett PAC-skript (Proxy Auto-Configuration). Ange till exempel `http://proxy.contoso.com/proxy.pac`.

## <a name="settings-for-basic-profiles-only"></a>Inställningar endast för basprofiler

- **Trådlös säkerhetstyp**: Ange det säkerhetsprotokoll som används för att autentisera enheter i nätverket. Alternativen är:
  - **Öppet (ingen autentisering)**: Använd bara det här alternativet om nätverket är oskyddat.
  - **WPA/WPA2-personligt**

## <a name="settings-for-enterprise-profiles-only"></a>Inställningar endast för företagsprofiler

- **Enkel inloggning (SSO)**: Gör att du kan konfigurera enkel inloggning (SSO), där autentiseringsuppgifter delas för nätverksinloggning med dator och Wi-Fi. Alternativen är:
  - **Inaktivera**: Inaktiverar SSO-beteende. Användaren måste autentisera till nätverket separat.
  - **Aktivera innan användaren loggar in på enheten**: Använd enkel inloggning för att autentisera till nätverket precis före användarens inloggningsprocess.
  - **Aktivera efter användaren loggar in på enheten**: Använd enkel inloggning för att autentisera till nätverket omedelbart efter användarens inloggningsprocess är klar.
  - **Längsta tid att autentisera före timeout**: Ange det maximala antalet sekunder att vänta före autentisering till nätverket, 1–120 sekunder.
  - **Tillåt Windows att fråga användaren om ytterligare autentiseringsuppgifter**: Om du väljer **Ja** tillåts Windows-systemet att fråga användaren om ytterligare autentiseringsuppgifter om autentiseringsmetoden som kräver det. Välj **Nej** för att dölja dessa frågor.

- **Aktivera cachelagring av Pairwise Master Key (PMK)**: Välj **Ja** för att cachelagra PMK som används vid autentisering. Den här cachelagringen gör vanligtvis att autentisering till nätverket slutförs snabbare. Välj **Nej** för att framtvinga autentiseringshandskakningen vid anslutning till Wi-Fi-nätverket varje gång.

  - **Längsta tid som en PMK lagras i cacheminnet**: Ange hur många minuter som en Pairwise Master Key (PMK) lagras i cacheminnet, 5–1440 minuter.
  - **Maximalt antal PMK:er som lagras i cacheminnet**: Ange hur många nycklar som lagras i cacheminnet, 1–255.

- **Aktivera förautentisering**: Förautentisering gör att profilen kan autentisera till alla åtkomstpunkter för nätverket i profilen före anslutning. Vid flyttning mellan åtkomstpunkter återansluter förautentisering användaren eller enheter snabbare. Välj **Ja** för att profilen ska autentisera till alla åtkomstpunkter för det här nätverket som ligger inom räckvidd. Välj **Nej** om du vill kräva att användaren eller enheten autentiserar till varje åtkomstpunkt separat.

  - **Högsta antal förautentiseringsförsök**: Ange antalet försök att förautentisera, 1–16.

- **EAP-typ**: Välj EAP-typ (Extensible Authentication Protocol) för autentisering av skyddade trådlösa anslutningar. Alternativen är:

  - **EAP-SIM**
  - **EAP-TLS**
  - **EAP-TTLS**
  - **Skyddad PEAP** (PEAP)

### <a name="more-options-when-you-choose-the-eap-type"></a>Ytterligare alternativ när du väljer EAP-typ

> [!NOTE]
> För närvarande stöds endast SCEP-certifikatprofiler när du använder en EAP-typ. PKCS-certifikatprofiler stöds inte. Varje gång en användare uppmanas att ange ett certifikat ska ett SCEP-certifikat väljas.

#### <a name="server-trust"></a>Serverförtroende

|Inställningsnamn|Mer information|Använd när|
|--------------|-------------|----------|
|**Certifikatservernamn**|Ange ett eller flera gemensamma namn som används i de certifikat som utfärdats av en betrodd certifikatutfärdare (CA). Om du anger den här informationen kan du hoppa över dialogrutan för dynamiskt förtroende som visas på användarenheter när de ansluter till Wi-Fi-nätverket.|EAP-typen är **EAP-TLS**, **EAP-TTLS** eller **PEAP**|
|**Rotcertifikat för serververifiering**|Välj den betrodda rotcertifikatsprofil som ska användas för att autentisera anslutningen. |EAP-typen är **EAP-TLS**, **EAP-TTLS** eller **PEAP**|
|**Identitetssekretess (yttre identitet)**|Ange den text som ska skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel.|EAP-typen är **PEAP**|

#### <a name="client-authentication"></a>Klientautentisering

| Inställningsnamn | Mer information | Använd när |
|---|---|---|
| **Klientcertifikat för klientautentisering (identitetscertifikat)** |  Välj den SCEP-certifikatsprofil som ska användas för att autentisera anslutningen. | EAP-typen är **EAP-TLS** |
| **Autentiseringsmetod** | Välj autentiseringsmetod för anslutningen:<br><br>- **Certifikat**: Välj det SCEP-klientcertifikat som är det identitetscertifikat som presenteras för servern.<br><br>- **Användarnamn och lösenord**: Ange en **Annan metod än EAP (inre identitet)** för autentisering. Alternativen är:<br><br>- **Okrypterat lösenord (PAP)**<br>- **Utmaningshandskakning (CHAP)**<br>- **Microsoft CHAP (MS-CHAP)**<br>- **Microsoft CHAP Version 2 (MS-CHAP v2)**<br><br>- **Identitetssekretess (yttre identitet)**: Ange den text som skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel. | EAP-typen är **EAP-TTLS** |

## <a name="use-an-imported-settings-file"></a>Använd en importerad inställningsfil

För alla inställningar som inte är tillgängliga i Intune kan du exportera Wi-Fi-inställningar från en annan Windows-enhet. Den här exporten skapar en XML-fil med alla inställningarna. Importera sedan den här filen i Intune och använd den som Wi-Fi-profilen. Se [Exportera och importera Wi-Fi-inställningar för Windows-enheter](wi-fi-settings-import-windows-8-1.md).

## <a name="next-steps"></a>Nästa steg
[Konfigurera Wi-Fi-inställningar i Intune](wi-fi-settings-configure.md)