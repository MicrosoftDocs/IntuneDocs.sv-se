---
title: "Hur du lägger till Windows Phone 8.1 Store-appar i Intune | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Lär dig mer om hur man lägger till Windows Phone 8.1 Store-appar i Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/11/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a95e575-2c63-4bfc-b9c4-f0a132eef618
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 01e5bfeb98aee9314fa04679cc27c8aba0e18fb0
ms.openlocfilehash: 307819e2416ebefa091166af338e6b1a0a8a6cc7

---

# <a name="how-to-add-windows-phone-81-store-apps-to-intune"></a>Lägga till Windows Phone 8.1 Store-appar i Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Hantera appar** på **Intune**-bladet.
4. Välj **Hantera** > **appar** i arbetsbelastningen **Mobilappar**.
5. Välj **Lägg till** ovanför applistan.
6. Välj **Appinformation** på bladet **Lägg till app**.
7. Konfigurera följande information på bladet **Redigera app**. När du är klar klickar du på **Lägg till**. Beroende på vilken app du har valt kan det hända att några av värdena i det här bladet har fyllts i automatiskt:
    - **Appnamn** – Ange namnet på appen så som det ska visas i företagsportalen. Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna för användare i företagsportalen.
    - **Appbeskrivning** – Ange en beskrivning för appen. Detta visas för användare i företagsportalen.
    - **Utgivare** – Ange namnet på appens utgivare.
    - **App Store-URL** – Ange App Store-URL:en för den app som du vill skapa.
    - **Minsta operativsystem** – Välj den minsta operativsystemversion som appen kan installeras på. Om appen tilldelas till en enhet med ett äldre operativsystem installeras den inte.
    - **Kategori (valfritt)** – Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Det gör det enklare för användarna att hitta appen när de söker i företagsportalen.
    - **Visa den här som aktuell app på företagsportalen** – Visa appen på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    - **Informations-URL** – Du kan välja att ange webbadressen till en webbplats som innehåller information om den här appen. Webbadressen visas för användare i företagsportalen.
    - **Sekretess-URL (valfritt)** – Ange webbadressen till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användare i företagsportalen.
    - **Utvecklare (valfritt)** – Ange apputvecklarens namn.
    - **Ägare (valfritt)** – Ange ett namn på appägaren, t.ex. **Personalavdelningen**.
    - **Anteckningar** – Ge eventuella kommentarer som du vill koppla till den här appen.
    - **Ladda upp ikon** – Överför en ikon som ska kopplas till appen. Den här ikonen visas med appen när användare söker i företagsportalen.
8. När du är klar väljer du **Spara** på bladet **Lägg till App**.

Den app som du har skapat visas i listan över appar där du kan välja att tilldela den till olika grupper. Mer information finns i [Tilldela appar till grupper](/intune-azure/manage-apps/deploy-apps).


<!--HONumber=Feb17_HO1-->

