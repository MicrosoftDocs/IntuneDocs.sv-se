---
title: "Så återställer du lösenordet från företagsportalens webbplats | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
searchScope:
- User help
ROBOTS: 
ms.reviewer: mamoriss
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: f293901d3865f0b10ed876e83b151cf59a046cba
ms.openlocfilehash: 68725bb63ae2750e89a03c16027f8b4fd9111255
ms.lasthandoff: 02/24/2017


---

# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>Så återställer du enhetens lösenord från företagsportalens webbplats

Om du har tappat bort PIN-koden eller lösenordet för en enhet som du har registrerat i Intune kan du återställa det på [företagsportalens webbplats](http://portal.manage.microsoft.com). Du kan använda webbplatsen för företagsportalen för att hantera datorer och enheter som du har registrerat i Intune och för att utföra de flesta av de uppgifter som du kan utföra när du använder företagsportalappen.

> [!NOTE]
> Det kan hända att du inte kan se knappen **Återställ lösenord** på företagsportalens webbplats. Om du inte gör det måste du kontakta din IT-administratör för att få support via företagsportalens webbplats.

Så här återställer du lösenordet:

1.    På [webbplatsen för företagsportalen](http://portal.manage.microsoft.com) trycker du på __menyknappen__ ![En liten bild på menyknappen (tre vågräta streck)](/Intune/whats-new/media/CP_hamburger_menu.png) och väljer __Mina enheter__.

2. På sidan __Mina enheter__ väljer du namnet på den enhet som du vill återställa lösenordet för.

  ![En skärmbild på sidan Min enhet med ett par oidentifierade enheter ovanför popup-meddelandet om att registrera enheter som inte finns i listan eller identifiera oidentifierade enheter.](./media/macOS_enroll_002_tap_here_banner.png)

3.    Enheten öppnas i ett popup-fönster. Välj knappen **Återställ lösenord**.

    ![Alla alternativ för den valda enheten på webbplatsen för företagsportalen, inklusive Byt namn, Ta bort, Återställ enhet, Återställ lösenord och Fjärrlås. ](./media/iwp-screen-with-all-options.png)

4.  Ett popup-meddelande visas som ber dig bekräfta att du vill återställa lösenordet och att enheten loggar ut dig när detta är gjort. Sedan måste du vänta i fem minuter innan du kan logga in igen.

  ![Meddelande om att återställa lösenordet med en varning om att lösenordet för enheten återställs och information om hur användaren loggas ut. Knapparna för indata från användaren är Logga ut och Avbryt.](./media/iwp-reset-passcode-popup.png)

4.  Välj **Logga ut** så får du ett meddelande om att lösenordet tas bort från enheten. Ta inte bort lösenordet om du inte har enheten med dig. Om någon annan har fysisk åtkomst till enheten har den personen åtkomst till nästan all information på enheten, både privat information och företagsinformation.

  ![Det andra meddelandet om återställning av lösenord med en varning om att lösenordet återställs för enheten och information om hur lösenordet tas bort från enheten. Meddelandet innehåller också information om hur du anger ett nytt lösenord via enhetsinställningarna.](./media/iwp-reset-passcode-2nd-popup.png)


Eftersom olika enheter har olika typer av lösenord kan du se i tabellen nedan hur en återställning av lösenordet kan påverka din specifika enhet. 

    |Enhetstyp|Vad händer när du återställer|
    |------------|-----------|
    |Android|Tar bort det befintliga lösenordet och skapar ett tillfälligt lösenord som innehåller både bokstäver och siffror|
    |iOS|Tar bort det befintliga lösenordet men skapar inte ett tillfälligt lösenord. Om du använder Touch-IDs fingeravtryckskanner för att öppna din enhet eller för att utföra inköp måste du konfigurera det igen.|
    |Windows 10 Mobil|Tar bort det befintliga lösenordet och skapar ett tillfälligt lösenord som innehåller både bokstäver och siffror. Om du använder Windows Hello-ansiktsigenkänning för att logga in stöds det fortfarande.|
    |Windows Phone 8.1|Tar bort det befintliga lösenordet och skapar ett tillfälligt lösenord som endast innehåller siffror.|

    5.  Lås upp enheten och ange ett nytt lösenord eller ändra det tillfälliga lösenordet genom att gå till enhetens **Inställningar**.

    Om du vill visa ett meddelande som bekräftar att lösenordet har återställts klickar du på meddelandeflaggan längst upp till höger på företagsportalens webbplats.

Behöver du fortfarande hjälp? Kontakta IT-administratören. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](http://portal.manage.microsoft.com).
