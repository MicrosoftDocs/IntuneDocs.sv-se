---
title: Inkludera och exkludera apptilldelningar i Microsoft Intune
titleSuffix: ''
description: Läs om hur du kan använda Microsoft Intune till att inkludera och exkludera apptilldelningar.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59f6df5-3317-4dff-8f19-fdeec33faedf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c743b25ce2823c952b1e4b8ab764a48488c0ca5d
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725107"
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>Inkludera och exkludera apptilldelningar i Microsoft Intune

I Intune kan du se vem som har åtkomst till en app genom att tilldela grupper av användare som ska inkluderas och exkluderas. Innan du tilldelar grupper till appen måste du ange tilldelningstyp för den. Tilldelningstypen gör appen tillgänglig, obligatorisk eller avinstallerar appen. 

För att ställa in tillgängligheten för en app inkluderar och exkluderar du apptilldelningar till en grupp med användare eller enheter genom att använda en kombination av grupptilldelningar som inkluderar och exkluderar. Den här funktionen kan vara användbar när du gör appen tillgänglig genom att inkludera en stor grupp och sedan begränsar valda användare genom att även exkludera en mindre grupp. Den mindre gruppen kan vara en testgrupp eller en exekutiv grupp. 

När du exkluderar grupper från en apptilldelning kan du endast exkludera användargrupper eller enhetsgrupper. Du kan inte utelämna en blandning av användargrupper och enhetsgrupper. 

Intune tar inte hänsyn till några kopplingar mellan användare och specifika enheter vid exkludering av grupper. Om du väljer att inkludera användargrupper och samtidigt exkludera enhetsgrupper kommer du aldrig att få önskat resultat. Inkludering har företräde framför exkludering. Om du till exempel riktar en iOS-app till **Alla användare** och exkluderar **Alla iPad-enheter** blir resultatet att alla användare som använder en iPad fortfarande får appen. Om du däremot riktar iOS-appen till **Alla enheter** och exkluderar **Alla iPad-enheter** så lyckas distributionen.  

> [!NOTE]
> När du ställer in en grupptilldelning för en app blir typen **Ej tillämplig** inaktuell och ersätts med gruppfunktioner för att exkludera. 
>
> Intune tillhandahåller de i förväg skapade grupperna **Alla användare** och **Alla enheter** i konsolen. Grupperna har inbyggda optimeringar för din bekvämlighet. Vi rekommenderar starkt att du använder de här grupperna för att ange alla användare och alla enheter som mål i stället för grupperna för ”Alla användare” eller ”Alla enheter” som du kanske själv har skapat.  
>
> Android enterprise stöder att inkludera och exkludera grupper. Du kan använda de inbyggda grupperna **Alla användare** och **Alla enheter** vid Android enterprise-apptilldelning. 


## <a name="include-and-exclude-groups-when-assigning-apps"></a>Inkludera och exkludera grupper när du tilldelar appar 
Tilldela en app till grupper med hjälp av en tilldelning för att inkludera eller exkludera:
1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Välj **Klientappar** i **Intune**-fönstret.
4. I fönstret **Klientappar** väljer du **Appar**. Listan över tillagda appar visas.
5. Markera appen som du vill tilldela. En instrumentpanel visar information om appen. 
6. I avsnittet**Hantera** på menyn, väljer du **Tilldelningar**. 

    ![Inkludera apptilldelningar när du tilldelar appar](./media/apps-inc-exl-assignments/apps-inc-exl-01.png)
7. Välj **Lägg till grupp** för att lägga till grupper av användare som har tilldelats appen. 
8. I fönstret **Lägg till grupp**, väljer du en **Tilldelningstyp** från tillgängliga tilldelningstyper.
9. Välj **Tillgänglig med eller utan registrering** som tilldelningstyp.

    ![Apptilldelningar i Intune – Lägg till grupp](./media/apps-inc-exl-assignments/apps-inc-exl-02.png)
10. Välj **Inkluderade grupper** för att välja grupper av användare som du vill göra appen tillgänglig för.

    > [!NOTE]
    > Om någon annan grupp redan har inkluderats för en viss tilldelning när du lägger till en grupp så blir appen förvald och kan inte ändras för andra tilldelningstyper för inkludering. Gruppen som har använts kan inte användas som en inkluderad grupp.

11. Välj **Ja** för att göra appen tillgänglig för alla användare.

    ![Apptilldelningar i Intune – Inkludera grupper](./media/apps-inc-exl-assignments/apps-inc-exl-03.png)
12. Välj **OK** för att ställa in så att gruppen inkluderar.
13. Välj **Exkluderade grupper** för att välja grupper av användare som du vill göra appen otillgänglig för. 
14. Välj grupperna som ska exkluderas. Detta gör att den här appen inte är tillgänglig i dessa grupper.

    ![Apptilldelningar i Intune – Exkludera grupper](./media/apps-inc-exl-assignments/apps-inc-exl-04.png)
15. Klicka på **Välj** för att slutföra valet av grupper.
16. I fönstret **Lägg till grupp** väljer du **OK**. Listan över **Apptilldelningar** visas.
17. Klicka på **Spara** för att aktivera grupptilldelningar för appen.

När du gör grupptilldelningar är grupper som redan har tilldelats inte tillgängliga för ändring. Om du vill välja en grupp som för närvarande inte är tillgänglig kan du först ta bort appen från appens tilldelade lista. 

För att redigera tilldelningar i app-listan **Tilldelningar** väljer du den rad som innehåller gruppen som du vill ändra. Du kan också ta bort en tilldelning genom att välja ellipsen ( **...** ) i slutet av en rad och sedan välja **Ta bort**. För att ändra vyn för listan **Tilldelningar** grupperar du efter **Tilldelningstyp** eller **Inkluderade/Exkluderade**.

![Apptilldelningar i Intune – Slutförda](./media/apps-inc-exl-assignments/apps-inc-exl-05.png)

## <a name="next-steps"></a>Nästa steg

- Mer information om att inkludera och exkludera grupptilldelningar för appar finns på [Microsoft Intune-bloggen](https://aka.ms/new_app_assignment_process).
- Lär dig att [övervaka appinformation och tilldelningar](apps-monitor.md).