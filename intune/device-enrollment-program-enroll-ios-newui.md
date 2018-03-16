---
title: "Registrera iOS-enheter – Enhetsregistreringsprogrammet"
titlesuffix: Azure portal
description: "Läs hur du registrerar företagsägda iOS-enheter med programmet för enhetsregistrering (nytt gränssnitt).”"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/08/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7ddbf360-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 48b74b81c9f3f8b9c936ae22a343ccfb565b4ec1
ms.sourcegitcommit: cccbb6730a8c84dc3a62093b8910305081ac9d24
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/15/2018
---
# <a name="automatically-enroll-ios-devices-with-apples-device-enrollment-program"></a>Registrera iOS-enheter automatiskt med Apples DEP (Device Enrollment Program)

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

> [!NOTE]
> ### <a name="temporary-user-interface-differences"></a>Tillfälliga skillnader i användargränssnittet
> Användargränssnitt för de funktioner som beskrivs i den här sidan håller på att uppdateras. De här uppdateringarna lanseras över alla användarkonton fram till slutet av April.
>
> Om din sida för **Enhetsregistrering** ser ut som på bilden nedan, har du det uppdaterade användargränssnittet och kan använda den här hjälpsidan.
>
> ![Nytt användargränssnitt](./media/appleenroll-newui.png)
>
> Om din sida för **Enhetsregistrering** ser ut som på bilden nedan, har ditt konto ännu uppdaterats till det nya användargränssnittet. Gå till [den här hjälpsidan](device-enrollment-program-enroll-ios.md).
>
> ![Gammalt användargränssnitt](./media/appleenroll-oldui.png)

