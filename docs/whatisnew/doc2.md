---
id: doc2
title: Latest Releases
---
## What's new in 1907

**1907 for On-Premises Customers**: Workspace ONE UEM 1907 for on-premises customers contains all the features and resolved issues from the previous SaaS-only releases.

For more information on the features and resolved issues from these releases, see [VMware Workspace ONE UEM 1904 Release Notes](https://docs.vmware.com/en/VMware-Workspace-ONE-UEM/1904/rn/VMware-Workspace-ONE-UEM-Release-Notes-1904.html) and [VMware Workspace ONE UEM 1905 Release Notes](https://docs.vmware.com/en/VMware-Workspace-ONE-UEM/1905/rn/VMware-Workspace-ONE-UEM-Release-Notes-1905.html).


#### Workspace ONE UEM console

*   **We've improved logging back into the console after your session times out.**  
    The console now remembers whether you are a SAML or non-SAML user. When timed-out, SAML users can log back in without any clicks. Non-SAML users, with a remembered user name and password, see their credentials auto-populated on the screen and can log back in with one click. This improvement is enabled by default.  
    To learn more, see [Logging In to the UEM Console](../../1907/UEM_ConsoleBasics/GUID-AWT-LOGINTOCONSOLE.html).   

*   **Know if your APNs certificates are connecting over the HTTP/2 protocol.**  
    We've given you an option to manually conduct the test and check whether your APNs certificates are connecting over the HTTP/2 protocol.   
    To learn more, see [Checking APNs Connectivity over HTTP/2 Protocol](../../1907/UEM_ConsoleBasics/GUID-9BAE8236-9C00-41EA-AD2D-02E03E1DE0A0.html).  

*   **Device tags no longer show the tag color and the tag type in the console.**  
    Options for the device tag color and the device tag type are removed from the console.  

*   **Unassign a device tag from multiple devices in a one sitting.**  
    You can now unassign device tags from multiple devices at the same time.  
    To learn more, see [Unassign Tags from Multiple Devices](../../1907/UEM_Managing_Devices/GUID-0284EC69-DE9B-4FC4-A28D-9DB57517CD7C.html).  

*   **We offer a simplified integration with Adaptiva to support your peer-to-peer software distribution deployments.**  
    Workspace ONE UEM supports a new version of the Adaptiva server. For all existing customers, Workspace ONE UEM still supports the previous version of the Adaptiva server. To use the new integration, update your Adaptiva server and your AirWatch Cloud Connector to version 1907.  
    To learn more, see [Configuring Peer Distribution Software Setup with Adaptiva](../../1907/Peer-to-Peer_Distribution_Management/GUID-AWT-P2P-CONFIG-SETTINGS.html).   

*   **AirWatch Express got a new name. It's now called Workspace ONE Express.**  
    Workspace ONE Express has all the same functionality as AirWatch Express, but with a new name.   
    To learn more, see [Introduction to Workspace ONE Express](../../1907/WS1_Express/GUID-AWT-INTROAWEX.html).  

*   **We've improved privacy by adding a location data question to Workspace ONE Express.**  
    Privacy is important to our customers. Selecting Yes in the Getting Started survey prompts the user on their device if they choose to share the location data. If the user declines, then location data is not collected.  
    To learn more, see [Express Setup Survey](../../1907/WS1_Express/GUID-AWT-AWEX-SETUPINTROSURVEY.html).  

*   **Get a better idea of the batch import task status in Workspace ONE Express.**  
    You can now see the status of batch import tasks. Navigate to** Accounts > Users > Batch Status** to see the status of the batch import jobs you have already initiated.  
    To learn more, see [Batch Import Users or Devices](../../1907/WS1_Express/GUID-AWT-BATCHIMPORTUSERS.html).  

*   **Make the most out of your Telecom List View page with the new export option.**  
    We've given you an option to export your usage and roaming details in CSV and XLSX formats. The exported file is available for download in the **Monitor > Reports and Analytics > Exports** page.   
    To learn more, see [Plan Usage Details for Telecom Assets](../../1907/Telecom/GUID-AWT-PLANSMANAGEMENT.html).  

*   **We've enhanced our directory user status synchronization logic.**  
    The status of Administrator and Enrollment user accounts in the UEM console now syncs correctly with deactivations made to your Active Directory service provided the following assumptions. The user named in the **Bind User Name** option, located in **Groups & Settings > All Settings > System > Enterprise Integration > Directory Services** in the **Server** tab, must have Active Directory administrator privileges. The recycle bin must also be enabled using the Active Directory Administrative Center.  
    To learn more, see [Directory User Status Syncing](../../1907/UEM_ConsoleBasics/GUID-F2379F36-6BEB-43E1-8C8D-7DF83D1BB0E1.html).  

*   **LDAP configuration validation is now more comprehensive. Validate your LDAP configuration directly from the console.**   
    Administrators can now, at the time of Directory Services setup, validate directory users and user groups, and their attributes, even before adding them to the UEM Console. The enhanced capability helps avoid bad configurations that might arise due to incorrect Directory Services setup.  
    To learn more, see [Map Directory Services User Information](../../1907/Directory_Service_Integration/GUID-AWT-MAPDSUSERINFORMATION.html).  

*   **The Settings tab is removed from the Global Search results, which speeds up the search.**  
    If you choose to search for settings, initiate a search from the **Configurations** page. Navigate to **Groups & Settings > Configurations** and enter a keyword in the search text box.

<a id="Android" name="Android">**Android**</a>

*   **The configuration experience for Android public apps now lets you setup complex configurations supported by the OEM.  
    Our new updates include:**
    *   Support for nested bundle arrays.
    *   A better and simplified design with useful tooltips. 
    *   Choose to leave the unused application configuration options blank instead of deleting them from the UI.  
        ​To learn more, see [Assigning Applications for Android](../../1907/Application_Management-for-Android/GUID-AWT-ASSIGN-APPS-FP02.html).
*   **We've added programmatic migration workflows for moving your devices on legacy device administration to Work Profile.**  
    Migrate from your Android (Legacy) deployment to Android Enterprise(Formerly Android for Work) to gain more control and consistency across all OEM devices with the improved security and a better overall experience for employees with BYOD devices.  
    To learn more, see  [Android (Legacy) Device Administrator Migration](../../1907/Android_Platform/GUID-48D742FE-79FA-4134-9BB2-E80622099A07.html).   

*   **The improved Passcode profile provides better support for the native Android functionality.**  
    The Passcode profile for Android has been updated to support native features for Android 9.0\. You can now: 
    *   Force a separate passcode for the Work and personal side of the device.
    *   Increased the maximum amount of days for password expiration from 180 to 9999.
    *   Set additional biometric passcode options.   
        To learn more, see [Enforce Passcode Settings (Android )](../../1907/Android_Platform/GUID-AWT-PROFILE-PASSCODE.html).
*   **Keep your Work Managed and Corporate Owned Personally Enabled devices secure with an initial passcode.**  
    With the **Set Initial Passcode** option in the Passcode profile, you can now set an initial passcode at the device level on all deployed devices. After the deployment, it is possible to reset the passcode at the device level.  
    For more information, see Enforce Passcode Settings (Android) [Enforce Passcode Settings (Android )](../../1907/Android_Platform/GUID-AWT-PROFILE-PASSCODE.html).  

*   **The QR Code wizard now gives you more flexibility with system apps during device enrollment.**  
    For all your work-managed devices, enable system apps to keep non-critical system applications installed on your work-managed device, or select disable to remove these apps.  
    To learn more, see [Generate a QR Code Using the Enrollment Configuration Wizard](../../1907/Android_Platform/GUID-AWT-GENERATEQRCODEWITHENROLLCONFIGWIZ.html).

**<a id="Chrome OS" name="Chrome OS">Chrome OS</a>**

*   **Provide beta or development versions of Chrome OS and test the pre-release versions prior to general availability​.**  
    Determine if the devices will receive beta, development, or production builds of Chrome OS with the Release Channel field in the System Updates profile. This is useful for testing builds before pushing updates to your entire device fleet.  
    To learn more, see [Configure System Updates Profile(Chrome OS)](../../1907/Chrome_-OS_Platform/GUID-AWT-PROFILEDEVICE-SYSTEMUPDATES.html).

<a id="ios" name="ios">**iOS**</a>

*   **Enable data protection for your devices at all times**  
    We now give you an option whether or not to clear the device passcode when checking in a shared device.  
    To learn more, see [Configure Shared Devices](../../1907/iOS_Platform/GUID-AWT-CONFIGURESHAREDDEVICES.html). 
*   **Automatically convert on-demand apps to managed, if you choose to enable "Make App MDM Managed if User Installed"**  
    If you now install an app as unmanaged (e.g. through the App Store), the console automatically converts the app to managed when the **Make App MDM Managed if User Installed **setting is enabled regardless if the App Delivery Method is automatic or on demand.   
    To learn more, see [Add Assignment and Exclusions to applications](../../1907/Application_Management/GUID-AWT-FLEX-DPLYMNT-ADD.html). 

<a id="macOS" name="macOS">**macOS**</a>

*   **Rotate your recovery keys on-demand for better security compliance**  
    A new security enhancement is added to the Device Details and Self Service Portal where the FileVault Personal Recovery Key (PRK) is automatically rotated 15 minutes after it is accessed by the user or the administrator.  
    To learn more, see [Personal Recovery Key Rotation](../../1907/macOS_Platform/GUID-AWT-MACOS-ROTATERECOVERYKEY.html).   

*   **Control the restrictions for Smart card pairing on macOS 10.12.4 and later devices**  
    We've now added a new profile payload to configure the settings and restrictions for the Smart Card usage.  
    To learn more, see  [Configure a Smart Card Profile](../../1907/macOS_Platform/GUID-870D2CB4-1DE8-434F-9C8A-339CF248BAAE.html).   

*   **Restrict or allow capturing of screen recordings and screenshots**  
    We added a new restriction key that disables the user's ability to take screenshots of the display or capture a screen recording.  
    To learn more, see [Configure a Restrictions Profile](../../1907/macOS_Platform/GUID-AWT-MACPROFILERESTRICTIONS.html). 

<a id="MCM" name="MCM">**Mobile Content Management**</a>

*   **Select multiple files and delete them at the same time using the AirWatch Managed Content List View.**  
    AirWatch Managed Content List View now supports bulk file removal.  
    To learn more, see [Content Management List View](../../1907/MCM/GUID-AWT-CM-LIST-VIEW.html).  

**<a id="Tunnel" name="Tunnel">Tunnel</a>**

*   **We're getting ready for something new. The Workspace ONE Tunnel for Windows app needs a new framework and additional settings for its upcoming release.**  
    In the UEM console, you will see new settings referring to Workspace ONE Tunnel for Windows. Wait to use these additional settings till our new app is available.  
    To learn more, see [Configure Per-App Tunnel Profile for Windows Desktop App](../../1907/Tunnel_Linux/GUID-FBE6F3ED-401E-47E5-927D-081E62D74472.html).
*   **It's time to move your Safari Domains from iOS VPN Profile Payload to Device Traffic Rules setup.**  
    We've removed the Safari Domain section from the VPN Profile XML. If you are upgrading to 1907 from an older version, plan for a smooth migration strategy and move all your Safari Domains from iOS VPN Profile Payload to Device Traffic Rules setup. 

<a id="Window" name="Window">**Windows**</a>

*   **Looking to keep your Windows 10 devices configured to industry best practices? The Baselines feature is now available to all customers.**  
    Baselines allows you to keep your devices secure and aligned with industry standards such as CIS Benchmarks. With Baselines, you can set and manage your preferred configurations completely over the air without any dependency on VPN or your domain. You can also create custom baselines using GPO policies. New enhancements to Baselines include editing and deleting your custom baselines.  
    To learn more, see [Using Baselines](../../1907/Windows_Desktop_Device_Management/GUID-35F5B92C-9331-48B6-B9D1-69DB682368B3.html). 

## What's new in 1905

**Workspace ONE UEM console**

*   **Get the most out of AirWatch Express with the new default configurations​.**
        *   Location collection is now turned on by default for new AirWatch Express deployments. . End users will now receive a confirmation prompt on their devices asking for permission to collect location data. If granted, location data appears in Device Details on the UEM console.
        *   App Catalog is now enabled by default for new AirWatch Express deployments. After enrollment, the App Catalog webclip appears on the device home screen and allows end users to see all assigned apps.
        *   Quickly unlock iOS devices placed in Lost Mode from the actions toolbar on the Device Details view.
    *   Several configuration improvements have been made to AirWatch Express that impacts location collection, app catalog, and lost mode for the iOS devices.
    *   **Retrieve your user accounts and groups with the all new SCIM API.**  
        A new SCIM API helps retrieve all the groups that a user belongs to. 
    *   **Auto-approve your applications from the Office 365 Getting Started wizard.**  
        The Office 365 Getting Started Wizard lets you automatically approve Office 365 apps for Android Enterprise. This is now the normal flow.
    *   **Export your reports to XLSX files, just like CSV files.**  
        In addition to exporting CSV files, you can now export list views and reports as XLSX files. With this new choice, you can avoid the formatting issues caused by CSV formats.

**Workspace ONE Intelligent Hub**

*   **Easily activate your Hub Services if you are already using VMware Identity Manager and Workspace ONE UEM.**  
        You can now easily enable Hub Services if you are already using VMware Identity Manager and Workspace ONE UEM.  
        Just enter your existing VMware Identity Manager URL to activate Hub Services. No need to reenter the admin user credentials again. We use the one you already provided to link VMware Identity Manager and Workspace ONE UEM.

**<a id="iOS" name="iOS">iOS</a>**

*   **Start reporting on both physical SIMs and eSIMs with the new dual SIM support.**  
        Admins can now report on both physical SIMs and eSIMs configured on supported iOS devices like the iPhone XR, XS and XS Max.

    <a id="MCM" name="MCM">**Mobile Content Management**</a>

*   **Add wildcard values to stop your users from creating manual repositories and sub folders.**  
        You can now use the wildcard character (*) at the beginning and the end of the file path to stop your users from creating manual repositories and sub folders using the manual template.

**<a id="Rugged" name="Rugged">Rugged</a>**

*   **Add apps to the Launcher profile with the ease of automation.**  
        You can now create dynamic rules to automatically whitelist apps added to a Launcher profile. These rules support wildcard characters in the App Field. After you add a wildcard, the app icon displays as a bundle of apps and appear in the Launcher in the available space. You do not need to republish the app every time you add a new app.
*   **We've extended Content Delivery Network (CDN) to VMware Workspace ONE Launcher.**  
        Content Delivery Network (CDN) is now extended to VMware Workspace ONE Launcher.During enrollment, when the Launcher is pushed to the device it is pushed through CDN instead of Device Services. This improves the performance of Launcher delivery to devices and reduces the server load when new version of Launcher is deployed.

<a name="Windows" style="background-color: rgb(255, 255, 255);">**Windows**</a>

*   **Make the most out of your Dell devices with the updated BIOS profile and Dell Command | Monitor integration.**  
        You no longer need to manually push Dell Command | Monitor to your Windows Desktop devices to use the BIOS profile. When you push the profile to your devices, Workspace ONE UEM automatically pushes Dell Command | Monitor to the devices.
*   **Give knowledge to the users. Enable a progress display for Windows Desktop devices enrolling using the Out of the Box Experience (OOBE) workflow.**  
        The new progress display informs the user what is happening behind the screen during the OOBE enrollment. You can also allow your users to skip OOBE after a specific timeout period.
*   **End-user devices no longer require Intelligence Hub to use the Windows Desktop Antivirus profile.**  
        Now it is easier than before to keep your Windows Desktop devices secure with the Windows Defender as we no longer require agent with the updated Antivirus profile for Windows Desktop devices.

*   **Devices have a huge number of attributes associated. Harness the power of Sensors to target the specific devices you want.**  
        Windows Desktop devices have tons of attributes to remember such as hardware, OS, certificates, patches, apps, and more. To track all these attributes, we created Sensors. <span style="font-size:11.0pt;font-family:&quot;Calibri&quot;,sans-serif;
        mso-fareast-font-family:Calibri;mso-fareast-theme-font:minor-latin;mso-ansi-language:
        EN-US;mso-fareast-language:EN-US;mso-bidi-language:AR-SA">Now you can create a sensor for a specific attribute and view this data in Workspace ONE Intelligence by creating visualizations on dashboards and customizing reports.”</span>
