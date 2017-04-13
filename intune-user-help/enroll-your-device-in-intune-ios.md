---
title: Registrera din iOS-enhet i Intune | Microsoft Docs
description: Beskriver hur du registrerar en iOS-enhet i Intune
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: 
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: 1ba0dab35e0da6cfe744314a4935221a206fcea7
ms.openlocfilehash: af3313e6ba5cbf9184aaaa9b197f7a3b2b9d4c3e
ms.lasthandoff: 03/13/2017


---


# <a name="enroll-your-ios-device-in-intune"></a>Registrera din iOS-enhet i Intune

Om företaget eller skolan använder Microsoft Intune kan du registrera din iOS-enhet så att den får tillgång till företagets e-post, filer och andra resurser. När du registrerar dina enheter kan IT-avdelningen hantera deras arbets- eller skolresurser, skydda dem och samtidigt ge dig friheten att använda den enhet du önskar för att utföra ditt arbete. Mer information om registrering finns i [Vad händer om man installerar företagsportalappen och registrerar enheten i Intune?](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios.md)

<iframe src="https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

> [!NOTE]
> Om du försöker registrera en macOS-enhet, t.ex. en MacBook Pro eller iMac, [kan du prova de här anvisningarna i stället](enroll-your-device-in-intune-macos.md).

**Innan du börjar**

- Se till att du avslutar registreringen efter att du påbörjat stegen. Om du pausar under mer än ett par minuter, så stoppas vanligtvis processen, och du måste att starta om den.
- Om din registrering av någon anledning misslyckas måste du gå tillbaka till företagsportalsappen och försöka igen.
- Kontrollera att din Wi-Fi fungerar. Annars misslyckas registreringen.
- Om du har blockerat Safari på enheten, avblockera Safari. Du måste använda Safari för att registrera.


**Så här registrerar du din iOS-enhet:**

1.  Följ stegen i [Installera och logga in på Intune-företagsportalappen](install-and-sign-in-to-the-intune-company-portal-app-ios.md).

2. Tryck på **Börja** på sidan **Konfiguration av företagsåtkomst**.

    ![ios-enroll-comp-access-setup-begin](./media/ios-enroll-1a-comp-access-setup.png)

3. På skärmen **Varför ska jag registrera enheten?** kan du läsa vad du kan göra när du har registrerat enheten. Tryck sedan på **Fortsätt**.

    ![ios-enroll-why-enroll](./media/ios-enroll-1b-why-enroll.png)

> [!NOTE]
> De gula trianglarna innebär inte att du redan har råkat ut för ett fel. Ikonerna anger att det fortfarande finns oavslutade steg i registreringsprocessen.

4. Läs igenom listan över vad IT-administratören kan och inte kan se på den registrerade enheten och tryck sedan på **Fortsätt**.

    ![ios-enroll-what-it-can-see](./media/ios-enroll-1c-we-care-privacy.png)

5.  På skärmen **Vad kommer härnäst** kan du läsa om vad som händer under registreringen. Tryck sedan på **Registrera**.

     ![ios-enroll-what-comes-next](./media/ios-enroll-1d-what-comes-next.png)

6.  Tryck på **Installera** på skärmen **Installera profil** och ange ditt lösenord om du uppmanas att göra det.

    ![ios-enroll-install-profile](./media/ios-enroll-2-mgt-profile-install.png)

7.  Tryck på **Installera**.

    ![ios-enroll-tap-install](./media/ios-enroll-3-mgt-profile-install-2.png)    

8.  Tryck på **Installera** för att visa att du har läst varningen.

       ![ios-enroll-tap-install-after-warning](./media/ios-enroll-4-warning.png)

9.  Tryck på **Förtroende**.

       ![ios-enroll-tap-trust](./media/ios-enroll-5-trust.png)

10.  När skärmen ändras och visar att installationen av profilen är klar trycker du på **Klar**.

     ![ios-enroll-tap-done](./media/ios-enroll-6-done.png)

    Ett meddelande om att enheten registreras visas på skärmen.

11.  När ett meddelande frågar om du vill öppna sidan i företagsportalen trycker du på **Öppna**.

    ![ios-enroll-open-comp-portal](./media/ios-enroll-7-open-cp.png)

12. Tryck på **Fortsätt** på skärmen **Konfiguration av företagsåtkomst**. Om IT-administratören har konfigurerat ytterligare säkerhetskrav, t.ex. att ett lösenord måste anges, följer du anvisningarna på skärmen tills du uppfyller alla kompatibilitetskrav och kommer tillbaka till skärmen Konfiguration av företagsåtkomst. Tryck sedan på **Fortsätt**.

    ![ios-enroll-comp-access-tap-continue](./media/ios-enroll-8-comp-access-setup-compliance.png)

13. Tap **Klar**.

    ![ios-enroll-tap-done](./media/ios-enroll-9-comp-access-setup-complete.png)

Enheten har nu registrerats i Intune och du kommer tillbaka till företagsportalappen.

> [!Note]
> Om din organisation använder kostnad hanteringsprogramvara för telekomtjänster måste ytterligare ett part steg utföras innan enheten har registrerats fullständigt. Läs mer [här](enroll-your-device-with-telecom-expense-management-ios.md).

Behöver du fortfarande hjälp? Kontakta IT-administratören. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](http://portal.manage.microsoft.com).
