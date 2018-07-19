---
title: Felsöka enhetsregistrering
description: Förslag på hur du kan felsöka problem med enhetsregistrering.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6982ba0e-90ff-4fc4-9594-55797e504b62
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b540cd2b2751712604c0ae7172015cb109c9c1d8
ms.sourcegitcommit: 024cce10a99b12a13f32d3995b69c290743cafb8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/14/2018
ms.locfileid: "39039445"
---
# <a name="troubleshoot-device-enrollment-in-intune"></a>Felsöka enhetsregistrering i Intune

Den här artikeln innehåller förslag på hur du kan felsöka problem med enhetsregistrering. Om du inte lyckas lösa problemet med hjälp av den här informationen läser du [Ta reda på hur du kan få support för Microsoft Intune](get-support.md), som beskriver hur du kan få hjälp på fler sätt.


## <a name="initial-troubleshooting-steps"></a>Inledande felsökningssteg

Kontrollerar att du har konfigurerat Intune korrekt så att registrering är aktiverat innan du påbörjar felsökningen. Du kan läsa om konfigurationskraven i:

-   [Dags att registrera enheter i Microsoft Intune](setup-steps.md)
-   [Konfigurera iOS- och Mac-enhetshantering](ios-enroll.md)
-   [Konfigurera Windows-enhetshantering](windows-enroll.md)
-   [Konfigurera hantering av Android-enhet](android-enroll.md) – Inga ytterligare åtgärder krävs

Du kan också kontrollera att tid och datum på användarens enhet är inställt på rätt sätt:

1. Starta om enheten.
2. Kontrollera att tid och datum är inställt nära GMT-standarder (+ eller - 12 timmar) i förhållande till slutanvändarens tidszon.
3. Avinstallera och installera Intune-företagsportalen igen (om tillämpligt).

Användare av hanterade enheter kan samla in registrerings- och diagnostikloggar som du kan granska. Anvisningar för hur användare samlar in loggar finns i:

