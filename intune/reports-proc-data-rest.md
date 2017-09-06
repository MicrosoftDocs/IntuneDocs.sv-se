---
title: "Hämta data från API för informationslager med en REST-klient"
description: "Hämta data från Intune-informationslagret med ett RESTful-API."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: D6D15039-4036-446C-A58F-A5E18175720A
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1bbb0e8ba84e221df3a434da79c513939267648b
ms.sourcegitcommit: b8ef9d8387b4d9b2ea4e6ce937635304771e6532
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/11/2017
---
# <a name="get-data-from-the-intune-data-warehouse-api-with-a-rest-client"></a>Hämta data från API för Intune-informationslagret med en REST-klient

Du når datamodellen Intune-informationslager via RESTful-slutpunkter. Klienten måste auktorisera med Microsoft Azure Active Directory (Azure AD) med hjälp av OAuth 2.0 för att få åtkomst till dina data. Om du vill aktivera åtkomst måste du först ställa in en inbyggd app i Azure och ge behörighet till Microsoft Intune-API. Den lokala klienten får behörighet och kan sedan kommunicera med informationslagrets slutpunkter via den inbyggda appen.

När du ska ställa in en klient för att hämta data från informationslager-API:et måste du:

1. Skapa en klientapp som inbyggd app i Azure
3. Ge klientappen åtkomst till Microsoft Intune-API
3. Skapa en lokal REST-klient som ska hämta data

