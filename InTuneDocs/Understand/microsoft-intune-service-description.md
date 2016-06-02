---
# required metadata

title: Beskrivning av tjänst | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 40fa5a2e-6c0f-4150-9740-d5ddc0cdbda0

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Beskrivning av Microsoft Intune-tjänsten

Microsoft Intune är en molnbaserad tjänst som hjälper dig att hantera Windows-datorer och mobila enheter med iOS, Mac OS X, Android och Windows. Intune hjälper också till att skydda företagsprogram och -data. Du kan använda Intune enbart eller integrera det med System Center 2012 R2 Configuration Manager för att utöka dina hanteringsfunktioner.

Microsoft erbjuder Intune Onboarding-förmåner för berättigade tjänster i berättigade planer. Med Onboarding-förmånerna kan du arbeta på distans med Microsoft-specialister för att färdigställa din Intune-miljö. Mer information finns i [Beskrivning av Microsoft Intune Onboarding-förmåner](http://go.microsoft.com/fwlink/?LinkId=619281).

Du kan börja använda Intune med en kostnadsfri 30-dagars utvärderingsversion som innehåller 100 användarlicenser. Påbörja din kostnadsfria utvärderingsperiod genom att [klicka här för att besöka sidan Intune-registrering](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/). Om din organisation har ett företagsavtal eller motsvarande volymlicensavtal, kontaktar du din Microsoft-representant om du vill konfigurera den kostnadsfria utvärderingsversionen.

> [!NOTE]
> Om din organisation redan har ett arbets- eller skolkonto för Microsoft Online Services och kanske kommer att fortsätta med den här Intune-prenumerationen i produktion efter det att utvärderingsperioden har löpt ut, klickar du på alternativet **Logga in** på sidan Logga in och autentiserar med hjälp av din organisations globala administratörskonto. Den här åtgärden säkerställer att din Intune-utvärderingsversion länkar till det befintliga arbets- eller skolkontot.

En lista över inställningar du kan konfigurera för mobila enheter finns här:

-   [Funktioner för hantering av mobila enheter i Microsoft Intune](mobile-device-management-capabilities-in-microsoft-intune.md)

-   [Allmänna inställningar för mobila enheter i Configuration Manager](https://technet.microsoft.com/en-us/library/dn376523.aspx)

Information om System Center 2012 R2 Configuration Manager finns i [dokumentationsbiblioteket för System Center 2012 Configuration Manager](https://technet.microsoft.com/library/gg682041.aspx).

## Förstå hur uppdateringar av Intune-tjänsten påverkar dig
Eftersom Intune är en onlinetjänst kan Microsoft uppdatera den regelbundet.

Använd informationen i det här avsnittet för att förstå hur ofta dessa tjänsteuppdateringar genomförs och den avisering i förväg som vi skickar till dig när en uppdatering kan påverka din användning av tjänsten.

Information om ändringar i Intune-tjänsten finns i [Nyheter i Microsoft Intune](/intune/deploy-use/Whats-new-in-microsoft-intune.md). På [Microsoft Intune-bloggen](http://blogs.technet.com/b/microsoftintune/) diskuteras också ändringar i tjänsten och du får nyttiga tips så att du kan få ut mesta möjliga av Intune.

Dessutom förmedlas viktiga uppdateringar av tjänsten till dig direkt från Intune-konsolen på anslagstavlan.

Här är de typer av meddelanden som Microsoft tillhandahåller om Intune-tjänsten:
-   Som hjälp att planera för tjänsteändringar meddelar vi dig minst 30–90 dagar innan tjänsteuppgraderingen beroende på effekten av ändringen. Detta sker med hjälp av kommunikationskanaler i produkten som anslagstavleaviseringar. Exempel på ändringar:
* Uppdateringar som kan påverka regelefterlevnaden
* Ändringar av användarupplevelse, användargränssnitt och arbetsflöden
* Nya eller ändrade API:er – du får ett meddelande om att du måste utföra tester för att säkerställa bakåtkompatibilitet för anpassade appar
* Ändringar av systemkrav, till exempel hur gammal webbläsarversionen får lov att vara
* Alla uppdateringar som kräver att du vidtar åtgärder för att aktivera funktionen eller för att undvika tjänsteavbrott för funktionen.
-   Microsoft tillhandahåller information om nya funktioner och förbättringar av befintliga funktioner i vår månatliga tjänstuppdatering. I allmänhet skickar Microsoft ut tjänstuppdateringar runt mitten av varje månad. Uppdateringar beskrivs i [Nyheter i Microsoft Intune](/intune/deploy-use/whats-new-in-microsoft-intune.md).
-   Om Intune-tjänsten skulle dras tillbaka meddelas du 12 månader i förväg.

## Välj den hanteringslösning som passar dig
Du kan konfigurera Intune på ett antal sätt för att hantera och skydda företagets mobila enheter och datorer (kallas **enheter** i det här dokumentet).

-   **Fristående Intune-konfiguration.** Använd den webbaserade administrationskonsolen i Intune för att hantera enheter i organisationen. Intune kan användas utan att det finns någon lokal IT-infrastruktur, men om du använder Intune med Active Directory Domain Services, kan du använda domänanvändarkonton som du hanterar med domäntjänster med Intune.

-   **Intune med System Center Configuration Manager.** Använd hanteringskonsolen i Configuration Manager för att hantera datorer och mobila enheter i företaget. Den här konfigurationen kan hjälpa dig att hantera organisationens enheter genom en enda konsol, nämligen administratörskonsolen i Configuration Manager. Configuration Manager stöder ett stort antal mobila enheter, servrar och datorer. Mer information finns i [Hantera mobila enheter med Configuration Manager och Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=271118) i [dokumentationsbiblioteket för System Center 2012 Configuration Manager](https://technet.microsoft.com/library/gg682041.aspx).  Mer hjälp för att avgöra vilket arbetssätt som passar dig bäst finns i [Användning av mobilitet i företag](/intune/plan-design/ways-to-do-enterprise-mobility.md)

-   Hantering av mobila enheter som tillhandahålls av Office 365, enligt beskrivningen i [Användning av mobilitet i företag](/intune/plan-design/ways-to-do-enterprise-mobility.md)

## Läs mer om Intune
Använd dessa resurser om du vill veta mer om Intune:

-   [Microsoft Intune Trust Center](http://www.microsoft.com/en-us/server-cloud/products/intune-trust-center/) innehåller information om säkerhet och sekretess samt efterlevnadsregler för Intune och beskriver även några av certifieringarna för Intune.

-   [Funktioner för hantering av mobila enheter i Microsoft Intune](/intune/understand-explore/mobile-device-management-capabilities-in-microsoft-intune.md)

### Se även
[Microsoft Intune](https://docs.microsoft.com/intune/)
[Dokumentationsbibliotek för System Center 2012 Configuration Manager](https://technet.microsoft.com/library/gg682041.aspx)

[Nyheter i Microsoft Intune](/intune/deploy-use/whats-new-in-microsoft-intune.md)


<!--HONumber=May16_HO1-->

