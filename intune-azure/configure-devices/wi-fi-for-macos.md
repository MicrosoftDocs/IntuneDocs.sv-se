---
title: "Wi-Fi-inställningar för macOS-enheter i Intune| Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Lär dig mer om Intune-inställningar som du kan använda för att konfigurera Wi-Fi-anslutningar på macOS-enheter."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 322a38d5-21f5-48ee-bc59-0a4f9da78d38
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ac907e4cb63e4175dafc4c50239d3e0cbe581ad9
ms.openlocfilehash: 46c567dbcbfb84d4e0f8e3c3e8567cc6498befcf


---

# <a name="intune-wi-fi-settings-for-macos-devices-in-intune-azure-preview"></a>Wi-Fi-inställningar för macOS-enheter i förhandsversionen av Intune Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="wi-fi-settings-for-basic-and-enterprise-profiles"></a>Wi-Fi-inställningar för bas- och företagsprofiler

- **Nätverksnamn** – Ange ett namn för den här Wi-Fi-anslutningen. Detta är det namn som användarna ser när de söker i listan över tillgängliga anslutningar på sina enheter.
- **SSID** – Förkortning för nätverksnamn. Detta är det verkliga namnet på det trådlösa nätverk som enheterna ska ansluta till. Användare ser dock bara det nätverksnamn som du skapade ovan när de väljer anslutningen.
- **Anslut automatiskt** – Gör att enheten ansluter när den är inom intervallet för det här nätverket.
- **Dolt nätverk** – Förhindrar att det här nätverket visas i listan över tillgängliga nätverk på enheten.
- **Proxyinställningar** – Välj från:
    - **Ingen** – Inga proxyinställningar kommer att konfigureras.
    - **Manuell** – Ange **proxyserveradressen** (som en IP-adress) och dess tillhörande **portnummer**.
    - **Automatisk** – Använd en fil för att konfigurera proxyservern. Ange den **webbadress till proxyserver** (till exempel **http://proxy.contoso.com**) som innehåller konfigurationsfilen.

## <a name="wi-fi-settings-for-basic-profiles-only"></a>Wi-Fi-inställningar endast för basprofiler

- **Säkerhetstyp** – Välj det säkerhetsprotokoll som ska användas för att autentisera med Wi-Fi-nätverket:
    - **Öppet (ingen autentisering)** – Använd bara det här alternativet om nätverket är oskyddat.
    - **WPA/WPA2 – Personal**
    - **WEP**

## <a name="wi-fi-settings-for-enterprise-profiles-only"></a>Wi-Fi-inställningar endast för företagsprofiler

- **EAP-typ** – Välj den EAP-typ (Extensible Authentication Protocol) som ska användas för att autentisera skyddade trådlösa anslutningar:
    - **EAP-FAST**
    - **EAP-SIM**
    - **EAP-TLS**
    - **EAP-TTLS**
    - **LEAP**
    - **PEAP**

### <a name="further-options-when-you-choose-an-eap-type"></a>Ange ytterligare alternativ när du väljer en EAP-typ


|Inställningsnamn|Mer information|Använd när|
|--------------|-------------|----------|
|**PAC-inställningar (Protected Access Credential)**|Välj det här alternativet om du vill etablera en autentiserad tunnel mellan klienten och autentiseringsservern. Välj en av:<br>- **Använd PAC** – Använd en befintlig PAC-fil om det finns en sådan.<br>- **Använd och etablera PAC** – Etablerar PAC-filen till dina enheter.<br>- **Använd och etablera PAC anonymt** – Etablera PAC-filen till dina enheter och säkerställ att PAC-filen etableras utan att servern autentiseras.|EAP-typen är **EAP-FAST**|

#### <a name="server-trust"></a>Serverförtroende


|Inställningsnamn|Mer information|Använd när|
|--------------|-------------|----------|
|**Certifikatservernamn**|Ange ett eller flera gemensamma namn som används i de certifikat som utfärdats av en betrodd certifikatutfärdare (CA). Om du anger den här informationen kan du hoppa över dialogrutan för dynamiskt förtroende som visas på slutanvändares enheter när de ansluter till det här Wi-Fi-nätverket.|EAP-typen är **EAP-TLS**, **EAP-TTLS** eller **PEAP**.|
|**Rotcertifikat för serververifiering**|Välj den betrodda rotcertifikatsprofil som ska användas för att autentisera anslutningen. |EAP-typen är **EAP-TLS**, **EAP-TTLS** eller **PEAP**|
|**Identitetssekretess (yttre identitet)**|Ange vilken text som ska skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel.|EAP-typen är **PEAP**|


#### <a name="client-authentication"></a>Klientautentisering


|Inställningsnamn|Mer information|Använd när|
|--------------|-------------|----------|
|**Klientcertifikat för klientautentisering (identitetscertifikat)**|Välj den SCEP- eller PKCS-certifikatsprofil som ska användas för att autentisera anslutningen.|EAP-typen är **EAP-TLS**|
|**Autentiseringsmetod**|Välj autentiseringsmetod för anslutningen:<br>- **Certifikat** för att markera det SCEP- eller PKCS- klientcertifikat som är identitetscertifikatet som presenterats för servern.<br><br>- **Användarnamn och lösenord** för att ange en annan metod för autentisering. <br><br>Om du har valt **Användarnamn och lösenord**, konfigurera:<br><br>-  **Annan metod än EAP (inre identitet)** och välj sedan hur du ska autentisera anslutningen:<br>- **Inga**<br>- **Okrypterat lösenord (PAP)**<br>- **CHAP (Challenge Handshake Authentication Protocol)**<br>- **Microsoft CHAP (MS-CHAP)**<br>- **Microsoft CHAP Version 2 (MS-CHAP v2)**<br>Vilka alternativ som är tillgängliga beror på vilken EAP-typ du väljer.<br><br>**och**<br><br>- **Identitetssekretess (yttre identitet)** – Ange texten som skickas som svar på en begäran om EAP-identitet. Den här texten kan ha vilket värde som helst. Vid autentisering skickas den här anonyma identiteten från början och sedan följs den av den verkliga identifieringen som skickas i en säker tunnel.|EAP-typen är **EAP-TTLS** eller **PEAP**|



<!--HONumber=Feb17_HO1-->

