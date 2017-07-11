---
title: Distribuera appar till Android for Work-enheter
description: "Använd det här avsnittet för att synkronisera och sedan distribuera appar till Android for Work-enheter från Google Play for Work Store."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd0bbd90-d3fe-4efc-83fd-d1f3f86800d4
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: adc4a343e610a1a75f8a5bc51a1894f6fcf998bb
ms.sourcegitcommit: c9b3a95bf529b6cb2a2bdacbc49127dfa0c233e5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/05/2017
---
# <a name="how-to-deploy-apps-to-android-for-work-devices-with-intune"></a>Så distribuerar du appar till Android for Work-enheter med Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Du distribuerar appar till Android for Work-enheter på ett annat sätt än du distribuerar dem till vanliga Android-enheter. Alla appar som du installerar för Android for Work kommer från Google Play for Work-butiken. Du kan logga in i butiken, bläddra efter de appar som du vill ha och godkänna dem.
Appen visas sedan i noden **Volyminköpsappar** i Intune-konsolen. Härifrån kan du hantera distributionen av apparna på samma sätt som du distribuerar andra appar.

Dessutom kan du distribuera dina egna verksamhetsspecifika (LOB)-appar som du har skapat enligt följande:
- Du måste registrera dig för ett Google-utvecklarkonto som låter dig att publicera appar på en privat plats i Google Play-butiken.
- Synkronisera apparna med Intune.

## <a name="before-you-start"></a>Innan du börjar

Kontrollera att du har konfigurerat Intune och Android for Work tillsammans i fliken **Admin** i Intune-konsolen.

## <a name="synchronize-an-app-from-the-google-play-for-work-store"></a>Synkronisera en app från Google Play for Work-butiken


1. Gå till [Google Play for Work store](https://play.google.com/work) (Google Play for Work-butiken). Logga in med samma konto som du använde för att konfigurera anslutningen mellan Intune och Android for Work.
2. Sök i butiken efter den app som du vill distribuera med hjälp av Intune.
3. På sidan för den app som du har valt trycker du på **Godkänn**. I det här exemplet har du valt appen Microsoft Excel.<br>
  ![Exempel på hur du godkänner en app](media/approve.png)
4. Ett fönster för appen öppnas där du uppmanas att tilldela behörigheter till appen för att utföra olika åtgärder. Välj **Godkänn** för att fortsätta.<br>
  ![Exempel på hur du godkänner appbehörigheter](media/approve-app-permissions.png)
5. Appen godkänns och visas i IT-administrationskonsolen.

## <a name="publish-then-synchronize-a-line-of-business-app-from-the-google-play-for-work-store"></a>Publicera och synkronisera en verksamhetsspecifik app från Google Play for Work-butiken

1. Gå till Google Play-utvecklarkonsolen [play.google.com/apps/publish](https://play.google.com/apps/publish).
2. Logga in med samma konto som du använde för att konfigurera anslutningen mellan Intune och Android for Work. Om du loggar in för första gången måste du registrera dig och betala en avgift för att bli medlem i Google-utvecklarprogrammet.
3. I konsolen väljer du **Lägg till nytt program**.
4. Du kan överföra och tillhandahålla information om din app på samma sätt som du publicerar en app i Google Play-butiken. Du måste dock välja inställningen **Only make this application available to my organization (Gör det här programmet tillgängligt endast för min organisation) (<*organisationsnamn*>)**:<br>
  ![Alternativ för att endast göra appen tillgänglig för din organisation](media/restrict.png)<br>
Detta säkerställer att appen endast är tillgänglig för din organisation och inte är tillgänglig i den offentliga Google Play-butiken.
Mer information om hur du överför och publicerar Android-appar finns i [Google Developer Console Help](https://support.google.com/googleplay/android-developer/answer/113469) (Hjälp med Google-utvecklarkonsolen).
5. När du har publicerat din app går du till [Google Play for Work store](https://play.google.com/work) (Google Play for Work-butiken). Logga in med samma konto som du använde för att konfigurera anslutningen mellan Intune och Android for Work.
6. Kontrollera att du kan se appen som du har publicerat i noden **appar** i butiken. Den godkänns automatiskt för synkronisering med Intune.

## <a name="deploy-an-android-for-work-app"></a>Distribuera en Android for Work-app

Om du har godkänt en app från butiken men den ännu inte visas i noden **Volyminköpta appar** i arbetsytan **Appar** kan du framtvinga en omedelbar synkronisering genom att göra följande:

1. I [Intune-administrationskonsolen](https://manage.microsoft.com) väljer du **Admin** > **Hantering av mobila enheter** > **Android for Work**.
2. På sidan **Android for Work Mobile Device Management Setup** (Konfiguration av hantering av mobila enheter med Android for Work) väljer **Synkronisera nu**.
3. Sidan visar även tid och status för den senaste synkroniseringen.

När appen visas i noden **Volyminköpta appar** i arbetsytan **Appar** kan du välja [Deploy it just like you would so with any other app](deploy-apps-in-microsoft-intune.md) (Distribuera den på samma sätt som andra appar). Du kan endast distribuera appen till grupper av användare. För närvarande kan du bara välja åtgärderna **Nödvändig** och **Avinstallera**.

Möjligheten att distribuera en app som **Tillgänglig** utnyttjar den nya grupperings- och målmiljön. Nyligen etablerade Intune Service-konton kan använda den här funktionen när den lanseras. Befintliga Intune-kunder kan använda den här funktionen när deras klientorganisationer har migrerats till Intune Azure-portalen. Befintliga kunder är välkomna att skapa ett Intune-utvärderingskonto för att planera för och testa den här funktionen tills deras klientorganisationer har migrerats.

När du har distribuerat appen kommer den att installeras på de enheter du angett. Användaren av enheten kommer inte att bli ombedd att godkänna installationen.

## <a name="manage-app-permissions"></a>Hantera programbehörigheter
Android for Work kräver att du godkänner appar i Googles Play-webbskonsol innan de synkroniseras i Intune and distribueras till användarna.  Eftersom Android for Work låter dig distribuera dessa appar till användarnas enheter tyst och automatiskt måste du acceptera appens behörigheter för alla användare.  Slutanvändare ser inga programbehörigheter när de installerar, så det är viktigt att du har läst och förstått dessa behörigheter.

När apputvecklare publicerar en ny version av appen med uppdaterade behörigheter tillåts de inte automatiskt, även om du har godkänt tidigare behörigheter. Enheter som kör den gamla versionen av programmet kan fortfarande använda det, men appen uppgraderas inte förrän de nya behörigheterna har godkänts. Enheter utan appen kan inte installera den förrän du har godkänt dess nya behörigheter.

### <a name="how-to-update-app-permissions"></a>Så här uppdaterar du programbehörigheter

Du bör regelbundet besöka den hanterade Google Play-konsolen för att söka efter nya behörigheter. Du kan konfigurera Google Play att skicka dig eller andra ett e-postmeddelande när nya behörigheter krävs för en godkänd app. Om du tilldelar en app och noterar att den inte installeras på enheterna, söker du efter nya behörigheter med följande steg:

1. Besök http://play.google.com/work
2. Logga in med det Google-konto som du använde för att publicera och godkänna apparna.
3. Besök fliken **uppdateringar** för att se om några appar kräver en uppdatering.  Alla appar i listan kräver nya behörigheter och kan inte tilldelas utan dessa.  

Du kan också konfigurera Google Play att automatiskt godkänna appbehörigheter på nytt skilt för varje app. 