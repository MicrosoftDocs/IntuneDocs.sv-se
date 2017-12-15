---
title: "Tillämpa efterlevnadsprinciper för Jamf-hanterade enheter"
titlesuffix: Azure portal
description: "Använd efterlevnad för att säkra Jamf-hanterade enheter."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/30/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 06cc4d70b30ec92946baefbc020aa4cda28b0c88
ms.sourcegitcommit: 520eb7712625e129b781e2f2b9fe16f9b9f3d08a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/01/2017
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Tvinga fram efterlevnad på Mac-datorer som hanteras med Jamf Pro

|Gäller för: Intune på Azure Portal |
|--|
|Letar du efter dokumentation om Intune på den klassiska portalen? [Gå hit](/intune/introduction-intune?toc=/intune-classic/toc.json).|
| |

|För tillfället i privat förhandsvisning|
|--|
|De funktioner som beskrivs i det här avsnittet är bara tillgängliga för kunder som är med på den privata förhandsvisningen. Det här meddelandet tas bort när det har släppts för alla kunder.|
| |

Du kan använda Azure Active Directory och Microsoft Intunes principer för villkorlig åtkomst för att tillse att dina slutanvändare efterlever organisationens krav. Du kan tillämpa de här principerna på Mac-datorer som är [hanterade med Jamf Pro](conditional-access-integrate-jamf.md). Detta kräver tillgång till både Intune- och Jamf Pro-konsolerna.

## <a name="set-up-device-compliance-policies-in-intune"></a>Ställ in efterlevnadsprinciper för enheter i Intune

1. Öppna Microsoft Azure och gå till **Intune** > **enhetsefterlevnad** > **principer**. Du kan skapa principer för macOS, inklusive att välja en serie åtgärder (t.ex. skicka varnings-e-post) till icke-kompatibla användare och grupper.
2. Sök efter önskade grupper och tillämpa principer för dem.

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>Distribuera företagsportalappen för macOS i Jamf Pro

Det finns två sätt att distribuera företagsportalappen för macOS i Jamf Pro:

- Gör distributionen av företagsportalappen tillgänglig i Jamf Self Service, eller,
- Som en bakgrundsinstallation så att användarna följer anvisningarna nedan:

1. På en macOS-enhet laddar du ned den aktuella versionen av [företagsportalappen för macOS](https://go.microsoft.com/fwlink/?linkid=862280).
2. Öppna Jamf Pro och gå till **datorhantering** > **paket**.
3. Skapa ett nytt paket med företagsportalappen för macOS och klicka sedan på **spara**.
4. Öppna **datorer** > **principer** och välj **ny**.
5. Använd nyttolasten **Allmänt** för att konfigurera inställningar för principen. Inställningarna bör vara: 
   - Utlösare: välj **Registreringen är klar** och **Återkommande incheckning**
   - Körningsfrekvens: välj **En gång per dator**
6. Välj nyttolasten **paket** och klicka på **konfigurera**.
7. Klicka på **lägg till** för att välja paketet med företagsportalappen.
8. Välj **installera** från popup-menyn **åtgärd**.
9. Konfigurera inställningarna för paketet.
10. Klicka på fliken **omfång** för att ange vilka datorer företagsportalappen ska installeras på. Klicka på **Spara**. Principen kommer att köra begränsade enheter nästa gång den markerade utlösaren inträffar på datorn och uppfyller villkoren i nyttolasten **allmänt**.

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>Skapa en princip i Jamf Pro för att få användarna att registrera sina enheter med Azure Active Directory

> [!NOTE]
> Du behöver [distribuera företagsportalen](conditional-access-assign-jamf.md#require-the-company-portal-app-for-macos) för macOS innan du går igenom nästa steg.  

Slutanvändare behöver starta företagsportalappen via Jamf Self Service att registrera enheten med Azure AD som en enhet som hanteras av Jamf Pro. Detta kräver att slutanvändarna vidtar åtgärder. Vi rekommenderar att du [kontaktar användaren](end-user-educate.md) via e-post, Jamf Pro-meddelanden eller på andra sätt för att be dem att klicka på knappen i Jamf Self Service.

> [!WARNING]
> Företagsportalappen måste startas från Jamf Self Service för att påbörja enhetsregistrering. <br><br>Om du startar företagsportalappen manuellt (t.ex. från Program eller mappen Nedladdningar) registreras inte enheten. Om en slutanvändare startar företagsportalen manuellt visas varningen "AccountNotOnboarded".

1. I Jamf Pro, går du till **datorer** > **principer** och skapar en ny princip för enhetsregistrering.
2. Konfigurera nyttolasten **Microsoft Intune-integrering**, inklusive utlösare och körningsfrekvens. Ställ in prioriteten till **efter**.
3. Klicka på fliken **omfång** och begränsa principen till alla målriktade enheter.
4. Klicka på fliken **självbetjäning** för att göra principen tillgänglig i Jamf Self Service. Inkludera principen i kategorin **enhetsefterlevnad**. Klicka på **Spara**.

## <a name="next-steps"></a>Nästa steg

- [Villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Kom igång med villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)