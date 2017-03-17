---
title: "Du får felmeddelanden när du försöker registrera din iOS-enhet | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 92a8d06d-0ecb-4912-898b-993e8eaf4e58
searchScope:
- User help
ROBOTS: 
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: a87fe0cf9591040f1455d71b1f40cd0705ba8abf
ms.openlocfilehash: 06866b9db458851dbb23d5ccf741cad3e1d4c5d0
ms.lasthandoff: 01/24/2017


---

# <a name="you-see-errors-while-trying-to-enroll-your-ios-device-in-intune"></a>Du får felmeddelanden när du försöker registrera din iOS-enhet i Intune

Följande tabell innehåller felmeddelanden som kan visas när du registrerar en iOS-enhet i Intune. Dela den här länken med din IT-administratör. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](http://portal.manage.microsoft.com).

|Felmeddelande|Problem|Vad du ska berätta för din IT-administratör|
|-----------------|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|NoEnrollmentPolicy|Ingen registreringsprincip|Kontrollera att alla krav för registrering har konfigurerats, till exempel APNs-certifikatet (Apple Push Notification Service), och att ”iOS som en plattform” är aktiverat. Anvisningar finns i [Konfigurera iOS- och Mac-enhetshantering](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).|
|DeviceCapReached|Du har för många registrerade mobila enheter.|För att kunna registrera en ny enhet måste användaren först ta bort en registrerad mobil enhet från företagsportalen. Se anvisningar för den typ av enhet som du använder: [Android](unenroll-your-device-from-intune-android.md), [iOS](unenroll-your-device-from-intune-ios.md), [Windows](unenroll-your-device-from-intune-windows.md).|
|APNSCertificateNotValid|Det är problem med det certifikat som gör det möjligt för den mobila enheten att kommunicera med företagets nätverk.<br /><br />Kontakta IT-administratörerna och berätta att du fått meddelandet **APNSCertificateNotValid** när du försökte registrera din mobila enhet. Be dem också ta en titt på lösningen i den här tabellen.|Apple Push Notification Service (APNs) tillhandahåller en kanal som kan användas för att nå ut till registrerade iOS-enheter. Om alla steg för att erhålla ett APNs-certifikat inte utfördes, eller om APNs-certifikatet har upphört att gälla, misslyckas registreringsförsöket och det här meddelandet visas.<br /><br />Mer information om hur du konfigurerar användare finns i [Synkronisera Active Directory och lägga till användare i Intune](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3) och [Ordna användare och enheter](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5).|
|AccountNotOnboarded|Det är problem med det certifikat som gör det möjligt för den mobila enheten att kommunicera med företagets nätverk.<br /><br />Kontakta IT-administratörerna och berätta att du fått meddelandet **APNSNotOnboarded** när du försökte registrera din mobila enhet. Be dem också ta en titt på lösningen i den här tabellen.|Apple Push Notification Service (APNs) tillhandahåller en kanal som kan användas för att nå ut till registrerade iOS-enheter. Om alla steg för att erhålla ett APNs-certifikat inte utfördes, eller om APNs-certifikatet har upphört att gälla, misslyckas registreringsförsöket och det här meddelandet visas.<br /><br />Mer information finns i [Konfigurera och iOS- och Mac-hantering med Microsoft Intune](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).|
|DeviceTypeNotSupported|Du kan ha försökt att registrera en icke-iOS-enhet. Den typ av mobil enhet som du försöker registrera stöds inte.<br /><br />Kontrollera att enheten kör iOS version 8.0 eller senare.<br /><br />Kontakta IT-administratörerna och berätta att du fått meddelandet **DeviceTypeNotSupported** när du försökte registrera din mobila enhet. Be dem också ta en titt på lösningen i den här tabellen.|Kontrollera att användarens enhet kör iOS version 8.0 eller senare.|
|UserLicenseTypeInvalid|Du kan inte registrera din mobila enhet eftersom ditt användarkonto ännu inte är medlem i någon obligatorisk användargrupp.<br /><br />Kontakta IT-administratörerna och berätta att du fått meddelandet **UserLicenseTypeInvalid** när du försökte registrera din mobila enhet. Be dem också ta en titt på lösningen i den här tabellen.|Innan användarna kan registrera sina enheter måste de vara medlemmar i rätt användargrupp. Det här meddelandet anger att de har fel licenstyp för den angivna hanteringsauktoriteten för mobila enheter. Det här felet visas till exempel om Intune har angetts som utfärdare för hantering av mobila enheter och användarna har en licens för System Center 2012 R2 Configuration Manager.<br /><br />Läs följande om du vill ha mer information:<br /><br />Läs [Konfigurera iOS- och Mac-hantering med Microsoft Intune](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) och informationen om hur du konfigurerar användare i [Synkronisera Active Directory och lägga till användare i Intune](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3) och [Ordna användare och enheter](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5).|
|MdmAuthorityNotDefined|IT-administratören måste konfigurera hur mobila enheter i företaget ska hanteras.<br /><br />Kontakta IT-administratörerna och berätta att du fått meddelandet **MdmAuthorityNotDefined** när du försökte registrera din mobila enhet. Be dem också ta en titt på lösningen i den här tabellen.|Utfärdaren för hantering av mobila enheter har inte angetts i Intune.<br /><br />Läs punkt 1 i avsnittet ”Steg 6: Registrera mobila enheter och installera en app” i [Kom igång med en 30-dagars utvärderingsversion av Microsoft Intune](/Intune/Understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune).|
