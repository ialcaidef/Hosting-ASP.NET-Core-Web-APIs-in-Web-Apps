# Hosting-ASP.NET-Core-Web-APIs-in-Web-Apps
20487C_MOD05_DEMO_L2

# Hosting Services in Web Apps Feature of Azure App Service

### Demonstration: Hosting ASP.NET Core Web APIs in Web Apps

1. Open Microsoft Azure Portal.

2. If a page appears asking for your email address, enter your email address, and then click **Continue**. Wait for the sign-in page to appear, enter your email address and password, and then click **Sign In**.

   >**Note**: During the sign-in process, if a page appears asking you to choose from a list of previously used accounts, select the account that you previously used, and then continue to provide your credentials.

3. If the **Windows Azure Tour** dialog box appears, to close it, click **X**.

4. In the navigation blade, click **App Services**. 

5. To create a new app service, in the menu at the top, click **Add**.

6. In the **Web** blade, in the **Web Apps** section, select **Web App**, and then click **Create**.

7. In the **App name** box, enter a unique name.

8. Copy the **App name** value to any code editor.

9. Click **App service plan/Location**, and then click **Create new**.

10. From the **Location** list, select the region that is closest to your location.

11. In the **App Service plan** box, type **MyAppService**, and then click **OK**.

12. Click **Create**. Wait for the web app to be created. Click the newly created web app.

![20487D_Images](https://github.com/ialcaidef/Hosting-ASP.NET-Core-Web-APIs-in-Web-Apps/blob/master/Images/01.png)

13. In the newly created web app blade, in the **Deployment** section, click **Deployment Center**, select **FTP** and then Click **Dashboard**.

![20487D_Images](https://github.com/ialcaidef/Hosting-ASP.NET-Core-Web-APIs-in-Web-Apps/blob/master/Images/02.png)

14. In the **FTP** pane, click **User Credentials**, in the **username** box enter a unique name.

![20487D_Images](https://github.com/ialcaidef/Hosting-ASP.NET-Core-Web-APIs-in-Web-Apps/blob/master/Images/03.png)

![20487D_Images](https://github.com/ialcaidef/Hosting-ASP.NET-Core-Web-APIs-in-Web-Apps/blob/master/Images/05.png)

15. In the **Password** and **Confirm password** inputs, enter a new password.

    >**Note**: You will need these credentials for the next steps. Copy them to any code editor.

16. In the newly created web app, click **Overview**.

17. Open the Command Prompt window.

18. To change directory to **HostInAzure** folder, run the following command:

    ```bash
    cd [Repository Root]\Allfiles\Mod05\DemoFiles\HostInAzure
    ```

19. At the command prompt, paste the following command to create a new web app and then press Enter:

    ```bash
      dotnet new webapi --name BlueYonder.Hotels.Service --output "[RepositoryRoot]\Allfiles\Mod05\DemoFiles\HostInAzure"
    ```

20. Open File Explorer and browse to *[RepositoryRoot]***\Allfiles\Mod05\DemoFiles\HostInAzure**.

21. In the **Properties** folder, create a new folder **PublishProfiles**.

22. In the **PublishProfiles** folder, create a new file called **Azure** with the extension **.pubxml**.

23. Open the file in any code editor and paste the following XML content to define the publish settings:

    ```xml
    <Project>
        <PropertyGroup>
        <PublishProtocol>Kudu</PublishProtocol>
        <PublishSiteName>{Your App name}</PublishSiteName>
        <UserName>{Your FTP/deployment username}</UserName>
        <Password>{Your FTP/deployment password}</Password>
        </PropertyGroup>
    </Project>
    ```
    
    ![20487D_Images](https://github.com/ialcaidef/Hosting-ASP.NET-Core-Web-APIs-in-Web-Apps/blob/master/Images/04.png)

24. Replace the **PublishSiteName**, **UserName** and **Password** values with the values that you have copied earlier.

25. Save the file.

26. To point to your new web app folder, at the command prompt, paste the following command:

    ```bash
        cd [RepositoryRoot]\Allfiles\Mod05\DemoFiles\HostInAzure
    ```

27. To host your web app in an app service that you created in Azure, paste the following command:

    ```bash
        dotnet publish /p:PublishProfile=Azure /p:Configuration=Release
    ```

![20487D_Images](https://github.com/ialcaidef/Hosting-ASP.NET-Core-Web-APIs-in-Web-Apps/blob/master/Images/06.png)

![20487D_Images](https://github.com/ialcaidef/Hosting-ASP.NET-Core-Web-APIs-in-Web-Apps/blob/master/Images/07.png)
