---
title: "Så här fungerar en normal migreringscykel i Intune | Microsoft Docs"
description: "Syftet med den här artikeln är att förklara hur en migreringscykel i Intune fungerar och ge exempel på hur kunden kan hantera migreringscykeln."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3688b724-9521-4210-bf4d-bcf47d8d4ca0
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab5aa4e12d951d818c5afb4e1ac5e866b05733fb
ms.openlocfilehash: aa8fb215772b6e8d3a913d929c030d68e363970b
ms.lasthandoff: 03/27/2017


---

# <a name="phase-2-typical-migration-cycle"></a>Fas 2: Normal migreringscykel

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Det är vanligt att organisationer startar sin Intune-migrering med ett litet pilotprojekt genom att rikta in sig på en del av sina användare på IT-avdelningen. I syfte att fastställa ett tidsschema för migreringen kan din organisation dessutom behöva diskutera sådana faktorer som gruppens beredvillighet för förändring, antal användare, komplexitet, krav, plats och affärsrisk.

Här följer ett exempel på hur dina målgrupper kan schemaläggas:

  | **Målgrupper för migrering** | **Tidsperiod 1** | **Tidsperiod 2** | **Tidsperiod 3** | **Tidsperiod 4** | **...**
|:---:|:---:|:---:|:---:|:---:|:---:|
| Begränsat pilotprojekt – IT-avdelningen (50 användare) | Presentera planen | Ge anvisningar om registrering | Ge en deadline | Framtvinga villkorlig åtkomst |  |                                                        
| Utvidgat pilotprojekt – IT-avdelningen (200 användare) |  | Presentera planen | Ge anvisningar om registrering | Ge en deadline | Framtvinga villkorlig åtkomst | 
| Migreringsfas 1: Tekniksmarta användare (2000) |  |  | Presentera planen | Ge anvisningar om registrering | Ge en deadline | 
| Migreringsfas 2: Östra USA |  |  |  | Presentera planen | Ge anvisningar om registrering | 
| Alla regioner |  |  |  |  | Presentera planen | 

## <a name="customer-migration-case-study"></a>Fallstudie av kundmigrering

### <a name="adatum-corporation"></a>Adatum Corporation

- Se [hur Adatum Corporation genomförde migreringsprocessen från en MDM-tredjepartsprovider till Intune](https://gallery.technet.microsoft.com/Intune-migration-guide-893a95e3?redir=0).

## <a name="monitoring-migration"></a>Övervaka migrering

Microsoft Intune erbjuder flera olika sätt på vilka du kan övervaka migreringen:

1.  Intune-användargruppsvyer

2.  En uppsättning inbyggda rapporter och

3.  konsolaviseringar.

Du bör kontrollera hur många användare som har registrerat enheter efter respektive, så att du sedan kan:

-   Utvärdera hue effektiv din kommunikationsplan var.

-   Beräkna effekten av att tillämpa villkorlig åtkomst.

Lär dig [hur man övervakar en Intune-migrering](https://docs.microsoft.com/intune/deploy-use/understand-microsoft-intune-operations-by-using-reports).

## <a name="post-migration"></a>Efter migreringen

Du måste inaktivera den tidigare MDM-providern och/eller avsluta prenumerationen på tjänsten när du har migrerat till Intune. Dessutom måste du ta bort eventuella onödiga infrastrukturkrav genom att följa MDM-providerns anvisningar.
