---
title: "Hantera enhetsinställningar med principer"
description: "Med Intune kan du skapa och distribuera principer som styr inställningar och funktioner på de registrerade enheter som du hanterar."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 09bae0b9-4f79-4658-8ca1-a71ab992c1b2
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f8ceb98181543d846934a16b8c9551207892ae0e
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="manage-settings-and-features-on-your-devices-with-microsoft-intune-policies"></a>Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune-*principer* är grupper med inställningar som styr funktioner på datorer och mobila enheter. Du skapar principer med hjälp av mallar som innehåller rekommenderade eller anpassade inställningar och distribuerar dem till enhets- eller användargrupper.

## <a name="types-of-policies"></a>Typer av principer

Intune-principer hör till följande kategorier. Den kategori som du använder påverkar hur du skapar och distribuerar principen.


- **Konfigurationsprinciper**: De används ofta för att hantera säkerhetsinställningar och -funktioner på dina enheter. Använd informationen i det här avsnittet om du vill veta mer om hur du skapar och distribuerar de här principerna och utforska de tillgängliga inställningarna.
- **Efterlevnadsprinciper för enheter**: De definierar reglerna och inställningarna som en enhet måste följa för att den ska anses vara kompatibel med principerna för villkorlig åtkomst. Du kan också använda efterlevnadsprinciper för att övervaka och åtgärda enheters efterlevnad oberoende av villkorlig åtkomst.
Mer information finns i [Efterlevnadsprinciper för enheter i Microsoft Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md).
- **Principer för villkorlig åtkomst**: De här principerna skyddar e-post och andra tjänster utifrån de villkor du anger.
Mer information finns i [Begränsa åtkomsten till e-post och O365-tjänster med Microsoft Intune](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)
- **Principer för registrering av företagets enheter**: Information om principer för registrering av företagets enheter finns i [Konfigurera iOS- och Mac-hantering med Microsoft Intune](set-up-ios-and-mac-management-with-microsoft-intune.md).
- **Resursåtkomstprinciper**: Dessa principer fungerar tillsammans så att användarna får åtkomst till de filer och resurser som de behöver för att utföra sitt arbete, oavsett var de befinner sig.
Mer information finns i [Ge åtkomst till företagsresurser med Microsoft Intune](enable-access-to-company-resources-with-microsoft-intune.md).


En fullständig lista över Intune-principer finns i [Principreferens för Microsoft Intune](microsoft-intune-policy-reference.md).

## <a name="create-a-configuration-policy"></a>Skapa en konfigurationsprincip

1.  Öppna [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com/) och välj **Princip** &gt; **Konfigurationsprinciper** &gt; **Lägg till**.

2.  Välj den princip som du vill använda. Du kan välja de rekommenderade inställningarna för principen (du kan ändra inställningarna senare) eller skapa en anpassad princip med dina egna inställningar.

    > [!TIP]
    > Mer hjälp om vilken princip du ska använda finns i [Principreferens för Microsoft Intune](microsoft-intune-policy-reference.md).

3.  Välj **Skapa princip** när du är klar.

4.  Konfigurera ett namn och en valfri beskrivning för principen på skärmen **Skapa princip**.

