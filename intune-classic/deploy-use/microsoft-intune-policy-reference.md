---
title: "Referens för konfigurationsprincip"
description: "Använd informationen i det här avsnittet för att avgöra vilken Microsoft Intune-princip som du behöver använda för att hantera dina enheter."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/11/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d27f2739-9791-4aae-a9db-01a4e59ccfe5
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: af13a591bdd0e3185a92702aab093d9ae3bc6434
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="microsoft-intune-configuration-policy-reference"></a>Referens för konfigurationsprinciper för Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Informationen i det här avsnittet hjälper dig att avgöra vilken Microsoft Intune-konfigurationsprincip som du behöver för att hantera dina enheter.

> [!TIP]
> Mer detaljerad information om hur du använder principer finns i [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).


## <a name="android-configuration-policies"></a>Principer för Android-konfiguration

|Principnamn|Använd när du vill|
|---------------|------------------------|
|**Anpassad konfiguration (Android 4 och senare, Samsung KNOX Standard 4.0 och senare)**<br><br>**Anpassad konfiguration (Andoid for Work)**|Distribuera OMA-URI-inställningar (Open Mobile Alliance Uniform Resource Identifier), t.ex. Wi-Fi-inställningar som kan användas för att kontrollera enheters funktioner. Detta är användbart när inställningen du behöver inte är tillgänglig i en konfigurationsprincip.<br /><br />Mer information finns i [Inställningar för Android-principer i Microsoft Intune](android-policy-settings-in-microsoft-intune.md).|
|**E-postprofil (Samsung KNOX Standard 4.0 och senare)**<br><br>**E-postprofil (Android for Work – Gmail)**<br><br>**E-postprofil (Android for Work – Nine Work)**|Skapa, distribuera och övervaka Exchange Active Sync-e-postinställningar på hanterade enheter. Detta gör att användarna kan komma åt företagets e-post på sina personliga enheter utan att behöva göra några särskilda inställningar.<br /><br />Mer information finns i [Konfigurera åtkomst till företagets e-post med hjälp av e-postprofiler med Microsoft Intune](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md).|
|**Allmän konfiguration (Android 4 och senare, Samsung KNOX Standard 4.0 och senare)**<br><br>**Allmän konfiguration (Andoid for Work)**|Konfigurera säkerhets- och funktionsinställningar för mobil enhet.<br />Specificera appar som är kompatibla eller icke-kompatibla, och rapportera när de används.<br />Konfigurera helskärmsläge som låser enheter så att endast vissa funktioner fungerar, till exempel tillåta att enheten kör endast en app eller inaktivera volymknapparna.<br /><br />Mer information finns i [Inställningar för Android-principer i Microsoft Intune](android-policy-settings-in-microsoft-intune.md).|
|**PKCS #12-certifikatprofil (.PFX) (Android 4 och senare)**<br><br>**PKCS #12-certifikatprofil (.PFX) (Android for Work)**|Använd den här profilen om du vill skapa och distribuera PFX-inställningar för enheternas certifikatförfrågningar.<br /><br />Mer information finns i [Skydda resursåtkomst med certifikatprofiler i Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**SCEP-certifikatprofil (Android 4 och senare)**<br><br>**SCEP-certifikatprofil (Android for Work)**|Konfigurera ett SCEP-certifikat (Simple Certificate Enrollment Protocol) som kan användas med ett certifikat för betrodd mobil för att autentisera mobila enheter så att de kan komma åt nätverksresurser, till exempel nätverksresurser som konfigurerats av Wi-Fi- och VPN-profiler.<br /><br />Mer information finns i [Skydda resursåtkomst med certifikatprofiler i Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**Certifikatprofil för betrodd mobil (Android 4 och senare)**<br><br>**Betrodd certifikatprofil (Android for Work)**|Konfigurera ett certifikat för betrodd mobil enhet som kan användas för att autentisera mobila enheter så att de kan komma åt nätverksresurser, till exempel nätverksresurser som konfigurerats av Wi-Fi- och VPN-profiler.<br /><br />Mer information finns i [Skydda resursåtkomst med certifikatprofiler i Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**VPN-profil (Android 4 och senare)**<br><br>**VPN-profil (Android for Work)**|Konfigurera och distribuera inställningar som ger användare säker åtkomst till företagets nätverk från användarens mobila enhet. Genom att distribuera inställningarna gör du det enklare för användarna att ansluta till företaget.<br /><br />Mer information finns i [VPN-anslutningar i Microsoft Intune](vpn-connections-in-microsoft-intune.md).|
|**Wi-Fi-profil (Android 4 och senare)**<br><br>**Wi-Fi-profil (Android for Work)**|Konfigurera och distribuera trådlösa nätverksinställningar till användare i organisationen. Genom att distribuera inställningarna gör du det enklare för användarna att ansluta till det trådlösa nätverket.<br /><br />Mer information finns i [Wi-Fi-anslutningar i Microsoft Intune](wi-fi-connections-in-microsoft-intune.md).|
|**Konfigurationsprincip för mobilappar (Android for Work)**|Använd konfigurationsprinciper för mobilappar om du vill definiera inställningar automatiskt som kan krävas när användaren kör en Android for Work-app.<br /><br />Mer information finns i [Konfigurera Android for Work-appar med konfigurationsprinciper för mobilappar i Microsoft Intune](afw-app-configuration-policy.md).

