---
title: Data som JAMF Pro skickar till Intune | Microsoft Intune
description: Lista över data som Jamf Pro skickar till Microsoft Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 22d81c768fb7f80498da483421f8b358d59ab8c2
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57233261"
---
# <a name="data-jamf-pro-sends-to-intune"></a>Data Jamf Pro skickar till Intune

När du använder [Jamf Pro](https://www.jamf.com) för att hantera dina slutanvändares Mac-datorer med Intune, samlar Jamf Pro in inventeringsuppgifter om hanterade macOS-enheter. Jamf Pro rapporterar följande information till Intune:

* Enhetens Azure AD-ID
* JAMF-inventeringstillstånd (inventeringstillstånd på en dator som checkats in med Jamf Pro under de senaste 24 timmarna)
* OS-version
* Användarens Azure AD-ID
* Krypterade (FileVault 2)
* Gatekeeper-status
* Lösenord: lägst antal teckenuppsättningar
* Lösenordets giltighetstid (i dagar)
* Lösenordstyp – enkel, alfanumerisk eller okänd
* Förhindra automatisk inloggning
* Nödvändig längd på lösenord
* Lösenord: antalet tidigare lösenord för att förhindra återanvändning
* Systemintegritetsskydd
* Senaste incheckningstid
* Arkitekturtyp
* Tillgängliga RAM-minnesplatser
* Batterikapacitet
* Start-ROM
* Busshastighet
* Cachestorlek
* Enhetsnamn
* Domänanslutning
* Jamf-ID
* MAC-adress
* Tillverkning
* Modell
* Modellidentifierare
* NIC-hastighet
* Antal kärnor
* Antal processorer
* Operativsystem
* Plattform
* Processorhastighet
* Processortyp
* Sekundär MAC-adress
* Serienummer
* SMC-version
* RAM-minne totalt
* UDID
* Användarens e-post


Du kan ta bort en Jamf-hanterad enhet från Intune-konsolen genom att välja **Ta bort** i vyn **Alla enheter**. Du kan aktivera massborttagning av enheter genom att välja flera enheter och klicka på **Ta bort**.

Få information om hur du [tar bort en Jamf-hanterad enhet i Jamf Pro-dokumenten](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). Du kan även skicka in ett supportärende med [Jamf-support](https://www.jamf.com/support/) för ytterligare hjälp. 
