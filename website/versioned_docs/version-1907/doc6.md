---
id: version-1907-doc6
title: Boxer
original_id: doc6
---
Introducing VMware Workspace ONE Boxer, a faster, smarter email, calendar and contacts app that can be configured to the unique way you work.
With tools like custom swipe gestures and quick-reply templates, quick sharing of calendar availability and more, Boxer is the most efficient way to manage your email. Get more done in less time with Boxer!

**Modern Email, Calendar and Contacts in a Single App**
Productivity never looked so good. With an intuitive design built for the modern professional, Boxer helps you easily conquer your email, manage your calendars, and find colleagues quickly on-the-go.

**Intelligent, Configurable Inbox to Fit the Unique Way You Work**
Boxer helps you work smarter and faster than ever with features like bulk actions, configurable quick replies, custom swipe gestures, a send availability feature you have to see to believe, and many more.

**Handling Your Day is a Breeze**
Full-featured calendar management is just a tap away, keeping you on top of your schedule. Easily create and manage events, view calendar attachments, send meeting invites and view availability inside of Boxer.

**Single Tap Dial into Conference Calls**
Another phone conference? Say goodbye to flipping back and forth to enter an access code or meeting number on your mobile device. With Boxer, you can instantly dial into conferences with a single tap!

**Protect Your Data and Your Peace of Mind**
Boxer ensures your business stays your business. Boxer is built to support some of the most security-conscious organizations in the world. But great security doesn't have to come with an impossible user experience. With touch ID and PIN support, you can access the things you need in an instant.


## Pre-Requisites

### Console Requirements
* Workspace ONE UEM console 9.0 and higher

### Supported Devices
iOS | Android
------------ | -------------
iOS 10 and higher | Android Version 5.0 and higher

### Supported Email Infrastructure
* Supports the following email infrastructures for Boxer integration:
* iOS – G Suite, 2010, 2013, 2016, Office 365, IBM Notes Traveler version 9.0.1.
* Android – G Suite, 2010, 2013, 2016, Office 365, IBM Notes Traveler version 9.0.1.
* Requires a Public trusted SSL certificate such as Symantec, GoDaddy, Verisign.

## Capabilities

### Enrollment
You can use Workspace ONE Boxer on devices enrolled and managed in Workspace ONE UEM or on iOS and Android devices using standalone enrollment.

Typical enrollment uses the Workspace ONE Intelligent Hub or the AirWatch Container to enroll the device into Workspace ONE UEM. You can also enroll devices through Workspace ONE step-up enrollment.

Standalone enrollment is unique to Workspace ONE Boxer. This enrollment method allows end users to download the Workspace ONE Boxer app from the App Store or the Google Play Store without enrolling first. When the end user configures Workspace ONE Boxer, they must provide their login credentials such as their user name, password, server URL, and group ID.

Standalone Enrollment supports (optional) Workspace ONE UEM Autodiscovery that can be configured on the UEM console. Autodiscovery system allows end users to enroll devices to environments and organization groups (OG) using their email addresses.

Workspace ONE UEM does not support Boxer web-enrollment and only publishing Boxer as a managed application.

For more information on the Autodiscovery setup and configuration, see the VMware Workspace ONE UEM Mobile Device Management Documentation.

>Note:
The server URL and user group ID are pre-populated on the end-user devices from the Autodiscovery Service during standalone enrollment.

### S/MIME
As an admin, you can upload S/MIME certificates from the UEM console (v9.0+). End users can upload the certificates to the Self Service Portal (SSP) or can send the certificates as email attachments for the installation on their device. To allow users to decrypt and view emails that are encrypted using expired S/MIME encrypted emails, upload the expired certificate at Accounts > User > Edit > Advanced > Certificates > Old Encryption Certificate. Once uploaded, the device users can view the expired certificate. Navigate to Boxer > Settings > Account > SMIME > Sign and/or Settings > Account > SMIME > Encrypt.

>Note:
An email user can have an S/MIME certificate that has multiple email addresses. You can scan such certificate that has multiple identities through a list of addresses for signing and encryption.
Historical S/MIME Certificates

You can decrypt and read old S/MIME emails that have been encrypted with older certificates of encryption. You can parse old certificates from different sources, store those certificates, and ensure that these certificates are processed properly so that old emails can be successfully read.

### Common Criteria Certification
Workspace ONE Boxer version 5.4 is declared as a National Information Assurance Partnership (NIAP) Common Criteria evaluated product. It has been certified in compliance with the international security standard for the application software, defined under the Common Criteria Recognition Arrangement (CCRA). Boxer is the first email client to receive the international Common Criteria security certification.

