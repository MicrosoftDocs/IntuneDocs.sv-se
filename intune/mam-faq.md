---
title: "Vanliga frågor och svar om MAM och appskydd"
description: "Den här artikeln ger svar på några vanliga frågor om Intune mobile application management (MAM) och Intune appskydd."
keywords: 
author: Erikre
ms.author: erikre
manager: angrobe
ms.date: 02/06/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 149def73-9d08-494b-97b7-4ba1572f0623
ms.reviewer: erikre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 23ab21e21ff2ffd471523f8132acffd7545358f0
ms.sourcegitcommit: 9bd6278d129fa29f184b2d850138f8f65f3674ea
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/09/2018
---
# <a name="frequently-asked-questions-about-mam-and-app-protection"></a>Vanliga frågor och svar om MAM och appskydd

Den här artikeln ger svar på några vanliga frågor om Intune MAM (Mobile Application Management) och appskyddet i Intune.


## <a name="mam-basics"></a>Grundläggande om MAM


**Vad är MAM?** Med [Intune mobile application management](/intune/app-lifecycle) avses den svit av Intune-hanteringsfunktioner som låter dig publicera, pusha, konfigurera, skydda, övervaka och uppdatera mobilappar för dina användare.

**Vilka är fördelarna med appskyddet i MAM?** MAM skyddar företagets data inom ett program. Med MAM utan registrering (MAM-WE), kan en arbets- eller skolrelaterad app som innehåller känsliga data hanteras på nästan alla enheter, inklusive personliga enheter i BYOD-scenarier (Bring Your Own Device).
 Många produktivitetsappar, som till exempel Microsoft Office-apparna, kan hanteras av Intune MAM. Se listan över officiella [Intune-hanterade appar](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) tillgängliga för allmänt bruk.

**Vilka enhetskonfigurationer har MAM stöd för?** Intune MAM stöder två konfigurationer:
- **Intune MDM + MAM**: IT-administratörer kan bara hantera appar med MAM och appskyddsprinciper på enheter som är registrerade med Intune mobil enhetshantering (MDM). För att hantera appar med hjälp av MDM + MAM, ska kunder använda Intune-konsolen i Azure-portalen på http://portal.azure.com.

- **MAM utan enhetsregistrering**: Med MAM utan enhetsregistrering, eller MAM-WE, kan IT-administratörer hantera appar med hjälp av MAM och appskyddsprinciper på enheter som inte har registrerats med Intune MDM. Detta innebär att appar kan hanteras av Intune på enheter som registrerats med tredje parts EMM-leverantörer. För att hantera appar med hjälp av MAM-WE ska kunder använda Intune-konsolen i Azure-portalen på http://portal.azure.com. Appar kan också hanteras av Intune på enheter som har registrerats med tredje parts-leverantörer av Enterprise Mobility Management (EMM) eller inte har registrerats alls med MDM.


## <a name="app-protection-policies"></a>Appskyddsprinciper

**Vad är appskyddsprinciper**? Appskyddsprinciper är regler som säkerställer att organisationens data förblir säkra eller inkluderas i en hanterad app. En princip kan vara en regel som tillämpas när användaren försöker få åtkomst till eller flytta "företagsdata", eller en uppsättning åtgärder som är förbjudna eller övervakas när användaren är inne i appen.

**Vilka exempel finns det på appskyddsprinciper?** Se [Inställningar för Android-appskyddsprinciper](app-protection-policy-settings-android.md) och [Inställningar för iOS-appskyddsprinciper](app-protection-policy-settings-ios.md) för detaljerad information om respektive inställning av appskyddprincip.

## <a name="apps-you-can-manage-with-app-protection-policies"></a>Appar som du kan hantera med appskyddsprinciper

**Vilka appar kan hanteras med appskyddsprinciper?** Alla appar som har integrerats med [Intune App-SDK](/intune/app-sdk) eller inslutits av [Intunes programhanteringsverktyg](/intune/apps-prepare-mobile-application-management) kan hanteras med Intunes appskyddsprinciper. Se listan över officiella [Intune-hanterade appar](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) tillgängliga för allmänt bruk.

**Vilka är de grundläggande kraven för att använda appskyddsprinciper på en Intune-hanterad app?**
- Slutanvändare måste ha ett Azure Active Directory-konto (AAD). Se [Lägg till användare och ge administrativ behörighet till Intune](/intune/users-permissions-add) för information om hur du skapar Intune-användare i Azure Active Directory.

- Slutanvändaren måste ha en licens för Microsoft Intune som tilldelats deras Azure Active Directory-konto. Se [Hantera Intune-licenser](/intune/licenses-assign) för information om hur du tilldelar Intune-licenser till slutanvändare.

