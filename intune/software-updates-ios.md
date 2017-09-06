---
title: Konfigurera iOS-uppdateringsprinciper
titleSuffix: Intune on Azure
description: "Konfigurera uppdateringsprinciper för iOS för att tvinga övervakade iOS-enheter att automatiskt installera den senaste tillgängliga uppdateringen."
keywords: 
author: dougeby
manager: dougeby
ms.date: 08/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6334421-85e1-4457-9c44-e5db8d4ee00e
ms.openlocfilehash: d4af2d58ec21c54362cf451eac1a33b2088885d5
ms.sourcegitcommit: 7674efb7de5ad54390801165364f5d9c58ccaf84
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2017
---
# <a name="configure-ios-update-policies"></a>Konfigurera iOS-uppdateringsprinciper
Uppdateringsprinciper för iOS gör det möjligt att tvinga övervakade iOS-enheter att automatiskt installera den senaste tillgängliga uppdateringen. Du kan konfigurera de dagar och tider då du inte vill att enheter ska installera uppdateringen.

## <a name="configure-the-ios-update-policy"></a>Konfigurera iOS-uppdateringsprincipen
1. Gå till Intune-bladet i Azure-portalen.
2. Välj **Programuppdateringar** > **iOS-uppdateringsprinciper** på **Intune**-bladet.
4. På principbladet väljer du **Skapa** och anger sedan namn och beskrivning för principen.
5. Välj **Inställningar** > **Konfigurera** och ange information om när iOS-enheter inte ska tvingas att installera den senaste uppdateringen.
6. Spara konfigurationen genom att välja **OK**. Nu är du tillbaka på bladet **Skapa uppdateringsprincip**. Skapa principen och spara inställningarna genom att välja **Skapa**.

Profilen skapas och visas på bladet med listan över iOS-uppdateringsprinciper.

## <a name="assign-an-ios-update-policy-to-users"></a>Tilldela en iOS-uppdateringsprincip till användare
Om du vill tilldela en iOS-uppdateringsprincip till användare väljer du en princip som du har konfigurerat. Befintliga principer finns på bladet **Programuppdateringar** > **iOS-uppdateringsprinciper**.
1. Välj den princip som du vill tilldela till användarna och välj **Tilldelningar**. Då öppnas det blad där du kan välja Azure Active Directory-säkerhetsgrupper och tilldela dem till principen.
2. Öppna bladet som visar säkerhetsgrupper för Azure AD genom att välja **Välj grupper**. Välj **Välj** om du vill distribuera principen till användarna.

Du har tillämpat principen på användarna. Uppdateringsefterlevnaden hos de enheter som används av de användare som principen är inriktad på kommer att utvärderas.

## <a name="change-the-restricted-days-for-the-policy"></a>Ändra begränsade dagar för principen
1. På bladet **Programuppdateringar** väljer du **iOS-uppdateringsprinciper**.
2. Välj den iOS-uppdateringsprincip som du vill uppdatera.
3. Välj **Egenskaper** och uppdatera informationen om begränsade dagar.