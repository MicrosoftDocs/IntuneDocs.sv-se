---
title: "Inställningar för Mac OS X-principer | Microsoft Docs"
description: "I Intune finns en uppsättning inbyggda allmänna inställningar som du kan konfigurera i Mac OS X-enheter. Du kan också använda verktyget Apple Configurator för att skapa anpassade inställningar som inte är tillgängliga från Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 98b2f19b-bee8-42d7-a215-a716d56a25a3
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e7d1760a10e63233fe7cc7f6fd57a68c5283647c
ms.openlocfilehash: 58dc1d872e7e12978652542d80061dd7ed86aeb2
ms.lasthandoff: 12/30/2016


---

# <a name="mac-os-x-configuration-policy-settings-in-microsoft-intune"></a>Inställningar för Mac OS X-konfigurationsprinciper i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

I Intune finns en uppsättning inbyggda allmänna inställningar som du kan konfigurera i Mac OS X-enheter. Du kan också använda verktyget Apple Configurator för att skapa anpassade inställningar som inte är tillgängliga från Intune.

## <a name="general-configuration-policy-settings"></a>Generella inställningar för konfigurationsprinciper

Använd Microsoft Intunes **allmänna konfigurationsprincip** för Mac OS X om du vill konfigurera inställningar för:

-   **Enhetssäkerhet**. Välj i en lista med fördefinierade inställningar som du kan använda för att styra många av enhetens egenskaper och funktioner.

-   **Kompatibla och icke-kompatibla appar**. Ange en lista över appar i företaget som är kompatibla eller inkompatibla. Inkompatibilitetsrapporter för appar kan användas för att visa om de appar du har angett i listan är kompatibla med appar som användare har installerat (men det går inte att blockera installationen av appen).

Om den inställning som du söker efter inte visas i listan kan du eventuellt skapa den med hjälp av en anpassad Mac OS X-princip med vilken du kan importera inställningar som du har skapat med hjälp av Apple Configurator-verktyget. Mer information finns i "Anpassade principinställningar" senare i det här avsnittet.

### <a name="password-settings"></a>Inställningar för lösenord

|Inställningsnamn|Information|
|----------------|---------------|
|**Kräv ett lösenord för att låsa upp enheter**|Ange om användaren måste använda ett lösenord för att komma åt Mac-datorn. **Viktigt!** Till skillnad från iOS-enheter uppmanas användare på Mac OS X-enheter inte genast att uppdatera sitt lösenord för att följa den här inställningen.|
|**Lösenordstyp krävs**|Ange om lösenordet kan vara endast **Numeriskt** eller om det måste vara **Alfanumeriskt** (innehålla bokstäver och siffror). **Viktigt!** Den här inställningen stöds endast i Mac OS X version 10.10.3 och senare.|
|**Antal avancerade tecken som krävs i lösenord**|Ange det antal avancerade tecken som krävs i lösenordet (**0** till **4**).<br /><br />Ett avancerat tecken är en symbol som **?**.|
|**Minsta längd på lösenord**|Ange minimilängden för lösenordet (**4** till **14** tecken).|
|**Tillåt enkla lösenord**|Låt användarna skapa enkla lösenord som **0000** eller **1234**.|
|**Antal minuters inaktivitet innan lösenord krävs**|Ange hur länge datorn måste vara inaktiv innan ett lösenord krävs för att låsa upp den.|
|**Lösenordets giltighetstid (i dagar)**|Ange efter hur många dagar användaren måste byta lösenord (**1** till **255** dagar).|
|**Kom ihåg tidigare lösenord**|Förhindra att användaren använder ett lösenord som har använts tidigare. När den här inställningen används kan du även konfigurera **Förhindra återanvändning av tidigare lösenord** om du vill ange ett antal tidigare lösenord som inte får återanvändas (**1** till **24**).|
|**Minuter av inaktivitet innan skärmsläckaren aktiveras**|Ange hur länge datorn måste vara inaktiv innan skärmsläckaren aktiveras.|

### <a name="settings-for-compliant-and-noncompliant-apps"></a>Inställningar för kompatibla och icke-kompatibla appar
I listan **Kompatibla &amp; inkompatibla appar för Mac OS X** aktiverar du **Hanterade inställningar för enheter** och skapar sedan en lista över kompatibla eller inkompatibla appar med hjälp av följande information:

> [!NOTE]
> En enda princip kan innehålla endast en lista över kompatibla appar eller en lista över inkompatibla appar. Du kan inte ange båda i samma princip.
>
> Intune gör det möjligt att rapportera enheter med inkompatibla appar. Den blockerar inte installation eller tar bort inkompatibla appar.

