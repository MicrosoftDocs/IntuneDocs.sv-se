---
title: "UI-uppdateringar för Intune-appar för slutanvändare"
description: "Ta reda på vad som har ändrats i gränssnittet för appar som fungerar på slutanvändarenheter med Intune."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b782e382-8deb-48a7-a437-d7c5a17163f1
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 948a7d2e4e0ad80088d864708db5733f08db77c5
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="ui-updates-for-intune-end-user-apps"></a>UI-uppdateringar för Intune-appar för slutanvändare
Lär dig mer om de senaste uppdateringarna i användargränssnittet för appar som dina slutanvändare ser i den här versionen av Microsoft Intune. Detta kan hjälpa dig med användarkommunikation och att uppdatera anpassad dokumentation som du har skapat för att stödja distributionen. Det underlättar också felsökningen av eventuella problem som användarna har om de kontaktar supportavdelningen för att få hjälp med att använda företagsportalen.

## <a name="week-of-july-31-2017"></a>Veckan 31 juli 2017

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Förbättrad inloggning i företagsportalens appar för alla plattformar <!--User Story 1132123-->

Vi presenterar en ändring under de kommande månaderna som förbättrar inloggningen för Intune-företagsportalens appar för Android, iOS och Windows. Det nya användargränssnittet visas automatiskt på alla plattformar för företagsportalappen när Azure AD genomför ändringen. Dessutom kan användarna nu logga in på företagsportalen från en annan enhet med en engångskod som genereras. Detta är särskilt användbart när användarna måste logga in utan autentiseringsuppgifter.  

Nedan kan du se föregående inloggning, den nya inloggningen med autentiseringsuppgifter och den nya inloggningen från en annan enhet.

__Föregående inloggning__

![Företagsportalens inloggningssida med en ikon för en person framför en grafisk representation av en webbplats. Nedanför finns knappen ”Logga in”. En länk längst ner leder till Microsofts information om sekretess och cookies.](./media/cp_ios_aad_signin_before_1704_001.png)

![Användarna anger sina autentiseringsuppgifter på den här sidan när de har tryckt på Logga in, vilken begär användarens e-post och lösenord, tillsammans med förslag på att lösa lösenordsfel.](./media/cp_ios_aad_signin_before_1704_002.png)

![När de har angett sina lösenord loggas de in på företagsportalappen, vilket visas med en förloppsindikator.](./media/cp_ios_aad_signin_before_1704_003.png)

__Ny inloggning__

![Företagsportalens inloggningssida med en ikon för en person framför en grafisk representation av en webbplats. Nedanför finns knappen ”Logga in”. En länk längst ner leder till Microsofts information om sekretess och cookies.](./media/cp_ios_aad_signin_after_1704_001.png)

![Användaren ombeds endast att ange sin e-postadress, i stället för sin e-post och lösenord på samma skärm.](./media/cp_ios_aad_signin_after_1704_002.png)

![Användaren uppmanas att ange lösenordet när e-postadressen har accepterats.](./media/cp_ios_aad_signin_after_1704_003.png)