- [Skicka Android-registreringsfel till IT-administratören](https://docs.microsoft.com/intune-user-help/send-enrollment-errors-to-your-it-admin-android)
- [Skicka iOS-fel till IT-administratören](https://docs.microsoft.com/intune-user-help/send-errors-to-your-it-admin-ios)


## <a name="general-enrollment-issues"></a>Allmänna registreringsproblem
Dessa problem kan uppstå på alla enhetsplattformar.

### <a name="device-cap-reached"></a>Enhetstaket har nåtts
**Problem:** En användare får ett fel på enheten under registreringen, som **Företagsportalen är för tillfället otillgänglig** på en iOS-enhet och DMPdownloader.log på Configuration Manager innehåller felet **DeviceCapReached**.

**Lösning:**

#### <a name="check-number-of-devices-enrolled-and-allowed"></a>Kontrollera antalet enheter som har registrerats och som tillåts

Kontrollera att användaren inte är tilldelad mer än det maximala antalet enheter genom att följa dessa steg:

1. Välj **Enhetsregistrering** > **Registreringsbegränsningar** > **Begränsningar för enhetsgräns**. Notera värdet i kolumnen **Enhetsgräns**.

2. Välj **Användare** > **Alla användare** > Välj användaren > **Enheter** i Intune. Notera antalet enheter.

3. Om användarens antal registrerade enheter redan är lika med enhetsgränsen kan de inte registrera fler innan:
    - [Befintliga enheter tas bort](devices-wipe.md), eller
    - Du ökar enhetsgränsen genom att [ställa in enhetsbegränsningar](enrollment-restrictions-set.md#set-device-limit-restrictions).

För att undvika att nå enhetsgränser kan du vara noga med att ta bort inaktuella enhetsposter.

> [!NOTE]
> 
> Du kan undvika taket för enhetsregistrering genom att använda ett enhetsregistreringshanterarkonto. Mer information finns i [Registrera företagsägda enheter med Enhetsregistreringshanteraren i Microsoft Intune](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).
> 
> Ett användarkonto som läggs till i enhetsregistreringshanterarkontot kommer inte att kunna slutföra en registrering när en princip för villkorlig åtkomst för villkorlig åtkomst tillämpas för den specifika användarinloggning.

### <a name="company-portal-temporarily-unavailable"></a>Företagsportalen är för tillfället otillgänglig
**Problem:** Användare får felet **Företagsportalen är för tillfället otillgänglig** på enheten.

**Lösning:**

1.  Ta bort företagsportalappen för Intune från enheten.

2.  Öppna webbläsaren i enheten, bläddra till [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com) och prova med en användarinloggning.

3.  Användaren kan prova ett annat nätverk om de inte kan logga in.

4.  Om det inte går ska du validera att användarens autentiseringsuppgifter har synkroniserats korrekt med Azure Active Directory.

5.  Om användaren loggar in uppmanas denne av en iOS-enhet att installera företagsportalappen för Intune och registrera sig. På en Android-enhet måste du manuellt installera företagsportalappen för Intune, och sedan kan du prova att registrera dig igen.

### <a name="mdm-authority-not-defined"></a>MDM-auktoritet har inte definierats
**Problem:** Användaren får felet **MDM-utfärdare har inte definierats**.

**Lösning:**

1.  Kontrollera att utfärdaren för hantering av mobila enheter har [angetts korrekt](mdm-authority-set.md).
    
2.  Kontrollera att användarens autentiseringsuppgifter har synkroniserats korrekt med Azure Active Directory genom att kontrollera att användarens UPN matchar Active Directory-informationen i Office 365-portalen.
    Om aktuellt UPN inte överensstämmer med Active Directory-informationen:

    1.  Inaktivera DirSync på den lokala servern.

    2.  Ta bort den felmatchade användaren från användarlistan **Intune kontoportal** .

    3.  Vänta ungefär en timme så att Azure-tjänsten kan ta bort felaktiga data.

    4.  Aktivera DirSync igen och kontrollera om användaren nu är korrekt synkroniserad.

3.  I ett scenario där du använder System Center Configuration Manager med Intune ska du kontrollera att användaren har ett giltigt molnanvändar-ID:

    1.  Öppna SQL Management Studio.

    2.  Anslut till rätt DB.

    3.  Öppna databasmappen och leta upp och öppna mappen **CM_DBName** där DBName är namnet på kunddatabasen.

    4.  Klicka på **Ny fråga** överst och kör följande frågor:

        -   Om du vill visa alla användare: `select * from [CM_ DBName].[dbo].[User_DISC]`

        -   Om du vill se specifika användare använder du följande fråga där %testuser1% representerar username@domain.com för den användare som du vill söka efter: `select * from [CM_ DBName].[dbo].[User_DISC] where User_Principal_Name0 like '%testuser1%'`

        När du har skrivit frågan väljer du **!Kör**.
        När resultatet har returnerats, leta efter molnanvändar-ID:et.  Om det finns något ID är inte användaren licensierad för att använda Intune.

### <a name="unable-to-create-policy-or-enroll-devices-if-the-company-name-contains-special-characters"></a>Det går inte att skapa en princip eller registrera enheter om företagets namn innehåller specialtecken
**Problem:** Du kan inte skapa en princip eller registrera enheter.

**Lösning:** I [administrationscenter för Office 365](https://portal.office.com/) tar du bort specialtecknen från företagets namn och sparar företagsinformationen.

### <a name="unable-to-sign-in-or-enroll-devices-when-you-have-multiple-verified-domains"></a>Det går inte att logga in eller registrera enheter om det finns flera verifierade domäner
**Problem:** När du lägger till en andra verifierad domän i ADFS kanske användare med UPN-suffixet (användarens huvudnamn) för den andra domänen inte kan logga in på portalerna eller registrera enheter.


<strong>Lösning:</strong> Microsoft Office 365-kunder som använder enkel inloggning (SSO) via AD FS 2.0 och som har flera domäner på toppnivå för användarnas UPN-suffix i organisationen (till exempel @contoso.com eller @fabrikam.com) måste distribuera en separat instans av AD FS 2.0 Federation Service för varje suffix. Nu finns det en [sammanslagning för AD FS 2.0](http://support.microsoft.com/kb/2607496) som fungerar tillsammans med växeln <strong>SupportMultipleDomain</strong> och som gör att AD FS-servern har stöd det här scenariot utan att ytterligare AD FS 2.0-servrar krävs. Mer information finns i [den här bloggen](https://blogs.technet.microsoft.com/abizerh/2013/02/05/supportmultipledomain-switch-when-managing-sso-to-office-365/).


## <a name="android-issues"></a>Android-problem

### <a name="android-enrollment-errors"></a>Registreringsfel i Android

I följande tabell finns de felmeddelanden som kan visas när användarna registrerar Android-enheter i Intune.

|Felmeddelande|Problem|Lösning|
|---|---|---|
|**Administratören behöver tilldela en licens för åtkomst**<br>IT-administratören har inte gett dig behörighet till den här appen. Kontakta IT-administratören eller försök igen senare.|Enheten kan inte registreras eftersom användarkontot inte har den nödvändiga licensen.|Innan användarna kan registrera sina enheter måste de ha tilldelats rätt licenser. Det här meddelandet anger att de har fel licenstyp för den angivna hanteringsauktoriteten för mobila enheter. Det här felet visas till exempel om Intune har angetts som utfärdare för hantering av mobila enheter och användarna har en licens för System Center 2012 R2 Configuration Manager.<br><br>Mer information finns i [Tilldela Intune-licenser till dina användarkonton](/intune/licenses-assign).
|**IT-administratören måste ange MDM-utfärdare**<br>Det verkar som om din IT-administratör inte har angett en MDM-utfärdare. Kontakta IT-administratören eller försök igen senare.|Utfärdaren för hantering av mobila enheter har inte definierats.|Utfärdaren för hantering av mobila enheter har inte angetts i Intune. Se information om att [ange hantering av mobila enheter](/intune/mdm-authority-set).|


### <a name="devices-fail-to-check-in-with-the-intune-service-and-display-as-unhealthy-in-the-intune-admin-console"></a>Enheter kan inte checka in med Intune-tjänsten och visas som "Ohälsosamma" i Intune-administrationskonsolen
**Problem:** vissa Samsung-enheter som kör Android 4.4.x och 5.x kan sluta checka in med Intune-tjänsten. Om enheter inte checkar in:

- Kan de inte ta emot princip, appar och fjärranslutna kommandon från Intune-tjänsten.
- Visare de hanteringstillståndet **ohälsosamma** i administratörskonsolen.
- Användare som är skyddade med principer för villkorlig åtkomst kan förlora åtkomst till företagets resurser.

Samsung har bekräftat att Samsung Smart Manager-programvaran, som medföljer vissa Samsung-enheter, kan inaktivera Intunes företagsportal och dess komponenter. När företagsportalen är i ett inaktiverat tillstånd, kan den inte köras i bakgrunden och kan därför kan inte kontakta tjänsten Intune.

**Lösning nr 1:**

Be användarna att starta företagsportalappen manuellt. När appen startar om, checkar enheten in med Intune-tjänsten.

> [!IMPORTANT]
> Att öppna företagsportalappen manuellt är en tillfällig lösning eftersom Samsung Smart Manager kan inaktivera företagsportalenappen igen.

**Lösning nr 2:**

Be användarna att försöka uppgradera till Android 6.0. Inaktiveringsproblemet inträffar inte på Android 6.0-enheter. För att kontrollera om en uppdatering är tillgänglig, kan användare gå till **Inställningar** > **Om enheten** > **Hämta uppdateringar manuellt** och följa anvisningarna på enheten.

**Lösning nr 3:**

Om lösning nr 2 inte fungerar kan du be användarna att följa de här stegen så att Smart Manager exkluderar företagsportalappen:

1. Starta Smart Manager-appen på enheten.

   ![Välj Smart Manager-ikonen på enheten](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-icon.png)

2. Välj panelen **Batteri**.

   ![Välj panelen Batteri](./media/troubleshoot-device-enrollment-in-intune/smart-manager-battery-tile.png)

3. Under **App-energibesparing** eller **App-optimering**, väljer du **Detaljer**.

   ![Välj Detaljer under App-energibesparing eller App-optimering](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-power-saving-detail.png)

4. Välj **Företagsportalen** från listan över appar.

   ![Välj Företagsportalen från listan över appar](./media/troubleshoot-device-enrollment-in-intune/smart-manager-company-portal.png)

5. Välj **Avstängd**.

   ![Välj Avstängd från dialogrutan App-optimering](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-optimization-turned-off.png)

6. Under **App-energibesparing** eller **App-optimering**, bekräftar du att Företagsportalen är avstängd.

   ![Kontrollera att Företagsportalen är avstängd](./media/troubleshoot-device-enrollment-in-intune/smart-manager-verify-comp-portal-turned-off.png)


### <a name="profile-installation-failed"></a>Det gick inte att installera profilen
**Problem:** En användare får felmeddelandet **Det gick inte att installera profilen** på en Android-enhet.

**Lösning:**

1.  Bekräfta att användaren har tilldelats en lämplig licens för den version av Intune-tjänsten som du använder.

2.  Kontrollera att enheten inte redan har registrerats för en annan MDM-provider eller att den inte redan har en hanteringsprofil installerad.

3.  Bekräfta att Chrome för Android är standardwebbläsaren och att cookies har aktiverats.

### <a name="android-certificate-issues"></a>Certifikatfel (Android)

**Problem**: Användaren får följande meddelande på sin enhet: *Du kan inte logga in eftersom enheten saknar ett obligatoriskt certifikat.*

**Lösning 1**:

Användaren kanske kan hämta certifikatet som saknas genom att följa instruktionerna i [Enheten saknar ett obligatoriskt certifikat](/intune-user-help/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator). Om problemet kvarstår kan du försöka med lösning 2.

**Lösning 2**:

Om användaren fortfarande ser ett fel om saknat certifikat efter att ha angett sin företagsinloggning och omdirigerats för federerad inloggning, kan ett mellanliggande certifikat saknas på AD FS-servern (Active Directory Federation Services).

Certifikatfel uppstår eftersom Android-enheter kräver att mellanliggande certifikat ingår i en [SSL-servers hälsning](https://technet.microsoft.com/library/cc783349.aspx). För närvarande skickar en AD FS-standardserver eller WAP - AD FS Proxy-serverinstallation bara AD FS-tjänstens SSL-certifikat i SSL-serverns hälsningssvar till en SSL-klients hälsning.

Om du vill åtgärda problemet importerar du certifikaten till datorns personliga certifikat på AD FS-servern eller proxyservrar enligt följande:

1.  På ADFS- och proxy-servrarna högerklickar du på **Start** > **Kör** > **certlm.msc** för att starta Local Machine Certificate Management Console.
2.  Expandera **Personligt** och välj **Certifikat**.
3.  Hitta certifikatet för din AD FS-tjänstkommunikation (ett offentligt signerat certifikat) och dubbelklicka för att se dess egenskaper.
4.  Välj fliken **Certifieringssökväg** för att se certifikatets överordnade certifikat.
5.  På varje överordnat certifikat väljer du **Visa certifikat**.
6.  Välj **Information** > **Kopiera till fil...**.
7.  Följ anvisningarna i guiden för att exportera eller spara den offentliga nyckeln för överordnat certifikatet på önskad plats.
8.  Högerklicka på **Certifikat** > **Alla aktiviteter** > **Importera**.
9.  Följ guidens uppmaningar att importera överordnade certifikat till **Lokal dator\Personliga\Certifikat**.
10. Starta om AD FS-servrarna.
11. Upprepa stegen ovan på alla dina AD FS- och proxyservrar.

För att kontrollera om certifikatet har installerats på rätt sätt kan du använda diagnostikverktyget som finns på [https://www.digicert.com/help/](https://www.digicert.com/help/). I rutan **Serveradress**, ange din ADFS-servers FQDN (IE: sts.contso.com) och klicka på **Kontrollera server**.

**Så här kontrollerar du att certifikatet har installerats**:

Följande steg beskriver bara en av många metoder och verktyg som du kan använda för att kontrollera att certifikatet har installerats.

1. Gå till [det kostnadsfria Digicert-verktyget](ttps://www.digicert.com/help/).
2. Ange det fullständiga domännamnet (t.ex. sts.contoso.com) för AD FS-servern och välj **KONTROLLERA SERVER**.

Om servercertifikatet har installerats korrekt, ser du alla kryssmarkeringar i resultaten. Om problemet ovan kvarstår, ser du ett rött X i avsnitten ”Certifikatnamnmatchningar” och ”SSL-certifikatet är korrekt installerat” i rapporten.


## <a name="ios-issues"></a>iOS-problem

### <a name="ios-enrollment-errors"></a>Fel vid iOS-registrering
I följande tabell finns de felmeddelanden som kan visas när användarna registrerar iOS-enheter i Intune.

|Felmeddelande|Problem|Lösning|
|-----------------|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|NoEnrollmentPolicy|Ingen registreringsprincip hittades|Kontrollera att alla krav för registrering har konfigurerats, till exempel APNs-certifikatet (Apple Push Notification Service), och att ”iOS som en plattform” är aktiverat. Anvisningar finns i [Konfigurera iOS- och Mac-enhetshantering](ios-enroll.md).|
|DeviceCapReached|Det finns redan för många registrerade mobila enheter.|För att kunna registrera en ny enhet måste användaren först ta bort en registrerad mobil enhet från företagsportalen. Se anvisningar för den typ av enhet som du använder: [Android](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android), [iOS](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-ios), [Windows](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-windows).|
|APNSCertificateNotValid|Det är problem med det certifikat som gör det möjligt för den mobila enheten att kommunicera med företagets nätverk.<br /><br />|Apple Push Notification Service (APNs) tillhandahåller en kanal som kan användas för att nå ut till registrerade iOS-enheter. Om alla steg för att erhålla ett APNs-certifikat inte utfördes eller om APNs-certifikatet har upphört att gälla misslyckas registreringsförsöket och det här meddelandet visas.<br /><br />Mer information om hur du konfigurerar användare finns i [Synkronisera Active Directory och lägga till användare i Intune](users-add.md) och [Ordna användare och enheter](groups-add.md).|
|AccountNotOnboarded|Det är problem med det certifikat som gör det möjligt för den mobila enheten att kommunicera med företagets nätverk.<br /><br />|Apple Push Notification Service (APNs) tillhandahåller en kanal som kan användas för att nå ut till registrerade iOS-enheter. Om alla steg för att erhålla ett APNs-certifikat inte utfördes eller om APNs-certifikatet har upphört att gälla misslyckas registreringsförsöket och det här meddelandet visas.<br /><br />Mer information finns i [Konfigurera och iOS- och Mac-hantering med Microsoft Intune](ios-enroll.md).|
|DeviceTypeNotSupported|Användaren kan ha försökt att registrera en enhet som inte är iOS. Den typ av mobil enhet som du försöker registrera stöds inte.<br /><br />Kontrollera att enheten kör iOS-version 8.0 eller senare.<br /><br />|Kontrollera att användarens enhet kör iOS version 8.0 eller senare.|
|UserLicenseTypeInvalid|Enheten kan inte registreras eftersom användarens konto ännu inte är medlem i någon obligatorisk användargrupp.<br /><br />|Innan användarna kan registrera sina enheter måste de vara medlemmar i rätt användargrupp. Det här meddelandet anger att de har fel licenstyp för den angivna hanteringsauktoriteten för mobila enheter. Det här felet visas till exempel om Intune har angetts som utfärdare för hantering av mobila enheter och användarna har en licens för System Center 2012 R2 Configuration Manager.<br /><br />Se följande artiklar för mer information:<br /><br />Läs [Konfigurera iOS- och Mac-hantering med Microsoft Intune](ios-enroll.md) och informationen om hur du konfigurerar användare i [Synkronisera Active Directory och lägga till användare i Intune](users-add.md) och [Ordna användare och enheter](groups-add.md).|
|MdmAuthorityNotDefined|Utfärdaren för hantering av mobila enheter har inte definierats.<br /><br />|Utfärdaren för hantering av mobila enheter har inte angetts i Intune.<br /><br />Läs punkt 1 i avsnittet ”Steg 6: Registrera mobila enheter och installera en app” i [Kom igång med en 30-dagars utvärderingsversion av Microsoft Intune](free-trial-sign-up.md).|

### <a name="devices-are-inactive-or-the-admin-console-cannot-communicate-with-them"></a>Enheterna är inaktiva eller så kan administratörskonsolen inte kommunicera med dem
**Problem:** iOS-enheter checkar inte in med Intune-tjänsten. Enheter måste regelbundet checka in med tjänsten för att behålla åtkomst till skyddade företagsresurser. Om enheter inte checkar in:

- Kan de inte ta emot princip, appar och fjärranslutna kommandon från Intune-tjänsten.
- Visare de hanteringstillståndet **ohälsosamma** i administratörskonsolen.
- Användare som är skyddade med principer för villkorlig åtkomst kan förlora åtkomst till företagets resurser.

**Lösning:** Dela följande lösningar med dina slutanvändare för att hjälpa dem att återfå åtkomst till företagets resurser.

När användarna startar iOS-företagsportalappen kan den identifiera om enheten har tappat kontakten med Intune. Om appen upptäcker att det inte finns någon kontakt försöker den automatiskt att synkronisera med Intune för att återansluta. Användaren ser då det infogade meddelandet **Försöker synkronisera...** .

  ![Meddelandet ”Försöker att synkronisera”](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_trying_to_sync_notification.png)

Om synkroniseringen lyckas visas ett infogat meddelande som lyder **Synkronisering är klar** i iOS-företagsportalappen. Detta betyder att enheten är i felfri.

  ![Meddelandet ”Synkronisering är klar”](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_sync_successful_notification.png)

Om synkroniseringen misslyckas visas ett infogat meddelande som lyder **Det går inte att synkronisera** i iOS-företagsportalappen.

  ![Meddelandet ”Det går inte att synkronisera”](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_unable_to_sync_notification.png)

För att åtgärda problemet måste användarna trycka på knappen **Konfigurera** till höger om meddelandet **Det går inte att synkronisera**. Knappen Konfigurera tar användarna till skärmen Konfiguration av företagsåtkomst, där de kan följa anvisningarna för att registrera sina enheter.

  ![Skärmen Konfiguration av företagsåtkomst](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_company_access_setup.png)

När de registrerats återgår enheterna till ett felfritt tillstånd och återfår åtkomst till företagets resurser.

### <a name="verify-ws-trust-13-is-enabled"></a>Kontrollera att WS-Trust 1.3 är aktiverat
**Problem** Det går inte att registrera iOS-enheter med programmet för enhetsregistrering (DEP)

Registrering av DEP-enheter med användartillhörighet kräver att WS-Trust 1.3-slutpunkten användarnamn/kombinerad är aktiverad för att kunna begära användartokens. Active Directory aktiverar den här slutpunkten som standard. Hämta en lista med aktiverade slutpunkter med hjälp av PowerShell-cmdleten Get-AdfsEndpoint, som söker efter slutpunkten trust/13/UsernameMixed. Exempel:

      Get-AdfsEndpoint -AddressPath “/adfs/services/trust/13/UsernameMixed”

Mer information finns i [dokumentationen för Get-AdfsEndpoint](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

Mer information finns i [Metodtips för att skydda Active Directory Federation Services](https://technet.microsoft.com/windows-server-docs/identity/ad-fs/operations/best-practices-securing-ad-fs). Om du behöver ytterligare hjälp för att avgöra om WS-Trust 1.3 användarnamn/kombinerad är aktiverat hos din identitetsfederationsprovider kontaktar du Microsoft Support om du använder ADFS eller din tredjeparts identitetsleverantör.


### <a name="profile-installation-failed"></a>Det gick inte att installera profilen
**Problem:** En användare får felmeddelandet **Det gick inte att installera profilen** på en iOS-enhet.

### <a name="troubleshooting-steps-for-failed-profile-installation"></a>Felsökningssteg för misslyckad profilinstallation

1.  Bekräfta att användaren har tilldelats en lämplig licens för den version av Intune-tjänsten som du använder.

2.  Kontrollera att enheten inte redan har registrerats för en annan MDM-provider eller att den inte redan har en hanteringsprofil installerad.

3.  Gå till [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com) och försök att installera profilen när du uppmanas till detta.

4.  Bekräfta att Safari för iOS är standardwebbläsaren och att cookies har aktiverats.

### <a name="enrolled-ios-device-doesnt-appear-in-console-when-using-system-center-configuration-manager-with-intune"></a>En registrerad iOS-enhet visas inte i konsolen när System Center Configuration Manager används med Intune
**Problem:** Användaren registrerar iOS-enheten, men den visas inte i administrationskonsolen i Configuration Manager. Enheten visar inte att den har registrerats. Möjliga orsaker:

- Microsoft Intune Connector på din plats för konfigurationshanteraren kommunicerar inte med Intune-tjänsten.
- Antingen bearbetar inte Data Discovery Manager (ddm)-komponenten eller State Manager (statmgr)-komponenten meddelanden från Intune-tjänsten.
- Du kanske har hämtat MDM-certifikatet från ett konto och använt det för ett annat.


**Lösning:** Granska följande loggfiler efter möjliga fel:

- dmpdownloader.log
- ddm.log
- statmgr.log

Exempel läggs snart till om vad du ska leta efter i loggfilerna.


## <a name="issues-when-using-system-center-configuration-manager-with-intune"></a>Problem när du använder System Center Configuration Manager med Intune
### <a name="mobile-devices-disappear"></a>Mobila enheter försvinner
**Problem:** När du registrerar en mobil enhet i Configuration Manager försvinner den från samlingen med mobila enheter, men enheten har fortfarande hanteringsprofilen och visas i CSS Gateway.

**Lösning:** Detta kan inträffa eftersom du har en egen process som tar bort enheter som inte är anslutna till en domän eller för att användaren har dragit tillbaka enheten från prenumerationen. Följ stegen nedan om du vill kontrollera vilken process eller vilket användarkonto som tog bort enheten från Configuration Manager-konsolen.

#### <a name="check-how-device-was-removed"></a>Kontrollera hur enheten har tagits bort

1.  I administrationskonsolen i Configuration Manager väljer du **Övervakning** &gt; **Systemstatus** &gt; **Statusmeddelandefrågor**.

2.  Högerklicka på **Medlemsresurser för samlingar som togs bort manuellt** och välj **Visa meddelanden**.

3.  Välj lämplig tid/datum eller de senaste 12 timmarna.

4.  Hitta enheten i fråga och granska hur enheten har tagits bort. Exemplet nedan visar att kontot SCCMInstall tog bort enheten via ett okänt program.

    ![Skärmbild av enhetsborttagningsdiagnostik](./media/troubleshoot-device-enrollment-in-intune/CM_With_Intune_Unknown_App_Deleted_Device.jpg)

5.  Kontrollera att Configuration Manager inte har någon schemalagd aktivitet, något skript eller någon annan process som automatiskt kan rensa något som inte är anslutet till någon domän, någon, mobil eller andra relaterade enheter.




### <a name="other-ios-enrollment-errors"></a>Övriga iOS-registreringsfel
En lista med iOS-registreringsfel finns i vår dokumentation i [Felsökning av iOS-enhet med registreringsproblem i Microsoft Intune](https://support.microsoft.com/help/4039809/troubleshooting-ios-device-enrollment-in-intune).

## <a name="pc-issues"></a>Datorproblem


|Felmeddelande|Problem|Lösning|
|---|---|---|
|**Administratören behöver tilldela en licens för åtkomst**<br>IT-administratören har inte gett dig behörighet till den här appen. Kontakta IT-administratören eller försök igen senare.|Enheten kan inte registreras eftersom användarkontot inte har den nödvändiga licensen.|Innan användarna kan registrera sina enheter måste de ha tilldelats rätt licenser. Det här meddelandet anger att de har fel licenstyp för den angivna hanteringsauktoriteten för mobila enheter. Det här felet visas till exempel om Intune har angetts som utfärdare för hantering av mobila enheter och användarna har en licens för System Center 2012 R2 Configuration Manager.<br>Läs mer om hur du [tilldelar Intune-licenser till dina användarkonton](https://docs.microsoft.com/intune/licenses-assign).|



### <a name="the-machine-is-already-enrolled---error-hr-0x8007064c"></a>Datorn har redan registrerats – Fel hr 0x8007064c
**Problem:** Registreringen misslyckas med felet **Datorn har redan registrerats**. Registreringsloggen visar felet **hr 0x8007064c**.

Detta kan bero på att datorn har registrerats tidigare eller att den har den klonade avbildningen av en dator som har registrerats. Kontocertifikatet för det tidigare kontot finns kvar på datorn.



**Lösning:**

1. Öppna **Start**-menyn och ange **Kör** -> **MMC**.
1. Välj **Arkiv** > **Lägg till eller ta bort snapin-moduler**.
1. Dubbelklicka på **Certifikat**, välj **Datorkonto** > **Nästa** och sedan **Lokal dator**.
1. Dubbelklicka på **Certifikat (lokal dator)** och välj **Personliga certifikat**.
1. Leta efter Intune-certifikat som utfärdats av Sc_Online_Issuing och ta bort det om det visas.
1. Ta bort följande registernyckel om den finns: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\OnlineManagement regkey** och alla undernycklar.
1. Försök att registrera igen.
1. Om datorn fortfarande inte kan registreras letar du upp och tar bort följande nyckel, om den finns: **KEY_CLASSES_ROOT\Installer\Products\6985F0077D3EEB44AB6849B5D7913E95**.
1. Försök att registrera igen.

    > [!IMPORTANT]
    > Avsnittet, metoden eller uppgiften som beskrivs innehåller information om hur du ändrar registret. Tänk på att allvarliga problem kan inträffa om du ändrar registret på fel sätt. Se därför till att du följer anvisningarna noga. För extra skydd rekommenderar vi att du säkerhetskopierar registret innan du gör några ändringar. Du kan sedan återställa registret om det uppstår problem.
    > Mer information om hur du säkerhetskopierar och återställer registret finns i avsnittet [Säkerhetskopiera och återställa registret i Windows](https://support.microsoft.com/kb/322756)

## <a name="general-enrollment-error-codes"></a>Felkoder för allmänna registreringsfel

|Felkod|Möjligt problem|Föreslagen lösning|
|--------------|--------------------|----------------------------------------|
|0x80CF0437 |Klockan på klientdatorn är inte inställd på rätt tid.|Kontrollera att klockan och tidszonen på klientdatorn är inställda på rätt tid och tidszon.|
|0x80240438, 0x80CF0438, 0x80CF402C|Det går inte att ansluta till Intune-tjänsten. Kontrollera klientens proxyinställningar.|Kontrollera att proxykonfigurationen på klientdatorn stöds av Intune och att klientdatorn har Internetanslutning.|
|0x80240438, 0x80CF0438|Proxyinställningarna i Internet Explorer och Lokalt system har inte konfigurerats.|Det går inte att ansluta till Intune-tjänsten. Kontrollera klientens proxyinställningar och bekräfta att proxykonfigurationen på klientdatorn stöds av Intune och att klientdatorn har Internetanslutning.|
|0x80043001, 0x80CF3001, 0x80043004, 0x80CF3004|Registreringspaketet är inaktuellt.|Hämta och installera det aktuella klientprogramvarupaketet från arbetsytan Administration.|
|0x80043002, 0x80CF3002|Kontot är i underhållsläge.|Du kan inte registrera nya klientdatorer när kontot är i underhållsläge. Logga in på ditt konto för att visa dina kontoinställningar.|
|0x80043003, 0x80CF3003|Kontot har tagits bort.|Kontrollera att ditt konto och din prenumeration på Intune fortfarande är aktiva. Logga in på ditt konto för att visa dina kontoinställningar.|
|0x80043005, 0x80CF3005|Klientdatorn har tagits bort.|Vänta några timmar, ta bort alla äldre versioner av klientprogramvaran på datorn och pröva sedan att installera klientprogramvaran igen.|
|0x80043006, 0x80CF3006|Maximalt antal tillåtna klienter för kontot uppnått.|Din organisation måste köpa fler platser innan du kan registrera fler klientdatorer i tjänsten.|
|0x80043007, 0x80CF3007|Det gick inte att hitta certifikatfilen i samma mapp som installationsprogrammet.|Extrahera alla filer innan du påbörjar installationen. Byt inte namn på eller flytta någon av de hämtade filerna: alla filer måste finnas i samma mapp annars misslyckas installationen.|
|0x8024D015, 0x00240005, 0x80070BC2, 0x80070BC9, 0x80CFD015|Det går inte att installera programvaran eftersom klientdatorn väntar på att startas om.|Starta om datorn och pröva sedan att installera klientprogramvaran igen.|
|0x80070032|Ett eller flera installationskrav för klientprogramvaran kunde inte bekräftas på klientdatorn.|Kontrollera att alla nödvändiga uppdateringar är installerade på klientdatorn och pröva sedan att installera klientprogramvaran igen.|
|0x80043008, 0x80CF3008|Det gick inte att starta tjänsten Uppdatering av Microsoft onlinehantering.|Kontakta Microsoft-supporten. Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](get-support.md).|
|0x80043009, 0x80CF3009|Klientdatorn har redan registrerats i tjänsten.|Du måste inaktivera klientdatorn innan du kan registrera den igen i tjänsten.|
|0x8004300B, 0x80CF300B|Det går inte att köra installationspaketet för klientprogramvaran eftersom den version av Windows som körs på klienten inte stöds.|Intune stöder inte den version av Windows som körs på klientdatorn.|
|0xAB2|Windows Installer kunde inte komma åt VBScript-körtiden för en anpassad åtgärd.|Det här felet beror på en anpassad åtgärd som baseras på DLL:er (Dynamic-Link Libraries). När du felsöker DLL-filen kan du behöva använda de verktyg som beskrivs i [Microsoft Support-artikeln KB198038: Användbara verktyg för paket- och distributionsproblem](https://support.microsoft.com/kb/198038).|
|0x80cf0440|Anslutningen till tjänstslutpunkten avbröts.|Utvärderings- eller betalkontot har inaktiverats tillfälligt. Skapa ett nytt utvärderings- eller betalkonto och registrera dig igen.|




### <a name="next-steps"></a>Nästa steg
Om du inte lyckas lösa problemet med hjälp av den här felsökningsinformationen kontaktar du Microsoft-supporten. Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](get-support.md).