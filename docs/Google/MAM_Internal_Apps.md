---
id: MAM_Internal_Apps
title: Deploying Internal Apps
---

With Android Enterprise, internally developed apps can either be hosted on Google Play, or within the Workspace ONE UEM console. Deploying your private apps on Google Play has many benefits:

* Your app is limited to your organization (or a list of organizations of your choosing). Although the app is uploaded to Play, it'll only be available to users within your organization.
* Your apps are scanned by Google to ensure it meets best practices for Android app development.
* You can leverage Google's global Play Store infrastructure for app delivery and app updates.
* Alpha and beta testing can be achieved through Google Play.
* End users can download the app directly from managed Google Play on their enrolled device.

Hosting internally developed apps within the Workspace ONE UEM console is not available with all forms of enrollment. Review the table below to understand when an app can be hosted on Google Play and when it can be hosted in Workspace ONE UEM.

|             Enrollment             |      Host in Google Play      |   Host in Workspace ONE UEM   |
|:----------------------------------:|:-----------------------------:|:-----------------------------:|
|            Work Profile            |           Supported           |         Not Supported         |
|            Work Managed            |           Supported           |           Supported           |
| Corporate Owned Personally Enabled | Supported (Work Profile only) | Supported (Work Managed only) |
