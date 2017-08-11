---
title: Konfigurera Lookout-integreringen med Intune
titleSuffix: Intune on Azure
description: Konfigurera prenumerationen av Lookout med Intune
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5b0d7644-3183-45ba-a165-0d82d70cb71e
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c6af49be38e760e14824eb380e4cf3467a695df8
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="set-up-your-lookout-mobile-threat-defense-integration-with-intune"></a>Konfigurera Lookout Mobile Threat Defense-integreringen med Intune

Följande steg krävs för att konfigurera Lookout Mobile Threat Defense-prenumerationen:

| #        |Steg  |
| ------------- |:-------------|
| 1 | [Hämta Azure AD-information](#collect-azure-ad-information) |
| 2 | [Konfigurera din prenumeration](#configure-your-subscription) |
| 3 | [Konfigurera registreringsgrupper](#configure-enrollment-groups) |
| 4 | [Konfigurera tillståndssynkronisering](#configure-state-sync) |
| 5 | [Konfigurera information om e-postmottagare av felrapporter](#configure-error-report-email-recipient-information) |
| 6 | [Konfigurera registreringsinställningar](#configure-enrollment-settings) |
| 7 | [Konfigurera e-postaviseringar](#configure-email-notifications) |
| 8 | [Konfigurera hotklassificering](#configure-threat-classification) |
| 9 | [Bevaka registrering](#watching-enrollment) |

> [!IMPORTANT]
> En befintlig Lookout Mobile Endpoint Security-klient som inte redan är associerad med Azure AD-klient kan inte användas för integreringen med Azure AD och Intune. Kontakta Lookout-supporten för att skapa en ny Lookout Mobile Endpoint Security-klient. Använd den nya klienten att publicera dina Azure AD-användare.

## <a name="collect-azure-ad-information"></a>Hämta Azure AD-information
Din Lookout Mobility Endpoint Security-klient kommer att associeras med din Azure AD-prenumeration för att integrera Lookout med Intune. Om du vill aktivera tjänsteprenumerationen för Lookout Mobile Threat Defense, behöver Lookout-supporten (enterprisesupport@lookout.com) följande information:

* **Azure AD-klient-ID**
* **Azure AD-gruppobjekt-ID** för **fullständig** Lookout-konsolåtkomst
* **Azure AD-gruppobjekt-ID** för **begränsad** Lookout-konsolåtkomst (valfritt)

Använd följande steg för att samla in den information du måste förse Lookout-supportteamet med.

1. Logga in på [Azure-portalen](https://portal.azure.com) och välj prenumeration. 

2. När du väljer namnet på din prenumeration måste den URL som bildas omfatta prenumerations-ID.  Om du har problem med att hitta ditt prenumerations-ID kan du läsa den här [Microsoft support-artikeln](https://support.office.com/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b) och få hjälp.

3. Hitta ditt grupp-ID för Azure AD. Lookout-konsolen stöder två åtkomstnivåer:  
  * **Fullständig åtkomst:** Azure AD-administratören kan skapa en grupp för användare som kommer att ha fullständig åtkomst och de kan även skapa en grupp med användare som har begränsad tillgång.  Endast användare i dessa grupper kommer att kunna logga in till **Lookout-konsolen**.
  * **Begränsad åtkomst:** Användarna i den här gruppen kommer inte ha åtkomst till ett flertal konfigurations- och registreringsrelaterade moduler i Lookout-konsolen, och ha skrivskyddad åtkomst till **Säkerhetsprincip**-modulen i Lookout-konsolen.  

    > [!TIP] 
    > Mer information om behörigheterna finner du i [den här artikeln](https://personal.support.lookout.com/hc/articles/114094105653) på webbplatsen Lookout.

    > [!NOTE] 
    > **Grupp-objekt-ID:t** finns på **egenskapssidan** för gruppen i **Azure AD-hanteringsportalen**.

4. Kontakta Lookout-supporten (e-post: enterprisesupport@lookout.com) när du har samlat in den här informationen. Lookout-supporten kommer att samarbeta med din primära kontakt för att publicera din prenumeration och skapa ditt företagskonto för Lookout med hjälp av informationen som du samlat in.

## <a name="configure-your-subscription"></a>Konfigurera din prenumeration

1. När Lookout har skapat ditt Lookout Enterprise-konto skickas ett e-postmeddelande från Lookout till den primära kontakten för ditt företag med en länk till inloggnings-url-adressen: https://aad.lookout.com/les?action=consent.

2.  Den första inloggningen på Lookout-konsolen måste ske med ett användarkonto som har Azure AD-rollen global administratör för att kunna registrera Azure AD-klienten. Inloggningen kräver inte denna nivå på Azure AD-behörighet senare. En samtyckessida visas. Välj **Acceptera** för att slutföra registreringen. När du har accepterat och samtyckt till villkoren omdirigeras du till Lookout-konsolen.

    ![skärmbild av sidan för den första inloggningen i Lookout-konsolen](./media/lookout_mtp_initial_login.png)
    > [Obs!] Se [felsöka Lookout-integrering](https://docs.microsoft.com/intune/troubleshoot/troubleshooting-lookout-integration) om du vill ha hjälp med inloggningsproblem.

3.  I [Lookout-konsolen](https://aad.lookout.com) går du till **System**-modulen och väljer fliken **Kopplingar** och sedan **Intune**.

    ![skärmbild som visar Lookout-konsolen med fliken för anslutningar öppen och alternativet Intune markerat](./media/lookout_mtp_setup-intune-connector.png)

4.  Välj **Kopplingar** > **Anslutningsinställningar** och ange **Pulsslagsfrekvens** i minuter.

    ![skärmbild av fliken för anslutningsinställningar som visar hur pulsslagsfrekvensen konfigurerats](./media/lookout-mtp-connection-settings.png)

## <a name="configure-enrollment-groups"></a>Konfigurera registreringsgrupper
1. Du bör skapa en Azure AD-säkerhetsgrupp i [Azure AD-hanteringsportalen](https://manage.windowsazure.com) som innehåller ett litet antal användare för att testa Lookout-integreringen.

    > [Obs!] Alla Intune-registrerade enheter som stöds av Lookout, tillhör användare i en registreringsgrupp, har identifierats och stöds registreras och kan aktiveras i Lookout MTD-konsolen.

2. I [Lookout-konsolen](https://aad.lookout.com) går du till **System**-modulen, väljer fliken **Anslutningar** och väljer **Registreringshantering** för att definiera en uppsättning användare vars enheter ska registreras med Lookout. Lägg till Azure AD-säkerhetsgruppens **Visningsnamn** för registrering.

    ![skärmbild som visar sidan registrering av Intune-anslutning](./media/lookout-mtp-enrollment.png)

    >[!IMPORTANT]
    > Detta **Visningsnamn** är skiftlägeskänsligt så som visas i **Egenskaper** i säkerhetsgruppen i Azure-portalen. Som bilden nedan visar är säkerhetsgruppens **Visningsnamn** en kamelnotation medan titeln endast använder gemener. I Lookout-konsolen är skiftläget för **Visningsnamn** samma som för säkerhetsgruppen.
    >![skärmbild av egenskaper-sidan för Azure Active Directory-tjänsten i Azure-portalen](./media/aad-group-display-name.png)

    >[!NOTE] 
    >Det rekommenderas att använda de inställningar som är standard (fem minuter) för tidsintervallerna då nya enheter eftersöks. Aktuella begränsningar: **Lookout kan inte verifiera gruppvisningsnamn:** Se till att fältet **VISNINGSNAMN** i Azure-portalen matchar Azure AD-säkerhetsgruppen exakt. **Det går inte att skapa kapslade grupper:** Azure AD-säkerhetsgrupper som används i Lookout får endast innehålla användare. De får inte innehålla andra grupper.

3.  Första gången en användare öppnar Lookout for Work-appen på en enhet efter att en grupp har lagts till aktiveras enheten i Lookout.

4.  När du är nöjd med resultaten kan du utöka registreringen till ytterligare användargrupper.

## <a name="configure-state-sync"></a>Konfigurera tillståndssynkronisering
För alternativet **Synkronisering av programtillstånd** anger du vilken typ av data som ska skickas till Intune.  Både enhetsstatus och hotstatus krävs för att Lookout Intune-integrationen ska fungera korrekt. De här inställningarna är aktiverade som standard.

## <a name="configure-error-report-email-recipient-information"></a>Konfigurera information om e-postmottagare av felrapporter
Ange den e-postadress som ska ta emot felrapporter i alternativet **Error Management** (Felhantering).

![skärmbild som visar sidan för felhantering för Intune Connector](./media/lookout-mtp-connector-error-notifications.png)

## <a name="configure-enrollment-settings"></a>Konfigurera registreringsinställningar
I modulen **System** på sidan **Kopplingar** anger hur många dagar innan en enhet betraktas som frånkopplad.  Frånkopplade enheter betraktas som icke-kompatibla och kommer att blockeras från att komma åt företagsprogrammen baserat på principer för villkorlig åtkomst i Intune. Du kan ange värden mellan 1 och 90 dagar.

![Lookout-registreringsinställningar](./media/lookout-console-enrollment-settings.png)

## <a name="configure-email-notifications"></a>Konfigurera e-postaviseringar
Logga in i [Lookout-konsolen](https://aad.lookout.com) med det användarkonto som ska ta emot meddelanden om du vill ta emot e-postaviseringar för hot. På fliken **Inställningar** i **System**-modulen väljer du de hotnivåer som ska generera meddelanden och ställer in dem på **PÅ**. Spara ändringarna.

![skärmbild som visar sidan för inställningar där användarkontot visas](./media/lookout-mtp-email-notifications.png) Om du inte längre vill ta emot e-postaviseringar väljer du alternativet **AV** för meddelanden och sparar ändringarna.

### <a name="configure-threat-classification"></a>Konfigurera hotklassificering
Lookout Mobile Threat Defense klassificerar olika typer av mobila hot. [Lookout-hotklassificeringar](http://personal.support.lookout.com/hc/articles/114094130693) är kopplade till standardrisknivåer. Dessa kan ändras när som helst för att passa företagets krav.

![skärmbild av sidan för principer som visar hot och klassificeringar](./media/lookout-mtp-threat-classification.png)

>[!IMPORTANT]
> Risknivåerna är en viktig del av Mobile Threat Defense eftersom Intune-integreringen beräknar enhetens efterlevnad enligt dessa risknivåer vid körning. Intune-administratören anger en regel i principen för att identifiera att en enhet är icke-kompatibel om den har ett aktivt hot med miniminivån **Hög**, **Medel** eller **Låg**. Principen för hotklassificering i Lookout Mobile Threat Defense styr direkt efterlevnadsberäkningen för enheten i Intune.

## <a name="watching-enrollment"></a>Bevakar registreringen
När installationen är klar börjar Lookout Mobile Threat Defense avsöka Azure AD efter enheter som motsvarar de angivna registreringsgrupperna.  Du hittar information om de enheter som registrerats i modulen Enheter.  Den första statusen för enheterna är ”väntar”.  Enhetens status ändras när Lookout for Work-appen har installerats, öppnats och aktiverats på enheten.  Mer information om hur du skickar Lookout for work-appen till enheten finns i avsnittet [Add Lookout for work apps with Intune](mtd-apps-ios-app-configuration-policy-add-assign.md) (lägga till Lookout for work-appar med Intune).
## <a name="next-steps"></a>Nästa steg
[Aktivera Lookout MTD-anslutning i Intune](mtd-connector-enable.md)