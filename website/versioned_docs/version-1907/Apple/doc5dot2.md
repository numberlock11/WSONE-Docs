---
id: version-1907-doc5dot2
title: User Enrollment
original_id: doc5dot2
---
## Technical Flow Diagram

### User Enrollment without entering GroupID
![DEP1.png](assets/UEflow.png)

### User Enrollment with entering GroupID
![DEP1.png](assets/UEflow2.png)

### Things to remember:

* If user group mapping exists for the enrollment user, that takes highest priority and the device will enroll to the OG specified in the user group mapping. User enrollment needs to be enabled in the UG mapping OG (either inherited or overridden).

* If no user group mapping exists, the device will enroll to the default enrollment organization group of the enrollment user if no Group ID is provided during enrollment. User enrollment needs to be enabled in the OG (either inherited or overridden).

* If Group ID is entered during enrollment and no UG mapping exists for the enrollment user, the device will enroll to the entered OG as long as user enrollment is enabled at that OG (either inherited or overridden).

* There will be a dummy device record created during enrollment that will be updated to the correct device info once user enrollment completes. If enrollment is aborted in the middle and restarted, a new device record will be created and the old one will continue to show in the device list view page. This is because there is no persistent device identifier that can be used to merge these two records.

* User enrollment is not supported through the Hub app so we need to perform web based enrollment and push down Hub as a managed app.

* The default ownership type for user enrolled devices will always be Employee Owned.

* No persistent identifier for UE devices. This means no serial number, IMEI, UDID etc.

* The UDID for the device is replaced with an Enrollment ID. In the dbo.Device table for a user enrolled device, the UDID column will be populated with the Enrollment ID of the device. DO NOT CONFUSE THIS WITH THE ACTUAL DEVICE UDID. However, any APIs that identify the device with its UDID will continue to work if we use the Enrollment ID as UDID.

* Public apps are not supported on user enrolled devices. Only VPP apps with user based licensing can install on UE devices.

### VPP things to remember for user enrollment:

* No invite will be sent to a user enrolled device. When a UE device enrolls or when an app is pushed, the VPP user for the enrollment user for the UE device will be associated with the managed Apple ID. Once this association is done, we are no longer required to send an invite to the device. This is called the silent invite accept process and will be done completely silently from the backend by calling the Register VPP user API.
* The LicenseTypeEligibility for a UE device will always be user based license. This means that even if the app has DBL enabled, we will issue UBL for a UE device for that app. This field can be found in the dbo.DeviceExtendedProperties table. Column name is LicenseTypeEligibility and the value should be 2 for UE devices.

### Logs to collect:

* For issues relating to the user enrollment UI before getting the prompt to download and install the MDM profile please collect DeviceManagement logs.
* For issues during or after redirection to the DS endpoint to download the MDM profile please collect DeviceServices logs.

### Database changes to know:

* Added a new column to dbo.DeviceExtendedProperties table to identify if the device is user enrolled. The column is called IsUserEnrolled
* LicenseTypeEligibility for a UE device will always be user based licensing. This can be found in the dbo.DeviceExtendedProperties table. Column name is LicenseTypeEligibility and value should be 2.
