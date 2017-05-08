# Call Office 365 services in Visual Studio with the Microsoft Graph API

You can use the Connected Services in Visual Studio to configure your app to call the Microsoft Graph API. This article describes how to get a signed in user's profile photo, upload it to OneDrive, and send an email with a sharing link to the photo.

## Set up and get the starter project

To use the Office 365 Connected Services with Microsoft Graph, download the [Visual Studio 2017 Preview](https://www.visualstudio.com/vs/preview/), if you haven't already.

    >**Note:** If you're using an earlier version of Visual Studio, you can use Visual Studio 2017 Preview side by side with your current version.

You will also need an Office 365 subscription. To get a free trial, join the [Office 365 Developer program](https://dev.office.com/devprogram).

Clone the [Microsoft Graph ASP.NET Connected Services Sample](https://github.com/microsoftgraph/aspnet-connect-sample/tree/Office365connectedservice) repository on GitHub. This sample includes the references that you need to authenticate against Microsoft Graph. Open the sample in Visual Studio 2017 Preview.

## Add the Connected Service

You're now ready to add the Microsoft Graph service to your Visual Studio project. 

1. In Solution Explorer, choose **Connected Services** to open the Connected Services tab. 

2. Choose the **Access Office 365 Services with Microsoft Graph** provider. Follow the wizard. Select the following permissions (you can change the permisssions later):

    - For the **File** APIs, set permissions to **Have full access to your files**.
    - For the **Mail** APIs, set permissions to **Send mail as you**.
    - For the **User** APIs, set permissions to **Sign you in and read your profile**.

## Call the Microsoft Graph API

The starter sample is configured to send a simple email. You can use Microsoft Graph to update the sample to send an email with a link to the signed-in user's profile photo in OneDrive.

1. Go to 'Models\GraphService.cs', which hosts the code to call Microsoft Graph.

2. Find and **Uncomment** calls to the SDK in the following methods. This shows how to call Microsoft Graph to get a profile photo, upload a file to OneDrive, and get a sharing link.

    ```csharp
        GetCurrentUserPhotoStream(GraphServiceClient graphClient)
    ```
    
    ```csharp
        UploadFileToOneDrive(GraphServiceClient graphClient, byte[] file)
    ```

    ```csharp
        GetSharingLink(GraphServiceClient graphClient, string Id)
    ```
 
> Tip: Each comment starts with '//Uncomment:'
 

## Run the sample
Build and run the sample.  

Choose the **Sign-in** link on the top right, and then choose **Send Email**.

This will send an email that includes a link to your profile photo.


## Explore the code

You can now use Visual Studio 2017 to connect to and configure your services. The starter sample creates the scaffolding and references for you.  

The starter sample includes the following files:

- [Startup.Auth.cs](https://github.com/microsoftgraph/aspnet-connect-sample/tree/Office365connectedservice/Microsoft%20Graph%20SDK%20ASPNET%20Sample/Microsoft%20Graph%20SDK%20ASPNET%20Sample/App_Start/Startup.Auth.cs) - Authenticates the current user and initializes the sample's token cache.

- Models\\[SessionTokenCache.cs](https://github.com/microsoftgraph/aspnet-connect-sample/tree/Office365connectedservice/Microsoft%20Graph%20SDK%20ASPNET%20Sample/Microsoft%20Graph%20SDK%20ASPNET%20Sample/TokenStorage/SessionTokenCache.cs) - Stores the user's token information. You can replace this with your own custom token cache. For more information, see [Caching access tokens in a multitenant application](https://azure.microsoft.com/en-us/documentation/articles/guidance-multitenant-identity-token-cache/).

- Models\\[SampleAuthProvider.cs](https://github.com/microsoftgraph/aspnet-connect-sample/tree/Office365connectedservice/Microsoft%20Graph%20SDK%20ASPNET%20Sample/Microsoft%20Graph%20SDK%20ASPNET%20Sample/Helpers/SampleAuthProvider.cs) - Implements the local IAuthProvider interface, and gets an access token. 

- Helpers\\[SDKHelper.cs](https://github.com/microsoftgraph/aspnet-connect-sample/tree/Office365connectedservice/Microsoft%20Graph%20SDK%20ASPNET%20Sample/Microsoft%20Graph%20SDK%20ASPNET%20Sample/Helpers/SDKHelper.cs) - Initializes the **GraphServiceClient** from the [Microsoft Graph .NET Client Library](https://github.com/microsoftgraph/msgraph-sdk-dotnet) that is used to interact with the Microsoft Graph.

- Controllers\\[HomeController.cs](https://github.com/microsoftgraph/aspnet-connect-sample/tree/Office365connectedservice/Microsoft%20Graph%20SDK%20ASPNET%20Sample/Microsoft%20Graph%20SDK%20ASPNET%20Sample/Controllers/HomeController.cs) - Contains methods that use the **GraphServiceClient** to build and send calls to the Microsoft Graph service and to process the response.

- Views\\Home\\[Graph.cshtml](https://github.com/microsoftgraph/aspnet-connect-sample/tree/Office365connectedservice/Microsoft%20Graph%20SDK%20ASPNET%20Sample/Microsoft%20Graph%20SDK%20ASPNET%20Sample/Views/Home/Graph.cshtml) - Contains the UI for the sample. 


## Need help?

If you need help, post your questions on [StackOverflow](https://stackoverflow.com/questions/tagged/microsoftgraph?sort=newest). Tag your post with {Microsoft Graph}.
