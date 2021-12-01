
1. On the computer where you have the ASP.NET project open in Visual Studio, right-click the project in Solution Explorer, and choose **Publish**.

   If you have previously configured any publishing profiles, the **Publish** pane appears. Click **New** or **Create new profile**.

1. Select the option to import a profile.

   ::: moniker range=">=vs-2019"
   In the **Publish** dialog box, click **Import Profile**.
   ::: moniker-end
   ::: moniker range="vs-2017"
   In the **Pick a publish target** dialog box, click **Import Profile**.
   ::: moniker-end

   ![Choose Publish](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. Navigate to the location of the publish settings file that you created in the previous section.

1. In the **Import Publish Settings File** dialog, navigate to and select the profile that you created in the previous section, and click **Open**.

   ::: moniker range=">=vs-2019"
   Click **Finish** to save the publishing profile, and then click **Publish**.

   Visual Studio begins the deployment process, and the Output window shows progress and results.

   If you get an any deployment errors, click **Edit** to edit settings. Modify settings and click **Validate** to test new settings. If the host name is not found, try the IP address instead of the host name in the **Server** and **Destination URL** fields.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Visual Studio begins the deployment process, and the Output window shows progress and results.

   If you get an any deployment errors, click **Settings** to edit settings. Modify settings and click **Validate** to test new settings. If the host name is not found, try the IP address instead of the host name in the **Server** and **Destination URL** fields.
   ::: moniker-end

   ![Edit settings in the Publish tool](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
