---
title: Hantera företagets webbåtkomst med en principskyddad webbläsare
titleSuffix: Microsoft Intune
description: Använd en principskyddad webbläsare som är tilldelad av Intune till att hantera företagets webbsurfning och överföring av webbdata.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1feca24f-9212-4d5d-afa9-7c171c5e8525
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 63e3a02f9df52052f27714403e8f189d089c6690
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725900"
---
# <a name="manage-web-access-using-a-microsoft-intune-policy-protected-browser"></a>Hantera Internetåtkomst med hjälp av en Microsoft Intune-principskyddad webbläsare

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Med en webbläsare som skyddas med Intune-principer (Microsoft Edge eller Intune Managed Browser) kan du vara säker på att åtkomsten till företagswebbplatser alltid är skyddad.  När de har konfigurerats med Intune kan skyddade webbläsare dra nytta av följande:

- Programskyddsprinciper
- Villkorlig åtkomst
- Enkel inloggning
- Inställningar för programkonfiguration
- Integrering av en Azure-programproxy

## <a name="microsoft-edge-support"></a>Microsoft Edge-stöd

Du kan använda Microsoft Edge för företagsscenarier på iOS- och Android-enheter. Microsoft Edge har stöd för samma hanteringsscenarier som Intune Managed Browser, men där finns dessutom förbättringar av användarupplevelsen. Nedanstående Microsoft Edge-företagsfunktioner som aktiveras med Intune-principer är tillgängliga:

- **Dubbel identitet** – Användarna kan lägga till både ett arbetskonto och ett personligt konto för surfning. Det finns en fullständig uppdelning mellan de två identiteterna, vilket liknar arkitektur och funktioner i Office 365 och Outlook. Intune-administratörer kommer att kunna ställa in de önskade principerna för en skyddad surfupplevelse på arbetskontot. 
- **Integrering med Intunes appskyddsprincip** – Administratörer kan nu använda appskyddsprinciper i Microsoft Edge, inklusive kontroll av klipp ut, kopiera och klistra in, förhindra skärmdumpar och säkerställa att användarvalda länkar bara öppnas i andra hanterade appar.
- **Integrering med Azure Application-proxy** – Administratörer kan styra åtkomsten till SaaS-appar och webbappar, vilket garanterar att webbläsarbaserade appar endast körs i den skyddade Microsoft Edge-webbläsaren, oavsett om användarna ansluter från företagets nätverk eller från Internet. 
- **Genvägar till hanterade favoriter och startsida** – För att underlätta åtkomsten kan administratörer ange URL:er som visas i Favoriter när slutanvändarna använder sin företagsmiljö. Administratörer kan ange en genväg till startsidan som visas som primär genväg när företagsanvändaren öppnar en ny sida eller en ny flik i Microsoft Edge.

Microsoft Intunes skyddsprinciper för Microsoft Edge hjälper till att skydda din organisations data och resurser. Intune-skyddade Microsoft Edge säkerställer att företagets resurser skyddas, inte bara i internt installerade appar, utan även när de öppnas via en webbläsare.

## <a name="getting-started"></a>Komma igång

Microsoft Edge och Intune Managed Browser är webbappar för webbläsare som du och slutanvändarna kan hämta från offentliga appbutiker för användning i din organisation. 

Operativsystemkrav för webbläsarprinciper:
- Android 4 och senare eller
- iOS 8.0 och senare.

Tidigare versioner av Android och iOS kommer att kunna fortsätta att använda Managed Browser, men kommer inte att kunna installera nya versioner av appen och kanske inte använda alla funktioner. Vi rekommenderar att du uppdaterar de här enheterna till en version av operativsystemet som stöds.

>[!NOTE]
>Managed Browser inte har stöd för det kryptografiska protokollet Secure Sockets Layer version 3 (SSLv3).


## <a name="application-protection-policies-for-protected-browsers"></a>Principer för programskydd för skyddade webbläsare

Eftersom Microsoft Edge och Managed Browser har integrering med Intune SDK kan du även använda appskyddsprinciper för dem, som att:
- Styra användningen av klipp ut, kopiera och klistra in.
- Förhindra skärmdumpar.
- Säkerställa att företagets länkar bara öppnas i hanterade appar och webbläsare.