## <a name="ios-configuration-policies"></a>Principer för iOS-konfiguration

|Principnamn|Använd när du vill|
|---------------|------------------------|
|**Anpassad konfiguration (iOS 8.0 och senare)**|Distribuera konfigurationsprofiler till iOS-enheter som du skapat med hjälp av Apple Configurator. Detta är användbart när inställningen du behöver inte är tillgänglig i en konfigurationsprincip.<br /><br />Mer information finns i [Principinställningar för iOS i Microsoft Intune](ios-policy-settings-in-microsoft-intune.md).|
|**E-postprofil (iOS 8.0 och senare)**|Skapa, distribuera och övervaka Exchange Active Sync-e-postinställningar på hanterade enheter. Detta gör att användarna kan komma åt företagets e-post på sina personliga enheter utan att behöva göra några särskilda inställningar.<br /><br />Mer information finns i [Konfigurera åtkomst till företagets e-post med hjälp av e-postprofiler med Microsoft Intune](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md).|
|**Allmän konfiguration (iOS 8.0 och senare)**|Konfigurera säkerhets- och funktionsinställningar för mobil enhet.<br />Specificera appar som är kompatibla eller icke-kompatibla, och rapportera när de används.<br />Konfigurera helskärmsläge som låser enheter så att endast vissa funktioner fungerar, till exempel tillåta att enheten kör endast en app eller inaktivera volymknapparna.<br /><br />Mer information finns i [Principinställningar för iOS i Microsoft Intune](ios-policy-settings-in-microsoft-intune.md).|
|**Konfigurationsprincip för mobilappar (iOS 8.0 och senare)**|Använd konfigurationsprinciper för mobilappar om du vill definiera inställningar automatiskt som kan krävas när användaren kör en iOS-app.<br /><br />Mer information finns i [Konfigurera iOS-appar med konfigurationsprinciper för mobilappar i Microsoft Intune](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md).|
|**Etableringsprofilprincip för mobila enheter (iOS 8.0 och senare)**|Verksamhetsspecifika Apple iOS-appar skapas med en inbyggd etableringsprofil och kod som signeras med ett certifikat. När appen körs på en iOS-enhet bekräftar iOS appens integritet och tillämpar de principer som etableringsprofilen definierar.<br><br>Signeringscertifikatet du använder för att signera appar gäller normalt i tre år. Däremot upphör etableringsprofilen att gälla efter ett år. Använd den här principen för att distribuera en ny etableringsprofilprincip till enheter som har appar som snart slutar att gälla medan certifikatet fortfarande är giltigt.<br><br>Mer information finns i [Använd etableringsprofilprinciper för iOS för att förhindra att dina appar upphör att gälla](ios-mobile-app-provisioning-profiles.md).|
|**PKCS #12 (.PFX)-certifikatprofil (iOS 8.0 och senare)**|Använd den här profilen om du vill skapa och distribuera PFX-inställningar för enheternas certifikatförfrågningar.<br /><br />Mer information finns i [Skydda resursåtkomst med certifikatprofiler i Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**SCEP-certifikatprofil (iOS 8.0 och senare)**|Konfigurera ett SCEP-certifikat (Simple Certificate Enrollment Protocol) som kan användas med ett certifikat för betrodd mobil för att autentisera mobila enheter så att de kan komma åt nätverksresurser, till exempel nätverksresurser som konfigurerats av Wi-Fi- och VPN-profiler.<br /><br />Mer information finns i [Skydda resursåtkomst med certifikatprofiler i Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**Certifikatprofil för betrodd mobil enhet (iOS 8.0 och senare)**|Konfigurera ett certifikat för betrodd mobil enhet som kan användas för att autentisera mobila enheter så att de kan komma åt nätverksresurser, till exempel nätverksresurser som konfigurerats av Wi-Fi- och VPN-profiler.<br /><br />Mer information finns i [Skydda resursåtkomst med certifikatprofiler i Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**VPN-profil (iOS 8.0 och senare)**|Konfigurera och distribuera inställningar som ger användare säker åtkomst till företagets nätverk från deras mobila enheter. Genom att distribuera inställningarna gör du det enklare för användarna att ansluta till företaget.<br /><br />Mer information finns i [VPN-anslutningar i Microsoft Intune](vpn-connections-in-microsoft-intune.md).|
|**Wi-Fi-profil (iOS 8.0 och senare)**|Konfigurera och distribuera trådlösa nätverksinställningar till användare i organisationen. Genom att distribuera inställningarna gör du det enklare för användarna att ansluta till det trådlösa nätverket.<br /><br />Mer information finns i [Wi-Fi-anslutningar i Microsoft Intune](wi-fi-connections-in-microsoft-intune.md).|


