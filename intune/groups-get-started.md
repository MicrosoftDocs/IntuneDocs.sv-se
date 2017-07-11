---
title: "Kom igång med grupper i förhandsversionen av Intune Azure Portal"
titleSuffix: Intune Azure preview
description: "Läs mer om nyheterna med grupper i förhandsversionen av Intune i Azure-portalen"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angerobe
ms.date: 01/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 323f384d-8a76-4adc-999b-e508d641bfa1
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 0a6e2b75b1c85c0cd0ed98623dcd9d87b15eb082
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="get-started-with-groups"></a>Kom igång med grupper

[!INCLUDE[azure preview](./includes/azure_preview.md)]

Vi har hört er feedback och har därför gjort några ändringar i hur man arbetar med grupper i Microsoft Intune.
Om du använder Intune från Azure-portalen, har dina Intune-grupper migrerats till Azure Active Directory-säkerhetsgrupper.

Fördelen för dig är att du nu använder samma grupper för alla dina Enterprise Mobility + Security och Azure AD-appar. Dessutom kommer du att kunna använda PowerShell och Graph API för att utöka och anpassa den här nya funktionen.

Azure AD-säkerhetsgrupper stöder alla typer av Intune-distributioner för både användare och enheter. Du kan dessutom använda dynamiska grupper i Azure AD som automatiskt uppdateras baserat på de attribut som du anger. Du kan till exempel skapa en grupp av enheter som kör iOS 9. När en enhet som kör iOS 9 registreras visas enheten automatiskt i den dynamiska gruppen.

## <a name="what-is-not-available"></a>Vad är inte tillgängligt?

Vissa av de funktioner för Intune-grupper som du tidigare kan ha använt är inte tillgängliga i Azure AD:

- Intune-grupperna **Användare utan grupp** och **Enheter utan grupp** är inte längre tillgängliga.
- Alternativet att **Exkludera vissa medlemmar** från en grupp finns inte i Azure-portalen. Du kan dock använda en Azure AD-säkerhetsgrupp med avancerade regler för att replikera dessa gruppers beteende. För att till exempel skapa en avancerad regel som inkluderar alla personer i din försäljningsavdelning i en säkerhetsgrupp, men exkludera de som har ordet "Assistent" i sina jobbtitlar, kan du använda den här avancerade regeln:

  `(user.department -eq "Sales") -and -not (user.jobTitle -contains "Assistant")`.
- Gruppen **Alla hanterade enheter i Exchange ActiveSync** i Intune-konsolen migrerades inte till Azure AD. Du kan emellertid fortfarande komma åt information om EAS-hanterade enheter från Azure Portal.

## <a name="how-to-get-started"></a>Hur kommer man igång?

- Läs följande avsnitt för mer information om Azure AD-säkerhetsgrupper och hur de fungerar:
    -  [Hantera åtkomst till resurser med Azure Active Directory-grupper](https://azure.microsoft.com/en-us/documentation/articles/active-directory-manage-groups/).
    -  [Hantera grupper i Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-manage-groups/).
    -  [Använda attribut för att skapa avancerade regler](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/).
-  Kontrollera att administratörer som behöver skapa grupper läggs till i Azure AD-rollen **Administratör för Intune-tjänsten**. Azure AD-rollen Tjänstadministratör inte har behörighet att **hantera grupper**.
-  Om dina Intune-grupper använder alternativet **Exkludera särskilda medlemmar** så måste du bestämma om du ska göra om dessa grupper utan att använda undantag, eller om du behöver avancerade regler för att uppfylla affärsbehoven.


## <a name="what-happened-to-intune-groups"></a>Vad hände med Intune-grupperna?
När grupper migreras från den klassiska Intune-portalen till Intune i Azure Portal används följande regler:

| Grupper i Intune|Grupper i Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Statisk användargrupp|Statisk Azure AD-säkerhetsgrupp|
|Dynamisk användargrupp|Statiska Azure AD-säkerhetsgrupper med hierarki för Azure AD-säkerhetsgrupper|
|Statisk enhetsgrupp|Statisk Azure AD-säkerhetsgrupp|
|Dynamisk enhetsgrupp|Dynamisk Azure AD-säkerhetsgrupp|
|En grupp med ett inkluderingsvillkor|Statisk Azure AD-säkerhetsgrupp som innehåller några statiska/dynamiska medlemmar från inkluderingsvillkoret i Intune|
|En grupp med ett exkluderingsvillkor|Migreras inte|
|De inbyggda grupperna:<br>- **Alla användare**<br>- **Användare utan grupp**<br>- **All -enheter**<br>- **Enheter utan grupp**<br>- **Alla datorer**<br>- **Alla mobila enheter**<br>- **Alla MDM-hanterade enheter**<br>- **Alla EAS-hanterade enheter**|Azure AD-säkerhetsgrupper|

## <a name="group-hierarchy"></a>Grupphierarki

I den klassiska Intune-konsolen hade alla grupper en överordnad grupp. Grupper kunde endast innehålla medlemmar från den överordnade gruppen. Underordnade grupper i Azure AD kan innehålla medlemmar som inte är i den överordnade gruppen.

## <a name="group-attributes"></a>Gruppattribut
Attribut är enhetsegenskaper som kan användas för att definiera grupper. Den här tabellen beskriver hur dessa villkor kommer att migreras till Azure AD-säkerhetsgrupper.

| Attribut i Intune|Attribut i Azure AD|
|-----------------------------------------------------------------------|-------------------------------------------------------------|
|Organisationsenhetsattribut för enhetsgrupper|Organisationsenhetsattribut för dynamiska grupper.|
|Domännamnsattribut för enhetsgrupper|Domännamnsattribut för dynamiska grupper.|
|Säkerhetsgrupper som ett attribut för användargrupper|Grupper kan inte vara attribut i dynamiska frågor i Azure AD. Dynamiska grupper kan endast innehålla specifika attribut för användare eller enheter.|
|Chefsattribut för användargrupper|Avancerad regeln för *chefs*attribut i dynamiska grupper|
|Alla användare från den överordnade enhetsgruppen|Statisk grupp med den gruppen som en medlem|
|Alla mobila enheter från den överordnade enhetsgruppen|Statisk grupp med den gruppen som en medlem|
|Alla mobila enheter som hanteras med Intune|Hantera typsattribut med ‘MDM’ som värde för en dynamisk grupp|
|Kapslade grupper i statiska grupper |Kapslade grupper i statiska grupper|
|Kapslade grupper i dynamiska grupper|Dynamisk grupp med en kapslingsnivå|

## <a name="what-happens-to-policies-and-apps-you-previously-deployed"></a>Vad händer med principer och appar som du tidigare har distribuerat?

Principer och appar fortsätter att distribueras till grupper precis som tidigare. Men du kan nu hantera dessa grupper från Azure Portal i stället för från den klassiska Intune-konsolen.
