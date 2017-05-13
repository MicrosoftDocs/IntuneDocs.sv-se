---
title: "Anpassade profilinställningar i Intune för Android for Work"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Lär dig hur du skapar en anpassad Intune-profil för Android for Work-enheter."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: 05afa9140e34b372cc49ace03a3ada965b907c17
ms.contentlocale: sv-se
ms.lasthandoff: 05/10/2017


---

# <a name="create-intune-custom-profile-settings-for-android-for-work-devices"></a>Skapa anpassade profilinställningar i Intune för Android for Work-enheter

Använd en anpassad konfigurationsprincip för Android for Work i Intune för att tilldela OMA-URI-inställningar som kan användas till att styra funktioner på Android for Work-enheter. Detta är standardinställningar som många tillverkare av mobila enheter använder för att styra enhetsfunktioner.

Funktionen är avsedd för att kunna tilldela Android-inställningar som inte går att konfigurera med Intune-principer. Intune har för närvarande stöd för ett begränsat antal anpassade Android-principer. Se exemplen i det här avsnittet för att ta reda på vilka principer du kan konfigurera.

## <a name="create-a-custom-profile"></a>Skapa en anpassad profil

1. Kom igång med hjälp av anvisningarna i [Konfigurera anpassade enhetsinställningar](how-to-configure-custom-settings.md).
2. På bladet **Anpassade OMA-URI-inställningar** väljer du **Lägg till** för att lägga till en ny inställning.
3. På bladet **Lägg till rad** konfigurerar du följande:
    - **Namn** – Ange ett unikt namn för den anpassade Android for Work-principen, som hjälper dig att identifiera den i Intune-portalen.
    - **Beskrivning** – Ange en beskrivning med en översikt av den anpassade Android-principen, samt annan information som gör det enkelt att hitta den.
    - **OMA-URI** – Ange den OMA-URI som du vill ange en inställning för.
    - **Datatyp** – Ange den datatyp som du vill specificera den här OMA-URI-inställningen med. Välj mellan **Sträng**, **Sträng (XML-fil)**, **Datum och tid**, **Heltal**, **Flyttal**, **Boolesk** eller **Base64 (fil)**.
    - **Värde** – Ange det värde som ska associeras med den OMA-URI som du tidigare angav. Metoden du använder för att ange värdet varierar beroende på datatypen som du har valt. Om du till exempel har valt **Datum och tid**, väljer du värdet från en datumväljare.
4. När du är klar väljer du OK för att återgå till **Anpassade OMA-URI-inställningar**. Lägg sedan till fler inställningar eller välj **Skapa** för att skapa den anpassade profilen.


## <a name="example"></a>Exempel

I det här exemplet skapar du en anpassad profil som kan användas för att begränsa om åtgärderna för att kopiera och klistra in mellan arbetsappar och personliga appar ska vara tillåtna på hanterade Android for Work-enheter.

1. Använd metoden i det här avsnittet för att skapa en anpassad profil för Android for Work-enheter med följande värden:
    - **Namn** – Ange ”Blockera kopiera och klistra in” eller välj en egen text.
    - **Beskrivning** – Ange ”Blockera kopiera/klistra in mellan arbetsappar och personliga appar” eller välj en egen text.
    - **OMA-URI** – Ange **./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste**.
    - **Datatyp** – Välj **Boolesk** för att visa att värdet för den här OMA-URI:n är antingen **Sant** eller **Falskt**.
    - **Värde** – Välj **Sant**.
2. Du bör få en inställning som liknar den här bilden.
![Blockera kopiera och klistra in för Android for Work.](./media/custom-policy-afw-copy-paste.png)
3. Nu när du tilldelar den här anpassade profilen till Android for Work-enheter som du hanterar, kommer funktionen för att kopiera och klistra in att blockeras mellan arbetsappar och personliga profiler.