## <a name="mac-os-x-configuration-policies"></a>Principer för Mac OS X-konfiguration

|Principnamn|Använd när du vill|
|---------------|------------------------|
|**Anpassad konfiguration (Mac OS X 10.9 och senare)**|Distribuera konfigurationsprofiler till Mac-datorer som du skapat med hjälp av Apple Configurator. Detta är användbart när inställningen du behöver inte är tillgänglig i en konfigurationsprincip.<br /><br />Mer information finns i [Principinställningar för Mac OS X i Microsoft Intune](mac-os-x-policy-settings-in-microsoft-intune.md).|
|**Allmän konfiguration (Mac OS X 10.9 och senare)**|Konfigurera säkerhets- och funktionsinställningar för mobil enhet.<br />Specificera appar som är kompatibla eller icke-kompatibla, och rapportera när de används.<br /><br />Mer information finns i [Principinställningar för Mac OS X i Microsoft Intune](mac-os-x-policy-settings-in-microsoft-intune.md).|
|**SCEP-certifikatprofil (Mac OS X 10.9 och senare)**|Konfigurera ett SCEP-certifikat (Simple Certificate Enrollment Protocol) som kan användas med ett certifikat för betrodd mobil för att autentisera mobila enheter så att de kan komma åt nätverksresurser, till exempel nätverksresurser som konfigurerats av Wi-Fi- och VPN-profiler.<br /><br />Mer information finns i [Skydda resursåtkomst med certifikatprofiler i Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**Betrodd certifikatprofil (Mac OS X 10.9 och senare)**|Konfigurera ett certifikat för betrodd mobil enhet som kan användas för att autentisera mobila enheter så att de kan komma åt nätverksresurser, till exempel nätverksresurser som konfigurerats av Wi-Fi- och VPN-profiler.<br /><br />Mer information finns i [Skydda resursåtkomst med certifikatprofiler i Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**VPN-profil (Mac OS X 10.9 och senare)**|Konfigurera och distribuera inställningar som ger användare säker åtkomst till företagets nätverk från deras mobila enheter. Genom att distribuera inställningarna gör du det enklare för användarna att ansluta till företaget.<br /><br />Mer information finns i [VPN-anslutningar i Microsoft Intune](vpn-connections-in-microsoft-intune.md).|
|**Wi-Fi-profil (Mac OS X 10.9 och senare)**|Konfigurera och distribuera trådlösa nätverksinställningar till användare i organisationen. Genom att distribuera inställningarna gör du det enklare för användarna att ansluta till det trådlösa nätverket.<br /><br />Mer information finns i [Wi-Fi-anslutningar i Microsoft Intune](wi-fi-connections-in-microsoft-intune.md).|

## <a name="windows-configuration-policies"></a>Principer för Windows-konfiguration
Gäller enbart för Windows Phone och registrerade Windows-enheter.

|Principnamn|Använd när du vill|
|---------------|------------------------|
|**Anpassad konfiguration (Windows 10 Desktop och Mobile och senare)**|Distribuera OMA-URI-inställningar som kan användas för att kontrollera enheters funktioner. Detta är användbart när inställningen du behöver inte är tillgänglig i en konfigurationsprincip.<br />    Mer information finns i [Principinställningar för Windows 10 i Microsoft Intune](windows-10-policy-settings-in-microsoft-intune.md).|
|**Anpassad konfiguration (Windows Phone 8.1 och senare)**|Distribuera OMA-URI-inställningar som kan användas för att kontrollera enheters funktioner. Detta är användbart när inställningen du behöver inte är tillgänglig i en konfigurationsprincip.<br /><br />Mer information finns i [Inställningar för Windows Phone 8.1 i Microsoft Intune](windows-phone-8-1-policy-settings-in-microsoft-intune.md).|
|**Uppgraderingsprincip för utgåva (Windows 10 Desktop och senare)**<br><br>**Uppgraderingsprincip för utgåva (Windows 10 Holographic och senare)**<br><br>**Uppgraderingsprincip för utgåva (Windows 10 Mobile och senare)**|Konfigurera och distribuera principer som innehåller licens- eller produktnyckelinformation som används för att uppdatera Windows 10-enheter till en senare version.<br><br>Mer information finns i [Inställningar för princip för versionsuppgradering i Microsoft Intune](edition-upgrade-policy-settings-in-microsoft-intune.md).|  
|**E-postprofil (Windows Phone 8.1 och senare)**<br /><br />**E-postprofil (Windows 10 Desktop och Mobile och senare)**|Skapa, distribuera och övervaka Exchange Active Sync-e-postinställningar på hanterade enheter. Detta gör att användarna kan komma åt företagets e-post på sina personliga enheter utan att behöva göra några särskilda inställningar.<br /><br />Mer information finns i [Konfigurera åtkomst till företagets e-post med hjälp av e-postprofiler med Microsoft Intune](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md).|
|**Allmän konfiguration (Windows 10 Desktop och Mobile och senare)**|Konfigurera säkerhets- och funktionsinställningar för mobila enheter för registrerade Windows 10 Desktop- och Windows 10 Mobile-enheter.<br /><br />Mer information finns i [Principinställningar för Windows 10 i Microsoft Intune](windows-10-policy-settings-in-microsoft-intune.md).|
|**Allmän konfiguration (Windows 10 Team och senare)**|Konfigurera säkerhets- och funktionsinställningar för registrerade Windows 10 Team-enheter (till exempel en Surface Hub-enhet).<br /><br />Mer information finns i [Inställningar för Windows Team-konfigurationsprincip i Microsoft Intune](windows-team-configuration-policy-settings-in-microsoft-intune.md).|
|**Allmän konfiguration (Windows 8.1 och senare)**|Konfigurera säkerhets- och funktionsinställningar för mobila enheter för registrerade Windows-enheter.<br /><br />Mer information finns i [Principinställningar för Windows i Microsoft Intune](windows-configuration-policy-settings-in-microsoft-intune.md).|
|**Allmän konfiguration (Windows Phone 8.1 och senare)**|Konfigurera säkerhets- och funktionsinställningar för mobil enhet.<br />Ange appar som användare kan eller inte kan använda och blockera inkompatibla appar från att installeras eller användas.<br /><br />Mer information finns i [Inställningar för Windows Phone 8.1 i Microsoft Intune](windows-phone-8-1-policy-settings-in-microsoft-intune.md).|
|**PKCS #12-certifikatprofil (.PFX) (Windows 10 Desktop och Mobile och senare)**|Använd den här profilen om du vill skapa och distribuera PFX-inställningar för enheternas certifikatförfrågningar.<br /><br />Mer information finns i [Skydda resursåtkomst med certifikatprofiler i Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**SCEP-certifikatsprofil (Windows 8.1 och senare)**<br /><br />**SCEP-certifikatprofil (Windows Phone 8.1 och senare)**|Konfigurera ett SCEP-certifikat (Simple Certificate Enrollment Protocol) som kan användas med ett certifikat för betrodd mobil för att autentisera mobila enheter så att de kan komma åt nätverksresurser, till exempel nätverksresurser som konfigurerats av Wi-Fi- och VPN-profiler.<br /><br />Mer information finns i [Skydda resursåtkomst med certifikatprofiler i Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**Betrodd certifikatsprofil (Windows 8.1 och senare)**<br /><br />**Certifikatprofil för betrodd mobil enhet (Windows Phone 8.1 och senare)**|Konfigurera ett certifikat för betrodd mobil enhet som kan användas för att autentisera mobila enheter så att de kan komma åt nätverksresurser, till exempel nätverksresurser som konfigurerats av Wi-Fi- och VPN-profiler.<br /><br />Mer information finns i [Skydda resursåtkomst med certifikatprofiler i Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**VPN-profil (Windows 10 Desktop och Mobile och senare)**<br /><br />**VPN-profil (Windows 8.1 och senare)**<br /><br />**VPN-profil (Windows Phone 8.1 och senare)**|Konfigurera och distribuera inställningar som ger användare säker åtkomst till företagets nätverk från deras mobila enheter. Genom att distribuera inställningarna gör du det enklare för användarna att ansluta till företaget.<br /><br />Mer information finns i [VPN-anslutningar i Microsoft Intune](vpn-connections-in-microsoft-intune.md).|
|**Wi-Fi-import**|Importera och distribuera Windows Wi-Fi-konfigurationer som du tidigare har exporterat till en fil.<br /><br />Mer information finns i [Wi-Fi-anslutningar i Microsoft Intune](wi-fi-connections-in-microsoft-intune.md).|
|**Windows informationsskydd**<br>(kallades tidigare företagsdataskydd)|Allt fler anställda använder egna enheter i företaget. Detta innebär en ökad risk för oavsiktliga dataläckage via appar och tjänster, till exempel e-post, sociala media och offentliga moln, som företaget inte har någon kontroll över. En medarbetare kan till exempel skicka de senaste ritningarna via sitt personliga e-postkonto, kopiera och klistra in produktinformation i en tweet eller spara en försäljningsrapport på en offentlig molnlagringsplats.<br><br>Windows informationsskydd bidrar till att skydda mot potentiella dataläckage utan att störa medarbetarnas användning. Informationsskyddet skyddar även företagsappar och företagsdata mot oavsiktliga dataläckage i företagsägda enheter och personliga enheter som medarbetarna tar med sig till jobbet utan att det behövs några ändringar i miljön eller andra appar.<br><br>Den här Intune-principen hanterar listan över appar som skyddas av Windows informationsskydd, företagsnätverksplatser, skyddsnivå och krypteringsinställningar.<br><br>Mer information finns i [Skydda företagsdata med Windows informationsskydd](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-edp).|


## <a name="software-policies"></a>Principer för programvara

|Principnamn|Använd när du vill|
|---------------|------------------------|
|**Princip för hanterad webbläsare (Android 4 och senare)**<br /><br />**Princip för hanterad webbläsare (iOS 8.0 och senare)**|Ange de webbplatser som användarna kan och inte kan komma åt när de använder appen för hanterade webbläsare.<br /><br />Mer information finns i [Hantera Internetåtkomst med hanterade webbläsarprinciper med Microsoft Intune](manage-internet-access-using-managed-browser-policies.md).|
|**Hantering av mobila program (Android 4 och senare)**<br /><br />**Hanteringsprincip för mobilprogram (iOS 8.0 och senare)**|Ändra funktionen för appar som du distribuerar för att anpassa dem efter företagets principer för efterlevnad och säkerhet. Du kan till exempel begränsa åtgärderna klipp ut, kopiera och klistra in inom en begränsad app eller konfigurera en app så att alla länkar öppnas i den hanterade webbläsaren.<br /><br />Mer information finns i [Konfigurera och distribuera hanteringsprinciper för mobilprogram i Microsoft Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)|

## <a name="common-mobile-device-settings"></a>Standardinställningarna för mobil enhet

|Principnamn|Använd när du vill|
|---------------|------------------------|
|**Exchange ActiveSync-princip**|Konfigurera säkerhets- och funktionsinställningar för mobila enheter för enheter som hanteras av Exchange ActiveSync.<br /><br />Mer information finns i [Exchange ActiveSync-principinställningar i Microsoft Intune](exchange-activesync-policy-settings-in-microsoft-intune.md).|
|**Säkerhetsprincip för mobil enhet**|<ul><li>Konfigurerar inställningar för mobila enheter (alla plattformar), däribland:<br /><br /><ul><li>Säkerhet</li><li>Kryptering</li><li>System</li><li>E-post</li><li>Program</li></ul></li></ul>
> [!IMPORTANT]
Microsoft Intune har nu separata **konfigurationsprinciper** för respektive enhetsplattform, och dessa principer innehåller de senaste uppdaterade inställningar som du kan använda. Du kan fortsätta att använda den befintliga säkerhetsprincipen för mobila enheter, och alla befintliga distributioner fungerar fortfarande, men du bör planera för att migrera till de nya konfigurationsprinciperna så snart som möjligt.<br />Mer information finns i [Säkerhetsprincipinställningar för mobila enheter i Microsoft Intune](mobile-device-security-policy-settings-in-microsoft-intune.md).

## <a name="policies-for-windows-pcs-managed-by-the-intune-software-client"></a>Principer för Windows-datorer som hanteras av Intune-klientprogrammet

|Principnamn|Använd när du vill|
|---------------|------------------------|
|**Inställningar för Microsoft Intune Agent**|Konfigurera Intune-klienten på datorer, inklusive inställningar för:<br /><br />-   Endpoint Protection<br />-   Programuppdateringar<br />-   Schema för principkontroll<br /><br />Den här typen av princip kan bara distribueras till grupper av enheter.<br /><br />Intune-klienter laddar ned nya och uppdaterade principer enligt inställningen **Frekvens för uppdatering och identifiering av program**, där standardinställningen är var åttonde timme. Du kan dock framtvinga en uppdatering av principen på datorer när som helst.<br /><br />Mer information finns i [Hålla Windows-datorer uppdaterade med programvaruppdateringar i Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md).|
|**Microsoft Intune Center-inställningar**|Konfigurera information som visas i Microsoft Intune Center på hanterade datorer.<br /><br />Den här typen av princip kan bara distribueras till grupper av enheter.<br /><br />Mer information finns i [Vanliga hanteringsuppgifter för Windows-datorer med Microsoft Intune-datorklienten](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).|
|**Inställningar för Windows-brandväggen**|Konfigurerar inställningar för Windows-brandväggen och undantag för vanlig nätverkskommunikation på datorer, bland annat:<br /><br />-   BranchCache<br />-   Fjärrhjälp<br />-   Mediedelning<br /><br />Den här typen av princip kan bara distribueras till grupper av enheter.<br /><br />Mer information finns i [Skydda Windows-datorer med Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).|

### <a name="see-also"></a>Se även

[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)