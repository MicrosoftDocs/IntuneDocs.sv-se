---
ms.openlocfilehash: 8483ed3d4198e228bdaaf4723b2c9c0dca9cecfc
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71830509"
---
<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Krav på Azure AD- och Intune-autentiseringsuppgifter

Autentisering och auktorisering bygger på Azure AD-autentiseringsuppgifter och Intune-rollbaserad åtkomstkontroll (RBAC). Alla globala administratörer och Intune-tjänstadministratörer för din klientorganisation har som standard åtkomst till informationslagerdatabasen. Använd Intune-roller till att ge fler användare åtkomst genom att de får tillgång till resursen **Intune-informationslager**.

Kraven för att få åtkomst till Intune-informationslagret (inklusive API) är:

- Användaren måste vara något av följande:
  - Global Azure AD-administratör
  - Intune-tjänstadministratör
  - Användare med rollbaserad åtkomst till resursen **Intune-informationslager**
  - Användarlös autentisering med [enbart programautentisering](../developer/data-warehouse-app-only-auth.md) 
