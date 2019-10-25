---
id: version-1907-Android_UEM_Overview
title: Android UEM Overview
custom_edit_url: https://github.com/numberlock11/WSONE-Docs/blob/master/docs/Google/Android_UEM_Overview.md
original_id: Android_UEM_Overview
---

VMware Workspace ONE UEM integrates with Google's Android Enterprise framework to provide a broad set of management features to meet your use cases. This section is meant to provide an overview of how Workspace ONE UEM interacts with Google APIs and frameworks to provide an understanding of how Android UEM management works. The section also includes considerations for choosing the right management model and network setup.

## Introduction to Android Enterprise

Android Enterprise is a standard feature set built into the Android operating system that allows UEM providers to secure employee-owned and corporate-owned Android devices. Google introduced the Android Enterprise framework as an optional feature set for OEMs as part of Android 5.0, but made Android Enterprise mandatory for all GMS-certified devices starting with Android 6.0. Android Enterprise has several benefits to make it the best management option for your Android devices:

* Since Android Enterprise is built into the operating system and is available with every GMS-certified device on Android 6.0+, management policies can be applied across a wide variety of OEMs without worry of fragmentation.
* Android Enterprise offers silent application install, allowing for a seamless device setup experience.
* Android Enterprise offers three management modes to meet your use cases: Work Profile, Work Managed, and Corporate Owned Personally Enabled.
* Google Play can be used to distribute and configure public, web and private apps.
* Personal and private data separation with privacy controls built into the operating system that prevent invasive policies from applying on an employee-owned device.

## How does Android Enterprise work?
In order to configure management policies for your Android devices, you need to register Workspace ONE UEM as the EMM provider for your organization with Google. This registration allows Workspace ONE UEM to enroll your Android devices into the management mode of your choice. During device enrollment using the Workspace ONE Intelligent Hub, two key events occur:

1) Workspace ONE UEM adds a Google account to the device for management purposes. This Google account is primarily used for app management through Google Play and controls the apps that the user can access for work.

2) Workspace ONE Intelligent Hub is given elevated permissions to successfully manage devices. For employee owned devices, the Intelligent Hub is provided Profile Owner(PO) permission and for locked down corporate owned devices, the Intelligent Hub is provided the Device Owner(DO) permission. Profile owners have significantly lesser control over the device than device owners, thereby ensuring that more restrictive and invasive policies cannot be applied to employee-owned devices.

Public app management capabilities such as assigning and installing apps from Play are accomplished primarily through Google Play APIs, without the involvement of the Intelligent Hub. Profiles, internal app management and advanced management features such as product provisioning are handled locally on the device through the Intelligent Hub.

## Choosing A Registration Method.

There are two ways to register Workspace ONE as your EMM provider with Google. Depending on your use of GSuite and your use case, you may prefer to deploy on one method over the other.

### Managed Google Accounts

Managed Google Accounts is preferred for most use cases, particularly when Google has no record of your organization's users. Registration steps are fairly simple and can be completed by simply logging in with a gmail.com account and clicking through a few screens. When enrolling devices using this method, Workspace ONE UEM will generate a new managed Google account for each enrollment user. No personally identifiable information is passed to create these Google accounts, and therefore, will appear on the device as random hash values, for example: 123456789@android-for-work.gserviceaccount.com. These EMM-generated Google accounts do not have a password and cannot be used to access Google apps or cloud storage. The accounts can only be created by EMMs, and are used only for management functionality. Managed Google Accounts registrations have the following advantages:

* Organizations can create multiple registrations since each registration simply needs a different gmail.com account. Therefore, multiple registrations for UAT and production environments are possible.
* No user-identifiable information is shared with Google when generating Google accounts for management.
* Google limits the number of devices for each Google account to 10 devices. For scenarios (such as bulk enrollment) where a single user will be used to enroll more than 10 devices, Workspace ONE UEM can generate unique user accounts per device (this is a configurable setting).

### Google Domain-Based Registration

