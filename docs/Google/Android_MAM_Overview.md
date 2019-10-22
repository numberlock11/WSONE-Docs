---
id: Android_MAM_Overview
title: Android App Management
custom_edit_url: https://github.com/numberlock11/WSONE-Docs/blob/master/docs/Google/Android_MAM_Overview.md
---

This section provides an overview of key concepts for app management with Android Enterprise. This section also includes considerations for hosting your internal applications based on your use case.

## Managed Google Play
Managed Google Play is used by organizations to select and approve apps for use at work. End users access managed Google Play on their device to view a curated list of apps approved and assigned to them by their organization. Although the look and feel of managed Google Play is similar to public Google Play, the user cannot search for (or view) apps that haven't been approved or assigned to them. Organizations can also curate the user experience for managed Google Play by creating custom categories for approved work apps.

### How to access managed Google Play
You have two options to easily approve and manage your work apps in managed Google Play:

1) Use the managed Google Play iframe in the Workspace ONE UEM Console: This is the easiest way to add and approve new Android public apps, add new web apps, or even upload private apps to Google Play. On the Workspace ONE UEM console, navigate to Apps & Books > Applications > Native > Public > Add Application. Select Android under 'Platform' and click 'Search'.

2) Navigate to Managed Google Play in the browser: You can navigate to https://play.google.com/work and log in using the same Google account that was used to complete the registration process. Once you login, you can manage admins for your Android EMM registration or approve apps.

> Approving an app does not automatically make the app available to a user. App approvals enable adding the app to the Workspace ONE UEM console, after which the app can be assigned to a user.

## Deploying internally developed apps
With Android Enterprise, internally developed apps can either be hosted on managed Google Play, or within the Workspace ONE UEM console. Hosting the app in managed Google Play provides several benefits and is the preferred option for delivering apps. These benefits are listed below:

* Your app is limited to your organization (or a list of organizations of your choosing). Although the app is uploaded to Play, it'll only be available to users within your organization.
* Your apps are scanned by Google to ensure it meets best practices for Android app development.
* You can leverage Google's global Play Store infrastructure for app delivery and app updates.
* Alpha and beta testing can be achieved through Google Play.
* End users can download the app directly from managed Google Play on their enrolled device.

Learn more about Android App Management in our Android Video Series:
[![Android App Management](https://img.youtube.com/vi/DdSE-qFmRt8/0.jpg)](https://www.youtube.com/watch?v=DdSE-qFmRt8&t "VMware Series Episode 5: App Management")