5.  Konfigurera nödvändiga principinställningar och välj **Spara princip**.

    Om du behöver hjälp med några principinställningar väljer du principtypen i följande lista:

    - [Inställningar för iOS-enheter](ios-policy-settings-in-microsoft-intune.md)
    - [Inställningar för Android-enheter](android-policy-settings-in-microsoft-intune.md)
    - [Inställningar för Android for Work-enheter](android-for-work-policy-settings-in-microsoft-intune.md)
    - [Inställningar för Windows 8- och Windows 8.1-enheter](windows-configuration-policy-settings-in-microsoft-intune.md)
    - [Inställningar för Windows Phone 8.1-enheter](windows-phone-8-1-policy-settings-in-microsoft-intune.md)
    - [Inställningar för stationära och mobila Windows 10-enheter](windows-10-policy-settings-in-microsoft-intune.md)
    - [Inställningar för Windows Team-enheter](windows-team-configuration-policy-settings-in-microsoft-intune.md)
    - [Inställningar för uppgradering av Windows-utgåva](edition-upgrade-policy-settings-in-microsoft-intune.md)
    - [Inställningar för Mac OS X-enheter](mac-os-x-policy-settings-in-microsoft-intune.md)
    - [Inställningar för Exchange ActiveSync](exchange-activesync-policy-settings-in-microsoft-intune.md)
    - [Inställningar för villkorsprincipen](terms-and-condition-policy-settings-in-microsoft-intune.md)
    - [Allmänna inställningar för mobila enheter (äldre)](mobile-device-security-policy-settings-in-microsoft-intune.md)

4.  I bekräftelsedialogrutan väljer du **Ja** om du vill distribuera principen nu eller **Nej** om du vill skapa principen utan att distribuera den.

Du kan visa och redigera den nya principen genom att gå igenom ämnena för respektive principtyp på arbetsytan **Princip**.

När du skapar en princip som använder de rekommenderade inställningarna är namnet på den nya principen en kombination av mallnamn, datum och tid. När du redigerar principen uppdateras namnet med tiden och datumet för redigeringen.

När du har skapat en princip vill du förmodligen distribuera den till en eller flera grupper med användare eller enheter.

> [!TIP]
> Du distribuerar inte alla principtyper. Exempelvis distribuerar du inte hanteringsprincipen för mobilprogram (MAM). Den här principtypen associeras i stället med en app, som du sedan distribuerar.

## <a name="deploy-a-configuration-policy"></a>Distribuera en konfigurationsprincip

1.  På arbetsytan **Princip** markerar du den princip som du vill distribuera och väljer sedan **Hantera distribution**.

2.  I dialogrutan **Hantera distribution** :

    -   Om du vill distribuera principen väljer du en eller flera grupper som du vill distribuera principen till. Välj sedan **Lägg till** &gt; **OK**.

    -   Om du vill stänga dialogrutan utan att distribuera principen väljer du **Avbryt**.

När du väljer en distribuerad princip visas ytterligare information om distributionen i den nedre delen av principlistan.

## <a name="manage-policies"></a>Hantera principer

1.  I [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com/) väljer du **Princip** och bläddrar sedan till, och markerar, den princip som du vill hantera.

2.  Välj någon av följande åtgärder:

- **Redigera**: Öppnar egenskaperna för den markerade principen så att du kan göra ändringar.
- **Ta bort**: Tar bort den markerade principen.<br>När du tar bort en princip tas den bort från alla grupper som den har distribuerats till.
- **Hantera distribution**: Välj den grupp som du vill distribuera principen till och välj sedan **Lägg till**.


## <a name="frequently-asked-questions-about-intune-policies"></a>Vanliga frågor om Intune-principer

### <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-deployed"></a>Hur lång tid tar det innan principerna eller apparna når mobilenheterna efter att de har distribuerats?
När en princip eller app distribueras börjar Intune genast att uppmana enheten att kontakta Intune-tjänsten. Detta brukar ta mindre än fem minuter.

Om enheten inte kontaktar tjänsten för att be om principen när den första aviseringen har skickats, görs ytterligare tre försök.  Om enheten är offline (till exempel om den är avstängd eller inte är ansluten till ett nätverk) kanske den inte får aviseringarna. I så fall får enheten principen vid nästa schemalagda kontakt med Intune-tjänsten enligt följande:

- iOS och Mac OS X: Var 6:e timme.
- Android: Var 8:e timme.
- Windows Phone: Var 8:e timme.
- Windows 8.1- och Windows 10-datorer som har registrerats som enheter: Var 8:e timme.

Om enheten precis har registrerats sker kontrollerna oftare enligt följande:

