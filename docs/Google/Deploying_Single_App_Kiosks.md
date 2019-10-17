---
id: Deploying_Single_App_Kiosks
title: Deploying Single App Kiosks and Digital Signs
---

Android devices can be locked down to present a single app for kiosk and digital signage use cases. Users can only have access to the app in the foreground, and cannot navigate back to the Android home screen or alter device settings. Single app kiosks and signs can be easily achieved by using VMware Launcher.

### Configuring VMware Launcher for kiosks and digital signage

## How does VMware Launcher enable single app kiosks?
VMware Intelligent Hub uses Android's lock task feature to lock Launcher in the foreground. The lock task features built into Android are also used to allow customization of which settings are available to the user during single app mode. For instance, access to settings such as Wi-FI can be prevented and notification bar access can be customized.

## Best practices for Enrollment
The best option to meet the kiosk use case is to use Work Managed enrollment with device based accounts. The recommendation is based on two key assumptions:

* Devices used for kiosks and digital signs typically don't have an end user associated with them.
* Enrollments will be performed in bulk. The enrollment will occur at a central location and then shipped to the location where the device will be used as a kiosk.

# Configure device-based accounts 
>> Device based accounts is only available when Android EMM is registered using Managed Google Accounts.

Device based accounts add a unique managed Google account on each device, even if the enrollment user is the same. This is important because Google limits how many devices can be used by a single user (limited to 10). With device based accounts, any number of devices can be enrolled with the same user.


## Creating the VMware Launcher Profile

1. Navigate to Devices > Profiles & Resources > Profiles > Add > Add Profile > Android .
2. Configure the profile's General settings.These settings determine how the profile deploys and who receives it.
3. Select the Launcher profile.
4. Select Single App mode.
5. Drag and drop the app you want to lock to the foreground.
6. Under Layout, select portrait or landscape based on how you'd like the app to be displayed.
7. Under Settings, configure settings and utilities that you'd like the user of the device to gain access to.
>> We recommend that an Administrative passcode is configured under Settings. This ensures that admin users can back out of single app mode for simplified troubleshooting (either in person or through Workspace ONE Assist)

8. Click Save to add the profile to AirWatch or Save & Publish to add the profile and immediately deploy it to applicable Android devices.


## Best practices for enrolling Android devices for Kiosks
