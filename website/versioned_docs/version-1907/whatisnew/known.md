---
id: version-1907-known
title: Known Issues
original_id: known
---

## Known Issues in 1907

*   **AGGL-5484: Enrollment date gets updated to last sync time for the Chrome OS devices.**

    Enrollment date and time gets updated to the latest sync time for Chrome OS devices when the devices are retrieved from Google Cloud. It should instead read the actual device enrollment time shared in the Google cloud response.

*   **AGGL-5725​:App assignments cannot be saved when NSX is enabled.**

    When NSX is enabled, application assignment security groups cannot be saved.

    As a workaround, disable NSX, add app assignments, and re-enable NSX.

*   **AGGL-5744​: Approved Apps fails to get installed on the devices from Play Store intermittently on Xiaomi devices.**

    The apps approved on the UEM server are not visible intermittently for Xiomi devices when enrolled in to the Android Enterprise. 

*   **AGGL-5906​: Android Enterprise device creates device passcode instead of Work Profile passcode.**

    The reason hub shows notification to set the device passcode when the work profile passcode is sent is because the profile XML has both device passcode policy(com.airwatch.android.androidwork.passwordpolicy) and the work passcode policy (com.airwatch.android.androidwork.apppasswordpolicy)

    Select the "Change Work App Passcode" notification and set the passcode for the work enrolled device.

*   **AGGL-6014​: Single-user Staging does not work as expected.**

    Single-user Staging does not complete due to HMAC errors.

*   **AMST-17019 ​: Install context and detection criteria is not editable for new MSP version if previous version is deployed. **

    If a MSP is added to already deployed MSI, install context and detection criteria are not editable after saving despite being a new version in unknown status. 

*   **AMST-17022: Application Install failures are not updated in the UEM console.**

    Selective app list sample is not queued for app install failures and hence needs an app list sample to update the status. 

*   **AMST-17581: App status changes to "Not Installed" and "Installing" in the Apps tab. After the app uninstall fails, the status changes to "Not Installed" and execution failure.**

    SFD Client sends zero in the sample when the application uninstall is queued. This causes the app status on the console to change to not installed and subsequently install failure instead on uninstall failure.

*   **AMST-17591: File Exists displays incorrect version number.**

    File Exists criteria displays the version info that belongs to the "App Exists" criteria.

*   **AMST-17881: Profile payload modification does not work as expected.**

    If all configurations in new payloads are set to Not Configured, payload must revert to un-configured status. Currently we continue to show the payload highlighted in green bar, edit icon, trash icon, and so on.

*   **AMST-18107​: Application deployment criteria fails if quotes are used in the configuration.**

    Using the registry criteria or contingencies with quotation marks included in the configuration fails application deployment.

*   **AMST-18160: Add Contingencies header shows Add Criteria.**

    When adding contingencies the header / type text refers to "criteria." Ideally, the header  must display "Add Contingencies" and the type text would show "Contingency Type".

*   **AMST-18221: Restrictions profile blocks all the third- party cookies even if the profile has the cookies set to allow. **

    When the user sets a restriction policy and allows browser cookies the edge browser still blocks third party cookies. 

    As a workaround, use any other browser.

*   **AMST-18762 ​: Managed apps displays incorrect status message. **

    Assume managed apps with uninstallation failure remains in "pending removal" status. 

*   **ARES-8578: Last Action Taken does not update on Microsoft Store for Business application removal with the MAM count feature flag ON.**

    Application status does not update for BSP application.

*   **ARES-8427​: Single-user Staging does not work as expected due to HMAC errors.**

    Single-user Staging does not work as expected due to HMAC errors.

*   **CMCM-188249​: AirWatch Managed Content download does not work as expected. **

    contentavailable_search takes too long to respond.

*   **CMCM-188259: Content assigned to the child OG fails to get applied on the device if the category is created at the sibling OG.**

    AW Content must not be assigned to the sibling OG's with categories created at other sibling OG's.

    As a workaround, assign content to other sibling OG's or create category at the assigned OG.

*   **CMEM-185217: SEG configuration is displayed in the Admin panel**

    SEG MemConfig is displayed under **Monitor -> Admin Panel.**

*   **ENRL-1292: API event Notification fails to trigger on Device attribute change.**

    Event notification subscription is not triggered when configured for device attribute change or while changing the Organization group for device

*   **FCA-190413​: Hub configuration request cloud tenant ToS will not load or will delay while loading.**

    Hub Configuration request cloud tenant ToS pdf is not loading in Firefox and Chrome browser takes lot of time to load

    As a workaround, use chrome browser to go through the Terms of Services.

*   **PPAT-5464:Outbound proxies page in STR does not get refreshed automatically.**

    Deleting an outbound proxy from the STR list creates a duplicate entry in the UI.

    As a workaround, close the page and reload.