Mer information finns i [Vad är appskyddsprinciper?](app-protection-policy.md)

Du kan tillämpa inställningarna för att:

- Enheter som har registrerats med Intune
- Registrerade med en annan MDM-produkt
- Ohanterade enheter

>[!NOTE]
>Om användarna installerar Managed Browser från appbutiken och Intune inte hanterar den, kan den användas som en vanlig webbläsare med stöd för enkel inloggning via webbplatsen Microsoft MyApps. Användarna dirigeras direkt till webbplatsen MyApps där de kan se alla sina etablerade SaaS-program.
Eftersom Managed Browser och Microsoft Edge inte hanteras av Intune har de inte åtkomst till några data från andra Intune-hanterade program. 


## <a name="conditional-access-for-protected-browsers"></a>Villkorlig åtkomst för skyddade webbläsare

Managed Browser är nu en godkänd klientapp för villkorlig åtkomst. Det innebär att du kan begränsa mobil webbläsaråtkomst till Azure AD-anslutna webbappar där användarna bara kan använda Managed Browser, vilket blockerar åtkomsten från andra oskyddade webbläsare som Safari eller Chrome. Det här skyddet kan tillämpas på Azure-resurser som Exchange Online och SharePoint Online, Administrationscenter för Microsoft 365 och även lokala platser som du exponerar för externa användare via [Azure AD-programproxyn](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started). 

Om du vill begränsa Azure AD-anslutna webbappars användning av Intune Managed Browser på mobila plattformar, kan du skapa en villkorsstyrd åtkomstprincip som kräver godkända klientprogram. 

> [!TIP]  
> Villkorsstyrd åtkomst är en Azure Active Directory-teknik (Azure AD). Den nod för villkorsstyrd åtkomst som nås från *Intune* är samma nod som den som nås från *Azure AD*.  


1. I Intune-portalen väljer du **Villkorsstyrd åtkomst** > **Ny princip**. 
2. Välj därefter **Bevilja** i avsnittet **Åtkomstkontroller** på bladet. 
3. Klicka på **Kräv godkänd klientapp**. 
4. Klicka på **Välj** på bladet **Bevilja**. Den här principen måste tilldelas till de molnappar som du vill ska vara tillgängliga enbart för appen Intune Managed Browser.

    ![Azure AD – villkorlig åtkomstprincip för Managed Browser](./media/app-configuration-managed-browser/managed-browser-conditional-access-01.png)

5. I avsnittet **Tilldelningar** väljer du **Villkor** > **Klientappar**. Bladet **Klientappar** visas.
6. Klicka på **Ja** under **Konfigurera** för att tillämpa principen på specifika klientappar.
7. Kontrollera att **Webbläsare** har valts som klientapp.

    ![Azure AD – Managed Browser – Välj klientappar](./media/app-configuration-managed-browser/managed-browser-conditional-access-02.png)

    > [!NOTE]
    > Om du vill begränsa vilka interna appar (icke-webbläsarbaserade appar) som har åtkomst till dessa molnprogram kan du också välja **Mobilappar och skrivbordsklienter**.

8. I avsnittet **Tilldelningar** väljer du **Användare och grupper** och sedan de användare eller grupper som du vill tilldela den här principen till. 

    > [!NOTE]
    > Användarna måste också använda principen Intune-appskydd för att kunna ta emot principer för appkonfiguration. Mer information om att skapa Intune-appskyddsprinciper finns i [Vad är appskyddsprinciper?](app-protection-policy.md)

9. I avsnittet **Tilldelningar** går du till **Molnappar** och väljer vilka appar som ska skyddas med den här principen.

När du har konfigurerat principen ovan tvingas användarna använda Intune Managed Browser för att få åtkomst till de Azure AD-anslutna webbappar som du har skyddat med den här principen. Om användarna försöker använda en ohanterad webbläsare i det här scenariot, visas ett meddelande om att Intune Managed Browser måste användas i stället.

