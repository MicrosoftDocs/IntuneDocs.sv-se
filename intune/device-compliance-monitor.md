---
title: "Hur du övervakar enhetsefterlevnad"
titleSuffix: Intune on Azure
description: "Läs hur du övervakar enhetsefterlevnad.”"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0790934b-48b9-435b-a8aa-e83ed5b73191
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f18bfa7fb045dbad4ab785c2c8e1bc13fc439db
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-monitor-device-compliance-in-intune"></a>Så här övervakar du enhetsefterlevnad i Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Du kan visa en sammanfattning av statusen för dina **efterlevnadsprofiler** på bladet **Översikt**.
Du kan klicka dig igenom diagrammen interaktivt eller gå ner på detaljnivå. Om du har flera konfigurerade efterlevnadsprofiler kan du även visa statusen för varje enskild princip genom att gå till principbladet och välja **Rapporter** i avsnittet **Hantera**.  Information från rapporterna som finns tillgängliga listas nedan.

##  <a name="device-compliance"></a>Efterlevnad för enhet

Enhetsefterlevnadsrapportens sammanfattningsvy börjar med att visa dig samlad information om antalet enheter som rapporterar på något av följande sätt:

- **Kompatibel**: Enheten har nyligen utvärderats för efterlevnad och har fastställts uppfylla de efterlevnadsprofilsinställningar som du har angett.
- **Icke-kompatibel**: Enheten har utvärderats och fastställts vara icke-kompatibel.  Om det har angetts en respitperiod i profilen, så har den upphört att gälla och gett enheten en icke-kompatibel status.
- **Respitperiod**: Enheten har utvärderats och fastställts vara icke-kompatibel. Respittiden gäller dock fortfarande tills enheten faktiskt har markerats som inkompatibel.

Du kan öka detaljnivån i varje avsnitt om du vill ha mer information om enskilda enheter och användare.

## <a name="setting-compliance"></a>Ställa in efterlevnad

Inställningskompatibilitetsrapporten ger detaljerad information om de enskilda efterlevnadsinställningarna, t.ex.:

- Antalet enheter som inte är kompatibla med inställningen.
- Den plattform som inställningen gäller.

Du kan öka detaljnivån för varje inställning om du vill se mer information om de profiler som inställningarna har aktiverats för, samt inställningens värde.