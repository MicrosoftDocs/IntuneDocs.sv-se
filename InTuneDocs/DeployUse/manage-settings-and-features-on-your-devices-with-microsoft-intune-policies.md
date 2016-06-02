---
# required metadata

title: Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 09bae0b9-4f79-4658-8ca1-a71ab992c1b2

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer
Microsoft Intune-**principer** är grupper med inställningar som styr funktioner på datorer och mobila enheter. Du skapar principer med hjälp av mallar som innehåller rekommenderade eller anpassade inställningar och distribuerar dem till enhets- eller användargrupper.

## Vilka typer av principer kan du använda?

Intune-principer hör till följande kategorier. Den kategori som du använder påverkar hur du skapar och distribuerar principen.


- **Konfigurationsprinciper:** De används ofta för att hantera säkerhetsinställningar och -funktioner på dina enheter. Använd informationen i det här avsnittet om du vill veta mer om hur du skapar och distribuerar de här principerna och utforska de tillgängliga inställningarna.
- **Efterlevnadsprinciper för enheter:** De definierar reglerna och inställningarna som en enhet måste följa för att anses vara kompatibel med principerna för villkorlig åtkomst. Du kan också använda efterlevnadsprinciper för att övervaka och åtgärda enheters efterlevnad oberoende av villkorlig åtkomst.
Mer information finns i [Enhetsefterlevnadsprinciper i Microsoft Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md).
- **Principer för villkorlig åtkomst:** De här principerna skyddar e-post och andra tjänster utifrån de villkor du anger.
Mer information finns i [Begränsa åtkomsten till e-post och O365-tjänster med Microsoft Intune](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).
- **Principer för registrering av företagets enheter:** Information om principer för registrering av företagets enheter finns i [Konfigurera iOS- och Mac-hantering med Microsoft Intune](set-up-ios-and-mac-management-with-microsoft-intune.md).
- **Resursåtkomstprinciper:** Den här gruppen med principer fungerar tillsammans så att användarna får åtkomst till de filer och resurser som de behöver för att utföra sitt arbete, oavsett var de befinner sig.
Mer information finns i [Ge åtkomst till företagsresurser med Microsoft Intune](enable-access-to-company-resources-with-microsoft-intune.md).


En fullständig lista över Intune-principer finns i [Principreferens för Microsoft Intune](microsoft-intune-policy-reference.md).




## Skapa en konfigurationsprincip

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com/) klickar du på **Princip** &gt; **Konfigurationsprinciper** &gt; **Lägg till**.

2.  Välj den princip som du vill använda, välj att använda de rekommenderade inställningarna för principen (om de är tillgängliga kan du ändra inställningarna senare) eller välj att skapa en anpassad princip med dina egna inställningar.

    > [!TIP]
    > Hjälp med att välja rätt princip finns i [Principreferens för Microsoft Intune](microsoft-intune-policy-reference.md).

3.  Klicka på **Skapa princip** när du är klar.

4.  Konfigurera ett namn och en valfri beskrivning för principen på skärmen **Skapa princip** .

5.  Konfigurera nödvändiga principinställningar och klicka på **Spara princip**.

    Om du behöver hjälp med några principinställningar väljer du principtypen i följande lista:

    - [Inställningar för iOS-enheter](ios-policy-settings-in-microsoft-intune.md)
    - [Inställningar för Android-enheter](android-policy-settings-in-microsoft-intune.md)
    - [Inställningar för Windows 8- och Windows 8.1-enheter](windows-configuration-policy-settings-in-microsoft-intune.md)
    - [Inställningar för Windows Phone 8.1-enheter](windows-phone-8-1-policy-settings-in-microsoft-intune.md)
    - [Inställningar för stationära och mobila Windows 10-enheter](windows-10-policy-settings-in-microsoft-intune.md)
    - [Inställningar för Windows Team-enheter](windows-team-configuration-policy-settings-in-microsoft-intune.md)
    - [Inställningar för uppgradering av Windows-utgåva](edition-upgrade-policy-settings-in-microsoft-intune.md)
    - [Inställningar för Mac OS X-enheter](mac-os-x-policy-settings-in-microsoft-intune.md)
    - [Inställningar för Exchange ActiveSync](exchange-activesync-policy-settings-in-microsoft-intune.md)
    - [Inställningar för villkorsprincipen](terms-and-condition-policy-settings-in-microsoft-intune.md)
    - [Allmänna inställningar för mobila enheter (äldre)](mobile-device-security-policy-settings-in-microsoft-intune.md)

