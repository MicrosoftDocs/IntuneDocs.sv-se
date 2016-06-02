---
# required metadata

title: Förstå dina enheter med inventering i Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 312911fe-b963-4949-9911-ae425e0590b2

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Förstå dina enheter inventering i Microsoft Intune
Med Microsoft Intune kan du visa inventeringen för registrerade enheter och Windows-datorer som kör Intune-klientprogrammet.

## Vad samlas in från registrerade enheter?
Om du vill se inventeringen som samlas in av mobila enheter kör du [Rapporter om inventering av mobila enheter](understand-microsoft-intune-operations-by-using-reports.md). Intune samlar in följande inventering från registrerade enheter:

|Egenskap|Samlas in av|
|------------|-----------------------|
|**Namn**|All -enheter|
|**Operativsystem**|All -enheter|
|**Tillverkare**|All -enheter|
|**Modell**|All -enheter|
|**Hanteringskanal**|All -enheter|
|**AAD-registrerad**|Alla enheter utom Mac OS X|
|**Kompatibel**|All -enheter|
|**EAS-aktiverad**|Alla enheter utom Mac OS X|
|**Aktiverings-ID för EAS**|Alla enheter utom Mac OS X|
|**Aktiveringstid för EAS**|Alla enheter utom Mac OS X|
|**Hanteringstillstånd**|All -enheter|
|**E-postadress**|All -enheter|
|**Exchange ActiveSync ID**|All -enheter|
|**Jailbrokad eller rotad**|Endast iOS- och Android-enheter|
|**Unikt enhets-ID**|Alla enheter utom Exchange ActiveSync|
|**Serienummer**|iOS-, Mac OS X-, Android-, Windows 8.1- och Windows 10-enheter|
|**Totalt lagringsutrymme**|iOS-, Mac OS X-, Windows 8.1- och Windows 10-enheter|
|**Ledigt lagringsutrymme**|iOS-, Mac OS X-, Windows 8.1- och Windows 10-enheter|
|**Telefonnummer**<br>Exempelvis identifieras telefoner som kategoriserats som företagets med sina fullständiga telefonnummer när du kör en inventeringsrapport för mobila enheter. BYOD-telefonnummer maskeras med &#42;, och bara de sista fyra siffrorna visas.|iOS-, Android- och Windows Phone-enheter|
|**IMEI**|Exchange ActiveSync-, iOS-, Android- och Windows Phone-enheter|
|**MEID**<br>MEID (Mobile Equipment Identifier)|Endast iOS-enheter|
|**Wi-Fi MAC**|Alla enheter utom Exchange ActiveSync|
|**Abonnentens operatör**|Endast iOS- och Android-enheter|
|**Mobilteknik**|Endast iOS- och Android-enheter|
|**Övervakas**|Endast iOS-enheter|
|**Status för aktiveringslås**|Endast iOS-enheter|
|**Registreringsdatum**|All -enheter|
|**Senast uppdaterad**|All -enheter|
|**Ethernet MAC**|Endast Mac OS X-enheter|
|**Aktiveringslåset är aktiverat**|Endast iOS-enheter|
|**Kryptering är aktiverat**|All -enheter|

## Det här samlas in från Windows-datorer
> [!IMPORTANT]
> Det här avsnittet gäller endast för Windows-datorer som kör Intunes Windows-PC-klientprogramvara.

Om du vill visa inventeringen som samlas in av Windows-datorer kör du [datorinventeringsrapporterna](understand-microsoft-intune-operations-by-using-reports.md). Intune samlar in följande inventering från Windows-datorer:

-   **Namn**

-   **Chassityp**

-   **Tillverkare**

-   **Modell**

-   **Operativsystem**

-   **TPM-version**

-   **Totalt diskutrymme**

-   **Använt diskutrymme**

-   **Ledigt diskutrymme**

-   **Namn på disk på operativsystem**

-   **Diskutrymme på operativsystem**

-   **Ledigt diskutrymme på operativsystem**

-   **Fysiskt minne**

-   **Processornamn**

-   **Processorarkitektur**

-   **Processorhastighet**

-   **IP-adress**

-   **Serienummer**

-   **Senast inloggade användare**

-   **Tilldelad användare**

-   **Senast uppdaterad**

### Se även
[Övervakning och rapporter med Microsoft Intune](monitoring-and-reports-with-microsoft-intune.md)



<!--HONumber=May16_HO1-->

