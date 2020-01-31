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

## Configuring & Assigning Device Enrollment Profiles

## Enrolling Devices Synced from Apple Business Manager

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