4.  I bekräftelsedialogrutan klickar du på **Ja** om du vill distribuera principen nu eller klickar på **Nej** om du vill skapa principen utan att distribuera den.

Du kan visa och redigera den nya principen genom att gå igenom ämnena för respektive principtyp på arbetsytan **Princip** .

När du skapar en princip som använder de rekommenderade inställningarna är namnet på den nya principen en kombination av mallnamn, datum och tid. När du redigerar principen uppdateras namnet med tiden och datumet för redigeringen.

Nu när du har skapat en princip vill du förmodligen distribuera den till en eller flera grupper med användare eller enheter.

> [!TIP]
> Du distribuerar inte alla principtyper. Exempelvis distribuerar du inte hanteringsprincipen för mobilprogram. Den här principtypen associeras i stället med en app, som du sedan distribuerar.

## Distribuera en konfigurationsprincip

1.  Välj den princip som du vill distribuera på arbetsytan **Princip** och klicka sedan på **Hantera distribution**.

2.  I dialogrutan **Hantera distribution** :

    -   **Om du vill distribuera principen** – Markera en eller flera grupper som du vill distribuera principen till och klicka sedan på **Lägg till** &gt; **OK**.

    -   **Om du vill stänga dialogrutan utan att distribuera den** – Klicka på **Avbryt**.

När du väljer en distribuerad princip visas ytterligare information om distributionen i den nedre delen av principlistan.

## Hantera principer

