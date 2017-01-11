---
title: "Registrera dig för en 30-dagars kostnadsfri utvärderingsversion av Microsoft Intune | Microsoft Docs"
description: "Registrera dig för och konfigurera en 30-dagars kostnadsfri utvärderingsversion av Microsoft Intune."
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 11/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 619a1d11-3d22-4635-8f70-770eba3e1712
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: a65ead23e62870647245120d1663706fc46810ac


---

# <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Registrera dig för en kostnadsfri utvärderingsversion av Microsoft Intune
Den här artikeln tar dig igenom registreringsproceduren för en utvärderingsversion av Intune och hjälper dig att förbereda utvärderingsversionen med några användare, så att du sedan kan följa den associerade utvärderingsguiden om du vill se hur Intune hanterar mobila enheter. <!---or app data when devices are not enrolled in Intune.--->

## <a name="assumptions"></a>Antaganden
I den här registrerings- och utvärderingsguiden förutsätter vi att du använder utvärderingsversionen i utvärderingssyfte och vill börja med en ren miljö när du prenumererar.

För att göra det lättare för dig att komma igång med utvärderingsversionen har vi konfigurerat en väldigt enkel miljö som enbart använder Intune och förutsätter att detta är din enda metod för att hantera enheter (även kallad MDM-auktoritet). Men igenom hela guiden gör vi dig uppmärksam på fördjupat tekniskt innehåll som du kan utforska vidare om du vill.

Du kan göra allt i utvärderingsversion som du kan göra i en prenumerationsversion. Den enda skillnaden är att du är begränsad till 100 användarkonton i utvärderingsversionen.

## <a name="sign-up-for-your-trial"></a>Registrera dig för din utvärderingsversion
Besök sidan för [Intune-registrering](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20) och fyll i registreringsformuläret för en utvärderingsprenumeration.

