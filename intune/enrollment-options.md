---
title: "Registreringsalternativ för Intune"
description: 
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cf4ad6d4-423f-4826-ab8d-6eb7a7cfb559
ms.openlocfilehash: dcc97e5bcffb35752b65e8ce275d38b9578da6fa
ms.sourcegitcommit: bee30f4c9e04129d70305fcafc4152c6e062a8b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/11/2017
---
# <a name="enrollment-options-for-intune"></a>Registreringsalternativ för Intune

Som Intune-administratör kan du konfigurera enhetsregistreringen för att hjälpa användarna och aktivera Intune-funktioner.  Intune innehåller följande registreringsalternativ:

## <a name="terms-and-conditions"></a>Villkor

Du kan kräva att användarna måste godkänna företagets allmänna villkor innan de kan använda företagsportalen för att registrera sina enheter och få åtkomst till företagsresurser som appar och e-post. Konfigurationen av de allmänna villkoren är valfri. Läs mer om [villkor](terms-and-conditions-create.md).

## <a name="enrollment-restrictions"></a>Registreringsbegränsningar

Du kan välja att begränsa enhetsregistreringen efter:
- Enhetsplattform
- Antalet enheter per användare
- Blockera personliga enheter

Läs mer om [registreringsbegränsningar](enrollment-restrictions-set.md).

## <a name="enable-apple-device-enrollment"></a>Aktivera Apple-enhetsregistrering

Det krävs ett MDM-pushcertifikat för registrering av iOS- och Mac OS enheter. Läs mer om [MDM-pushcertifikat](apple-mdm-push-certificate-get.md).

## <a name="corporate-identifiers"></a>Företagsidentifierare

Du kan visa en lista över IMEI-nummer (International Mobile Equipment Identifier) och serienummer för att identifiera företagsägda enheter. Läs mer om [företagsidentifierare](corporate-identifiers-add.md).

## <a name="device-enrollment-manager"></a>Hanterare av enhetsregistrering
Du kan utse användare till enhetsregistreringshanterare (DEM).  Enhetsregistreringshanterare kan registrera många mobila enheter med ett enda användarkonto. Kontot för en enhetsregistreringshanterare kan registrera upp till 1 000 enheter. Läs mer om [enhetsregistreringshanterare](device-enrollment-manager-enroll.md).

## <a name="device-categories"></a>Enhetskategorier

Du kan använda enhetskategorier för att automatiskt lägga till enheter i grupper baserat på kategorier som du definierar. Det blir enklare att hantera enheterna om du lägger till dem i grupper. Läs mer om [enhetskategorier](device-group-mapping.md).