Det här avsnittet hjälper dig att aktivera registrering av iOS-enheter som köpts via Apples [program för enhetsregistrering (DEP)](https://deploy.apple.com). Du kan aktivera DEP-registrering för ett stort antal enheter utan att behöva röra dem. Du kan leverera enheter som iPhone och iPad direkt till användare. När användaren sätter på enheten körs installationsassistenten med de konfigurerade inställningarna och enheten registreras i hanteringen.

Om du vill aktivera DEP-registrering kan du använda både Intune och Apples DEP-portal. En lista med serienummer eller inköpsordernummer krävs så att du kan tilldela enheter till Intune för hantering. Du kan skapa DEP-registreringsprofiler som innehåller inställningar som verkställs på enheterna under registreringen.

DEP-registreringen fungerar dock inte med [enhetsregistreringshanteraren](device-enrollment-manager-enroll.md).

## <a name="what-is-supervised-mode"></a>Vad är övervakat läge?
Apple införde övervakat läge i iOS 5. En iOS-enhet i övervakat läge kan hanteras med fler kontroller. Det är därför användbart för företagsägda enheter. Intune har stöd för konfigurering av enheter för övervakat läge som en del av Apples program för enhetsregistrering (DEP). 

<!--
**Steps to enable enrollment programs from Apple**
1. [Get an Apple DEP token and assign devices](#get-the-apple-dep-token)
2. [Create an enrollment profile](#create-an-apple-enrollment-profile)
3. [Synchronize DEP-managed devices](#sync-managed-device)
4. [Assign DEP profile to devices](#assign-an-enrollment-profile-to-devices)
5. [Distribute devices to users](#end-user-experience-with-managed-devices)
-->
## <a name="prerequisites"></a>Krav
- Enheter som köpts i [Apples enhetsregistreringsprogram](http://deploy.apple.com)
- [MDM-utfärdare](mdm-authority-set.md)
- [Apple MDM-pushcertifikat](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Hämta en Apple DEP-token

Innan du kan registrera iOS-enheter med DEP behöver du en DEP-tokenfil (.p7m) från Apple. Med denna token kan Intune synkronisera information om DEP-enheter som ditt företag äger. Intune kan även överföra registreringsprofiler till Apple och tilldela enheter till dessa profiler.

Du kan använda Apples DEP-portal för att skapa en DEP-token. Du kan också använda DEP-portalen för att tilldela enheter till Intune för hantering.

> [!NOTE]
> Om du tar bort denna token från den klassiska Intune-portalen innan du migrerar till Azure, kan Intune återställa en borttagen Apple DEP-token. Du kan ta bort DEP-token från Azure-portalen igen. Du kan ta bort DEP-token från Azure-portalen igen.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>Steg 1. Ladda ned certifikatet för den offentliga Intune-nyckeln som krävs för att skapa token.

1. I Intune i Azure-portalen, väljer du **Enhetsregistrering** > **Apple-registrering** > **Registreringsprogramtokens** > **Lägg till**.

    ![Hämta en registreringsprogramtoken.](./media/device-enrollment-program-enroll-ios/image01.png)

2. Välj **Hämta den offentliga nyckeln** om du vill hämta och spara krypteringsnyckelfilen (.pem) lokalt. Filen .pem används för att begära ett förtroendecertifikat från portalen Apples DEP.
  ![Skärmbild av rutan Registreringsprogramtoken i arbetsytan för Apple-certifikat. Nedladdning av offentlig nyckel.](./media/device-enrollment-program-enroll-ios/image02.png)

### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>Steg 2. Använd din nyckel för att hämta en token från Apple.

1. Välj **Skapa en token för Apples enhetsregistreringsprogram** för att öppna Apples portal för distributionsprogram och logga in med ditt företags Apple-ID. Du måste använda detta Apple-ID för att kunna förnya DEP-token.
2.  Gå till Apples [portal för driftsättningsprogram](https://deploy.apple.com) och välj **Kom igång** för **Enhetsregistreringsprogram**.

3. På sidan **Hantera servrar** väljer du **Lägg till MDM-server**.
4. Ange **MDM-servernamnet** och välj **Nästa**. Servernamnet är för din egen referens och hjälper dig att identifiera MDM-servern (hantering av mobilenheter). Det är inte namnet eller URL-adressen för Microsoft Intune-servern.

5. Dialogrutan **Lägg till &lt;ServerName&gt;**  öppnas med meddelandet **Upload Your Public Key** (Överför din offentliga nyckel). Välj **Välj fil** för att överföra PEM-filen och välj sedan **Nästa**.

6. Gå till **Distributionsprogram** &gt; **Program för enhetsregistrering** &gt; **Hantera enheter**.
7. Under **Choose Devices By** (Välj enheter efter) anger du hur enheterna ska identifieras:
    - **Serienummer**
    - **Ordernummer**
    - **Ladda upp CSV-fil**.

   ![Skärmbild av någon som anger enheterna ska visas efter serienummer, väljer åtgärden Assign to Server (Tilldela till server) och sedan servernamnet.](./media/enrollment-program-token-specify-serial.png)

8. Välj **Assign to Server** (Tilldela till server) för **Välj åtgärd** och välj **servernamnet** som angetts för Microsoft Intune och sedan &lt;OK&gt;. Apples portal tilldelar de angivna enheterna till Intune-servern för hantering och visar sedan meddelandet **Assignment Complete** (Tilldelningen är klar).

   Gå till Apple-portalen och **Driftsättningsprogram** &gt; **Enhetsregistreringsprogram** &gt; **View Assignment History (Visa historik för tilldelning)** för att se en lista över enheter och deras MDM-servertilldelning.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>Steg 3. Spara det Apple-ID som användes för att skapa den här token.

I Intune på Azure-portalen anger du ditt Apple-ID för framtida bruk.

![Skärmbild av någon som anger det Apple-ID som användes för att skapa registreringsprogramtoken och bläddrat till denna token.](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token"></a>Steg 4. Överför din token.
I rutan **Apple-token**, bläddrar du till certifikatfilen (.pem), väljer **Öppna** och väljer sedan **Skapa**. Med pushcertifikatet kan Intune registrera och hantera iOS-enheter genom push-överföring av principer till registrerade mobila enheter. Intune synkroniseras automatiskt med Apple och visar ditt registreringsprogramkonto.

## <a name="create-an-apple-enrollment-profile"></a>Skapa en Apple-registreringsprofil

Nu när du har installerat din token kan skapa du en registreringsprofil för DEP-enheter. En enhetsregistreringsprofil definierar inställningarna som tillämpas på en grupp av enheter vid registreringen.

1. I Intune på Azure-portalen väljer du **Enhetsregistrering** > **Apple-registrering** > **Token för registreringsprogram**.
2. Välj en token, välj **Profiler** och välj sedan **Skapa profil**.
    ![Skapa en profilskärmbild.](./media/device-enrollment-program-enroll-ios/image04.png)
3. Under **Skapa profil**, anger du ett **Namn** och **Beskrivning** för profilen för administrationssyfte. Användarna kan inte se den här informationen. Du kan använda fältet **Namn** för att skapa en dynamisk grupp i Azure Active Directory. Använd profilnamnet för att definiera parametern enrollmentProfileName för att tilldela registreringsprofilen till enheter. Läs mer om [dynamiska Azure Active Directory-grupper](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects).
    ![Profilnamn och beskrivning.](./media/device-enrollment-program-enroll-ios/image05.png)

4. Ange om enheter med den här profilen måste registreras med eller utan en tilldelad användare under **Användartillhörighet**.
    - **Registrera med användartillhörighet** – välj det här alternativet för enheter som tillhör användare och som vill använda företagsportalen för tjänster som installation av appar. Det här alternativet låter också användare autentisera sina enheter med företagsportalen. Mappning mellan användare kräver [WS-Trust 1.3 användarnamn/kombinerad slutpunkt](https://technet.microsoft.com/library/adfs2-help-endpoints). [Läs mer](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

    - **Registrera utan användartillhörighet** – välj det här alternativet för enheter som inte är kopplade till en enda användare. Använd det här för enheter som utför uppgifter utan att komma åt lokala användardata. Appar som företagsportalappen fungerar inte.

5. Om du väljer **Registrera med användartillhörighet**, får du alternativet att låta användare autentisera sig med Företagsportalen istället för Apple Installationsassistenten.

    ![Autentisera med Företagsportalen.](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > Multifaktorautentisering (MFA) fungerar inte vid DEP-registrering om du har profilegenskaperna inställda på **Registrera med användartillhörighet** och du inte använder en Företagsportal. Efter registreringen fungerar MFA som förväntat på enheterna. Enheterna kan inte uppmana användare som behöver ändra sina lösenord när de loggar in första gången. Användare vars lösenord har upphört att gälla ombeds inte att återställa sina lösenord under registreringen. Användarna måste återställa lösenordet från en annan enhet.

6. Välj **Inställningar för enhetshantering** och välj om du vill att enheter som använder den här profilen ska övervakas.
    **Övervakade** enheter ger dig fler hanteringsalternativ och inaktiverar aktiveringslåset som standard. Microsoft rekommenderar att du använder DEP som mekanism för att aktivera övervakat läge, särskilt för organisationer som distribuerar större antal iOS-enheter.

    Användare meddelas att deras enheter är övervakade på två sätt:

    - Låsskärmen säger: ”Den här iPhone hanteras av Contoso.”
    - Skärmen **Inställningar** > **Allmänt** > **Om** säger: ”Den här iPhone är övervakad. Contoso can monitor your Internet traffic and locate this device." (Denna iPhone är övervakad. Contoso kan övervaka din Internettrafik och hitta denna enhet.)

     > [!NOTE]
     > En enhet som registrerats utan övervakning kan bara återställas genom att använda Apple Configurator. Om du återställer enheten på det här sättet, måste du ansluta en iOS-enhet till en Mac-dator med en USB-kabel. Läs mer om detta i [dokumentation för Apple Configurator](http://help.apple.com/configurator/mac/2.3).
     
7. Välj om du vill ha låst registrering för enheter som använder den här profilen. **Låst registrering** inaktiverar iOS-inställningarna som tillåter att hanteringsprofilen tas bort från **Inställningar**-menyn. När enhetsregistreringen är klar går det inte att ändra inställningen utan att göra en fabriksåterställning av enheten. Sådana enheter måste ha hanteringsläget **Övervakad** inställt på *Ja*. 

8. Välj om du vill att enheter som använder den här profilen ska kunna **Synkronisera med datorer**. Om du väljer **Tillåt Apple Configurator efter certifikat** måste du välja ett certifikat under **Apple Configurator-certifikat**.

9. Om du väljer **Tillåt Apple Configurator efter certifikat** i föregående steg, väljer du ett Apple Configurator-certifikat att importera.

10. Välj **OK**.

11. Välj **Inställningar för inställningsassistenten** för att konfigurera följande profilinställningar: ![Anpassning av inställningsassistenten.](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)

    | Inställningen | Description |
    | --- | --- |
    | **Avdelningsnamn** | Visas när användare trycker på **Om konfiguration** vid aktiveringen. |
    | **Avdelningens telefonnummer** | Visas när användaren klickar på knappen **Behöver hjälp** vid aktiveringen. |
    | **Alternativ för installationsassistenten** | Följande valfria inställningar kan ställas in senare i iOS **Inställningar**-menyn. |
    | **Lösenord** | Fråga efter lösenord under aktiveringen. Kräv alltid ett lösenord om inte enheten är skyddad eller åtkomstkontrolleras på något annat sätt (t.ex. helskärmsläge som begränsar enheten till en app). |
    | **Platstjänster** | Om den här funktionen är aktiverad frågar installationsassistenten efter tjänsten under aktivering. |
    | **Återställa** | Om den här funktionen är aktiverad frågar Installationsassistenten om iCloud-säkerhetskopiering vid aktivering. |
    | **iCloud och Apple-ID** | Om det här alternativet är aktiverat, ber installationsassistenten användaren att logga in med ett Apple-ID och skärmen Appar och Data låter enheten återställas från iCloud-säkerhetskopiering. |
    | **Villkor** | Om det här alternativet är aktiverat, ber installationsassistenten användare att godkänna Apples villkor vid aktiveringen. |
    | **Touch ID** | Om det här alternativet är aktiverat, frågar installationsassistenten efter den här tjänsten under aktivering. |
    | **Apple Pay** | Om det här alternativet är aktiverat, frågar installationsassistenten efter den här tjänsten under aktivering. |
    | **Zoom** | Om det här alternativet är aktiverat, frågar installationsassistenten efter den här tjänsten under aktivering. |
    | **Siri** | Om det här alternativet är aktiverat, frågar installationsassistenten efter den här tjänsten under aktivering. |
    | **Diagnostikdata** | Om det här alternativet är aktiverat, frågar installationsassistenten efter den här tjänsten under aktivering. |

12. Välj **OK**.

13. Spara profilen genom att välja **Skapa**.

## <a name="sync-managed-devices"></a>Synkronisera hanterade enheter
Nu när Intune har fått behörighet att hantera dina enheter, kan du synkronisera Intune med Apple och se dina hanterade enheter i Intune på Azure-portalen.

1. I Intune i Azure-portalen, väljer du **Enhetsregistrering** > **Apple-registrering** > **Registreringsprogramtokens** > välj en token i listan > **Enheter** > **Synkronisera**. ![Skärmbild där noden Registreringsprogramenheter har valts och länkvärde håller på att väljas.](./media/device-enrollment-program-enroll-ios/image06.png)
  
  För att följa Apples villkor för godkänd registreringsprogramtrafik tillämpar Intune följande begränsningar:
  - En fullständig synkronisering kan inte köras oftare än en gång var sjunde dag. Vid en fullständig synkronisering uppdateras Intune med alla Apple-serienummer som tilldelats till Intune. Om du försöker köra en fullständig synkronisering inom sju dagar efter den föregående fullständiga synkroniseringen uppdaterar Intune endast serienummer som inte redan visas i Intune.
  - Varje synkroniseringsbegäran har 15 minuter på sig att slutföras. Under den här tiden, eller tills begäran slutförts, är knappen **Synkronisera** inaktiverad.
  - Intune synkroniserar nya och borttagna enheter med Apple var 24:e timme.

## <a name="assign-an-enrollment-profile-to-devices"></a>Tilldela enheterna en registreringsprofil
Du måste tilldela en registreringsprogramprofil till enheterna innan de kan registreras.

>[!NOTE]
>Du kan även tilldela profiler serienummer från bladet **Apple-serienummer**.

1. I Intune i Azure-portalen, väljer du **Enhetsregistrering** > **Apple-registrering** > **Registreringsprogramtokens** > välj en token i listan.
2. Välj **Enheter** > välj enheter i listan > **Tilldela profil**.
3. Under **Tilldela profil**, väljer du en profil för enheterna och sedan **Tilldela**.

### <a name="assign-a-default-profile"></a>Ange som standardprofil

Du kan välja en standardprofil som ska tillämpas för alla enheter som registreras med en specifik token.

1. I Intune i Azure-portalen, väljer du **Enhetsregistrering** > **Apple-registrering** > **Registreringsprogramtokens** > välj en token i listan.
2. Välj **Ange standardprofil**, välj en profil i listmenyn och välj sedan **Spara**. Den här profilen kommer att tillämpas på alla enheter som registreras med token.

## <a name="distribute-devices"></a>Distribuera enheter
Du har aktiverat hantering och synkronisering mellan Apple och Intune, och har tilldelat en profil så att DEP-enheterna kan registreras. Du kan nu distribuera enheter till användare. Enheter med användartillhörighet kräver att varje användare tilldelas en Intune-licens. Enheter utan användartillhörighet kräver en enhetslicens. En aktiverad enhet kan inte använda en registreringsprofil förrän enheten har återställts till fabriksinställningarna.

Se [Registrera din iOS-enhet i Intune med enhetsregistreringsprogrammet](/intune-user-help/enroll-your-device-dep-ios).

