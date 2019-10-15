---
id: MAM_Internal_Apps
title: Deploying Internal Apps
custom_edit_url: https://github.com/numberlock11/WSONE-Docs/blob/master/docs/Google/MAM_Internal_Apps.md
---

With Android Enterprise, internally developed apps can either be hosted on managed Google Play, or within the Workspace ONE UEM console. Deploying your private apps on Google Play has many benefits:

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

## Deploying internal apps by hosting in managed Google Play

There are two ways of deploying internal apps to managed Google Play. Apps can be uploaded to managed Google Play through an iframe that is loaded in the Workspace ONE UEM console, or the app can be directly published to managed Google Play through the Play Developer console.

Publishing through the iframe in the Workspace ONE UEM console is the fastest and easiest method to publish apps quickly as managed Google Play will only require the apk file and the name of the app to start the publish. App metadata (such as description, screenshots etc.) can be added later within the Google Play developer console. However, any apps uploaded through the iframe can never be made public. Apps uploaded through the iframe are available in Google Play within 10 minutes of publishing the app.

Uploading apps directly to managed Google Play using the Google Play Developer console is a longer process. The Google Play developer console requires a complete store listing (including screenshots and description) and a content questionnaire to publish the app. Additionally, it could take up to 24 hours after publishing the app before it can be viewed on Google Play. If the app needs to be made public in the future, using Google Play developer console to upload the app is the best option.

>* Private applications can never be uploaded more than once as the Google Play ensures that each of the application has a unique package name.
>* Deleted Private applications cannot be re-uploaded with the same package name. Delete the private applications only if you never want to use the same package name again. The package name is a unique name to identify a specific app.

### Uploading internal apps using the iframe

1. Navigate to Apps & Books > Public > Add Application.
2. Select Android from the Platform drop-down menu.
3. Select Search App Store to search for the application in the app store. Leave the Name blank and select Next. Google Play opens directly from the Workspace ONE UEM console.
4. Access the Private Apps from the left menu.
5. Enter the Title and upload the APK file.
6. The app can take up to 10 minutes to publish on managed Google Play. Once the app is available, you can select it and add it to the Workspace ONE UEM console for assignment and distribution.

### Uploading internal apps using the Google Play Developer console

Google's documentation to upload apps in the Google Play developer documentation is available [here](https://support.google.com/googleplay/android-developer/answer/113469?hl=en&ref_topic=7072031). When [setting up pricing and distribution](https://support.google.com/googleplay/android-developer/answer/6334373), an option to publish to specific organizations is available in the managed Google Play section.