Följande anvisningar visar hur du auktoriserar och använder Postman som klient. Postman är ett verktyg som ofta används för felsökning och utveckling av REST-klienter som fungerar med API:er. Mer information om Postman finns på sajten [Postman](https://www.getpostman.com). Det här avsnittet innehåller också ett C#-kodexempel. Det innehåller ett exempel för auktorisering av en klient och hämtning av data från API:et.

## <a name="create-a-native-app-in-azure"></a>Skapa en inbyggd app i Azure

Skapa en inbyggd app i Azure. Den här inbyggda appen är klientappen. Klienten som körs på din lokala dator hänvisar till Intune-informationslagrets API när den lokala klienten begär autentiseringsuppgifter. 

1. Logga in på Azure Portal för din klientorganisation. Välj **Azure Active Directory** > **Appregistreringar** så att bladet **Appregistreringar** öppnas.
2. Klicka på **Ny appregistrering**.
3. Ange information om appen.
    1.  Skriv ett eget namn, till exempel Intune Data Warehouse Client som **namn**.
    2.  Välj**Intern** som **Programtyp**.
    3.  Skriv en webbadress för **Inloggningswebbadress**. Inloggningswebbadressen beror på den särskilda situationen men om du tänkt använda Postman skriver du `https://www.getpostman.com/oauth2/callback`. Du kommer sedan använda callback (återanrop) för klientautentiseringen när du autentiserar till Azure AD.
4.  Klicka på **Skapa**.

     ![API för Intune-informationslager](media\reports-get_rest_data_client_overview.png)

5. Observera appens värde för **Program-ID**. Det här värdet ska användas i nästa avsnitt.
6. Lägg till en nyckel om du ska använda Postman. Nyckeln används som klienthemlighet vid autentisering till Azure AD. Så här lägger du till en nyckel:
    1.  Klicka på **Nycklar** under **API-åtkomst** i Inställningar i appen.
    2.  Skriv ett namn på nyckeln, till exempel Klienthemlighet som **Beskrivning**.
    3.  Välj **1 år** för Varaktighet.
    4.  Klicka på **Spara**. 
    5.  Kopiera värdet för nyckeln. Du kan inte hämta nyckeln när du har stängt bladet **Inställningar** för Nycklar.

## <a name="grant-the-native-app-access-to-the-microsoft-intune-api"></a>Ge den inbyggda klientappen åtkomst till Microsoft Intune-API

Nu har du definierat en app i Azure. Bevilja åtkomst från inbyggda klientappen till Microsoft Intune-API.

1.  Klicka på den inbyggda appen. Du gav appen ett namn i stil med Intune Data Warehouse Client.
2.  Klicka på **Nödvändiga behörigheter** på bladet **Inställningar**
3.  Klicka på **Lägg till** på bladet **Nödvändiga behörigheter**.
4.  Klicka på **Välj ett API**.
5.  Sök efter namnet på webbappen. Namnet är **Microsoft Intune API**.
6.  Klicka på appen i listan.
7.  Klicka på **Välj**.
8.  Markera rutan **Delegerade behörigheter** för att lägga till **Hämta informationslagerdata från Microsoft Intune**.

    ![Aktivera åtkomst](media\reports-get_rest_data_client_access.png)

9.  Klicka på **Välj**.
10.  Klicka på **Klar**.
11.  Du kan också klicka på **Bevilja behörigheter** på bladet Nödvändiga behörigheter. Då får alla konton i den aktuella katalogen åtkomst. Dialogrutan för medgivande visas inte för användarna i klientorganisationen. Mer information finns i [Integrating applications with Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) (Integrera program med Azure Active Directory).
12.  Klicka på **Ja**.

## <a name="get-data-from-the-microsoft-intune-api-with-postman"></a>Hämta data från Microsoft Intune-API med Postman

Du kan arbeta med API för Intune-informationslager med en vanlig REST-klient, till exempel Postman. Postman kan ge information om API:ets funktioner, den underliggande OData-datamodellen och felsöka anslutningen till API-resurserna. I det här avsnittet hittar du information om hur du skapar en Auth2.0-token för en lokal klient. Token behövs för att klienten ska kunna autentiseras med Azure AD och få åtkomst till API-resurserna.

### <a name="information-you-will-need-to-make-the-call"></a>Information du behöver för att skicka anropet

Du behöver följande information för att skicka ett REST-anrop via Postman:

| Attribut        | Beskrivning                                                                                                                                                                          | Exempel                                                                                       |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| Callback URL (Webbadress för återanrop)     | Ställ in det här som webbadress för återanrop på appinställningssidan.                                                                                                                              | https://www.getpostman.com/oauth2/callback                                                    |
| Token Name (Tokennamn)       | En sträng som används för att skicka autentiseringsuppgifter till Azure-appen. Med den här processen skapas din token så att du kan anropa API för informationslagret.                          | Bearer                                                                                        |
| Auth URL (Auktoriseringswebbadress)         | Webbadressen som används för autentisering. | https://login.microsoftonline.com/common/oauth2/authorize?resource=https://api.manage.microsoft.com |
| Access Token URL (Webbadress för åtkomsttoken) | Webbadressen som används för att bevilja token.                                                                                                                                              | https://login.microsoftonline.com/common/oauth2/token |
| Klient-ID        | Du skapade och antecknade det här när du skapade den inbyggda appen i Azure.                                                                                               | 4184c61a-e324-4f51-83d7-022b6a81b991                                                          |
| Client Secret (Klienthemlighet)    | Du skapade och antecknade det här när du lade till en nyckel för klientappen i Azure.                                                                                              | JZoRZGPmN9xwsUnfX9UW877dkV5Fn/qQClhr7SuyMUQ=                                                  |
| Scope (Optional) (Omfång, valfritt) | Tom                                                                                                                                                                               | Du kan lämna fältet tomt.                                                                     |
| Grant Type (Typ av beviljande)       | Token är en auktoriseringskod.                                                                                                                                                  | Authorization code (Auktoriseringskod)                                                                            |

Du behöver en slutpunkt. I det här exemplet ska vi hämta data från entiteten **datum**. Entiteten **dates** har följande format: `https://fef.{aus}.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=beta`. Du ska använda klientorganisationens hanteringswebbadress. Du använde klientorganisationens hanteringswebbadress när du skapade webbappen.

### <a name="make-the-rest-call"></a>Skicka ett REST-anrop

Om du vill hämta en ny åtkomsttoken för Postman måste du lägga till Azure AD-auktoriseringswebbadressen, klient-id och klienthemlighet. Postman läser in auktoriseringssidan där du anger dina autentiseringsuppgifter.

#### <a name="add-the-information-used-to-request-the-token"></a>Lägg till informationen som används för att begära token

1.  Ladda ned Postman om det inte redan är installerat. Information om hur du laddar ned Postman finns i [www.getpostman](https://www.getpostman.com).
2.  Öppna Postman. Välj HTTP-åtgärden **GET**.
3.  Klistra in slutpunktswebbadressen i adressfältet. Det bör se ut ungefär så här:  

    `https://fef.msua06.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=beta`
4.  Välj fliken **Authorization** (Auktorisering) och välj **OAuth 2.0** i listan **Type** (Typ).
5.  Klicka på **Get New Access Token** (Hämta ny åtkomsttoken).
6.  Kontrollera att du har lagt till webbadressen för återanrop i appen i Azure. Webbadressen för återanrop är `https://www.getpostman.com/oauth2/callback`.
7.  Skriv Bearer som **Token Name** (Namn på token).
8.  Lägg till **Auth URL** (autentiseringswebbadressen). Det bör se ut ungefär så här:  

    `https://login.microsoftonline.com/common/oauth2/authorize?resource=https://api.manage.microsoft.com`
9.  Lägg till **Access Token URL**(webbadress för token). Det bör se ut ungefär så här:  

     `https://login.microsoftonline.com/common/oauth2/token`

10. Lägg till **Client ID** (Klient-id) från den inbyggda app du skapade i Azure med namnet `Intune Data Warehouse Client`. Det bör se ut ungefär så här:  

     `4184c61a-e324-4f51-83d7-022b6a81b991`

11. Lägg till den **Client Secret** (klienthemlighet) som du angav som nyckel när du skapade den inbyggda appen i Azure. Det bör se ut ungefär så här: 

     `F360R69M0MS72OB6YAqTyXO9MsXZx/OJTgAE2HB4k2k=`

12. Välj **Authorization Code** (Auktoriseringskod) och Request access token locally (Begär åtkomsttoken lokalt).

13. Klicka på **Request Token** (Begär token).

    ![Information för token](media\reports-postman_getnewtoken.png)

14. Ange dina autentiseringsuppgifter på auktoriseringssidan i Active AD. I listan över befintliga token i Postman finns nu token med namnet `Bearer`.
16. Välj token. Välj **Header** (Sidhuvud) vid Add token to (Lägg till token i).
17. Klicka på **Use Token** (Använd token). Listan över sidhuvuden innehåller det nya nyckelvärdet för auktorisering och värdet `Bearer <your-authorization-token>`.

#### <a name="send-the-call-to-the-endpoint-using-postman"></a>Skicka anropet till slutpunkten via Postman

1.  Klicka på **Skicka**.
2.  Returnerade data visas i svarstexten i Postman.

    ![Postman 200OK](media\reports-postman_200OK.png)

## <a name="create-a-rest-client-c-to-get-data-from-the-intune-data-warehouse"></a>Skapa en REST-klient (C#) för att hämta data från Intune-informationslagret

Följande exempel innehåller en enkel REST-klient. Koden använder klassen **httpClient** från .Net-biblioteket. När klienten har fått autentiseringsuppgifter till Azure AD skapar klienten ett GET REST-anrop för att hämta dates-entiteten från API:et för Intune-informationslager.

> [!Note]  
> Du kan öppna följande kodexempel [i GitHub](https://github.com/Microsoft/Intune-Data-Warehouse/blob/master/Samples/CSharp/Program.cs). De senaste ändringarna och uppdateringarna av exemplet hittar du i GitHub-databasen.

1.  Öppna **Microsoft Visual Studio**.
2.  Välj **File**(Arkiv) > **New project** (Nytt projekt). Expandera **Visual C#** och välj **Console App (.Net Framework)** (Konsolapp (.Net Framework)). 
3.  Ge projektet namnet ` IntuneDataWarehouseSamples`, bläddra dit där du vill spara projektet och klicka sedan på **OK**.
3.  Högerklicka på namnet på lösningen i Solution Explorer och välj sedan **Manage NuGet Packages for Solution** (Hantera NuGet-paket för lösning). Klicka på **Browse** (Bläddra) och skriv Microsoft.IdentityModel.Clients.ActiveDirectory i sökrutan.
4. Välj paketet och markera projektet **IntuneDataWarehouseSamples** under Manage Packages for Your Solution (Hantera paket för lösningen) och klicka sedan på **Install** (Installera). 
5. Klicka på **I Accept** (Jag accepterar) för att godkänna NuGet-paketlicensen.
6. Öppna `Program.cs` från Solution Explorer.

    ![Projekt i Visual Studio](media\reports-get_rest_data_in.png)

7.  Ersätt koden i Program.cs med följande kod:  
    ```csharp
namespace IntuneDataWarehouseSamples
{
    using System;
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Microsoft.IdentityModel.Clients.ActiveDirectory;

    class Program
    {
     static void Main(string[] args)
  {
   /**
    * TODO: Replace the below values with your own.
    * emailAddress - The email address of the user that you will authenticate as.
    *
    * password  - The password for the above email address.
    *    This is inline only for simplicity in this sample. We do not 
    *    recommend storing passwords in plaintext.
    *
    * applicationId - The application ID of the native app that was created in AAD.
    *
    * warehouseUrl   - The data warehouse URL for your tenant. This can be found in 
    *      the Azure portal.
    * 
    * collectionName - The name of the warehouse entity collection you would like to 
    *      access.
    */
   var emailAddress = "intuneadmin@yourcompany.com";
   var password = "password_of(intuneadmin@yourcompany.com)";
   var applicationId = "<Application ID>";
   var warehouseUrl = "https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta";
   var collectionName = "dates";

   var adalContext = new AuthenticationContext("https://login.windows.net/common/oauth2/token");
   AuthenticationResult authResult = adalContext.AcquireTokenAsync(
    resource: "https://api.manage.microsoft.com/",
    clientId: applicationId,
    userCredential: new UserPasswordCredential(emailAddress, password)).Result;

   var httpClient = new HttpClient();
   httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", authResult.AccessToken);

   var uriBuilder = new UriBuilder(warehouseUrl);
   uriBuilder.Path += "/" + collectionName;

   HttpResponseMessage response = httpClient.GetAsync(uriBuilder.Uri).Result;

   Console.Write(response.Content.ReadAsStringAsync().Result);
   Console.ReadKey();
  }
    }
    ```

8.  Uppdatera `TODO`-texten i kodexemplet.
9.  Tryck på **Ctrl + F5** för att skapa och köra Intune.DataWarehouseAPIClient-klienten i felsökningsläge.

    ![Datumentitet som hämtats i JSON-format.](media\reports-get_rest_data_output.png)

10.  Granska konsolutdata. Utdata består av data i ett JSON-format som hämtats från **dates**-entiteten i din Intune-klientorganisation.

## <a name="next-steps"></a>Nästa steg

Du hittar information om auktorisering, API:ets webbadresstruktur och OData-slutpunkter i [API-slutpunkt för Intune-informationslager](reports-api-url.md). 

I datamodellen Intune-informationslager hittar du också dataentiteterna i API:et. Mer information finns i [Datamodellen API för Intune-informationslager](reports-ref-data-model.md)