- iOS och Mac OS X: Var 15:e minut i 6 timmar och därefter var 6:e timme.
- Android: Var 3:e minut i 15 minuter, därefter var 15:e minut i 2 timmar och sedan var 8:e timme.
- Windows Phone: Var 5:e minut i 15 minuter, därefter var 15:e minut i 2 timmar och sedan var 8:e timme.
- Windows-datorer som registrerats som enheter: Var 3:e minut i 30 minuter och därefter var 8:e timme.

Användarna kan också söka efter principer när som helst genom att öppna företagsportalappen och synkronisera enheten.

### <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Vilka åtgärder gör att Intune genast skickar en avisering till en enhet?
Enheter kontaktar Intune antingen när de får en avisering som uppmanar dem att göra det, eller enligt schemalagda intervall.  När du specifikt riktar en åtgärd mot en enhet eller användare, t.ex. en rensning, låsning, återställning av lösenord, appdistribution, profildistribution (Wi-Fi, VPN, e-post osv.) eller principdistribution, börjar Intune genast att försöka meddela enheten att den ska kontakta Intune-tjänsten för att få dessa uppdateringar.

Andra ändringar, t.ex. en uppdatering av kontaktinformationen på företagsportalen, utlöser inte en omedelbar avisering till enheter.

### <a name="if-multiple-policies-are-deployed-to-the-same-user-or-device-how-do-i-know-which-settings-will-get-applied"></a>Hur vet jag vilka inställningar som tillämpas om flera principer distribueras till samma användare eller enhet?
När två eller fler principer distribueras till samma användare eller enhet så görs utvärderingen av vilken inställning som ska tillämpas på inställningsnivå:

-   Inställningar för efterlevnadsprinciper har alltid högre prioritet än inställningar för konfigurationsprinciper.

-   Den mest restriktiva efterlevnadsprincipinställningen tillämpas om den utvärderas och jämförs med samma inställning i en annan efterlevnadsprincip.

-   Om en konfigurationsprincipinställning hamnar i konflikt med en inställning i en annan konfigurationsprincip visas konflikten i Intune-konsolen. Du måste lösa dessa konflikter manuellt.

### <a name="what-happens-when-mobile-application-management-policies-conflict-with-each-other-which-one-will-be-applied-to-the-app"></a>Vad händer om hanteringsprinciper för mobilprogram (MAM) är i konflikt med varandra? Vilken används för appen?
Konfliktvärden är de mest restriktiva inställningarna som är tillgängliga i en MAM-princip, förutom fälten för nummerinmatning (t.ex. PIN-försök före återställning).  Nummerinmatningsfälten får samma värden som då du skapar en MAM-princip i konsolen med alternativet för rekommenderade inställningar.

Konflikter uppstår om två principinställningar är samma.  Anta att du har konfigurerat två MAM-principer som är identiska förutom inställningen för kopiera/klistra in.  I detta scenario används det mest restriktiva värdet för kopierings- och inklistringsinställningen, men resten av inställningarna tillämpas så som de konfigurerats.

Om en princip distribueras till appen och börjar tillämpas, och en andra princip distribueras senare, har den första principen företräde och fortsätter att tillämpas, medan den andra visas som i konflikt. Om båda tillämpas samtidigt, och det inte finns någon föregående princip, kommer båda att vara i konflikt. Som med alla inställningar i konflikt tillämpas de mest restriktiva värdena.

### <a name="what-happens-when-ios-custom-policies-conflict"></a>Vad händer om anpassade iOS-principer är i konflikt med varandra?
Intune utvärderar inte nyttolasten för Apple Configuration-filer eller anpassade OMA-URI-principer (Open Mobile Alliance Uniform Resource Identifier). Den fungerar bara som själva leveransmekanismen.

När du distribuerar en anpassad princip bör du se till att de konfigurerade inställningarna inte är i konflikt med efterlevnadsprinciper, konfigurationsprinciper eller andra anpassade principer. Om en anpassad princip har inställningar som är i konflikt med varandra tillämpas dessa inställningar i slumpmässig ordning.