For more information about setting up Workspace ONE Boxer in complete NIAP certified mode, see https://www.niap-ccevs.org/Product/Compliant.cfm?PID=10840.

### Enterprise Content Support for Boxer
Enterprise Content integrates a part of the VMware Workspace ONE Content application with Boxer to browse online repositories. Users can view email attachments, attach files to emails from online repositories, and save attachments from emails to online repositories. To access online repositories, you must configure the supported repositories in the UEM console. For information about the configuration of the enterprise content, see Enterprise Content section in Application Configuration for Workspace ONE Boxer.

Supported features of Enterprise Content:
* Enterprise Content supports the following online repositories:
* SharePoint
* Network File System
* SharePoint in Office 365.
* OneDrive for Business.
* Managed Content from the UEM console added by the administrator.
* User added repositories for Android devices.
> Note:
To support on-premises SharePoint, access to SharePoint and the device must be in the same network domain.

* Save email attachments to repositories.
* Compose a new email with an attachment from an online repository.
* Compose an email and attach one or more files from the Boxer Files.
* Reply to an email with one or more attachments from an online repository.
* Sort saved files by size, alphabets, and date modified.
* View a repository's information from the Boxer Settings.

The following list describes the limitations of Enterprise Content

* Users cannot the edit documents present in the repositories as this functionality is avialable only in the Workspace ONE Content application.
* User added repositories are supported only on Android devices.
* Enterprise Content does not support the local storage of the Content application.
* The Exchange server sets the email size limit.
* Search option is applicable for iOS devices only and is limited to the folders that users have traversed.

## Deployment

Assign Workspace ONE Boxer to devices with the assignment feature known as flexible deployment. Configure the security and email management features within the assignment procedure so that they meet your organization's needs.

>Important:
 If Passcode is set to None, then the Workspace ONE Boxer app is not encrypted. If you do not enforce an app-level passcode, then consider enforcing a device-level passcode using a device profile, which encrypts the iOS device.

* All attachment security, Data Loss Prevention (DLP), and encryption are handled from within the Workspace ONE Boxer app itself.
* Enabling **DLP > Caller ID** settings cause an error if end users have deleted their local address book. See Workaround for Third-Party Address Book – iOS for more information.

### Procedure
* Navigate with one of the following paths.
     *  Select **Add Assignment** in the Assignment window.
     This navigation reflects adding an assignment immediately after adding the application to the public tab of the console.
    * Go to **Apps & Books > Public**, select the Workspace ONE Boxer application in the List View, select Assign, and choose Add Assignment.
    This navigation reflects adding an assignment later after adding the application to the public tab of the console.
* Select **Save**.
* If you want to restrict copying and pasting of data from and to the Workspace ONE Boxer and other supported apps, configure these settings at **Apps > Settings and Policies > Security Policies > Data Loss Prevention**.
Authentication Type and Single Sign-On must be enabled for these settings to be applied on the end user devices. These restrictions are applied accross all supported VMware applications.


## Integrations

### Email Notification Service
The Email Notification Service (ENS) adds Apple Push Notification support to Exchange. On iOS, a third-party app can receive notifications using Apple’s background app refresh or Apple Push Notification Service (APNs) technologies. Background app refresh is used by default, as each app can provide irregular notifications using this method. However, iOS attempts to balance the needs of all apps and the system itself.

To provide notifications quickly and consistently, Apple also provides APNs. APNs allows a remote server to send notifications to the user for that application, however Exchange does not natively support these APNs. ENS adds APNs support to your deployment to allow quick and consistent notifications about the new items in your end users email inbox.

Deploy the Email Notification Service (ENS2) to provide real-time email notifications. Email Notification Service 2 (ENS2) is an initial rewrite of the solution for new email notifications for VMware Workspace ONE Boxer on both iOS and Android. The service works by monitoring the Exchange or Office365 back end for email events and sending updates to the end user devices through Apple or Google’s push notification services. The service works by monitoring the Exchange or Office365 back end for email events and sending updates to the end user devices through Apple or Google’s push notification services. The updates come through as new email banners and on iOS through the app’s badge counter.This provides a more robust security model, high availability, and a cloud deployment option.

For more information on deploying Email Notification Service, see the Workspace ONE UEM Online Help topic, Introduction to Email Notification Service 2.

### Workspace ONE UEM Mobile Email Management Models (Optional)
Configure one of the Workspace ONE UEM email deployment models, either Secure Email Gateway (SEG) or PowerShell. For more information on choosing a MEM deployment model, see the Workspace ONE UEM Online Help topic Protect Email Infrastructure.
