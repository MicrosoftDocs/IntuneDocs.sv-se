---
title: Ta bort en macOS-enhet
titleSuffix: Microsoft Intune
description: Läs hur du raderar alla data, inklusive operativsystemet, från en macOS-enhet.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/31/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ab396092-907a-44b7-a157-aabee62176a9
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e2f4ce1295d4a3f2250988d25246c532ff2cdd73
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728240"
---
# <a name="erase-all-data-from-a-macos-device"></a>Radera alla data från en macOS-enhet

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Du kan ta bort alla data från en macOS-enhet, inklusive operativsystemet. Enheten tas även bort från Intune-hantering. Ingen varning ges till slutanvändaren.

1. I [Intune i Azure Portal](https://aka.ms/intuneportal) väljer du till **Enheter** > **Alla enheter** > och väljer enheten som du vill ta bort.
![Skärmbild](./media/device-erase/choosedevice.png)
2. Klicka på **Mer** > **Radera** > och ange 6 siffror för **PIN-kod för återställning**. Det här är PIN-koden som du måste ge användarna så att de kan installera om operativsystemet på enheten. Se till att anteckna den här PIN-koden eftersom den inte är synlig igen när raderingsåtgärden har slutförts.
![Skärmbild](./media/device-erase/providepin.png)
3. Klicka på **OK** för att radera enheten.