### <a name="what-happens-when-a-policy-is-deleted-or-no-longer-applicable"></a>Vad händer när en princip tas bort eller inte längre är tillämplig?
När du tar bort en princip, eller när du tar bort en enhet från en grupp som en princip har distribuerats till, tas principer och inställningar bort från enheten enligt följande listor.

#### <a name="enrolled-devices"></a>Registrerade enheter

- Wi-Fi-, VPN-, certifikat- och e-postprofiler – De här profilerna tas bort från alla registrerade enheter som stöds.
- Alla andra principtyper:
    - **Windows- och Android-enheter**: Inställningarna tas inte bort från enheten.
    - **Windows Phone 8.1-enheter**: Följande inställningar tas bort:
        - Kräv ett lösenord för att låsa upp mobila enheter
        - Tillåt enkla lösenord
        - Minsta längd på lösenord
        - Lösenordstyp krävs
        - Lösenordets giltighetstid (i dagar)
        - Kom ihåg tidigare lösenord
        - Antal tillåtna, upprepad felinloggningar innan enheten rensas
        - Antal minuters inaktivitet innan lösenord krävs
        - Krävd lösenordstyp – minsta antal tecken
        - Tillåt kamera
        - Filkryptering på mobil enhet
        - Tillåt flyttbara lagringsenheter
        - Tillåt webbläsare
        - Tillåt appbutik
        - Tillåt skärmbild
        - Tillåt geolokalisering
        - Tillåt Microsoft-konto
        - Tillåt kopiera och klistra in
        - Tillåt Wi-Fi -delning
        - Tillåt automatisk anslutning till kostnadsfria, trådlösa surfpunkter
        - Tillåt rapportering av trådlösa surfpunkter
        - Tillåt fabriksåterställning
        - Tillåt Bluetooth
        - Tillåt NFC
        - Tillåt Wi-Fi

    - **iOS**: Alla inställningar tas bort, utom:
        - Tillåt röstroaming
        - Tillåt dataroaming
        - Tillåt automatisk synkronisering vid roaming

#### <a name="windows-pcs-running-the-intune-client-software"></a>Windows-datorer med Intune-klientprogramvaran

- **Endpoint Protection-inställningar**: Inställningarna återställs till rekommenderade värden. Det enda undantaget är inställningen **Delta i Microsoft Active Protection Service** där standardvärdet är **Nej**. Mer information finns i [Skydda Windows-datorer med Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).
- **Inställningar för programuppdateringar**: Inställningarna återställs till standardläget för operativsystemet. Mer information finns i [Hålla Windows-datorer uppdaterade med programvaruppdateringar i Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md).
- **Microsoft Intune Center-inställningar**: All kontaktinformation för support som konfigurerats av principen tas bort från datorerna.
- **Inställningar för Windows-brandväggen**: Inställningarna återställs till standardinställningarna för datorns operativsystem. Mer information finns i [Skydda Windows-datorer med Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).


### <a name="how-can-i-refresh-the-policies-on-a-device-to-ensure-that-they-are-current-applies-to-windows-pcs-running-the-intune-client-software-only"></a>Hur kan jag uppdatera principerna på en enhet för att säkerställa att de är aktuella (gäller endast Windows-datorer med Intune-klientprogramvaran)?

1.  Markera de enheter i en enhetsgrupp som du vill uppdatera principerna på och välj sedan **Fjärruppgifter** &gt; **Uppdatera principer**.
2.  Välj **Fjärruppgifter** i det nedre högra hörnet i Intune-administratörskonsolen för att kontrollera aktivitetsstatusen.

### <a name="where-can-i-find-help-troubleshooting-policies"></a>Var kan jag få hjälp med att felsöka principer?

Se [Felsökningsprinciper i Microsoft Intune](/intune-classic/troubleshoot/troubleshoot-policies-in-microsoft-intune).