- Slutanvändaren måste tillhöra en säkerhetsgrupp som är målet för en appskyddsprincip. Samma appskyddsprincip måste ha den specifika app som används som mål.
 Appskyddsprinciper kan skapas och distribueras i Intune-konsolen i [Azure-portalen](http://portal.azure.com). Säkerhetsgrupper kan för närvarande skapas i [Office-portalen](http://portal.office.com).

- Slutanvändaren måste logga in på appen med sitt AAD-konto.

**Vilka är de ytterligare krav som ställs för användning av [Outlook-mobilappen](https://products.office.com/outlook)?**

- Slutanvändaren måste ha Outlook-mobilappen installerad på sin enhet.

- Slutanvändaren måste ha en [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online)-postlåda och licens kopplad till sitt Azure Active Directory-konto.

  >[!NOTE]
  > Outlook-mobilappen har för närvarande endast stöd för Microsoft Exchange Online och har inte stöd för Exchange på plats eller Exchange i Office 365 Dedicated.

**Vilka är de ytterligare kraven för att använda [Word-, Excel- och PowerPoint](https://products.office.com/business/office)-apparna?**

- Slutanvändaren måste ha en licens för [Office 365 Business eller Enterprise](https://products.office.com/business/compare-more-office-365-for-business-plans) som länkats till deras Azure Active Directory-konto. Prenumerationen måste inkludera Office-apparna på mobila enheter och kan inkludera ett molnlagringskonto med [OneDrive för företag](https://onedrive.live.com/about/business/). Office 365-licenser kan tilldelas i [Office-portalen](http://portal.office.com) med hjälp av följande [instruktioner](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

- Slutanvändaren måste ha en hanterad plats som konfigurerats med detaljerade spara som-funktioner under inställningen för programskyddsprincipen Förhindra spara som. Om den hanterade platsen till exempel är OneDrive, ska [OneDrive](https://onedrive.live.com/about/)-appen vara konfigurerad i slutanvändarens Word-, Excel- eller PowerPoint-app.

- Om den hanterade platsen är OneDrive, måste appen vara mål för appskyddsprincipen som distribuerats till slutanvändaren.

  >[!NOTE]
  > Office mobilappar har för närvarande endast stöd för SharePoint Online och inte SharePoint på plats.

**Varför behövs en hanterad plats (d.v.s. OneDrive) för Office?** Intune markerar all data i appen som "företag" eller "personligt." Data anses som "företagets" när det kommer från en företagsplats. För Office-apparna betraktar Intune följande platser som företagets: e-post (Exchange) eller molnlagring (OneDrive-app med ett konto för OneDrive för företag).

**Vilka är de ytterligare krav som ställs för användning av Skype för företag?** Se licenskraven för [Skype för företag](https://products.office.com/skype-for-business/it-pros).
  >[!NOTE]
  > Skype för företag-mobilappen har för närvarande endast stöd för Skype för företag – Online.

## <a name="app-protection-features"></a>Appskyddsfunktioner

**Vad är stöd för flera identiteter?** Stöd för flera identiteter är möjligheten för Intune App SDK att bara tillämpa appskyddsprinciper på arbets- eller skolkontot som använts för inloggning i appen. Om ett personligt konto är inloggat i appen ändras inga data.


**Vad är syftet med stöd för flera identiteter?** Stöd för flera identiteter gör att appar med både företags- och konsumentanvändare (t.ex. Office-appar) kan släppas offentligt med Intunes appskyddsfunktioner för företagets konton.

**Vad gäller för Outlook och flera identiteter?** Eftersom Outlook har en kombinerad e-postvy över både personliga och "företagets" e-postmeddelanden frågar Outlook-appen efter Intune-PIN vid start.

**Vad är Intune-appens PIN-kod?** PIN-kod (Personal Identification Number) är ett lösenord som används för att verifiera att rätt användare har åtkomst till organisationens data i en app.

- **När uppmanas användaren att ange sin PIN-kod?** Intune frågar endast efter användarens PIN-kod för appen när användaren ska få åtkomst till företagsdata. I appar för flera identiteter som till exempel Word/Excel/PowerPoint uppmanas användarna att ange sina PIN-koder när de försöker öppna ett "företags"-dokument eller -fil. I appar för en identitet, till exempel branschspecifika appar som använder Intunes apphanteringsverktyg, efterfrågas PIN-koden redan vid start eftersom Intune App SDK:n vet att användarupplevelsen i appen alltid är företag.

- **Hur ofta kommer användaren uppmanas att ange PIN-koden för Intune?**
  IT-administratören kan definiera Intune-appskyddsprincipen ”Kontrollera åtkomskraven igen efter (minuter)” i Intune-administratörskonsolen. Den här inställningen anger hur lång tid som ska passera innan åtkomstkraven kontrolleras på enheten och appens PIN-skärm visas igen. Detta är dock viktig information om PIN-koden som påverkar hur ofta användaren uppmanas: 

    - **PIN-koden delas mellan appar från samma utgivare för att förbättra användarvänligheten:** I iOS delas en app-PIN mellan alla appar **från samma utgivare**. På Android delas en app-PIN mellan alla appar.
    - **Den löpande funktionen för timern som är kopplad till PIN-koden:** När en PIN-kod anges för att få åtkomst till en app (app A) och appen lämnar enhetens förgrund (huvudfokus) kommer PIN-timern att återställas för den PIN-koden. De appar (t.ex. app B) som delar denna PIN-kod kommer inte uppmana användaren att ange PIN-kod eftersom timern har återställts. Uppmaningen visas igen när värdet ”Kontrollera åtkomstkraven igen efter (minuter)” uppfylls igen. 

      >[!NOTE] 
      > För att verifiera användarens åtkomstkrav oftare (till exempel med en PIN-fråga), särskilt för appar som används ofta, rekommenderar vi att du minskar värdet för inställningen Kontrollera åtkomstkraven igen efter (minuter). 

- **Är PIN-kod säkert?** PIN-koden fungerar så att endast rätt användare får åtkomst till organisationens data i appen. Därför måste en slutanvändare logga in med sitt arbets- eller skolkonto innan de kan ställa in eller återställa Intune-appens PIN-kod. Den här autentiseringen hanteras av Azure Active Directory via utbyte av säker token och är inte transparent för Intune App SDK. Ur ett säkerhetsperspektiv är bästa sättet att skydda data från arbete eller skola att kryptera den. Kryptering är inte relaterad till appens PIN-kod, utan en egen appskyddsprincip.

- **Hur skyddar Intune PIN-koden mot nyckelsökningsattacker?** Som en del av appens PIN-princip kan IT-administratören ange det maximala antalet gånger som en användare kan försöka att autentisera sin PIN-kod innan appen blir låst. När antalet försök har uppfyllts kan Intune App SDK rensa företagets data i appen.
  
- **Varför måste jag ange en PIN-kod två gånger på appar från samma utgivare?**
  MAM (på iOS) tillåter för tillfället PIN på programnivå med alfanumeriska tecken och specialtecken (kallas lösenord) som kräver medverkan av program (d.v.s. WXP, Outlook, hanterad webbläsare, Yammer) för att integrera Intune APP SDK:n för iOS. Utan detta tillämpas inställningar för lösenord inte korrekt för de aktuella programmen. Detta var en funktion som introducerades i Intune SDK för iOS v. 7.1.12. <br><br> För att stödja den här funktionen och säkerställa bakåtkompatibilitet med tidigare versioner av Intune SDK för iOS, hanteras alla PIN-koder (numeriska eller lösenord) i 7.1.12+ separat från den numeriska PIN-koden i tidigare versioner av SDK. Därför måste en enhet som har program med Intune SDK för iOS-versioner före 7.1.12 och efter 7.1.12 från samma utgivare, ställa in två PIN-koder. <br><br> Med detta sagt är de två PIN-koderna (för varje app) inte relaterade på något sätt, d.v.s. de måste följa den appskyddsprincip som tillämpas på appen. Därför kan användare konfigurera samma PIN-kod två gånger *endast* om apparna A och B har samma principer tillämpade (med avseende på PIN-kod). <br><br> Det här beteendet är specifikt för PIN-koden på iOS-program som har aktiverats med Intune Mobile App Management. Med tiden när program inför senare versioner av Intune SDK för iOS, blir det inte ett så stort problem att behöva ange PIN-kod två gånger på appar från samma utgivare. Se avsnittet nedan för ett exempel.

  >[!NOTE]
  > Om t.ex. app A har skapats med en tidigare version än 7.1.12 och app B har byggts med en version som är högre än eller lika med 7.1.12 från samma utgivare, måste slutanvändaren ställa in PIN-koder separat för A och B om båda är installerade på en iOS-enhet. <br><br> Om en app C har SDK-version 7.1.9 installerad på enheten, delar den samma PIN-kod som app A. <br><br> En app D som skapats med 7.1.14 delar samma PIN-kod som app B. <br><br> Om bara apparna A och C är installerade på en enhet, behöver en PIN-kod anges. Detsamma gäller om bara apparna B och D är installerade på en enhet.

**Vad gäller för kryptering?** IT-administratörer kan distribuera en appskyddsprincip som kräver att appdata krypteras. Som en del av principen kan IT-administratören även ange när innehållet krypteras.

- **Hur krypterar Intune data?** Se [Inställningar för Android-appskyddsprinciper](app-protection-policy-settings-android.md) och [Inställningar för iOS-appskyddsprinciper](app-protection-policy-settings-ios.md) för detaljerad information om inställning av appskyddprincip för kryptering.

- **Vad krypteras?** Endast data som har markerats som "företagets" krypteras enligt IT-administratörens appskyddsprincip. Data anses som "företagets" när det kommer från en företagsplats. För Office-apparna betraktar Intune följande platser som företagets: e-post (Exchange) eller molnlagring (OneDrive-app med ett konto för OneDrive för företag). För branschspecifika appar som hanteras av Intunes programhanteringsverktyg, betraktas alla appdata som företag.

**Hur fjärrensar Intune data?** Intune kan rensa AppData på tre olika sätt: fullständig rensning av enheten, selektiv rensning för MDM och MAM-selektiv rensning. Läs mer om fjärrensning för MDM i [Ta bort enheter med fabriksåterställning eller ta bort företagsdata](devices-wipe.md#factory-reset). Mer information om selektiv rensning med hjälp av MAM finns i [Ta bort företagsdata](devices-wipe.md#remove-company-data) och [Så här tar du bort endast företagsdata från appar](apps-selective-wipe.md).

- **Vad är fabriksåterställning?** [Fabriksåterställning](devices-wipe.md) tar bort alla användardata och inställningar från **enheten** genom att återställa den till fabriksinställningarna. Enheten tas bort från Intune.
  >[!NOTE]
  > Fabriksåterställning kan bara ske på enheter som registrerats med Intunes hantering av mobila enheter (MDM).

- **Vad är selektiv rensning för MDM?** Se [Ta bort enheter – ta bort företagsdata](devices-wipe.md#remove-company-data) för att läsa om hur du tar bort företagsdata.

- **Vad är selektiv rensning för MAM?** Selektiv rensning för MAM tar helt enkelt bort företagsdata från en app. Begäran initieras med hjälp av Intune Azure-portalen. Information om hur du initierar en rensningsbegäran finns i [Så här rensar du endast företagsdata från appar](apps-selective-wipe.md).

- **Hur snabbt sker selektiv rensning för MAM?** Om användaren använder appen när selektiv rensning initieras söker Intune App SDK var 30:e minut efter en begäran om selektiv rensning från Intune MAM-tjänsten. Den söker även efter selektiv rensning när användaren startar appen för första gången och loggar in med sitt arbets- eller skolkonto.

**Varför fungerar inte tjänster på plats med Intunes appskydd?** Intunes appskydd är beroende av att användarens identiteten är konsekvent mellan appen och Intune App SDK. Det enda sättet att garantera detta är via modern autentisering. Det finns scenarier där appar kan fungera med en lokal konfiguration, men de är varken konsekventa eller garanterade.

**Finns det ett säkert sätt att öppna webblänkar från hanterade appar?** Ja! IT-administratören kan distribuera och ange appskyddsprincip för [Intune Managed Browser-appen](app-configuration-managed-browser.md), en webbläsare som har utvecklats av Microsoft Intune som enkelt kan hanteras med Intune. IT-administratören kan kräva att alla webblänkar i Intune-hanterade appar ska öppnas med Managed Browser-appen.


## <a name="app-experience-on-android"></a>App-upplevelse på Android

**Varför behövs företagsportalappen för att Intunes appskydd ska fungera på Android-enheter?** Många av appskyddets funktioner är inbyggda i företagsportalappen.
 Enhetsregistrering _krävs inte_, även om företagsportalappen alltid krävs. För MAM-WE behöver slutanvändaren bara ha företagsportalappen installerad på enheten.

## <a name="app-experience-on-ios"></a>App-upplevelse på iOS

**Jag kan använda delningtillägg i iOS för att öppna arbets- eller skoldata i ohanterade appar, även om dataöverföringsprincipen är inställd på "endast hanterade appar" eller "inga appar." Kan inte detta läcka data?** Intunes appskyddsprincip kan inte styra iOS resurstillägg utan att hantera enheten. Därför krypterar Intune  _**"företagets" data innan den delas utanför appen**_. Du kan verifiera detta genom att försöka öppna en "företags"-fil utanför den hanterade appen. Filen ska vara krypterad och inte kunna öppnas utanför den hanterade appen.

## <a name="see-also"></a>Se även
- [Implementera din Intune plan](planning-guide-onboarding.md)
- [Intune-testning och validering](planning-guide-test-validation.md)
- [Inställningar för hanteringsprincip för Android-mobilappar i Microsoft Intune](app-protection-policy-settings-android.md)
- [Inställningar för hanteringsprincip för iOS-mobilappar](app-protection-policy-settings-ios.md)
- [Validera dina appskyddsprinciper](app-protection-policies-validate.md)
- [Lägg till appkonfigurationsprinciper för hanterade appar utan enhetsregistrering](app-configuration-policies-managed-app.md)
- [Så kan du få support för Microsoft Intune](get-support.md)