1.  I [administrationskonsolen för Microsoft Intune](https://manage.microsoft.com/), klickar du på **Princip**, bläddrar sedan fram och markerar den princip som du vill hantera.

2.  Välj någon av följande åtgärder:

- **Redigera** – Öppnar egenskaperna för den markerade principen så att du kan göra ändringar.
- **Ta bort** – Tar bort den markerade principen.<br>När du tar bort en princip tas den bort från alla grupper som den har distribuerats till.
- **Hantera distribution** – Välj den grupp som du vill distribuera principen till och klicka på **Lägg till**.

## Uppgifter för Intune-principer

### Så här gör du om du vill uppdatera principerna på en enhet för att säkerställa att de är aktuella (gäller endast Windows-datorer med Intune-klientprogramvaran)

1.  I [administrationskonsolen för Microsoft Intune](https://manage.microsoft.com/), klickar du på **Grupper**och väljer en enhetsgrupp.

2.  Markera de enheter som du vill uppdatera principerna på och klicka sedan på **Fjärruppgifter** &gt; **Uppdatera principer**.

3.  Klicka på **Fjärruppgifter** i det nedre högra hörnet i Intune-administrationskonsolen för att kontrollera aktivitetsstatusen.

## Referensinformation för Intune-principer

### Hur lång tid tar det innan principerna eller apparna når mobilenheterna efter att de har distribuerats?
När en princip eller app distribueras börjar Intune genast att uppmana enheten att kontakta Intune-tjänsten. Detta brukar ta mindre än fem minuter.

Om enheten inte kontaktar tjänsten för att be om principen när den första aviseringen har skickats, görs ytterligare tre försök.  Om enheten är offline (till exempel om den är avstängd eller inte är ansluten till ett nätverk) kanske den inte får aviseringen.

I så fall får enheten principen vid nästa schemalagda kontakt med Intune-tjänsten enligt följande:

- iOS – Var 6:e timme
- Android – Var 8:e timme
- Windows Phone – Var 8:e timme
- Windows-datorer som registrerats som enheter – Var 24:e timme

Om enheten precis har registrerats sker kontrollerna oftare enligt följande:

- iOS – Var 15:e minut i 6 timmar och därefter var 6:e timme
- Android – Var 3:e minut i 15 minuter, därefter var 15:e minut i 2 timmar och sedan var 8:e timme
- Windows Phone – Var 5:e minut i 15 minuter, därefter var 15:e minut i 2 timmar och sedan var 8:e timme
- Windows-datorer som registrerats som enheter – Var 3:e minut i 30 minuter och därefter var 24:e timme

Användarna kan också söka efter principer när som helst genom att starta appen Företagsportal och synkronisera enheten.

### Vilka åtgärder gör att Intune genast skickar en avisering till en enhet?
Enheter kontaktar Intune antingen när de får en avisering som uppmanar dem att göra det, eller enligt de schemalagda intervall som anges i tabellerna ovan.  När du specifikt riktar en åtgärd mot en enhet eller användare, t.ex. en rensning, låsning, återställning av lösenord, appdistribution, profildistribution (Wi-Fi, VPN, e-post osv.) eller principdistribution, börjar Intune genast att försöka meddela enheten att den ska kontakta Intune-tjänsten för att få dessa uppdateringar.

Andra ändringar, t.ex. en uppdatering av kontaktinformationen på företagsportalen, utlöser inte en omedelbar avisering till enheter.

> [!TIP]
> När en princip som innehåller inställningar distribueras till en Android-enhet uppmanas användaren att vidta åtgärder för att följa principen. De nya principinställningarna börjar gälla när användaren vidtar dessa åtgärder eller när enheten startas om.

### Hur vet jag vilka inställningar som tillämpas om flera principer distribueras till samma användare eller enhet?
Det är viktigt att veta att när två eller fler principer distribueras till samma användare eller enhet så görs utvärderingen av vilken inställning som tillämpas på inställningsnivå.

-   Inställningar för efterlevnadsprinciper har alltid högre prioritet än inställningar för konfigurationsprinciper.

-   Den mest restriktiva efterlevnadsprincipinställningen tillämpas om den utvärderas och jämförs med samma inställning i en annan efterlevnadsprincip.

-   Den mest restriktiva konfigurationsprincipinställningen tillämpas om den utvärderas och jämförs med samma inställning i en annan konfigurationsprincip.

### Vad händer om hanteringsprinciper för mobilprogram (MAM) är i konflikt med varandra? Vilken används för appen?
Konfliktvärden är de mest restriktiva inställningarna som är tillgängliga i en hanteringsprincip för mobilprogram, förutom fälten för nummerinmatning (t.ex. PIN-försök före återställning).  Nummerinmatningsfälten får samma värden som då du skapar en MAM-princip i konsolen med alternativet för rekommenderade inställningar.

Konflikter uppstår om två principinställningar är samma.  Anta att du har konfigurerat två MAM-principer som är identiska förutom inställningen för kopiera/klistra in.  I detta scenario används det mest restriktiva värdet för kopierings- och inklistringsinställningen, men resten av inställningarna tillämpas så som de konfigurerats.

Om en princip distribueras till appen och börjar tillämpas, och en andra princip distribueras senare, har den första principen företräde och fortsätter att tillämpas, medan den andra visas som i konflikt. Om båda däremot tillämpas samtidigt, och det inte finns någon föregående princip, kommer båda att vara i konflikt, och som med alla inställningar i konflikt tillämpas de mest restriktiva värdena.

### Vad händer om anpassade iOS-principer är i konflikt med varandra?
Intune utvärderar inte nyttolasten för Apple Configuration-filer eller anpassade OMA-URI-principer, utan fungerar bara som själva leveransmekanismen.

När du distribuerar en anpassad princip bör du därför se till att de konfigurerade inställningarna inte är i konflikt med efterlevnads- och konfigurationsprinciper eller andra anpassade principer. Om en anpassad princip har inställningar som är i konflikt med varandra tillämpas dessa inställningar i slumpmässig ordning.

### Vad händer när en princip tas bort eller inte längre tillämpas
När du tar bort en princip eller tar bort en enhet från en grupp som en princip har distribuerats till, tas principer och inställningar bort från enheten enligt följande tabeller:

#### Registrerade enheter

- Wi-Fi-, VPN-, certifikat- och e-postprofiler – De här profilerna tas bort från alla registrerade enheter som stöds.
- Alla andra principtyper
    - **Windows- och Android-enheter** – Inställningarna tas inte bort från enheten.
    - **Windows Phone 8.1-enheter** – Följande inställningar tas bort:
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
    
    - **iOS** – Alla inställningar tas bort, utom:
        - Tillåt röstroaming
        - Tillåt dataroaming
        - Tillåt automatisk synkronisering vid roaming

#### Windows-datorer med Intune-klientprogramvaran

- **Endpoint Protection-inställningar** – Inställningarna återställs till rekommenderade värden. Det enda undantaget är inställningen **Delta i Microsoft Active Protection Service** där standardvärdet är **Nej**. Mer information finns i [Skydda Windows-datorer med Endpoint Protection för Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).
- **Inställningar för programuppdateringar** – Inställningarna återställs till standardläget för operativsystemet. Mer information finns i [Hålla Windows PC-datorerna uppdaterade med programvaruuppdateringar i Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md).
- **Microsoft Intune Center-inställningar** – All kontaktinformation för support som konfigurerats av principen tas bort från datorerna.
- **Inställningar för Windows-brandväggen** – Inställningarna återställs till standardinställningarna för datorns operativsystem. Mer information finns i [Skydda Windows-datorer med Endpoint Protection för Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).





<!--HONumber=May16_HO1-->