Google Domain-Based registration is ideal if an existing domain is already managed with Google (for example, through GSuite). Workspace ONE UEM can be added as the EMM provider for Google Accounts in the domain. In this scenario, Workspace ONE UEM will not generate a Google account for the enrollment user during enrollment. Instead, the user's Google identity (the user's GSuite account) will be used for management. The Google domain-based registration setup is more complex; involves generating an EMM token within the Google Admin Console and creating a service account for management. Since the binding between an EMM and the Google domain is one to one, it is not possible to setup multiple registrations for UAT and production. Separate domains must be used for multiple registrations. Additionally, because Workspace ONE UEM does not generate a unique Google account for the user on each device for bulk enrollment, enrolling more than 10 devices per user is not possible. The primary advantages of using a Google Domain-Based Registration setup are:

* The user's GSuite account is automatically added to the device as part of enrollment and therefore, the user is logged into Google apps such as Docs, Sheets, Gmail and Slides by enrolling.
* The Google Admin Console offers a policy called 'Enforce EMM Policies'. Using this policy will prevent users from logging into an unmanaged Android device using their GSuite account.


## Choosing an enrollment method.

Android Enterprise offers three forms of enrollment. You may choose to use one or more of these enrollment methods across your deployment based on your use cases.

### Work Profile
Ideal for bring your own device (BYOD) use cases. The work profile provides the best solution for BYOD by ensuring end user privacy and allowing IT to control work data on the device. When a work profile is created on a user's Android device, a separation is created between work and personal data. Workspace ONE UEM only controls the work data on the device and cannot apply policy on the personal side of the device. The end user is in complete control over their personal data and can choose to remove the work profile at any time. To help the user easily identify work apps and personal apps, all work apps (and work app notifications) have a briefcase badge. Since the work profile is focused on end user privacy, many device-wide policies cannot be applied. For instance, IT can control if camera usage is acceptable within the work profile but cannot disable factory reset.

Learn more about the Work Profile in our Android Video Series:
[![Work Profile](http://img.youtube.com/vi/NmiJz8ZtRCI/0.jpg)](https://www.youtube.com/watch?v=NmiJz8ZtRCI "VMware Series Episode 2: Work Profile")

### Work Managed
Ideal for line of business and corporate owned use cases where complete control of the device is necessary. Devices have to be enrolled during device setup (factory reset state). Upon enrolling into Work Managed, the Android device will only contain work apps. The Play Store is locked down to work apps only. Work Managed devices provide additional management capabilities such as preventing factory reset, adding custom lock screen messages or even using VMware Launcher to customize where app icons should be placed. On Android, product provisioning and relay server distribution capabilities are only supported with Work Managed enrollments. Since the device is enrolled during device setup, specific steps have to be taken to ensure that the device enrolls as a Work Managed device instead of a consumer device. The Android operating system provides four methods: NFC, QR Code, an EMM identifier and Zero Touch (Knox Mobile Enrollment for Samsung devices). We'll cover these enrollment methods in more detail when we discuss Work Managed enrollment.

Learn more about Work Managed enrollments in our Android Video Series:
[![Work Managed](http://img.youtube.com/vi/d2LJdtou1ts/0.jpg)](https://www.youtube.com/watch?v=d2LJdtou1ts "VMware Series Episode 3: Work Managed")

### Corporate Owned Personally Enabled (COPE)
Ideal for deployments in which the organization purchases devices that are provided to end users for work and personal use. Corporate Owned Personally Enabled (or COPE for short) can be thought of as a combination of Work Profile and Work Managed enrollments. The user is still provided a visual work and personal separation on the phone, but more restrictive policies (that are reserved for Work Managed enrollments) can also be applied on the device. The device must be enrolled during device setup and the same options (NFC, QR Code, EMM identifier and Zero Touch/ Knox Mobile Enrollment) as Work Managed can be used for COPE enrollments as well. Because the device is essentially split into work and personal, but control over the entire device is retained, different policies can be applied across work and personal. For instance, the camera can be blocked within the work profile, but enabled on the personal side of the device.

Learn more about Corporate Owned Personally Enabled enrollments in our Android Video Series:
[![Corporate Owned Personally Enabled](http://img.youtube.com/vi/HXHjXyiiKLk/0.jpg)](https://www.youtube.com/watch?v=HXHjXyiiKLk "VMware Series Episode 4: Work Managed")