Om du har ett arbets- eller skolkonto och vill använda det för din Intune-utvärderingsversion av följer du [de här inloggningsanvisningarna](https://docs.microsoft.com/en-us/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-1) i stället. I den här artikeln och utvärderingen förutsätts det att du inte använder något sådant konto.

> [!TIP]
> Om de flesta av dina IT-åtgärder och användare använder ett annat språk än du gör, vill du kanske ange detta språk för testversionen för att kunna testa prestanda.

### <a name="post-sign-up-considerations"></a>Att tänka på efter registreringen
När du registrerar dig för en utvärderingsversion skickas ett e-postmeddelande med din kontoinformation till den e-postadress som du angav när du registrerade dig. E-postmeddelandet bekräftar att din utvärderingsversion är aktiv.

När du har slutfört inloggningsprocessen blir du omdirigerad till en sida där du kan lägga till användare och tilldela dem licenser med hjälp av Office 365 Administrationscenter. Nästa gång du loggar in till Intune omdirigeras du automatiskt till Intune-administrationskonsolen.

## <a name="keeping-the-admin-center-and-the-intune-administration-console-straight"></a>Skilja på Administrationscenter och Intune-administrationskonsolen
Det finns två portaler som du kan använda för Intune: Office 365 Administrationscenter ([portal.office.com](https://portal.office.com)) och Intune-administrationskonsolen ([manage.microsoft.com](https://manage.microsoft.com)).

Vanligtvis utför du ditt arbete i Intune-administrationskonsolen såsom visas nedan. Detta är den plats där du kan konfigurera och hantera grupper, principer, enheter och appar.

![Bild av Intune-administratörskonsolen](./media/sign-up/intune-admin-console.png)

Du använder dock Office 365-administrationscenter, som visas nedan, när du ska lägga till och hantera användare och olika kontofunktioner, t.ex. fakturering och support.

![Bild av Office 365-administratörscenter](./media/sign-up/office-admin-center.png)

Du kan navigera från Office 365 Administrationscenter till Intune-administrationskonsolen. Administrationscenterna hittar du under det sista objektet i det vänstra navigeringsfönstret. Öppna Intune-administrationskonsolen i en ny flik genom att välja **Intune**.

![Bild av länk till Intune-administratörskonsolen](./media/sign-up/link-to-intune.png)

Om du vill gå från Intune tillbaka till Office 365 Administrationscenter väljer du uppgiften **Lägg till användare** på sidan Översikt över grupper.

![Bild av länk tillbaka till Office 365-administratörscenter](./media/sign-up/task-add-users.png)

## <a name="add-users"></a>Lägg till användare
Innan du lämnar Office 365 Administrationscenter för att gå till Intune måste du lägga till några användare till ditt utvärderingskonto.

I Office 365 Administrationscenter kan du lägga till användare individuellt eller i grupp genom att ladda upp en .csv-fil. Vi konfigurerar din utvärderingsversion genom att göra båda sakerna. I din produktionsmiljö vill du dock förmodligen utnyttja dina Azure Active Directory-användarkonton, vilket du kan läsa mer om i guiden [Komma igång](https://docs.microsoft.com/en-us/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3) och i avsnittet [Nästa steg](#Next-steps) i den här artikeln.

### <a name="add-an-individual-user"></a>Lägg till en enskild användare
1. Välj ett av alternativen för att lägga till en användare. Då öppnas ett formulär där du kan skapa en användare. Endast de objekt som är markerade med en asterisk (\*) är obligatoriska.
![Bild av alternativ för knappen lägg till användare](./media/sign-up/add-user.png)


2.  När du lägger till en användare är det sista steget att skicka ett e-postmeddelande till användaren med hens tillfälliga Intune-lösenord. När det gäller den här utvärderingsversionen kan du använda din egen e-postadress på arbetet. På så vis får du tillgång till inloggningsinformationen och de e-postmeddelanden som skickas till dina användare. Du kan sedan använda dessa användaridentiteter för att registrera testenheter.<br/>

 ![Bild av sista steget för att lägga till användare](./media/sign-up/new-user-2.png)

3. Om du vill tilldela en användare en administratörsroll när du har skapat den kan du redigera rollen i Office 365 Administrationscenter genom att välja användarnamnet i listan över användare. Visa sedan listan över de användarroller som du kan välja bland och tilldela användaren genom att välja **Redigera** på raden Roll.

 ![Bild av alternativ för användarroll](./media/sign-up/change-user-role.png)

### <a name="import-multiple-users"></a>Importera flera användare
1. Du hittar guiden för att importera flera användare i listan **Mer**.

 ![Bild av möjlighet att lägga till flera användare](./media/sign-up/add-multiple-users.png)

2. Om du vill få hjälp med att konfigurera .csv-filen korrekt kan du hämta en mallfil som du fyller med dina användardata. Hämta den .csv-fil som innehåller rubriker och exempelanvändarinformation, så att du kan se exakt vilken typ av data som behövs för respektive fält.

 ![Bild av första steget i guiden massredigering](./media/sign-up/bulk-enroll-step-1.png)


3. Efter det att du har skapat och sparat .csv-filen kan du välja den genom att klicka på **Bläddra**. Verifiera och välj **Nästa**. Användarna överförs och läggs till i listan över aktiva användare.

Nu är det dags för dig att gå till Intune-administratörskonsolen och börja hantera dina användare och deras enheter och appar.

> [!NOTE]
> Dina användare visas inte i Intune förrän de har registrerat en enhet som ska hanteras.

## <a name="next-steps"></a>Nästa steg
Utvärderingsscenario: [Utvärdera mobilenhetshantering i Microsoft Intune](mobile-device-management-trial-guide-microsoft-intune.md)

Lär dig mer om hur du kan använda dina Azure Active Directory-användarkonton med Intune:
- [Identitetskrav](https://docs.microsoft.com/en-us/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)
- [Katalogsynkroniseringskrav](https://docs.microsoft.com/en-us/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)
- [Multifaktorautentiseringskrav](https://docs.microsoft.com/en-us/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)

Läs mer om hur du kan använda [Intune med System Center Configuration Manager](https://docs.microsoft.com/en-us/sccm/mdm/understand/hybrid-mobile-device-management)



<!--HONumber=Dec16_HO2-->

