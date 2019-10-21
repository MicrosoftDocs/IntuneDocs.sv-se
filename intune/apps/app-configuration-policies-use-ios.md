---
title: Lägg till appkonfigurationsprinciper för hanterade iOS-enheter
titleSuffix: Microsoft Intune
description: Lär dig hur du använder appkonfigurationsprinciper för att skicka konfigurationsdata till en iOS-app när den körs.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c9163693-d748-46e0-842a-d9ba113ae5a8
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 94480c8dcfe44dc451ea6a2409f52f06c2a87cf5
ms.sourcegitcommit: b8127c7a62d9ac4d0f768980fa1424567bb58733
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72350078"
---
# <a name="add-app-configuration-policies-for-managed-ios-devices"></a>Lägg till appkonfigurationsprinciper för hanterade iOS-enheter

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Använd appkonfigurationsprinciper i Microsoft Intune för att ge anpassade konfigurationsinställningar för en iOS-app. Med de här konfigurationsinställningarna kan en app anpassas efter appleverantörens önskemål. Du behöver få de här konfigurationsinställningarna (nycklar och värden) från appleverantören. För att konfigurera appen anger du inställningarna som nycklar och värden eller som XML som innehåller nycklarna och värdena.

Som Microsoft Intune-administratör kan du styra vilka användarkonton som läggs till i Microsoft Office-program på hanterade enheter. Du kan begränsa åtkomsten till endast tillåtna användarkonton i organisationen och blockera personliga konton på registrerade enheter. De stödjande programmen bearbetar appkonfigurationen och tar bort och blockerar icke-godkända konton. Inställningarna för konfigurationsprincipen används när appen söker efter dem, oftast första gången den körs.

När du lägger till en appkonfigurationsprincip kan du ange tilldelningar för den. När du anger tilldelningar för principen kan du välja att inkludera och exkludera grupper av användare som principen ska gälla för. När du väljer att inkludera en eller flera grupper kan du välja att utse specifika grupper att inkludera eller välja inbyggda grupper. Inbyggda grupper innefattar **Alla användare**, **Alla enheter** samt **Alla användare och alla enheter**. 

> [!NOTE]
> Intune tillhandahåller de i förväg skapade grupperna **Alla användare** och **Alla enheter** i konsolen med inbyggda optimeringar för att förenkla för dig. Vi rekommenderar starkt att du använder de här grupperna för att ange alla användare och alla enheter som mål i stället för grupperna för ”Alla användare” eller ”Alla enheter” som du själv har skapat.

När du har valt de grupper som ska inkluderas i programkonfigurationsprincipen kan du även välja de specifika grupper som du vill exkludera. Mer information finns i [Inkludera och exkludera apptilldelningar i Microsoft Intune](apps-inc-exl-assignments.md).

