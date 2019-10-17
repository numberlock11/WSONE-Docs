---
id: Deploying_Single_App_Kiosks
title: Deploying Single App Kiosks and Digital Signs
custom_edit_url: https://github.com/numberlock11/WSONE-Docs/blob/master/docs/Google/Deploying_Single_App_Kiosks.md
---

Android devices can be locked down to present a single app for kiosk and digital signage use cases. Users can only have access to the app in the foreground, and cannot navigate back to the Android home screen or alter device settings. Single app kiosks and signs can be easily achieved by using VMware Launcher.

## How does VMware Launcher enable single app kiosks?
VMware Intelligent Hub uses Android's lock task feature to lock Launcher in the foreground. The lock task features built into Android are also used to allow customization of which settings are available to the user during single app mode. For instance, access to settings such as Wi-FI can be prevented and notification bar access can be customized.

## Best practices for Enrollment
The best option to meet the kiosk use case is to use Work Managed enrollment with device based accounts. The recommendation is based on two key assumptions:

* Devices used for kiosks and digital signs typically don't have an end user associated with them.
* Enrollments will be performed in bulk. The enrollment will occur at a central location and then shipped to the location where the device will be used as a kiosk.

### Configure device-based accounts
> Device based accounts is only available when Android EMM is registered using Managed Google Accounts.

Device based accounts add a unique managed Google account on each device, even if the enrollment user is the same. This is important because Google limits how many devices can be used by a single user (limited to 10). With device based accounts, any number of devices can be enrolled with the same user.

To configure device-based accounts in the Workspace ONE UEM console:
1. Navigate to Groups & Settings > All Settings > Devices & Users > Android > Android EMM Registration > Enrollment Settings.
2. Set the Work Managed Enrollment Type to Device-Based.

### Selecting the right method for work managed enrollments
To ensure that the enrollment is easy to perform in bulk, the best option is to use a QR code. A QR code can be created within the Workspace ONE UEM console that includes server details, group ID and authentication details. By simply scanning the QR code during the out of box setup, the device will enroll without any further interaction.

To create a QR code in the Workspace ONE UEM console:
1. Navigate to Lifecycle > Staging > List view.
2. Click 'Configure Enrollment'.
3. Select 'Android' and 'QR Code', then click 'Configure'.
4. You can connect the device to Wi-Fi prior to enrollment by enabling the Wi-Fi toggle. This enabling action displays the following options.

|  Setting |                                       Description                                       |
|:--------:|:---------------------------------------------------------------------------------------:|
| SSID     | Enter the Service Set Identifier, more commonly known as the name of the Wi-Fi Network. |
| Password | Enter the Wi-Fi password for the entered SSID.                                          |

5. Select Next.

6. Select the Workspace ONE Intelligent Hub to push to devices during staging. The default selection is Use latest Workspace ONE Intelligent Hub. If you do not have an Workspace ONE Intelligent Hub added, select Hosted on an external URL and enter the address in the URL text box to point to an externally-hosted Workspace ONE Intelligent Hub Package.

7. Select Next.

8. Set the Enrollment Details settings. To use token-based authentication, leave both options disabled.

Configure Organization Group

|       Setting      |                             Description                             |
|:------------------:|:-------------------------------------------------------------------:|
| Organization Group | Enable and select the organization group to enroll the device into. |

Configure Login Credentials

|  Setting |                                      Description                                      |
|:--------:|:-------------------------------------------------------------------------------------:|
| Username | Enable to configure login credentials. Enter the Workspace ONE UEM account user name. |
| Password | Enter the corresponding password.                                                     |

9. Select Next.
10. The Summary page allows you to Download File of the PDF. You can also View PDF to see a preview of your QR Code Format selections.


## Creating the VMware Launcher Profile

1. Navigate to Devices > Profiles & Resources > Profiles > Add > Add Profile > Android .
2. Configure the profile's General settings.These settings determine how the profile deploys and who receives it.
3. Select the Launcher profile.
4. Select Single App mode.
5. Drag and drop the app you want to lock to the foreground.
6. Under Layout, select portrait or landscape based on how you'd like the app to be displayed.
7. Under Settings, configure settings and utilities that you'd like the user of the device to gain access to.
> We recommend that an Administrative passcode is configured under Settings. This ensures that admin users can back out of single app mode for simplified troubleshooting (either in person or through Workspace ONE Assist)

8. Click Save to add the profile to AirWatch or Save & Publish to add the profile and immediately deploy it to applicable Android devices.
