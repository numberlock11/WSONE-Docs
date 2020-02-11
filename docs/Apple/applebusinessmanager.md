---
id: applebusinessmanager
title: Apple Business Manager
---

# Overview

Apple Business Manager is an Apple portal for enterprise administrators to manage the setup, configuration, and distribution of their organization's devices, apps & books, and users in a single location. Apple Business Manager integrates with Workspace ONE UEM to make it easy to enroll devices and deploy content with advanced capabilities.

The three primary capabilities available through Apple Business Manager and its integration with Workspace ONE UEM are the ability to manage

+ [Devices](#Devices)
+ [Apps](#Apps)
+ [Users](#Users)

Previously, the capabilities of Apple Business Manager were achieved separately through the Device Enrollment Program (DEP) and Volume Purchase Program (VPP) portals. Upgrading from these to portals to Apple Business Manager consolidates the management features, and the DEP and VPP portals will no longer be available to manage devices, assignments, apps purchases, or manage content. As of December 2019, this migration is mandatory for all organizations using the legacy DEP and VPP portals.

For more information, review Apple's [documentation for Apple Business Manager](https://www.apple.com/business/docs/site/Apple_Business_Manager_Getting_Started_Guide.pdf) or contact your Apple representative.

# Devices

Apple Business Manager, like the DEP portal, allows admins to track devices purchased by their company and associate them with Organization Groups in Workspace ONE UEM. By doing this, admins can configure where and how these devices will be onboarded based on the needs of their organization. There are several customizable options admins can configure to define this process. By going through these steps, admins gain added functionality for their devices such as

+ Prevent removal of MDM profile on a device by users
+ Automatically and remotely provision devices in Supervised mode. Supervised mode is reserved for devices considered company owned and allow access to additional security and configuration settings. See our [supervision documentation](SUPERVISION-DOCUMENTATION) for all added functionality
+ Streamline the enrollment process by skipping unnecessary Setup Assistant options during onboarding
+ Waiting until a device is fully configured with assigned apps and profiles prior to users reaching the Home Screen


In order to achieve these benefits, the following links will help walkthrough:

+ Setting Up the Device Integration between Apple Business Manager and Workspace ONE UEM
+ Configuring & Assigning Device Enrollment Profiles
+ Enrolling Devices Synced from Apple Business Manager

## Setting Up the Device Integration between Apple Business Manager and Workspace ONE UEM

In order to sync devices into Workspace ONE UEM for enrollment configuration, trust must be established between an organization's Apple Business Manager portal and a Workspace ONE UEM organization group. To achieve this, an admin completing tasks in both the Workspace ONE UEM console and Apple Business Manager portal. All steps for these tasks, explained in detail, below must be completed and saved successfully in a single browser session. After saving, an admin can refresh their browser to confirm the setup has been successfully completed.


### Prerequisites

+ Access to an Apple Business Manager account with Adminstrator or Device Manager privileges –, If needed, review how to get started enrolling in Apple Business Manager [here](https://www.apple.com/business/docs/site/Apple_Business_Manager_Getting_Started_Guide.pdf).
+ If the Workspace ONE UEM console server is on-premise, ensure that the server is set up to communicate with _mdmenrollment.apple.com_ on port 443
+ Access to a Workspace ONE UEM console with the appropriate role such as Console Administrator

### Steps

 Integrating Apple Business Manager with Workspace ONE UEM is achieved by downloading a public key (.pem) that allows Workspace ONE UEM and Apple to mutually authenticate with each other in order to sync devices. To complete this authentication:

1. Log into the Workspace ONE UEM console and navigate to *Groups & Settings > All Settings > Devices & Users > Apple > Device Enrollment Program* and select *Configure*. A *Device Enrollment Program* window appears.
2. Download the public key by selecting the *MDM_DEP_PublicKey.pem* file. Save the public key in a convenient location. This is used to complete the DEP setup process.
3. Select the [Apple Deployment Programs](business.apple.com) link or open your Apple Business Manager portal by logging in with your Managed Apple ID at *business.apple.com*.
4. Sign in with your organization's managed Apple ID credentials
5. In Apple Business Manager, navigate to *Settings > Device Management Settings* and select *Add MDM Server*.
6. Set an MDM Server Name, check whether to allow the MDM server to release devices, upload the public key (.pem) previously downloaded in step 2, and click *Save*.
7. Select *Download Token* and save the token to a convenient location.
8. Return to the Workspace ONE UEM console and upload the saved token to the required Token step and click *Next*

## Configuring Device Enrollment Profiles

Once a trusted connection has been created between Apple Business Manager and Workspace ONE UEM, enrollment profiles are required to determine how devices in Apple Business Manager should enroll into Workspace ONE UEM. Follow the steps below to complete this.

### Prerequisites

+ Complete all steps in the above section for [**Setting Up the Device Integration between Apple Business Manager and Workspace ONE UEM**](#Setting-Up-Device-Integration-Apple-Business-Manager-Workspace-ONE-UEM)

### Steps

NOTE: If an admin is creating their first device enrollment profile, this is done immediately after setting up the integration to Apple Business Manager and begins with step 2 below. All subsequent profiles created will begin with step 1.

1. Log into the Workspace ONE UEM console and navigate to **Groups & Settings > All Settings > Devices & Users > Apple > Device Enrollment Program** and select **Add Profile**
2. Choose whether to enable Custom Enrollment. For more information, please review the [Custom Enrollment](#Custom-Enrollment) section.
+ **Custom Enrollment** **ON** will invoke Workspace ONE UEM enrollment screens during the device onboarding (iOS 13+ and macOS 10.15+ only). This settings may include Terms of Use acceptance, modern auth including multi-factor auth, or any branding settings applied.
+ Custom Enrollment OFF will use Apple's enrollment screens
3. Configure the **Authentication** settings to determine whether the user should be prompted for credentials during the device onboarding experience.
+ **Authentication** **ON** will prompt for user credentials during onboarding and enrolls directly to an end users. Admins will need to configure the following options:

| Setting | Description |
| --- | --- |
| Device Ownership Type | Determines the ownership type of the device upon enrollment, which can be either Corporate - Dedicated, Corporate - Shared, or Employee Owned.|
| Device Organization Group | Select the Organization Group where your end users will authenticate and begin enrollment.<br> <br> End users will authenticate using either their Active Directory credentials or basic Workspace ONE UEM credentials depending on which authentication type you have enabled under **Enrollment** settings at this Organization Group. <br><br> If **Custom Enrollment** is **ON**, other Enrollment settings will also be required to complete enrollment. Review the [Custom Enrollment](#Custom-Enrollment) section for more information.|
| Custom Prompt | Turn **ON** the **Custom Prompt** to enable custom text to appear on the device authentication screen during the Setup Assistant. Authentication occurs when end users are prompted for their credentials. <br> <br> For Apple School Manager, turn Off Custom Prompt if you are deploying shared iPads. <br> <br> This option will only appear on the device if **Custom Enrollment** is **OFF**. This is because the **Custom Prompt** is part of Apple's authentication screens which are not shown during **Custom Enrollment**.|
| Message Template | Select a message template to send as a Custom Prompt. (Supported for English-language only.) This option is not available when **Custom Prompt** is **OFF**. |

+ Authentication OFF will not prompt for user credentials. This implies the device intends to be staged with user authentication taking place at a later time. Admins will need to configure the following options:

| Setting | Description |
| --- | --- |
| Default Staging User | Select the staging enrollment user to automatically assign and enroll to the device. Each device assigned this profile will be enrolled to this staging user until the device is checked out to an end user via single or multi-user staging. |
| Device Ownership Type |	Determines the ownership type of the device upon enrollment, which can be either Corporate - Dedicated, Corporate - Shared, or Employee Owned. |
| Device Organization Group | Device Organization Group	Select the organization group where your devices are enrolled. Since authentication and custom enrollment are disabled, no enrollment screens will be presented on the device.|

4. Configure the **MDM Features** to set the behavior of the device after authentication and custom enrollment steps are complete.

| Setting | Description |
| --- | --- |
| Profile Name | This is the name that will appear for the enrollment profile in Workspace ONE UEM in list views, device assignments, and when setting default profiles.|
| Department  |  Displays on enrolling devices in the *About* section of the *Remote Management* screen to offer additional information for who is managing the device within the company. |
| Support Number  | Displays on enrolling devices in the *About* section of the *Remote Management* screen to offer additional information for how to contact the department or organization managing the device.  |
| Require MDM Enrollment | If enabled, the user is forced to enroll  and apply an MDM profile during the initial onboarding. Otherwise, the device cannot be activated. If disabled, the Setup Assistant on the device will give an option to skip the MDM enrollment. <br><br> For iOS 13+ devices, this option is always enforced and MDM enrolled is required for all devices. |
| Supervision | If enabled, the device will automatically be supervised over-the-air upon going through the Setup Assistant. <br><br> For iOS 13+ devices, this option is always enforced and supervision is required for all devices. |
| Lock MDM Profile  | If enabled, the option to remove the MDM profile is not available to the end user via the UI on the device. This setting can only be toggled if **Supervision** is enabled. |
| Anchor Certificate | If enabled, admin can upload certificates to be used as trusted anchor certificates (e.g. root certificates) when evaluating the trust of the connection to the MDM server URL. Otherwise, only the devices built-in root certificates are used. |
| Device Pairing | Supervised only. If disabled, the devices is not allowed to pair with other devices with the exception of the host device that performed the supervision. <br><br> Starting in iOS 13, this option is deprecated and always enabled. |
| Await Configuration | If enabled, onboarding devices will be held in Setup Assistant until all initial commands are confirmed as successfully sent to the device. <br><br> This allows for these commands to process prior to the user getting access to the Home Screen. |
| Auto Advance Setup | If enabled, the tvOS device will automatically skip all Setup Assistant screens and progress to the Home Screen where profiles and apps can be installed. If the device has a network connection via ethernet, this requires zero user touch to complete. Only available for tvOS devices. |

5. Configure which Setup Assistant screens the device should skip. Some screens are shared across platforms while others are unique to specific hardware. Below are the skippable options and their platforms

| Screen | Description | Platform |
| ------ | ----------- | -------- |
| Passcode | If skipped, user does not see the screen to setup a device passcode. | iOS 7.0|
| Biometric ID | If skipped, user does not see the screen to set up the devices biometric ID such as TouchID or FaceID. | iOS 8.1, macOS 10.12.4 |
| Location Services | If skipped, user will not see the screen to enable or disable Location Services during the Setup Assistant. The device will default to disabled if skipped. | iOS 7.0, macOS 10.11 |
| Restoring from Backup | If skipped, the user will not see the screen to restore the device from a backup. | iOS 7.0, macOS 10.9 |
| Move from Android | If skipped, user does not see the Move from Android option in the Restore pane on iOS Setup Assistant. Setting is automatically removed if Restore pane is skipped entirely. | iOS 9.0 |
| Sign in with Apple ID and iCloud | If skipped, user does not see the screen to set up their Apple ID. | iOS 7.0, tvOS 10.2, macOS 10.9 |
| Terms of Use and Conditions | If skipped, the user does not see the screen to accept Apple's Terms and Conditions.  | iOS 7.0, tvOS 10.2, macOS 10.9 |
| Siri | If skipped, the user does not see the option to enable Siri. This disables Siri by default if skipped. | iOS 7.0, tvOS 10.2, macOS 10.12 |
| Diagnostics | If skipped, user does not see the screen to send app analytics and usage data to Apple.| iOS 7.0, tvOS 10.2, macOS 10.9 |
| Registration | If skipped, the user is not see the screen to register their macOS device. | macOS 10.9 |
| Apple Pay | If skipped, the user does not see the screen to set up Apple Pay in Setup Assistant. | iOS 8.1, macOS 10.12.4 |
| Zoom | If skipped, the user does not see the option to set up the Zoom settings.  | iOS 8.3 |
| FileVault 2 | If skipped, user does not see the screen to set up FileVault. | macOS 10.10 |
| Display Tone | If skipped, user does not see the screen to set up DisplayTone. | iOS 9.3.2, macOS 10.13.6 |
| Home Button Sensitivity | If skipped, user does not see the "Meet the New Home Button" screen on iPhones 7, iPhone 7 Plus, iPhone 8, and iPhone 8 Plus. | iOS 10.0 |
| Tap to Set up | If skipped, the user does not see the Tap To Set Up option about using an iOS device to set up your Apple TV. | tvOS 10.2 |
| Screen Saver | If skipped, the user will not see the screen with information on using aerial screensavers. | tvOS 10.2 |
| Keyboard | If skipped, the user will not be prompted to select a keyboard preference during Setup Assistant. | iOS 11.0 |
| Onboarding | If skipped, the user is will not see the on-boarding informational screens for user education (e.g. Go Home, Cover Sheet, Multitasking & Control Center) in Setup Assistant. | iOS 11.0 |
| Watch Migration |  If skipped, the user does not see the screen to migrate their Apple Watch data. | iOS 11.0 |
| iMessage and FaceTime | If skipped, user does not see the option to set up iMessage and FaceTime in Setup Assistant. | iOS 12.0 |
| Software Update | If skipped, the user does not see the mandatory Software Update screen during Setup Assistant. | iOS 12.0 |
| Screen Time | If skipped, the user does not see the screen learn about Screen Time options. | iOS 12.0, macOS 10.15 |
| SIM Setup | If skipped, the user does not see the option to configure their SIM card settings. | iOS 12.0 |
| Welcome | If skipped, the user does not see the Get Started screen during Setup Assistant. | iOS 13.0 |
| Express Language | If skipped, the user does not see the screen to select an Express Language. | iOS 13.0 |
| Preferred Language | If skipped, the user does not see the screen to select a Preferred Language. | iOS 13.0 |
| Device To Device Migration | If skipped, user does not see the screen to migrate data from another device. | iOS 13.0 |
| Choose Your Look | If skipped, user does not see the Choose Your Look screen during Setup Assistant. | iOS 13.0, macOS 10.14 |
| iCloud Analytics | If skipped, user does not see the screen to allow iCloud Analytics. | macOS 10.12.4 |
| iCloud Documents and Desktop | If skipped, user does not see the screen to allow syncing iCloud Documents and Desktop | macOS 10.13.4 |
| TV Home Screen Sync | If skipped, the user does not see the Apple TV home screen layout sync. | tvOS 10.2 |
| TV Provider Sign In | If skipped, the user does not see the screen to sign into a TV provider. | tvOS 11.0 |
| Where is this Apple TV? | If skipped, the user does not see the screen to choose where the Apple TV is located (e.g. living room, bedroom, office). | tvOS 11.4 |
| Privacy | If skipped, the user does not see the screen to acknowledge Apple's privacy messaging. | iOS 11.13, tvOS 11.13, macOS 10.13.4 |
| Primary Account Setup | If skipped, the the user will not be prompted to create a user account and will need to login with directory credentials to complete the enrollment process. You must also define an Administrator account in the **Admin Account Creation** section. | macOS 10.11 |

6. If the admin chose not to skip the macOS **Primary Account Setup** screen in Setup Assistant, the admin must set up the Primary User Account for the device.

| Field | Values | Description | Version |
| ----- | ------ | ----------- | ------- |
| Account Type | <ul><li>Standard</li><li>Adminstrator</li></ul> |  |  |

7. Configure whether to sync all devices and assign the enrollment profile to newly synced devices.

| Setting | Description |
| ------ | ----------- |
| Sync Now and Assign To All Devices | Devices added to Apple Business Managed must be synced into Workspace ONE UEM. <br><br> If **YES** is selected, all devices currently assigned to this MDM server will be synced into Workspace ONE UEM and assigned this enrollment profile. <br><br> If **NO** is selected, admins can sync devices and assign profiles at a later time. |
| Auto Assign Default Profile | This setting means this profile will be automatically assigned to any devices synced in the future. Once a default profile is set, admins are not required to manually assign profiles to every new device. <br><br> If **YES** is selected, all the devices synced in the future will automatically get assigned the profile defined in the wizard. <br><br> If **NO** is selected, you can define a default profile on the Apple Enrollment Program page at a later time. |

**NOTE:** Once a device is synced in and assigned the *Default Enrollment Profile*, the assigned profile can only be changed by following the steps in [Assigning Enrollment Profiles to Devices](#Assigning-Enrollment-Profiles-to-Devices)

8. Click Save to create the enrollment profile.

9. Repeat this process using the **Add Profile** option on the **Device Enrollment Program** settings page to create multiple enrollment profiles.

## Syncing Devices from Apple Business Manager

Once enrollment profiles are created to determine how devices from Apple Business Manager should enroll into Workspace ONE UEM, the devices associated to the MDM server must be synced into Workspace ONE UEM. Follow the below steps to complete this.

### Prerequisites

+ Complete all steps in the above section for [**Configuring Device Enrollment Profiles**](#Configuring-Device-Enrollment-Profiles)
+ Assign devices to configured MDM Server in Apple Business Manager

### Steps

There are two ways to sync devices from Apple Business Manager into Workspace ONE UEM. Each method behaves differently and is meant for a unique purpose. Below are the two options and their descriptions.

If you have already completed a **Fetch All Devices** to sync in all devices for a given MDM server token, proceed to step 2. If this is a first time set up of the MDM server token, proceed to step 1.

1. Navigate to **Groups & Settings > All Settings > Devices & Users > Apple > Device Enrollment Program** and select **Fetch All Devices**.

2. Navigate to **Devices > Lifecycle > Enrollment Status** or select **View Enrollment Status Page** from the **Device Enrollment Program** settings page in step 1.

3. Select **Add > Sync Devices**

| Option | Description | Location |
| ------ | ----------- | -------- |
| Fetch All Devices | This option will sync all devices in Apple Business Manager assigned to the uploaded MDM server token. This option should be used immediately after uploading the MDM server token to perform the first sync. It can be a resource intensive request and should only be used infrequently.| Groups & Settings > All Settings > Devices & Users > Apple > Device Enrollment Program |
| Sync Devices | This option will request only the latest changes to devices added, removed, or edited in Apple Business Manager. This is the preferred method for all sync requests after the initial sync for all devices. | Devices > Lifecycle > Enrollment Status > Add > Sync Devices |

**NOTE:** These options will only appear if an MDM server token is configured at the organization group.

## Assigning and Removing Enrollment Profiles to Devices

In Workspace ONE UEM, assigning enrollment profiles is required for an onboarding Apple devices to enroll. Only one enrollment profile can be assigned to a device, and the profile can be automatically assigned using a default profile or manually assigned by the admin. Follow the steps below to complete the assigning of enrollment profiles.

### Prerequisites

 + Complete all steps in the above section for [**Syncing Devices from Apple Business Manager**](#Syncing-Devices-from-Apple-Business-Manager)

### Steps to Assign an Enrollment Profile

1. Navigate to **Groups & Settings > All Settings > Devices & Users > Apple > Device Enrollment Program**

2. Select a *Default Enrollment Profile* to assign to newly synced devices. This will automatically assign the selected profile to new devices. This will have no affect to already synced devices.

**NOTE:** Admins may also select None as an option. This will result in no enrollment profile being assigned to newly synced devices. Admins will need to assign a profile to these devices prior to onboarding.

3. Navigate to **Devices > Lifecycle > Enrollment Status**

4. Select at least one device in the list view

5. Select **More Actions > Assign Profile**

6. Select an enrollment profile from the dropdown and **Save**.

### Steps to Remove an Enrollment Profile

1. Navigate to **Devices > Lifecycle > Enrollment Status**

2. Select at least one device in the list view

3. Select **More Actions > Remove Profile**

4. Review the changes and **Save**.

## Configuring Custom Enrollment Options

Custom Enrollment is a new set of enrollment options available for iOS 13 and macOS 10.15 or greater devices added to Apple Business Manager. In traditional automated device enrollment, all onboarding screens were built into the Apple operating system. With Custom Enrollment, Workspace ONE UEM has the ability to display any web based enrollment screen.

Custom enrollment supports a subset of enrollment options compared to standard device enrollment via the Intelligent Hub or Safari web view. Custom enrollment supports the following optional settings:

+ Requiring Terms of Use acceptance
+ Modern authentication
+ Multi-factor authentication
+ Company branding

**NOTE:** These settings will take effect for all enrollments at the organization group. For more detailed guides for each setting, review our [Enrollment Settings](#Enrollment-Settings) guide.


### Prerequisites

+ Custom Enrollment enabled in an enrollment profile and assigned to Devices

### Steps

**NOTE:** These steps are all optional and can be completed in any order.

+ Terms of Use acceptance
  1. Navigate to **Groups & Settings > All Settings > General > Enrollment > Terms of Use**
  2. Set **Require Enrollment Terms of Use Acceptance** to **Enabled**
  3. Select **Add New Enrollment Terms of Use**
  4. Configure a **Name** and any other settings desired
  5. Add text to the message that will be presented to the user.
  6. Click **Save**.

+ Modern authentication
  1. Navigate to **Groups & Settings > All Settings > Device & Users > General > Enrollment > Authentication**
  2. Check option for *Directory* in **Authentication Mode(s)**
  3. Navigate to **Groups & Settings > All Settings > System > Enterprise Integration > Directory Services**
  4. Ensure your preferred directory settings are configured. For more detail on how to do this, review our [Directory Services](#Directory-Services) documentation.

+ Multi-factor authentication
  1. Navigate to **Groups & Settings > All Settings > Device & Users > General > Enrollment > Authentication**
  2. Toggle **Devices Enrollment Mode** to *Registered Devices Only*
  3. Toggle **Registration Token Type** to *Two-Factor*

+ Company branding
  1. Navigate to **Groups & Settings > All Settings > System > Branding**
  2. Configure preferred branding settings


# Apps

Apple Business Manager allows admins to select, purchase, and assign public or custom applications to Organization Groups in Workspace ONE UEM for deployment to devices. This was previously part of the VPP portal or redemption code purchases. Workspace ONE UEM can sync in applications configured in Apple Business Manager and assign them to devices for deployment. The following will help walkthrough:

+ Setting Up Application Sync between Apple Business Manager and Workspace ONE UEM
+ Deploying Applications to Devices with Device Based Licenses (Serial Number)
+ Deploying Applications to Devices with User Based Licenses (Apple ID)
+ Deploying Applications to Devices with Redemption Codes
+ Monitoring & Updating Deployed Applications

# Users

Apple Business Manager leverages Managed Apple IDs or Apple IDs generated on behalf of employees through federation to an external identity provider such as Azure Active Directory. These Managed Apple IDs allow users to sign into devices with a corporate identity on company owned or personal devices. This is primarily done today to achieve [User Enrollment](LINK TO USER ENROLLMENT). The following will help explain:

+ How are Managed Apple IDs Used
+ How to Create Managed Apple IDs
