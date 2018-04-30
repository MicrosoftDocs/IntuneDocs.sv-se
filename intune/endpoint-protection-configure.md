---
title: Konfigurera inställningar för slutpunktsskydd i Microsoft Intune – Azure | Microsoft Docs
description: Skapa inställningar för slutpunktsskydd när du skapar en profil för macOS- eller Windows 10-enheter i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b960b837cef5941fac829eeb878eb520b0274fba
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Lägga till inställningar för slutpunktsskydd i Intune

Med slutpunktsskydd kan du styra olika säkerhetsfunktioner på dina enheter, inklusive brandvägg, BitLocker, tillåta och blockera appar, Windows Defender, kryptering och mycket mer. Du kan konfigurera inställningarna i Microsoft Intune med hjälp av enhetsprofiler.

Du kan till exempel skapa en profil för slutpunktsskydd som endast tillåter att macOS-användare installerar appar från Mac App Store. Du kan också aktivera Windows SmartScreen när appar körs på Windows 10-enheter.

Den här artikeln visar hur du skapar en profil. Välj din enhetsplattform för att få mer information om de tillgängliga inställningarna.

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>Skapa en enhetsprofil med inställningar för slutpunktsskydd

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
4. Ange **Namn** och **Beskrivning** för slutpunktsskyddsprofilen.
5. Välj den enhetsplattform på vilken du vill tillämpa anpassade inställningar från listrutan **Plattform**. För närvarande kan du välja någon av följande plattformar för inställning av enhetsbegränsningar:
   - **macOS**
   - **Windows 10 och senare**
6. Välj **Endpoint Protection** i listrutan **Profiltyp**. 
7. Vilka inställningar du kan konfigurera varierar beroende på vilken plattform du väljer. Gå till något av följande avsnitt om du vill ha detaljerad information om respektive plattform:
   - [Inställningar för macOS](endpoint-protection-macos.md)
   - [Inställningar för Windows 10](endpoint-protection-windows-10.md)
8. När du är klar går du tillbaka till sidan **Skapa profil** och klickar på **Skapa**.

Profilen skapas och visas på sidan med profillistan. Om du vill tilldela profilen till grupper kan du läsa [Tilldela enhetsprofiler](device-profile-assign.md).

## <a name="next-steps"></a>Nästa steg
Om du vill tilldela profilen till grupper kan du läsa mer i [Tilldela enhetsprofiler](device-profile-assign.md).