Managed Browser har inget stöd för klassiska principer för villkorlig åtkomst. Mer information finns i [Migrera klassiska principer i Azure Portal](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-migration).

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>Enkel inloggning till Azure AD-anslutna webbappar i principskyddade webbläsare

Microsoft Edge och Intune Managed Browser i iOS och Android kan dra nytta av enkel inloggning till alla webbappar (SaaS och lokala) som är Azure AD-anslutna. Om Microsoft Authenticator-appen finns i iOS eller Intune-företagsportalappen i Android, kommer användare av principskyddade webbläsare att kunna komma åt Azure AD-anslutna webbappar utan att ange sina autentiseringsuppgifter på nytt.

Enkel inloggning kräver att din enhet har registrerats av Microsoft Authenticator-appen i iOS eller på Intune-företagsportalen i Android. Användare med Authenticator-appen eller Intune-företagsportalen uppmanas att registrera sin enhet när de navigerar till en Azure AD-ansluten webbapp i en principskyddad webbläsare, om enheten inte redan har registrerats av ett annat program. När enheten är registrerad med kontot som hanteras av Intune, kommer detta konto ha enkel inloggning aktiverat för Azure AD-anslutna webbappar. 

> [!NOTE]
> Enhetsregistrering är en enkel incheckning med Azure AD-tjänsten. Det kräver inte fullständig enhetsregistrering och inte ger IT-avdelningen ytterligare behörighet på enheten.

## <a name="create-a-protected-browser-app-configuration"></a>Skapa en appkonfiguration för en skyddad webbläsare

>[!IMPORTANT]
>För att appkonfigurationer ska tillämpas så måste den användarskyddade webbläsaren eller en annan app på enheten redan hanteras av [Intunes appskyddsprincip]( ../app-protection-policy.md)

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. På bladet **Klientappar** i listan Hantera väljer du **Appkonfigurationsprinciper**.
4. På bladet **Appkonfigurationsprinciper** väljer du **Lägg till**.
5. På bladet **Lägg till konfigurationsprincip** anger du ett **Namn** och en valfri **Beskrivning** för appkonfigurationsinställningarna.
6. För **Registreringstyp för enhet** väljer du **Hanterade appar**.
7. Välj alternativet **Välj den obligatoriska appen** och klicka på bladet **Riktade appar**. Välj sedan **Managed Browser** och/eller **Edge** för iOS, Android eller båda.
8. Välj **OK** för att återgå till bladet **Lägg till konfigurationsprincip**.
9. Välj **Konfigurationsinställningar**. På bladet **Konfiguration** definierar du nyckel- och värdepar för konfigurationerna för Managed Browser. Använd avsnitten senare i den här artikeln för mer information om andra nyckel- och värdepar som du kan definiera.
10. När du är klar väljer du **OK**.
11. På bladet **Lägg till konfigurationsprincip** väljer du **Lägg till**.
12. Den nya konfigurationen skapas och visas på bladet **Appkonfiguration**.


## <a name="assign-the-configuration-settings-you-created"></a>Tilldela de konfigurationsinställningar som du har skapat

Du kan tilldela inställningarna till Azure AD-grupper med användare. Om användaren har den aktuella skyddade webbläsaren installerad så hanteras appen med de inställningar du har angett.

1. På bladet **Klientappar** i instrumentpanelen för Intunes hantering av mobilprogram väljer du **Appkonfigurationsprinciper**.
2. Välj den du vill tilldela i listan med appkonfigurationer.
3. Välj **Tilldelningar** på nästa blad.
4. På bladet **Tilldelningar** väljer du den Azure AD-grupp som du vill tilldela appkonfigurationen till. Välj sedan **OK**.

## <a name="how-to-set-microsoft-edge-as-the-protected-browser-for-your-organization"></a>Så här ställer du in Microsoft Edge som den skyddade webbläsaren för din organisation

Med den här inställningen kan du konfigurera om användarna ska dirigeras till Microsoft Edge eller Intune Managed Browser, förutsatt att båda webbläsarna är riktade mot programskyddsprinciper. **Den här inställningen för programkonfigurationsprincipen ska vara riktad mot Intune-hanterade appar som webblänken öppnas från.** 

Om den här inställningen är inställd på ”True”:

