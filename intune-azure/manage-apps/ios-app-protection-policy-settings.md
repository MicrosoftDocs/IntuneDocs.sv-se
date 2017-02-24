---
title: "Principinställningar för iOS-appskydd | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: I det här avsnittet beskrivs principinställningarna för appskydd för iOS-enheter."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f8b08f2-504c-4b38-bea2-b8a4ef0526b8
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 291c380b861d3ad7df2fc1af4274d9e8bb014846
ms.openlocfilehash: 55faaa918e309616c9b84eeb429f42d52796c1d9


---

#  <a name="ios-app-protection-policy-settings"></a>Principinställningar för iOS-appskydd 
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

De principinställningar som beskrivs i det här avsnittet kan [konfigureras](app-protection-policies.md) för en appskyddsprincip på bladet **Inställningar** i Azure-portalen.

Det finns två kategorier för principinställningar: inställningar för dataflytt och åtkomst. I det här avsnittet används termen ***principhanterade appar*** för att hänvisa till appar som har konfigurerats med appskyddsprinciper.

##  <a name="data-relocation-settings"></a>Inställningar för dataflytt

| Inställningar | Använd så här | Standardvärde(n) |
|------|------|------|
| **Förhindra säkerhetskopiering av iTunes och iCloud** | Välj **Ja** för att förhindra att den här appen säkerhetskopierar arbets- eller skoldata till iTunes och iCloud. Välj **Nej** för att tillåta att den här appen säkerhetskopierar arbets- eller skoldata till iTunes och iCloud.| Ja |
| **Tillåt att appen överför information till andra appar** | Ange vilka appar som kan ta emot data från den här appen: <ul><li> **Principhanterade appar**: Tillåt endast överföring till andra principhanterade appar.</li> <li>**Alla appar**: Tillåt överföring till alla appar. </li> <li>**Inga**: Tillåt inte dataöverföring till någon app, inklusive andra principhanterade appar.</li></ul> Om du anger det här alternativet till **Principhanterade appar** eller **Ingen** blockeras dessutom iOS 9-funktionen som gör att Spotlight-sökning kan söka efter data i appar. <br><br> | Alla appar |
| **Tillåt att appen hämtar data från andra appar** | Ange vilka appar som kan överföra data till den här appen: <ul><li>**Principhanterade appar**: Tillåt endast överföring från andra principhanterade appar.</li><li>**Alla appar**: Tillåt dataöverföring från alla appar.</li><li>**Ingen**: Tillåt inte dataöverföring från någon app, inklusive andra principhanterade appar. | Alla appar |
| **Förhindra "Spara som"** | Välj **Ja** om du vill inaktivera alternativet Spara som i den här appen. Välj **Nej** om du vill tillåta att Spara som används. | Nej |
| **Begränsa klipp ut, kopiera och klistra in med andra appar** | Ange när åtgärderna klippa ut, kopiera och klistra in kan användas med den här appen. Välj mellan: <ul><li>**Blockerad**: Tillåt inte åtgärderna klipp ut, kopiera och klistra in mellan den här appen och andra appar.</li><li>**Principhanterade appar**: Tillåt endast åtgärderna klipp ut, kopiera och klistra in mellan den här appen och andra principhanterade appar.</li><li>**Principhanterade appar med inklistring**: Tillåt klipp ut och kopiera mellan den här appen och andra principhanterade appar. Tillåt att data från en annan app klistras in i den här appen.</li><li>**Alla appar**: Inga begränsningar för klipp ut, kopiera och klistra in till och från den här appen. | Alla appar |
|**Begränsa webbinnehåll till visning i Managed Browser** | Välj **Ja** för att tvinga webblänkar i appen att öppnas i appen Managed Browser. <br><br> För enheter som inte har registrerats i Intune kan webblänkar i principhanterade appar endast öppnas i appen Managed Browser. <br><br> Om du använder Intune för att hantera dina enheter läser du [Hantera Internetåtkomst med hanterade webbläsarprinciper med Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/manage-internet-access-using-managed-browser-policies). | Nej |
| **Kryptera appdata** | För principer för hanterade program krypteras data i viloläge med hjälp av krypteringsschemat på enhetsnivån som tillhandahålls av iOS. När en PIN-kod krävs krypteras data enligt inställningarna i appskyddsprincipen. <br><br> Gå till den officiella Apple-dokumentationen [här](https://support.apple.com/HT202739) för att se vilka iOS-krypteringsmoduler som är FIPS 140-2-certifierade eller väntar på FIPS 140-2-certifiering. <br><br> Ange när arbets- eller skoldata i den här appen ska krypteras. Välj mellan: <ul><li>**När enheten är låst**: Alla appdata som är associerade med den här principen krypteras när enheten är låst.</li><li>**När enheten är låst och det finns öppna filer**: Alla appdata som är associerade med den här principen krypteras när enheten är låst, utom data i filer som är öppna i appen.</li><li>**Efter omstart av enheten**: Alla appdata som är associerade med den här principen krypteras när enheten startas om, tills den första gången enheten låses upp.</li><li>**Använd enhetsinställningar**: Appdata krypteras baserat på standardinställningarna på enheten. <br><br> När du aktiverar den här inställningen måste användaren konfigurera och använda en PIN-kod för att komma åt sin enhet.  Om det inte finns någon PIN-kod startar inte apparna och användaren uppmanas att ange en PIN-kod. Ett meddelande visas som informerar användaren om att dennes organisation kräver att enheten har en PIN-kod för att det ska gå att komma åt appen. </li></ul> | När enheten är låst |
| **Inaktivera synkronisering av kontakter** | Välj **Ja** att förhindra att appen sparar data i den interna appen Kontakter på enheten. Om du väljer **Nej** kan appen spara data i den interna appen Kontakter på enheten. <br><br>När du utför en selektiv rensning för att ta bort arbets- eller skoldata från appen kommer kontakter som har synkats direkt från appen till den inbyggda appen Kontakter att tas bort. Kontakter som synkroniseras från den interna adressboken till en annan extern källa kan inte rensas. Detta gäller för närvarande endast för Microsoft Outlook-appen. | Nej |
| **Inaktivera utskrift** | Välj **Ja** att förhindra att appen skriver ut arbets- eller skoldata. | Nej |


> [!NOTE]
> Ingen av inställningarna för dataflytt styr den Apple-hanterade ”öppna med”-funktionen på iOS-enheter. Se [Hantera dataöverföring mellan iOS-appar med Microsoft Intune](manage-data-transfer-between-ios-apps-with-microsoft-intune.md) för hantering av ”öppna med”.


## <a name="access-settings"></a>Åtkomstinställningar

| Inställningar | Använd så här | Standardvärde(n) |
|------|------|------|
| **Kräv PIN-kod för åtkomst** | Välj **Ja** för att kräva en PIN-kod för att använda den här appen. Användarna uppmanas att konfigurera denna PIN-kod första gången de kör appen i en arbets- eller skolkontext. Standardvärde = **Ja**.<br><br> Konfigurera följande inställningar för PIN-styrka: <ul><li>**Antal försök före återställning av PIN**: Ange antalet försök som användaren har att ange rätt PIN-kod innan den måste återställas. Standardvärde = **5**.</li><li> **Tillåt enkel PIN-kod:** Välj **Ja** du om du vill tillåta att användarna använder enkla PIN-kodssekvenser, till exempel 1234 eller 1111. Välj **Nej** om du vill förhindra att de använder enkla sekvenser. Standardvärde = **Ja**. </li><li> **PIN-kodslängd**: Ange det minsta antalet siffror i en PIN-kodssekvens. Standardvärde = **4**. </li><li> **Kräv fingeravtryck istället för PIN (iOS 8.0+)**: Välj **Ja** om du vill kräva att [Touch-ID](https://support.apple.com/en-us/HT201371) används i stället för en PIN-kod för åtkomst till appen. Standardvärde = **Ja**.<br><br> På iOS-enheter kan du låta användaren bekräfta sin identitet med hjälp av [Touch-ID](https://support.apple.com/en-us/HT201371) i stället för en PIN-kod. När användarna försöker använda appen med ett arbets- eller skolkonto uppmanas de att lämna sitt fingeravtryck i stället för att ange en PIN-kod. </li></ul>| Kräv PIN-kod: Ja <br><br> PIN-återställningsförsök: 5 <br><br> Tillåt enkel PIN-kod: Ja <br><br> PIN-kodslängd: 4 <br><br> Tillåt fingeravtryck: Ja |
| **Kräv företagets autentiseringsuppgifter för åtkomst** | Välj **Ja** om du vill kräva att användaren loggar in med sitt arbets- eller skolkonto i stället för att ange en PIN-kod för åtkomst till appen. Om du väljer **Ja** åsidosätts kraven på PIN-kod eller Touch ID.  | Nej |
| **Hindra hanterade appar från att köras på jailbrokade eller rotade enheter** |  Välj **Ja** om du vill förhindra att den här appen körs på jailbrokade eller rotade enheter. Användaren kan fortfarande använda apparna för personliga uppgifter, men måste använda en annan enhet för att komma åt arbets- eller skoldata i denna app. | Ja |
| **Kontrollera åtkomstbehörigheterna på nytt efter (minuter)** | Konfigurera följande inställningar: <ul><li>**Tidsgräns**: Ange tiden (i minuter) innan åtkomstkraven för appen kontrolleras igen. Standardvärde = **30** minuter.</li><li>**Offlinerespittid**: Specificera tiden (i minuter) innan åtkomstkraven för appen kontrolleras igen om enheten är offline. Standardvärde = **720** minuter (12 timmar).</li></ul>| Tidsgräns: 30 <br><br> Offline: 720 |
| **Offlineintervall innan appdata rensas (dagar)** | Arbets- eller skoldata i den här appen kan rensas om en enhet har varit offline längre än en viss tid. Ange hur många dagar en enhet kan vara offline innan arbets- eller skoldata tas bort från enheten. <br><br> | 90 dagar |

##  <a name="add-ins-for-outlook-app"></a>Tillägg för Outlook-appen

Outlook införde nyligen iOS-tillägg i Outlook, så att du kan integrera populära appar med e-postklienten. Tillägg för Outlook är tillgängliga för Outlook på webben, Windows, Mac och Outlook för iOS. Eftersom tillägg hanteras via Microsoft Exchange kan användarna dela data och meddelanden via Outlook och ohanterade tilläggsprogram, såvida inte tilläggen har inaktiverats för användarna av Exchange.

Om du vill förhindra slutanvändarna från att få åtkomst till och kunna installera Outlook-tillägg (vilket påverkar alla Outlook-klienter) gör du följande rolländringar i Exchange-administrationscentret:

- Om du vill förhindra användare från att installera Office Store-tillägg tar du bort rollen Min Marketplace från dem.
- Om du vill förhindra användare från att läsa in tillägg separat tar du bort rollen Mina anpassade appar från dem.
- Om du vill förhindra användare från att installera alla tillägg tar du bort båda rollerna, Mina anpassade appar och Min Marketplace, från dem.

Dessa anvisningar gäller för Office 365, Exchange 2016, Exchange 2013 via Outlook på webben, Windows, Mac och mobilt.

- Lär dig mer om [tillägg för Outlook](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx).
- Lär dig mer om [hur du anger administratörer och användare som kan installera och hantera tillägg för Outlook-appen](https://technet.microsoft.com/library/jj943754(v=exchg.150).aspx).



<!--HONumber=Feb17_HO2-->