## Known Issues in 1905


*   **PPAT-3982: Customer can only have NSX configured at one OG at a time.**

    Syncing NSX on the second OG will wipe the security group settings from the first OG.

*   **PPAT-4817: Tunnel configuration is not displayed correctly while switching OGs.**

    When switching OGs, user interface shows incorrect tunnel configuration.The UI displays configuration from the original OG.

*   **PPAT-5382: Device traffic rules for Workspace ONE application is duplicated if the user sets the device traffic rules for Workspace ONE application and then runs Mobile SSO wizard from the getting started track.**

    Device Traffic Rules for Workspace ONE is duplicated instead of being skipped. 

    As a workaround, you can delete the duplicate entry. 

*   **PPAT-5388: Device Traffic rules can be misleading in a child OG that is not overridden if there are any rules for apps that exists at the parent level.**

    Applications do not show as they are managed by the parent.

*   **PPAT-4844: The UEM console allows same port for Per-App Tunnel and Proxy configuration.**

    There should be a validation for not allowing same ports if the same server is being used for both Proxy and Per-App Tunnel.

    As a workaround, configure Per-App Tunnel and Tunnel Proxy with different ports.

*   **AMST-17342​: Unable to remove FW rules.**

    Customers are unable to remove FW rules off of their devices on edit.

    As a workaround, delete or remove any profiles with rules to erase the configuration from the devices.

*   **ARES-6552: Application version sort does not work as expected.**

    **Other versions -> Sort By** version number in the UEM console does not work as expected.

*   **CMEM-185217: SEG MemConfig is displayed under Monitor -> Admin Panel.**

    SEG configuration should not be shown in the Admin panel.

*   **CMEM-184489: Sync Mailboxes status popup does not appear fine on the user interface.**

    Status popup is cut off from the user interface. 

*   **AMST-17297​: Customers are unable to edit the registry criteria as the app status remains  "Install command dispatched".**

    Install command gets processed when registry criteria has hkey_local_machine instead of HKLM. Ideally in such cases the install command is expected to fail.

    As a workaround, delete the application from the UEM console and add it back with appropriate detection criteria.

*   **AMST-17107: SFD task scheduler does not work as expected.**

    SFD task scheduler remains in the running status after the client upgrade. Any applications that gets queued after the upgrade is not processed till the SFD task scheduler is restarted.

    As a workaround, kill and restart the SFD task scheduler. This particular issue is an edge case since not all applications get stuck in the download in progress.

*   **AMST-17391: OOBE Blocking screen doesn't move automatically to the next page for RS3 devices.**

    The OOBE blocking screen fails to move automatically to the next page for RS3 devices. However users can click **Got It** button to continue with the w​orkflow. Also the setting 'Provision entities on windows OOBE enrollment' under 'Optional Prompt' does not work for RS3 devices.

*   **FCA-190511​: Mobile SSO wizard displays VMware tunnel setting status as "setup" instead of "Edit settings".**

    Even though the Mobile SSO wizard setup completes all the tunnel related configuration, the task status on the summary page does not show as "Edit settings".

*   **FCA-190415 : Bookmarks do not work as expected.**

    Favorite icon successfully adds a page to the bookmark list but fails to appear in the drop down. 

    As a workaround, refresh the page. 

*   **FCA-190417​: Navigation from the blueprint review tiles does not work as expected.**

    Administrator is navigated to the incorrect section from the AW Express blueprint review tiles.

    As a workaround,you can navigate using the breadcrumbs from the review page.

*   **AAPP-7212 ​: iOS Device SeedScript does not display the generation number.**

    Devices show as "iPad mini" and iPad Air" and does not display the generation number.

*   **AAPP- 7000: DEP page allows admins to choose Default Staging User managed at the Customer OG.**

    Administrators are able to see both the parent and child default staging user while configuring the DEP and may unknowingly select the wrong one. 

    As a workaround, Change the OG of any impacted devices, or re-enroll the device.

*   **AAPP- 6997: Custom B2B VPP applications is not displayed under promotions.**

    Search API does not currently return Custom B2B type for apps.

*   **CRSVC-4391: Changes to Bluecoat VPN profiles fail with error "Save failed - unable to fetch trusted certificates".**

    The integration between Workspace ONE UEM and Bluecoat leverages an authentication certificate seeded in the console and tenant identifier 'customer ID' input by an administrator in the VPN payload to initiate the integration. The seeded authentication certificate has expired which results in an error when the administrator attempts to make changes to the Bluecoat profile.

    At this time we have asked Bluecoat to provide a new certificate leveraging SHA-512 and we recommended that they offer tenant level certificates or vendor generated authentication certificates for added security. 

*   **FCA-190396: Admins are unable to accept the Terms of Use after console update.**

    Administrators are unable to log into the console.