- Användarna dirigeras till Microsoft Edge när länkar öppnas från Intune-hanterade appar som är riktade mot den här inställningen. 
- Om de ännu inte har appen kommer de att uppmanas att ladda ned Microsoft Edge från Store, oavsett om de redan har Intune Managed Browser.

Om den här inställningen är inställd på ”False”:

- Intune Managed Browser startas om **både** Managed Browser och Microsoft Edge finns på enheten. 
- Om **antingen** Managed Browser **eller** Microsoft Edge finns på enheten kommer den webbläsaren att öppnas. 
- Om användarna inte har hämtat någon webbläsare uppmanas de att ladda ned Managed Browser.

Använd proceduren ovan för att skapa en Microsoft Edge-appkonfiguration. Ange följande nyckel och värdepar när du väljer inställningarna för **Konfigurationsinställningar** på bladet **Konfiguration** (steg 9):

| Tangent                              |  Värde   |
|----------------------------------|----------|
| **com.microsoft.intune.useEdge** | **true** |

> [!NOTE]
> Se till att följande dataskyddsprincipinställningar är konfigurerade i appens skyddsprincip som hanterar Microsoft Edge och associerade appar som anges i appens konfiguration:
> - Skicka organisationsdata till andra appar: **Principhanterade appar**
> - Dela webbinnehåll med principhanterade webbläsare: **Kräv**

## <a name="how-to-configure-application-proxy-settings-for-protected-browsers"></a>Så här konfigurerar du programproxyinställningar för skyddade webbläsare

Microsoft Edge, Intune Managed Browser och [Azure AD-programproxy]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) kan användas tillsammans så att du kan hantera följande scenarier för användare av iOS och Android-enheter:

- En användare laddar ned och loggar in på Microsoft Outlook-appen. Intunes appskyddsprinciper tillämpas automatiskt. De krypterar sparade data och blockerar användaren från att överföra företagets filer till ohanterade appar och platser på enheten. När användaren sedan klickar på en länk till en intranätplats i Outlook kan du ange att länken ska öppnas i en skyddad webbläsare snarare än någon annan webbläsare. Den skyddade webbläsaren identifierar att intranätsplatsen har gjorts tillgänglig för användaren via programproxyn. Användaren omdirigeras automatiskt via programproxyn för att autentisera med alla tillämpliga multifaktorautentiseringar och principer för villkorlig åtkomst innan de når intranätplatsen. Den här platsen, som tidigare inte hittades när användaren använde en fjärranslutning, kan nu öppnas och länken i Outlook fungerar som förväntat.
- En fjärranvändare öppnar den skyddade webbläsaren och navigerar till en intranätplats via den interna webbadressen. Den skyddade webbläsaren identifierar att intranätsplatsen har gjorts tillgänglig för användaren via programproxyn. Användaren omdirigeras automatiskt via programproxyn för att autentisera med alla tillämpliga multifaktorautentiseringar och principer för villkorlig åtkomst innan de når intranätplatsen. Den här platsen, som tidigare inte hittades när användaren använde en fjärranslutning, kan nu öppnas.

### <a name="before-you-start"></a>Innan du börjar