![Efter att genomgått autentiseringsprocessen loggas företagsportalappen in, vilket visas med en förloppsindikator.](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

__Ny inloggning vid inloggning från en annan enhet__

![Företagsportalens inloggningssida med en ikon för en person framför en grafisk representation av en webbplats. Nedanför finns knappen ”Logga in”. En länk längst ner leder till Microsofts information om sekretess och cookies.](./media/cp_ios_aad_signin_from_another_device_after_1704_001.png)

Tryck på länken __Logga in från en annan enhet__.

![Instruktioner visas för att gå till sidan aka.ms/devicelogin med ett unikt lösenord från din arbetsdator. Därefter använder du koden för att logga in.](./media/cp_ios_aad_signin_from_another_device_after_1704_003.png)

Starta en webbläsare och gå till [https://aka.ms/devicelogin](https://aka.ms/devicelogin).

![En bild av användarens webbläsare på arbetsdatorn, i stället för företagsportalappen. Sidan ”Inloggning på enhet” visas och uppmanar användarna ange koden de fick i företagsportalsappen.](./media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

Ange koden som du såg i företagsportalsappen. När du väljer __Fortsätt__, kommer du att kunna autentisera med någon av metoderna som stöds av ditt företag, till exempel ett smartkort.

![Användaren har matat in sin unika kod i fältet och webbplatsen ”Inloggning på enhet” har begärt en bekräftelse på att Intunes företagsportal är rätt app för att få behörighet att logga in.](./media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

![En bekräftelsesida som anger att användaren har loggat in i företagsportalsappen på sin enhet visas nu, och den här sidan kan stängas.](./media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

Företagsportalappen börjar logga in.

![Efter att genomgått autentiseringsprocessen loggas företagsportalappen in, vilket visas med en förloppsindikator.](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

## <a name="week-of-june-12-2017"></a>Vecka 12 juni 2017

### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>Företagsportalappen för Android har nu ett nytt användargränssnitt för appskyddsprinciper <!--1305217-->
Baserat på feedback från våra kunder har vi ändrat företagsportalappen för Android så att den visar knappen **Åtkomst till företagsinnehåll**. Avsikten är att förhindra användare från att i onödan gå genom registreringsprocessen när de bara behöver åtkomst till appar som stöder appskyddsprinciper, en funktion i Intune för hantering av mobilappar.

Användaren kan då trycka på knappen **Åtkomst till företagsinnehåll** i stället för att börja registrera enheten.

![En bild av Android-företagsportalappen, som i stor text visar Åtkomst till företagsinnehåll i mitten i stället för att erbjuda registreringsalternativ som i standardfallet](./media/and_access_company_content_after_1706.png)

Användaren tas sedan till webbplatsen för företagsportalen för att auktorisera appen för användning på sin enhet. Användarens autentiseringsuppgifter verifieras på webbplatsen för företagsportalen.

![En bild på när webbplatsen för företagsportalen bekräftar inloggningen.](./media/and_iwp_sign_in_auth_page_after_1706.png)

Enheten kan fortfarande registreras för fullständig hantering genom att användaren trycker på menyn **Åtgärd**.

![En bild av företagsportalappen för Android som visar menyn från det övre högra hörnet på skärmen med ett alternativ för att registrera enheten.](./media/and_sign_in_menu_after_app_protection_policy_enrolled_after_1706.png)

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Förbättringar av appsynkronisering med Windows 10 Creators Update <!--676505-->

Företagsportalen för Windows 10 kommer automatiskt att initiera en synkronisering för appinstallationsbegäranden för enheter med Windows 10 Creators Update (1703). Detta minskar problemen där appen fastnar vid tillståndet ”Väntar på synkronisering” när installationer utförs. Dessutom kommer användare att kunna initiera en synkronisering från appen manuellt.

![En bild av företagsportalappen för Windows 10, där hämtningen av Microsoft Word är i ett väntande tillstånd från företagsportalens appbutik.](./media/w10_download_pending_after_1706.png)

![En bild av företagsportalappen för Windows 10 där den nya automatiska synkroniseringsstatusen visar ett statusmeddelande som anger att enheten synkroniseras och försöker ladda ned appen.](./media/w10_download_pending_syncing_after_1706.png)

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Ny guidad upplevelse för Windows 10-företagsportalen <!---1058938--->
Företagsportalappen för Windows 10 kommer att innehålla en guidad Intune-genomgång för enheter som inte har identifierats eller registrerats. Den nya guiden innehåller stegvisa anvisningar som hjälper användaren att utföra AAD-registrering (krävs för villkorliga åtkomstfunktioner) och MDM-registrering (krävs för enhetshanteringsfunktioner). Guiden kommer att vara tillgänglig på företagsportalens startsida. Användarna kan fortsätta att använda appen även om de inte slutför registreringen, men de får begränsad funktionalitet.

Den här uppdateringen visas bara på enheter som kör Windows 10 Anniversary Update (version 1607) eller senare.

![En bild av startsidan i företagsportalappen i Windows 10 med ett statusmeddelande i mitten av enhetslistan som talar om för användaren att enheten han eller hon använder inte har konfigurerats för företagsanvändning ännu och att användaren ska välja meddelandet för att påbörja installationen.](./media/win10_guided_enroll_select_setup_after_1706.png)

![En bild av konfigureringssidan i företagsportalappen i Windows 10 med en varning för användaren om att han eller hon behöver lägga till ett företagskonto till den här enheten och sedan registrera enheten för hantering.](./media/win10_guided_enroll_we_help_setup_after_1706.png)

![En bild av sidan add corporate account to this device page (lägg till ett företagskonto till den här enheten) i företagsportalappen i Windows 10, där användaren uppmanas att gå till appen Inställningar och välja Anslut för att slutföra registreringen. När användaren har gjort det visas ett meddelande om att användaren måste gå tillbaka till företagsportalappen och slutföra registreringen.](./media/win10_guided_enroll_leaving_for_iwp_after_1706.png)

![En bild av skärmen enroll into management (registrera för hantering) i företagsportalappen i Windows 10 som visar ett statusmeddelande om slutförd åtgärd som informerar om att användarens enhet nu har registrerats och att användaren ska trycka på Nästa för att fortsätta.](./media/win10_guided_enroll_youre_now_enrolled_after_1706.png)

![En bild av slutförandeskärmen i företagsportalappen i Windows 10, där användaren informeras om att allt är klart samt att enheten har registrerats och ett företagskonto har lagts till det på rätt sätt.](./media/win10_guided_enroll_youre_all_set_after_1706.png)

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>Ny menyåtgärd för att enkelt ta bort Företagsportalen <!--1164569-->
Baserat på användarfeedback har vi lagt till en ny menyåtgärd i företagsportalen för Android för att ta bort den från din enhet. Den här åtgärden tar bort enheten från Intune-hanteringen så att användaren kan ta bort appen från enheten.

![En bild av företagsportalappen för Android med åtgärdsmenyn öppnad i det övre högra hörnet. Det nya alternativet ”ta bort företagsportal” finns tillgängligt som det tredje alternativet under ”min profil” och ”inställningar” och ovanför ”användarvillkor”, ”hjälp och feedback” och ”om”.](./media/android_remove_cp_menu_action_after_1705.png)

![En bild av dialogrutan som visas när du har valt det nya alternativet ”ta bort företagsportalen” i åtgärdsmenyn. Dialogrutan informerar användaren att ”genom att ta bort företagsportalen kommer enheten inte längre att hanteras av IT-administratören och åtkomst till företagsdata, företagsappar och företagets e-post kan tas bort." Användaren ombes sedan att bekräfta att de vill ta bort företagsportalappen genom att välja ”Ja”.](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="week-of-june-5-2017"></a>Vecka 5 juni 2017

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>Förbättringar av appaneler i företagsportalappen för iOS
Vi har uppdaterat designen av appaneler på startsidan så att de återspeglar anpassningsfärgen som du angett för Företagsportalen.

**Före**

![En avbildning av företagsportalsappen för iOS från tidpunkten innan uppdateringen gjordes, och som visade förinställda utfyllningsbilder för ”alla appar”, ”aktuella appar” och ”kategorier."](./media/cp_ios_homepage_before_1705.png)

**Efter**

![En bild av företagsportalsappen för iOS efter uppdateringen, vilken nu visar möjligheten att välja de färger som är relevanta för din organisation.](./media/cp_ios_homepage_after_1705.png)

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>Kontoväljaren finns nu tillgänglig för företagsportalappen för iOS
Om användarna har använt sina arbets- eller skolkonton för att logga in till andra Microsoft-appar på sina iOS-enheter, så kan det hända att de ser den nya kontoväljaren när de loggar in på företagsportalen för första gången.

![En bild av kontoväljaren som visar testanvändaren Robin Swanson som väljer mellan en av två e-postadresser. Det finns olika knappar under de respektive adresserna, med vilka användaren kan välja konto att logga in med.](./media/cp_ios_multi-account-selector-after-1705.png)

## <a name="april-2017"></a>April 2017

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Nya ikoner för Managed Browser och företagsportalen <!--918433, 918431-->

Den hanterade webbläsaren får uppdaterade ikoner för både Android- och iOS-versionerna av appen. Den nya ikonen innehåller det uppdaterade Intune-märket så att det överensstämmer med andra appar i Enterprise Mobility + Security (EM+S).

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_manbro_before_042017.png" alt="The previous version of the Managed Browser app icon." width=200 height=366 align=center>
          </td>
          <td>
             <img src="/intune/media/cp_manbro_after_042017.png" alt="The updated version of the Managed Browser app icon." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

Företagsportalen har också fått uppdaterade ikoner för Android-, iOS- och Windows-versionerna av appen, för att förbättra enhetligheten med andra appar i EM+S. Dessa ikoner släpps gradvis till plattformarna från april till slutet av maj.

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Förloppsindikator för inloggning i Android-företagsportalen <!--953374-->

En uppdatering av Android-företagsportalappen visar en förloppsindikator för inloggning när användaren startar eller återupptar appen. Indikatorn visar nya statusmeddelanden, med början på ”Ansluter...”, sedan ”Loggar in...”, följt av ”Kontrollerar säkerhetskrav...” innan användaren får åtkomst till appen.

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_android_connecting_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Connecting' underneath it." width=200 height=366 align=center>
          </td>
          <td>
             <img src="/intune/media/cp_android_signing_in_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Signing in' underneath it." width=200 height=366 align=center>
           </td>
           <td>
              <img src="/intune/media/cp_android_checking_security_reqs_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Checking for security requirements' underneath it." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Appens installationsstatus har förbättrats för Företagsportalappen för Windows 10 <!--676495-->
Företagsportalappen för Windows 10 innehåller nu en förloppsindikator för installation på appinformationssidan. Den stöds för moderna appar på enheter som kör Windows 10 Anniversary Update och senare.

__Före__ ![En avbildning av den tidigare versionen av inläsningsskärmen där status bara angavs som "Installerar".](./media/cp_win10_install_status_before_1704.png)

__Efter__ ![En avbildning av den uppdaterade versionen av inläsningsskärmen nu visar en förloppsindikator för installationen.](./media/cp_win10_install_status_after_1704.png)

## <a name="february-2017"></a>Februari 2017

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622-announced-1702--"></a>Ny användarupplevelse för företagsportalappen för Android <!--621622, announced 1702-->
Från och med mars följer företagsportalsappen för Android [riktlinjer för materialdesign](https://material.io/guidelines/material-design/introduction.html) för att skapa en modernare känsla och ett modernare utseende. Den här förbättrade användarupplevelsen innehåller:

* __Färger__: Flikrubriken kan färgas enligt din anpassade färgpalett.

![Till vänster finns en avbildning av företagsportalappen för Android före uppdateringen. Till höger finns en avbildning av företagsportalappen för Android efter uppdateringen. Båda bilderna visar fliken Enheter som den valda fliken från de tre tillgängliga flikarna Appar, Enheter och Kontakta IT.](./media/CP_Android_DevicesTab_BeforeAfter.png)

* __Gränssnitt__: Knapparna __Aktuella appar__ och __Alla appar__ har uppdaterats på fliken __Appar__. __Sökknappen__ är nu flytande.

![Till vänster finns en avbildning av företagsportalappen för Android före uppdateringen. Till höger finns en avbildning av företagsportalappen för Android efter uppdateringen. Båda bilderna visar fliken Appar som den valda fliken från de tre tillgängliga flikarna Appar, Enheter och Kontakta IT.](./media/CP_Android_AppsTab_BeforeAfter.png)

* __Navigering__: Alla appar visar en flikvy över __Aktuella__, __Alla__ och __Kategorier__ för att underlätta navigeringen. __Kontakta IT__ har effektiviserats för bättre läsbarhet.

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_android_contactit_after.png" alt="The Company Portal app for Android displaying an updated version of the Contact IT tab. The tab shows available contact information for IT, including phone number, email address, IT website, and IT contact information." width=200 height=366 align=center>
          </td>
      </tr>
   </table>
</body>
</html>

## <a name="january-2017"></a>Januari 2017

### <a name="modernizing-the-company-portal-website---753980-announced-1701--"></a>Modernisera företagsportalswebbplatsen <!--753980, announced 1701-->
Från och med februari kommer företagsportalens webbplats att ha stöd för appar som är avsedda för användare som inte har några hanterade enheter. Webbplatsen anpassas med andra Microsoft-produkter och tjänster med hjälp av ett nytt kontrasterande färgschema, dynamiska bilder och en "hamburgarmeny", ![En liten bild på hamburgarmenyn som nu är tillagd i det övre vänstra hörnet på företagsportalens webbplats](./media/CP_hamburger_menu.png) som innehåller kontaktinformation till supportavdelningen och information om befintliga hanterade enheter. Landningssidan ordnas om för att betona appar som är tillgängliga för användare med karuseller för aktuella och nyligen uppdaterade appar.

![Till vänster visas en bild av den aktuella versionen av webbplatsen för företagsportalen med dess tidigare version av Appar, Mina enheter och vyerna Aktuellt och Kategorier. Till höger visas en bild av den uppdaterade versionen av webbplatsen för företagsportalen med en uppdaterad appkarusell, lista över nyligen publicerade appar och uppdaterad kategorivy.](./media/CP_Website_BeforeAfter_Feb2016.png)

## <a name="coming-soon-in-the-ui"></a>Kommer snart i användargränssnittet
Det här är våra planer för hur vi kan förbättra användarupplevelsen genom att uppdatera användargränssnittet.

> [!Note]
> Observera att bilderna nedan kan vara förhandsgranskningar och att den presenterade produkten kan skilja sig från presenterade versioner.

### <a name="ui-updates-to-the-company-portal-website---1313244-part-2--"></a>Gränssnittsuppdateringar på företagsportalswebbplatsen <!--1313244 part 2-->

__Uppdateringar av aktuella appar__ Vi har lagt till en särskild sida på webbplatsen där användarna kan bläddra bland appar som du har valt att presentera, och vi har gjort några gränssnittsförändringar på avsnittet Aktuella på startsidan.

![De färggranna ikonerna visar apparna. Det finns stora rutor med färg under varje app, där färgen hämtas från den huvudsakliga färgen i appens logotyp. Avsnittet ”Aktuella appar” visas längst upp i företagsportalappen.](./media/cp_win10_colorful_tiles_after_1708.png)

### <a name="see-also"></a>Se även
* [Microsoft Intune-blogg](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Översikt över molnplattformen](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Nyheter i Intune](https://docs.microsoft.com/intune/whats-new)