> [!TIP]
> Den här principen är för närvarande endast tillgänglig för enheter som kör iOS 8.0 och senare. Den stöder följande appinstallationstyper:
>
> - **Hanterade iOS-appar från App Store**
> - **App-paket för iOS**
>
> Mer information om appinstallationstyper finns i [Så här lägger du till en app i Microsoft Intune](apps-add.md). Mer information om hur du bygger in app config i ditt .ipa-appaket för hanterade enheter finns i konfiguration av hanterade appar i dokumentationen för [iOS Developer](https://developer.apple.com/library/archive/samplecode/sc2279/Introduction/Intro.html).

## <a name="create-an-app-configuration-policy"></a>Skapa en appkonfigurationsprincip

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Välj arbetsbelastningen **Klientappar**.
4. Under gruppen **Hantera** väljer du **Appkonfigurationsprinciper** och väljer sedan **Lägg till**.
5. Ange följande information:
    - **Namn** – namnet på den profil som visas i Azure Portal.
    - **Beskrivning** – beskrivning av den profil som visas i Azure Portal.
    - **Enhetsregistreringstyp** – Välj **Hanterade enheter** för enheter som har registrerats i Intune.
6. Välj **iOS** för **Plattform**.
7. Välj **Tillhörande app**. I fönstret **Tillhörande app** väljer du den hanterade app som du vill tillämpa konfigurationen på och sedan **OK**.
8. I fönstret **Lägg till konfigurationsprincip** väljer du **Konfigurationsinställningar**.
9. Välj **Format för konfigurationsinställningar**. Välj en av följande metoder för att lägga till konfigurationsinformation:
    - **Använd Configuration Designer**
    - **Ange XML-data**<br><br>
    Information om hur du använder Configuration Designer finns i [Använda Configuration Designer](#use-configuration-designer). Information om hur du anger XML-data finns i [Ange XML-data](#enter-xml-data). 
10. När du har lagt till konfigurationsinformationen väljer du **OK** och sedan väljer du **Lägg till** för att lägga till konfigurationsprincipen. Översiktsfönstret för konfigurationsprincipen visas.
11. Välj **Tilldelningar** för att visa alternativen för att inkludera och exkludera. 

    ![Skärmbild av fliken Inkludera för principtilldelningar](./media/app-configuration-policies-use-ios/app-config-policy01.png)
12. Välj **Alla användare** på fliken **Inkludera**.

    ![Skärmbild av principtilldelningar – listrutealternativet Alla användare](./media/app-configuration-policies-use-ios/app-config-policy02.png)
13. Välj fliken **Exkludera**. 
14. Klicka på **Välj grupper att utesluta** för att visa det relaterade fönstret.

    ![Skärmbild av principtilldelningar – bladet Välj grupper att undanta](./media/app-configuration-policies-use-ios/app-config-policy03.png)
15. Välj de grupper som du vill exkludera och klicka sedan på **Välj**.

    >[!NOTE]
    >Om någon annan grupp redan har inkluderats för en viss tilldelning när du lägger till en grupp så blir den förvald och kan inte ändras för andra tilldelningstyper för inkludering. Gruppen som har använts kan därför inte användas som en undantagen grupp.
16. Klicka på **Spara**.

## <a name="use-configuration-designer"></a>Använda Configuration Designer

Microsoft Intune ger konfigurationsinställningar som är unika för en app. Du kan använda Configuration Designer för appar både på enheter som har registrerats och enheter som inte har registrerats i Microsoft Intune. Med Designer kan du konfigurera specifika konfigurationsnycklar och värden som hjälper dig att skapa underliggande XML. Du måste även ange datatyp för varje värde. De här inställningarna skickas automatiskt till appar när apparna installeras.

### <a name="add-a-setting"></a>Lägg till en inställning

1. För varje nyckel och värde i konfigurationen anger du:
   - **Konfigurationsnyckel** – den nyckel som unikt identifierar den specifika konfigurationsinställningen.
   - **Värdetyp** – konfigurationsvärdets datatyp. Möjliga typer är heltals-, verklig, sträng- eller booleskt värde.
   - **Konfigurationsvärde** – värdet för konfigurationen.
2. Välj **OK** för att ange konfigurationsinställningar.

### <a name="delete-a-setting"></a>Ta bort en inställning

1. Välj de tre punkterna ( **...** ) bredvid inställningen.
2. Välj **Ta bort**.

Tecknen \{\{ och \}\} används endast av tokentyper och får inte användas för andra ändamål.

### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>Tillåt endast konfigurerade organisationskonton i appar med flera identiteter 

Använd följande nyckel-/värdepar för iOS-enheter:

| **Nyckel** | IntuneMAMAllowedAccountsOnly |
|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Värden** | <ul><li>**Aktiverad**: Det enda kontot som tillåts är det hanterade användarkonto som definierats av nyckeln [IntuneMAMUPN](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm).</li><li>**Inaktiverad** (eller ett värde som inte är en skiftlägesokänslig matchning till **Aktiverad**): Alla konton tillåts.</li></ul> |.

   > [!NOTE]
   > Du måste använda OneDrive för iOS 10.34 eller senare, Outlook för iOS 2.99.0 eller senare, eller Edge för iOS 44.8.7 eller senare. Appen måste vara riktad mot [Intunes appskyddsprinciper](app-protection-policy.md) när endast konfigurerade organisationskonton med flera identiteter tillåts.

## <a name="enter-xml-data"></a>Ange XML-data

Du kan ange eller klistra in en XML-egenskapslista som innehåller appkonfigurationsinställningarna för enheter som registrerats i Intune. Formatet på XML-egenskapslistan varierar beroende på vilken app du konfigurerar. Kontakta appleverantören för information om vilket format du ska använda.

Intune verifierar XML-formatet. Intune kontrollerar dock inte om XML-egenskapslistan (PList) fungerar med målappen.

Läs mer om XML-egenskapslistor:

- Hänvisa till [Understand XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) (Förstå XML-egenskapslistor) i iOS Developer Library.

### <a name="example-format-for-an-app-configuration-xml-file"></a>Exempelformat för en XML-fil för en appkonfiguration

När du skapar en appkonfigurationsfil kan du ange ett eller flera av följande värden med hjälp av det här formatet:

```xml
<dict>
  <key>userprincipalname</key>
  <string>{{userprincipalname}}</string>
  <key>mail</key>
  <string>{{mail}}</string>
  <key>partialupn</key>
  <string>{{partialupn}}</string>
  <key>accountid</key>
  <string>{{accountid}}</string>
  <key>deviceid</key>
  <string>{{deviceid}}</string>
  <key>userid</key>
  <string>{{userid}}</string>
  <key>username</key>
  <string>{{username}}</string>
  <key>serialnumber</key>
  <string>{{serialnumber}}</string>
  <key>serialnumberlast4digits</key>
  <string>{{serialnumberlast4digits}}</string>
  <key>udidlast4digits</key>
  <string>{{udidlast4digits}}</string>
  <key>aaddeviceid</key>
  <string>{{aaddeviceid}}</string>
</dict>
```

### <a name="supported-xml-plist-data-types"></a>XML PList-datatyper som stöds

Intune har stöd för följande datatyper i en egenskapslista:

- &lt;heltal&gt;
- &lt;verklig&gt;
- &lt;sträng&gt;
- &lt;matris&gt;
- &lt;dict&gt;
- &lt;sant/&gt; eller &lt;falskt/&gt;

### <a name="tokens-used-in-the-property-list"></a>Token som används i egenskapslistan

Dessutom stöder Intune följande typer av token i egenskapslistan:
- \{\{userprincipalname\}\} – till exempel **John@contoso.com**
- \{\{mail\}\} – till exempel **John@contoso.com**
- \{\{partialupn\}\} – till exempel **John**
- \{\{accountid\}\} – till exempel **fc0dc142-71d8-4b12-bbea-bae2a8514c81**
- \{\{deviceid\}\} – till exempel **b9841cd9-9843-405f-be28-b2265c59ef97**
- \{\{userid\}\} – till exempel **3ec2c00f-b125-4519-acf0-302ac3761822**
- \{\{username\}\} – till exempel **Johan Danielsson**
- \{\{serialnumber\}\} – till exempel **F4KN99ZUG5V2** (för iOS-enheter)
- \{\{serialnumberlast4digits\}\} – till exempel **G5V2** (för iOS-enheter)
- \{\{aaddeviceid\}\} – till exempel **ab0dc123-45d6-7e89-aabb-cde0a1234b56**

## <a name="configure-the-company-portal-app-to-support-ios-dep-devices"></a>Konfigurera företagsportalappen så att den stöder iOS DEP-enheter

DEP-registreringar (Apples enhetsregistreringsprogram) är inte kompatibla med App Store-versionen av företagsportalappen. Du kan dock konfigurera företagsportalappen så att den stöder iOS DEP-enheter med följande steg.

1. I Intune på Azure-portalen:
    - Lägg till Intune-företagsportalen vid behov genom att gå till **Intune** > **Klientappar** > **Appar** > **Lägg till**.
    - Gå till **Klientappar** > **Appkonfigurationsprinciper** för att skapa en konfigurationsprincip för appar för företagsportalappen.
2. Skapa en appkonfigurationsprincip med XML nedan. Mer information om hur du skapar en konfigurationsprincip för appar och anger XML-data finns i [Lägg till konfigurationsprinciper för hanterade iOS-enheter](app-configuration-policies-use-ios.md) eller, för hybrid MDM, [Tillämpa inställningar på iOS-appar med appkonfigurationsprinciper i System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-ios-apps-with-app-configuration-policies).

    ``` xml
    <dict>
        <key>IntuneCompanyPortalEnrollmentAfterUDA</key>
        <dict>
            <key>IntuneDeviceId</key>
            <string>{{deviceid}}</string>
            <key>UserId</key>
            <string>{{userid}}</string>
        </dict>
    </dict>
    ```

3. Distribuera företagsportalen till enheter där appkonfigurationsprincipen är riktad mot de önskade grupperna. Se till att endast distribuera principen till enhetsgrupper som redan är DEP-registrerade.
4. Be slutanvändarna att logga in på företagsportalappen när den installeras automatiskt.

## <a name="monitor-ios--app-configuration-status-per-device"></a>Övervaka konfigurationsstatus för iOS-appar per enhet 
När en konfigurationsprincip har tilldelats kan du övervaka iOS-appens konfigurationsstatus för varje hanterad enhet. Gå till **Microsoft Intune** i Azure Portal och välj **Enheter** > **Alla enheter**. Välj en specifik enhet från listan med hanterade enheter för att visa ett blad för enheten. Välj **Appkonfiguration** på enhetsbladet.  

## <a name="additional-information"></a>Ytterligare information

- [Distribuera appkonfigurationsinställningar för Outlook för iOS och Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)

## <a name="next-steps"></a>Nästa steg

Fortsätt sedan med att [tilldela](apps-deploy.md) och [övervaka](apps-monitor.md) appen.