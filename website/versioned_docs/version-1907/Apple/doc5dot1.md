---
id: version-1907-doc5dot1
title: Device Enrollment Program
original_id: doc5dot1
---
## Device not completing DEP enrollment

If you are receiving errors (ex: Invalid Profile) or experiencing issues with DEP enrollment, check to make sure the following conditions are met:

Navigate to the **DEP settings page** (```Groups and Settings > All Settings > Devices and Users > Apple > Device Enrollment Program```) within the AirWatch console. Select the DEP profile, which you have assigned to the device and check that the **custom prompt** option has been **turned off**.  If the custom prompt is turned on, edit the DEP profile and turn off custom prompt.  Once custom prompt has been turned off, go ahead and factory reset your device  

![DEP1.png](assets/rtaImage.png)

Make sure that your **DEP token** is still valid and has not expired.  If the token has expired, go ahead and renew.  In order to renew the DEP token, login to your **Apple DEP portal**.  Within the DEP portal, you should see a **MDM server**, select the server.  Next, select **generate new token** option and download the new DEP token. Upload the new token into AirWatch and factory reset the device.  

![DEP2.png](assets/rtaImage2.png)

Verify the device has been **assigned a DEP profile** by navigating to the **enrollment status page** (Devices > Lifecycle > Enrollment Status).  You can search for the specific device, by typing in the serial number.  Once you have found the device, click on the device and see if there is a DEP profile assigned.  If not, select the **more** option located at the top right side of the page and select **assign profile**.   select the profile you would like to assign and save the page.  Once the device has been assigned a profile, factory reset the device.

![DEP3.png](assets/rtaImage3.png)

## Not able to assign or remove DEP profile assignment

If you are having issues with removing and reassigning DEP profiles, please perform the following troubleshooting steps:

First, navigate to the **DEP settings page** (```Groups and Settings > All Settings > Devices and Users > Apple > Device Enrollment Program```) within AirWatch and make sure that the **DEP token is still valid**.  If not, renew the token and try assigning/removing the profile. In order to renew the DEP token, login to your **Apple DEP portal**.  Within the DEP portal, you should see a **MDM server**, select the server.  Next, select **generate new token** option and download the new DEP token.

![DEP4.png](assets/rtaImage4.png)

Navigate to the **Apple DEP portal** and make sure that the **Apple terms and conditions** have been accepted.  If the conditions have not been accepted, accept them and try assigning/removing the profile in AirWatch.

If you are still not able to assign/remove profile after completing the above two steps, the registration record for the device has been corrupted.  To get a new registration record, perform the following actions:

*   Unassign the device from the Apple DEP portal using the device serial number as the reference.
*   Navigate to the **enrollment status page** in AirWatch (Devices > Lifecycle > Enrollment Status) and perform a **sync device**.  
    ![DEP5.png](assets/rtaImage5.png)
*   Once the sync has completed, navigate back to the Apple DEP portal and **re-assign the device back to the MDM server.**
*   Lastly, navigate to the enrollment status page in AirWatch and perform a sync device again.  A new registration for the device should now be created and you should be able to assign/remove DEP profiles.

## DEP profile stuck in "Assignment in Progress"

If you noticed that the DEP profile is stuck at assignment in progress, then there are a few steps to take depending on the number of DEP profiles that have been created.

1.  If there is only **one DEP profile** created within your environment, the best option would be to **disable** and re-configure DEP.
2.  If there are **multiple DEP profiles** and this issue is affecting just one of the DEP profiles, then create a support ticket so that we can delete the profile from the database.  Once the profile has been deleted, you would be able to re-create and re-assign that DEP profile to all the devices.

## Devices are not syncing into the AirWatch console

If you are experiencing an issue where you are not able to sync in devices from the Apple DEP portal into the AirWatch console, please perform the following troubleshooting steps:

Make sure that your **DEP token** is still valid and has not expired.  If the token has expired, go ahead and renew.  In order to renew the DEP token, login to your **Apple DEP portal**.  Within the DEP portal, you should see a **MDM server**, select the server.  Next, select **generate new token** option and download the new DEP token.  Upload the new token into AirWatch and factory reset the device.

![DEP6.png](/docs/assets/rtaImage6.png)

Navigate to the **Apple DEP portal** and make sure that the **Apple terms and conditions** have been accepted.  If the conditions have not been accepted, accept them and try assigning/removing the profile in AirWatch.

If you have an **on premise instance** of AirWatch, navigate to the **console server**.  Within the console sever navigate to the **services tab within server manager**.  Here you should see a service called **AirWatch Batch Processing Service**. **Restart** this service and then try syncing the devices again from the console.

## Invalid Profile

More often than not, the “Invalid Profile” error occurs when the Organization Group where the DEP profile is configured and assigned does not have a Group ID. Verify the OG has a Group ID and the user is in an OG in which the DEP profile is assigned. Additional troubleshooting steps include the following:

*   Enroll the device while using a Hotspot
*   Renew the DEP token
*   Remove the profile from More actions and refresh the page, then re-assign the profile
*   Create a new DEP profile

## How to unenroll DEP devices

To reenroll a device with a different user, send a Device Wipe command from the AirWatch Console and enter the new user credentials during configuration. If you do not want to re-enroll the device as DEP, remove the DEP profile by navigating to ```Devices > Lifecycle > Enrollment Status > select the device > More > Remove Profile```. From here, perform a Device Wipe.

## How to reconfigure DEP

To reconfigure DEP, perform the following steps:

*   Navigate to the Organization Group where DEP is configured. From here, select ```Groups & Settings > All Settings > Devices & Users > Apple > Device Enrollment Program```.
*   Select **Disable** and save the page. Refresh the page.
*   Click **Configure** and download the public key by selecting MDM_DEP_PublicKey.pem.
*   Navigate to deploy.apple.com and log in using your Apple ID and password.
*   Upload the Public key to your AW MDM server, and download the Apple server token file from DEP.
*   Upload the Apple server token in the AirWatch Console by clicking **Upload**.
*   Finally, define the DEP profile settings.

## DEP devices prompting for iTunes ID and password to install applications

Upon encountering this issue, ensure the applications are VPP and have been assigned as device based. Additionally, verify the devices does not have any public applications assigned.

## How to reboot a DEP Mac without deleting any data

Run the following commands in Terminal:

```
sudo rm /var/db/.AppleSetupDone

sudo rm -rf /var/db/ConfigurationProfiles/

sudo rm /Library/Keychains/apsd.keychain

sudo reboot
```


## How to delete DEP devices from the Lifecycle Page

Under the ```DEP Portal > Devices payload```, pull the serial numbers you’d like to remove. From here, select the option to un-assign them from the AirWatch server. Once they are unassigned, log into the AirWatch Console and navigate to ```Devices > Lifecycle > Enrollment Status > Add > Sync Devices```. The device will no longer appear in the lifecycle page.