- Konfigurera dina interna program via Azure AD-programproxyn.
  - Se [installationsdokumentationen](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy) för att konfigurera programproxy och publicera program. 
  - [Användare måste tilldelas](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-add-on-premises-application#add-a-user-for-testing) till det företagsprogram för vilket omdirigeringen ska ske. Detta måste göras även om programmet är inställt på passthrough-läge för förautentisering och om kravet på användartilldelning har inaktiverats i inställningarna för programproxyn.
- Du måste använda version 1.2.0 eller senare av Managed Browser-appen.
- Användare av Managed Browser eller Microsoft Edge har en [Intune-appskyddsprincip](app-protection-policy.md) tilldelad till appen.

    > [!NOTE]
    > Det kan ta upp till 24 timmar innan omdirigeringsdata för en uppdaterad programproxy börjar gälla i Managed Browser eller Microsoft Edge.


#### <a name="step-1-enable-automatic-redirection-to-a-protected-browser-from-outlook"></a>Steg 1: Aktivera automatisk omdirigering till en skyddad webbläsare från Outlook
Outlook måste konfigureras med en appskyddsprincip som aktiverar inställningen **Begränsa webbinnehåll till visning i Managed Browser**.

#### <a name="step-2-assign-an-app-configuration-policy-assigned-for-the-protected-browser"></a>Steg 2: Tilldela en appkonfigurationsprincip som har tilldelats till den skyddade webbläsaren
Den här proceduren konfigurerar Managed Browser eller Microsoft Edge för omdirigering via en programproxy. 

Öppna fliken **Edge** i konfigurationsinställningarna för principen och välj **Aktivera** för omdirigeringsvärdet för programproxyn. Om du aktiverar den här inställningen får användarna åtkomst till företagslänkar och lokala webbappar som publicerats via Azure Application Proxy.

Mer information om hur du kan använda Managed Browser, Microsoft Edge och en Azure AD-programproxy tillsammans för sömlös (och skyddad) åtkomst till lokala webbappar finns i Enterprise Mobility + Security-blogginlägget [Bättre tillsammans: Intune och Azure Active Directory samarbetar för att förbättra användaråtkomsten](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access).

## <a name="how-to-configure-the-homepage-for-a-protected-browser"></a>Så här konfigurerar du startsidan för en skyddad webbläsare

Den här inställningen gör att du kan konfigurera vilken startsida användarna ser när de startar en skyddad webbläsare eller öppnar en ny flik. 
- Den här inställningen visar webbsidan i Managed Browser.  Edge visar en genväg till startsidan i stället.
- Genvägsikonen för startsidan visas som en ikon under sökkontrollen.  Den kan inte redigeras eller tas bort.
- Genvägen till startsidan visar namnet på din organisation för att särskilja den.  Den visas alltid som den första ikonen.

Använd proceduren för att skapa en appkonfiguration för Microsoft Edge eller Managed Browser och ange följande nyckel- och värdepar:

|                                Tangent                                |                                                           Värde                                                            |
|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| <strong>com.microsoft.intune.mam.managedbrowser.homepage</strong> | Ange en giltig URL. Felaktiga URL:er är blockerade som en säkerhetsåtgärd.<br>Exempel: `https://www.bing.com` |

## <a name="how-to-configure-bookmarks-for-a-protected-browser"></a>Så här konfigurerar du bokmärken för en skyddad webbläsare

Med den här inställningen kan du konfigurera en uppsättning bokmärken som är tillgängliga för användare i Microsoft Edge eller Managed Browser.

- De här bokmärkena kan inte tas bort eller ändras av användare
- De här bokmärkena visas överst i listan. Alla bokmärken som användare skapar visas under de här bokmärkena.
- Om du har aktiverat omdirigering av App Proxy kan du lägga till App Proxy-webbappar med antingen deras interna eller externa URL-adress.

Använd proceduren för att skapa en appkonfiguration för Microsoft Edge eller Managed Browser och ange följande nyckel- och värdepar:

|                                Tangent                                 |                                                                                                                                                                                                                                                         Värde                                                                                                                                                                                                                                                          |
|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <strong>com.microsoft.intune.mam.managedbrowser.bookmarks</strong> | Värdet för den här konfigurationen är en lista över bokmärken. Varje bokmärke består av bokmärkets rubrik och bokmärkets URL. Avgränsa rubriken och URL:en med tecknet <strong>&#124;</strong>.<br><br>Exempel:<br> <code>Microsoft Bing&#124;https://www.bing.com</code><br><br>Om du vill konfigurera fler bokmärken avgränsar du varje par med två tecken: <strong>&#124;&#124;</strong><br><br>Exempel:<br> <code>Bing&#124;https://www.bing.com&#124;&#124;Contoso&#124;https://www.contoso.com</code> |

## <a name="how-to-specify-allowed-and-blocked-urls-for-a-protected-browser"></a>Så här anger du tillåtna och blockerade webbadresser för en skyddad webbläsare

Använd proceduren för att skapa en appkonfiguration för Microsoft Edge eller Managed Browser och ange följande nyckel- och värdepar:

|Tangent|Värde|
|-|-|
|Välj mellan:<br><ul><li>Ange tillåtna URL:er (endast dessa URL:er tillåts, inga andra webbplatser kan nås):<br> **com.microsoft.intune.mam.managedbrowser.AllowListURLs**<br><br></li><li>Ange blockerade URL: er (alla andra platser kan nås):<br>**com.microsoft.intune.mam.managedbrowser.BlockListURLs**</li></ul>|Motsvarande värde för nyckeln är en lista med URL:er. Du anger alla URL:er som du vill tillåta eller blockera som ett enda värde, avgränsade med ett vertikalstreck **&#124;** .<br><br>Exempel:<br><br><code>URL1&#124;URL2&#124;URL3</code><br><code>http://*.contoso.com/*&#124;https://*.bing.com/*&#124;https://expenses.contoso.com</code>|

>[!IMPORTANT]
>Ange inte båda nycklarna. Om båda nycklarna används för samma användare tillämpas den tillåtna nyckeln eftersom det är det mest restriktiva alternativet.
>Se även till att du inte blockerar viktiga sidor som t.ex. företagets webbplatser.

### <a name="url-format-for-allowed-and-blocked-urls"></a>URL-format för tillåtna och blockerade URL:er
Använd följande information för att lära dig om tillåtna format och jokertecken som du kan använda när du anger URL:er i listorna för tillåtna och blockerade webbplatser:

- Du kan använda jokertecknet ( **&#42;** ) enligt reglerna i följande lista med tillåtna mönster:

- Kontrollera att du lägger till prefixet **http** eller **https** till alla URL:er när du lägger till dem i listan.

- Du kan ange portnummer i adressen. Om du inte anger ett portnummer, används följande värden:

  - Port 80 för http

  - Port 443 för http

  Jokertecken i portnummer stöds inte. `http://www.contoso.com:;` och `http://www.contoso.com: /;` stöds inte.

- Lär dig mer om de tillåtna mönster du kan använda när du anger URL:er med hjälp av följande tabell:

|                  URL                  |                     Information                      |                                                Matchar                                                |                                Matchar inte                                 |
|---------------------------------------|--------------------------------------------------|-------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
|        `http://www.contoso.com`         |              Matchar en enstaka sida               |                                            `www.contoso.com`                                            |  `host.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`contoso.com`/   |
|          `http://contoso.com`           |              Matchar en enstaka sida               |                                             `contoso.com/`                                              | `host.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`www.contoso.com` |
|    `http://www.contoso.com/&#42;`     | Matchar alla URL:er som börjar med `www.contoso.com` |      `www.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`www.contoso.com/videos/tvshows`      |              `host.contoso.com`<br /><br />`host.contoso.com/images`              |
|    `http://*.contoso.com/*`     |     Matchar alla underordnade domäner under contoso.com     | `developer.contoso.com/resources`<br /><br />`news.contoso.com/images`<br /><br />`news.contoso.com/videos` |                               `contoso.host.com`                                |
|     `http://www.contoso.com/images`     |             Matchar en enstaka mapp              |                                        `www.contoso.com/images`                                         |                          `www.contoso.com/images/dogs`                          |
|       `http://www.contoso.com:80`       |  Matchar en enstaka sida, med ett portnummer   |                                       `http://www.contoso.com:80`                                       |                                                                               |
|        `https://www.contoso.com`        |          Matchar en enstaka, säker sida           |                                        `https://www.contoso.com`                                        |                            `http://www.contoso.com`                             |
| `http://www.contoso.com/images/&#42;` |    Matchar en enstaka mapp och alla undermappar    |                  `www.contoso.com/images/dogs`<br /><br />`www.contoso.com/images/cats`                   |                            `www.contoso.com/videos`                             |

- Följande är några exempel på indata som du inte kan ange:

  - `*.com`

  - `*.contoso/*`

  - `www.contoso.com/*images`

  - `www.contoso.com/*images*pigs`

  - `www.contoso.com/page*`

  - IP-adresser

  - `https://*`

  - `http://*`

  - `http://www.contoso.com:*`

  - `http://www.contoso.com: /*`
  
## <a name="soft-transitions-from-work-to-personal-accounts"></a>Mjuka övergångar från arbetskonton till personliga konton

Grundstenen i Microsoft Edge Mobile Enterprise är modellen med dubbla identiteter, vilket innebär att Microsoft Edge har stöd för både arbetsidentiteter och personliga identiteter. Precis som med Office 365- och Outlook-appar kan du använda den här modellen med dubbla identiteter för att låta användarna använda Microsoft Edge för webbsurfning och enkelt växla mellan de två upplevelserna baserat på de innehållsprinciper som administratören har definierat. Webbsurfen i den personliga miljön påverkas inte och företagsinformation sparas helt och hållet arbetsmiljön i Microsoft Edge. 

En av fördelarna med den här modellen är att när användare försöker öppna en länk (till exempel en tidningsartikel osv.) till en plats som inte tillåts av din organisation kan de göra det i sin personliga miljö som är helt åtskild från arbetsmiljön. Dessa mjuka övergångar är aktiverade som standard. 

Använd proceduren för att skapa en appkonfiguration för Microsoft Edge eller Managed Browser och ange följande nyckel- och värdepar:

| Tangent                                                                | Värde                                                 |
|--------------------------------------------------------------------|-------------------------------------------------------|
| **com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock** | **False** blockerar dessa mjuka övergångar |

## <a name="how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios"></a>Komma åt loggar för hanterade appar med Managed Browser i iOS

Slutanvändare med Managed Browser installerade på sina iOS-enheter kan se hanteringsstatus för alla appar som har publicerats av Microsoft. De kan skicka loggar för felsökning av deras hanterade iOS-appar.

1. Öppna iOS **Inställningar**.
2. Välj programinställningar för hanterad **Webbläsare**.
3. Växla **Aktivera Intune-diagnostik** för att ställa in webbläsaren på felsökningsläge.
4. Öppna den hanterade **webbläsaren**. Klicka på **Visa status för Intune-app** om du vill granska enskilda programprincipinställningar.
5. Tryck på **Kom igång** och **Dela loggar** eller **Skicka loggar till Microsoft** om du vill skicka felsökningsloggarna till IT-administratören eller Microsoft.

Du kan också öppna webbläsaren i felsökningsläge från appen.

1. Öppna Managed Browser.
2. Skriv in `about:intunehelp` i adressrutan.
Webbläsaren startar felsökningsläget.

En lista över de inställningar som finns lagrade i apploggarna finns i [granska appskyddsloggarna i Managed Browser](app-protection-policy-settings-log.md).

## <a name="security-and-privacy-for-the-managed-browser"></a>Säkerhet och sekretess för Managed Browser

- Managed Browser använder inte inställningar som användare gör i den inbyggda webbläsaren på sina enheter. Managed Browser har inte åtkomst till de här inställningarna.

- Om du konfigurerar alternativet **Kräv enkel PIN-kod för åtkomst** eller **Kräv företagets autentiseringsuppgifter för åtkomst** i en appskyddsprincip som är associerad med Managed Browser och en användare väljer hjälplänken på autentiseringssidan så kan användaren bläddra på alla webbplatser, oavsett om de har lagts till i en blockeringslista i principen.

- Managed Browser kan endast blockera åtkomst till webbplatser när de öppnas direkt. Den blockerar inte åtkomst när mellanliggande tjänster (till exempel en översättningstjänst) används för åtkomst till webbplatsen.

- För att tillåta autentisering och få åtkomst till Intune-dokumentationen är **&#42;.microsoft.com** undantaget från listan Tillåt eller blockera. Den tillåts alltid.

### <a name="turn-off-usage-data"></a>Stäng av användningsdata
Microsoft samlar automatiskt in anonyma data om prestanda och användning av Managed Browser för att kunna förbättra Microsofts produkter och tjänster. Användare kan stänga av insamling av data med hjälp av inställningen **Användningsdata** på sina enheter. Du har ingen kontroll över insamlingen av dessa data.

- Webbplatser som har ett utgånget eller ej betrott certifikat kan inte öppnas på iOS-enheter.

## <a name="next-steps"></a>Nästa steg

- [Vad är appskyddsprinciper?](app-protection-policy.md) 