|Inställningsnamn|Information|
|----------------|---------------|
|**Rapportera inkompatibilitet när användare installerar apparna i listan**|Visar de Mac OS X-appar som användare inte tillåts att installera. Om användarna installerar någon av de här apparna rapporteras de i **Rapporter om ej kompatibla appar**.|
|**Rapportera inkompatibilitet när användare installerar appar som inte är listade**|Visar de Mac OS X-appar som användare tillåts att installera. Om användarna installerar några andra appar rapporteras de i **Rapporter om ej kompatibla appar**.|
|**Lägg till**|Lägg till en app i den markerade listan. Ange ett namn, eventuellt appens utgivare och paket-ID för appen. **Tips!** Hitta paket-ID:t för en app på en Mac-dator där appen är installerad:<ol><li>Öppna mappen där appen har installerats (till exempel **/Appar**).</li><li>Välj paketet *&lt;Appnamn&gt;***.app** och välj **Visa paketinnehåll**.</li><li>Öppna filen **Info.plist**.</li><li>Kontrollera värdet som är associerat med nyckeln **CFBundleIdentifier**.</li></ol>Formatet för paket-ID är **com.contoso.appname**.|
|**Importera appar**|Importera en lista med appar som du har angett i en fil med kommaseparerade värden. I filen använder du det här formatet: appnamn, utgivare, appaket-ID.|
|**Redigera**|Redigera namn, utgivare och appaket-ID för den valda appen.|
|**Ta bort**|Ta bort den markerade appen från listan.|
> [!TIP]
> Mer information om Intune-rapporter finns i [Förstå Microsoft Intune-aktiviteter med hjälp av rapporter](understand-microsoft-intune-operations-by-using-reports.md).

> [!IMPORTANT]
> När en Mac OS X-enhet är i viloläge kan inte principer och profiler levereras eller inventeras. Därför kan det hända att Intune-konsolen tillfälligt visar statusen **Principinställningar med fel** tills enheten väcks ur viloläge nästa gång.

### <a name="monitor-compliant-and-noncompliant-apps"></a>Övervaka kompatibla och icke-kompatibla appar
Använd **Rapporter om ej kompatibla appar** för att visa kompatibiliteten för angivna appar.

#### <a name="to-run-a-report"></a>Skapa en rapport

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) väljer du **Rapporter** &gt; **Rapporter om ej kompatibla appar**.

2.  Välj de enhetsgrupper du vill kontrollera, välj om du vill söka efter kompatibla appar, icke kompatibla appar eller båda och välj sedan **Visa rapport**.

## <a name="mac-os-x-custom-policy-settings-in-microsoft-intune"></a>Anpassade principinställningar för Mac OS X i Microsoft Intune
Använd Microsoft Intunes **anpassade konfigurationsprincip för Mac OS X** för att distribuera inställningar som du skapat med hjälp av [Apple Configurator-verktyget](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) till Mac OS X-enheter. Med detta verktyg kan du skapa många inställningar som styr driften av dessa enheter och exportera dem till en konfigurationsprofil. Du kan sedan importera denna konfigurationsprofil till en anpassad princip för Mac OS X i Intune och distribuera inställningarna för användare och enheter i organisationen.

Med den här funktionen kan du distribuera Mac OS X-inställningar som inte kan konfigureras med den allmänna konfigurationsprincipen för Mac OS X i Intune.

### <a name="prerequisites"></a>Förutsättningar
Innan du börjar måste du ha installerat Apple Configurator och skapat en konfigurationsfil som innehåller de inställningar som du vill distribuera till användare eller enheter. Du kan ladda ned och lära dig om Apple Configurator från [Mac App Store](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12).

> [!NOTE]
> Intune rapporterar inte uppfyllande av individuella inställningar i en anpassad princip för Mac OS X. Dock rapporteras uppfyllande av principen som helhet.

### <a name="general-settings"></a>Allmänna inställningar

|Inställningsnamn|Information|
    |----------------|--------------------|
    |**Namn**|Ange ett unikt namn för en anpassad princip för Mac OS X som hjälper dig att identifiera den i Intune-konsolen.|
    |**Beskrivning**|Ange en beskrivning som ger en översikt över den anpassade principen för Mac OS X och annan relevant information som hjälper dig att hitta den.|


### <a name="custom-settings"></a>Anpassade inställningar

|Inställningsnamn|Information|
    |----------------|--------------------|
    |**Anpassat konfigurationsprofilnamn (visas för användare)**|Ange ett namn för principen som den kommer att visas på enheten och i principrapporter för Intune.|
    |**Konfigurationsprofilfil**|Välj **Importera** och bläddra sedan till den konfigurationsprofil som du skapat med hjälp av Apple Configurator. **Tips!** Se "Skapa en konfigurationsprofilfil" i det här avsnittet för hjälp med hur du skapar konfigurationsprofilen.|
    |**Information om konfigurationsprofilen**|Visa XML-koden för den konfigurationsprofil du har importerat.|



### <a name="how-to-create-a-configuration-profile-file"></a>Skapa en konfigurationsprofilfil
Du kan skapa filen för konfigurationsprofil som används av den anpassade principen på två sätt:

-   Exportera filen (med tillägget **.mobileconfig**) från Apple-konfigureringsverktyget.

-   Redigera filen själv med lämpligt schema från [Nyckelreferens för Apple-konfigurationsprofil](https://developer.apple.com/library/ios/featuredarticles/iPhoneConfigurationProfileRef/Introduction/Introduction.html).


### <a name="see-also"></a>Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
