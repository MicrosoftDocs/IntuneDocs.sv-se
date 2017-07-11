---
title: "Hantera volyminköpta iOS-appar"
description: "Intune hjälper dig att hantera appar som du volyminköpt av Apple genom att importera licensinformationen från App Store, spåra hur många licenser som du har använt och hindra dig från att installera fler kopior av appen än du äger."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1dafc28a-7f8b-4fe0-8619-f977c93d1140
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f2600864eaf127810639e76932adbd422b4e0008
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Hantera iOS-appar som du har köpt via ett volyminköpsprogram med Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

I iOS App Store kan du köpa flera licenser för en app som du vill använda i företaget. Det hjälper dig att minska det administrativa arbetet med att spåra flera köpta kopior av appar.

Microsoft Intune hjälper dig att hantera appar som du har köpt via det här programmet genom att importera licensinformationen från App Store, spåra hur många licenser som du har använt och hindra dig från att installera fler kopior av appen än du äger.

> [!Important]
> Intune tilldelar för närvarande iOS-applicenser via volyminköpsprogrammet för företag (VPP) till användare och inte enheter. Därför måste användare ange sitt Apple-ID-lösenord för att installera appen.
> Apple VPP för utbildning stöds inte för den här versionen.

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Hantera appar som köpts genom volyminköpsprogrammet för iOS-enheter
Du kan köpa flera licenser för iOS-appar genom [Apples volyminköpsprogram för företag](http://www.apple.com/business/vpp/). När du gör det måste du bland annat skapa ett Apple VPP-konto från Apples webbplats och ladda upp din Apple VPP-token till Intune.  Sedan kan du synkronisera volyminköpsinformationen med Intune och spåra din användning av appar som du köpt genom volyminköpsprogrammet.

## <a name="before-you-start"></a>Innan du börjar
Innan du börjar måste du skaffa en VPP-token från Apple och ladda upp den till ditt Intune-konto. Du bör också känna till följande:

* Intune har stöd för att lägga till upp till 256 VPP-token.
* Om du tidigare har använt en VPP-token med en annan produkt måste du generera en ny som ska användas med Intune.
* Varje token är giltig i ett år.
* Som standard synkroniserar Intune med Apple VPP-tjänsten två gånger om dagen. Du kan starta en manuell synkronisering när som helst.
* När du har importerat VPP-token i Intune ska du inte importera samma token till andra enhetshanteringslösningar. Om du gör det kan licenstilldelningen och användarposter gå förlorade.
* Innan du börjar använda iOS VPP med Intune tar du bort alla befintliga VPP-användarkonton som skapats med andra MDM-leverantörer (hantering av mobila enheter). Intune synkroniserar inte de användarkontona till Intune som en säkerhetsåtgärd. Intune synkroniserar endast data från den Apple VPP-tjänst som skapades av Intune.
* Du kan endast distribuera iOS VPP-appar till användares enheter som har registrerats med hjälp av Device Enrollment Protocol (DEP) om enhetens användartillhörighet har konfigurerats.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Så här skaffar du och laddar upp en Apple VPP-token

1.  Gå till [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) och välj **Admin** &gt; **iOS och Mac OS X** &gt; **Volyminköpsprogram**.

2.  Välj länken **Apple VPP-konto**. Registrera dig för volyminköpsprogrammet för företag om du inte redan gjort det. När du har registrerat dig laddar du ned Apple VPP-token för ditt konto.

3.  På sidan **Hantera Apple VPP (Volume Purchase Program)** i Intune-konsolen väljer du **Överför VPP-token**.

4.  I dialogrutan **Överför en VPP-token** anger du eller klistrar in namnet på VPP-token och ditt Apple-ID och väljer sedan **Överför**.

5.  I varningsdialogrutan markerar du kryssrutan för att bekräfta att du är medveten om att du inte kan byta till ett annat VPP-konto senare och väljer sedan **Ja**.

På sidan **Volyminköpsprogram** kan du nu visa information om Apple VPP-token, inklusive när den senast uppdaterades, när den upphör att gälla och när den senast synkroniserades med Intune.

Du kan synkronisera data från Apple med Intune när som helst genom att välja **Synkronisera nu**.

## <a name="to-deploy-a-volume-purchased-app"></a>Distribuera en volyminköpt app

1.  Gå till [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) och välj **Appar** &gt; **Appar** &gt; **Volyminköpta appar**. I listan visas alla appar som har synkroniserats från Apple VPP-tjänsten.

2.  Välj den app som du vill distribuera, välj sedan **Hantera distribution** och slutför överföringen, skapa och distribuera appen med hjälp av anvisningarna i avsnittet [Distribuera appar i Microsoft Intune](deploy-apps-in-microsoft-intune.md).

> [!TIP]
> Du måste välja distributionsåtgärden **Krävs**. Tillgängliga installationer stöds för närvarande inte. Dessutom kan du bara distribuera appen till användargrupper.

När du distribuerar appar som en **obligatorisk** installation använder alla användare som installerar appen en licens.

Om du vill frisläppa en licens måste du ändra distributionsåtgärden till **Avinstallera**. Licensen frisläpps när appen avinstalleras.

När användare med kvalificerande enheter försöker installera en VPP-app ombeds de att gå med i Apples volyminköpsprogram. De måste göra detta innan appinstallationen fortsätter.

Distributionen misslyckas om det inte finns fler tillgängliga licenser.

## <a name="to-monitor-apple-vpp-apps"></a>För att övervaka Apple VPP-appar
Du kan övervaka vilka VPP-appar som har distribuerats och hur många licenser som används från arbetsýtan **Appar** i noden **Volyminköpta appar**.

> [!TIP]
> Du kan också använda **appfilter** för att kontrollera statusen för varje appinstallation.

### <a name="see-also"></a>Se även
[Distribuera appar i Microsoft Intune](deploy-apps-in-microsoft-intune.md)