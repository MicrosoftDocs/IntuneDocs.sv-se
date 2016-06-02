---
# required metadata

title: Lägg till appar för mobila enheter | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f5b1f1ae-f177-450a-9af9-936a02d052e3

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Lägg till appar för mobila enheter i Microsoft Intune

Använd informationen i det här avsnittet för att lära dig hur du lägger till appar i Intune innan du distribuerar dem.


> [!IMPORTANT]
> Informationen i det här avsnittet hjälper dig att lägga till appar som du vill distribuera till registrerade enheter och registrerade Windows-datorer. Om du vill lägga till appar för Windows-datorer som du hanterar med Intune-klientprogrammet läser du [Lägg till appar för Windows-datorer i Microsoft Intune](add-apps-for-windows-pcs-in-microsoft-intune.md).

## Lägg till appen
Du använder Intune-programvaruutgivaren för att konfigurera egenskaper för appen och, om tillämpligt, överföra den till molnlagringsutrymmet med följande metod:

1.  Använd [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com) och klicka på **Appar** &gt; **Lägg till appar** för att starta Intune-programvaruutgivaren.

    > [!TIP]
    > Du kan behöva ange ditt användarnamn och lösenord för Intune innan utgivaren startas.

2.  På sidan **Programvaruinstallation** för programvaruutgivaren väljer du något av följande alternativ för **Hur ska enheterna få tillgång till den här programvaran**:
    - **Installationsprogram för programvara**, för appar med filnamnstillägget **.msi** eller **.exe** anger du:
        - **Välj typ av programinstallationsfil** – Detta anger vilken typ av programvara som du vill distribuera. Om du till exempel vill installera en iOS-app väljer du **Appaket för iOS (&#42;.ipa-fil)**.
        - **Ange platsen för programvarans installationsfiler** – Ange platsen för installationsfilerna eller klicka på **Bläddra** för att välja platsen i en lista.
        - **Inkludera ytterligare filer och undermappar från samma mapp** – Endast för filtypen **Windows Installer**.<br>Vissa program som använder Windows Installer kräver stödfiler som vanligtvis finns i samma mapp som installationsfilerna. Välj det här alternativet om du även vill distribuera dessa filer.<br>Den här installationstypen använder en del av ditt molnlagringsutrymme.

  -   **Extern länk**, för appar som du vill skapa genom att ange en länk till en appbutik anger du:

        - **Ange webbadress (URL)** – Ange webbadressen för något av följande:
            - Webbadressen till App Store för den app som du vill distribuera. Om du till exempel vill distribuera appen Microsoft Remote Desktop för Android anger du **https://play.google.com/store/apps/details?id=com.microsoft.rdc.android**. Du hittar webbadressen till appen genom att använda en sökmotor för att hitta Store-sidan som innehåller appen. Om du till exempel vill hitta Remote Desktop-appen kan du söka efter **Microsoft Remote Desktop Android**.
            - En webbplats. Intune distribuerar en genvägsikon till platsen till enheten (kallas även för web clip).
            - En app på webben. Intune distribuerar en genvägsikon till appen på enheten.
        - **Kräv en hanterad webbläsare för att öppna den här länken (endast Android och iOS)** – När du distribuerar en länk till en webbplats eller webbapp till användare kan de bara öppna den i Intune Managed Browser som måste vara installerad på enheten.<br>Mer information om Managed Browser finns i [Hantera Internetåtkomst med hanterade webbläsarprinciper med Microsoft Intune](manage-internet-access-using-managed-browser-policies.md).<br>Den här installationstypen använder inte något av ditt molnlagringsutrymme.

  -   **Hanterad iOS-app från App Store**, för kostnadsfria appar från iTunes-butiken som du vill hantera med MAM-principer anger du:

        - **Ange webbadress (URL)** – Ange webbadressen i App Store för den app som du vill distribuera. Om du till exempel vill distribuera appen Microsoft Work Folders för iOS anger du **https://itunes.apple.com/us/app/work-folders/id950878067?mt=8**.<br>Den här installationstypen använder inte något av ditt molnlagringsutrymme.

        Om du till exempel vill distribuera appen Microsoft Word från iTunes-butiken till enheterna skulle sidan se ut så här:
        
        ![Intune Software Publisher](./media/publisher-for-mobile.png)

3.  På sidan **Programvarubeskrivning** konfigurerar du följande:

    > [!TIP]
    > En del av dessa värden kan anges automatiskt eller visas inte, beroende på den installationstyp som används.

    - **Utgivare** – Ange namnet på appens utgivare.
    - **Namn** – Ange namnet på appen så som det ska visas i företagsportalen.<br>Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna för användare i företagsportalen.
    - **Beskrivning** – Ange en beskrivning för appen. Detta visas för användare i företagsportalen.
    - **Webbadress (URL) för programinformation** – Endast tillgängligt om du har valt **Programinstallation**. Du kan välja att ange en webbadress till en webbplats som innehåller information om den här appen. Webbadressen visas för användare i företagsportalen.
    - **Sekretess-URL** – Endast tillgängligt om du har valt **Programinstallation**. Du kan välja att ange en webbadress till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användare i företagsportalen.
    - **Kategori** – (Valfritt) Välj någon av de inbyggda appkategorierna. Det gör det enklare för användarna att hitta appen när de söker i företagsportalen.
    - **Visa den här som en aktuell app och markera den i företagsportalen:** Visa appen på en framträdande plats på huvudsidan i företagsportalen när användarna söker efter appar.
    - **Ikon** – (Valfritt) Överför en ikon som ska kopplas till appen. Den här ikonen visas med appen när användare söker i företagsportalen.

        I det här exemplet konfigureras en beskrivning för Microsoft Word-appen för iOS:

        ![Exempel på programbeskrivning](./media/ios-software-description.png)

4.  På sidan **Krav** väljer du de krav som måste uppfyllas innan appen kan börja installeras på en enhet. För ett appaket för iOS kan du till exempel välja den lägsta version av iOS som krävs och vilken typ av enhet det måste vara, t.ex. iPhone eller iPad.

    > [!TIP]
    > Sidan **Krav** visas inte för alla typer av appar.

5.  Ytterligare guidesidor visas när du väljer filtypen **Windows Installer**. Den här filtypen används när du distribuerar programvara till datorer som kör Windows 10 eller senare och som har registrerats i Intune.

6.  På sidan **Sammanfattning** läser du igenom informationen du har angivit. När du är klar klickar du på **Överför**.

7.  Klicka på **Stäng** för att slutföra.

Appen visas i noden **Appar** på arbetsytan **Appar**.


## Nästa steg

När du har skapat en app är nästa steg att distribuera den. Mer information finns i [Distribuera appar i Microsoft Intune](deploy-apps.md)





<!--HONumber=May16_HO1-->

