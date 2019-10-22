---
id: customenrollment
title: Custom Enrollment
---

### Endpoints to remember

```
Device Management
(URL: https://<hostname>/DeviceManagement/DepEnrollment InitialValidation?depid=<depprofilesessionid>
```

The device management endpoint is the endpoint that's specified in the web_configuration_profile URL when custom enrollment is enabled in the DEP profile. The UEM console will do this in the backend and the admin does not have to specify this URL, all the admin has to do is enable the custom enrollment option in the dep profile or the dep configuration setup wizard.

![DEP1.png](assets/customenrollment.png)

> NOTE: The above screenshot shows an example for edit profile but the same is applicable for the add profile and DEP configuration setup wizard flows as well.

When the device is initially powered on and reaches out to the Apple DEP server, this URL is returned to the device and upon clicking next in the DEP landing screen on the device, this URL is it and then UEM console will render the landing page. Refer to the demo video attached in the bottom of this page. The landing page might be the user auth, token auth or SAML auth based on the setting enabled under the enrollment settings in the console. When the URL is hit we use the dep profile session id in the URL to load the DEP profile and create an enrollment staging record with a dummy device identifier in the mobileManagement.DeviceEnrollmentStaging table. This session id is then provided in the DS URL discussed below.

```
Device Services MDM Profile delivery
(URL: https://<hostname>/DeviceServices/AppleMdmProfileDelivery.aws?sid=<sessionid>
```
This URL is called by device management once the authentication is complete and the TOU has been accepted(if any). The session id generated in device management is passed on the URL which is then used to load the staging information. We then create a dummy device record with the device identifier generated in Device Management, generate and deliver the MDM profile to the device. In the MDM profile, when specifying the checkin URL, we append the device uuid that was created upon the creation of the dummy device record. Once the MDM profile is delivered, the web view on the device is closed and the device checks in to the checkin endpoint discussed below.

```
Device Services MDM Profile delivery
(URL: https://<hostname>//DeviceServices/AppleMDM/CheckIn.aspx?deviceId=<deviceuuid>
```

When the device checks in to this endpoint, this is the first instance where we have all device related properties such as Serial number, UDID, model etc. Using the device uuid in the URL, we will update the device record with the device reported properties. All other checkin related processing remains the same.

## Important notes for custom enrollment

* When custom enrollment is enabled, authentication is always required and will be defaulted to on and disabled.
* Custom enrollment applies to the DEP profile and can be enabled/disabled at the dep profile level.
* Enrollment restrictions are not supported.
* Optional prompts are not supported.
* If the enrollment user has UG mapping, that will always take precedence.
* If there is no UG mapping, the default OG context that the device will start enrollment is in the OG specified in the DEP profile.
* Once the user/token auth info is entered, the OG will be moved based on where the user is.
* If the DEP profile is at a higher OG than where the user is, the OG context is the OG where the user is at.
* If the DEP profile(or the assigned location group) is at a lower OG than where the user is, the OG context is the OG where the DEP profile(or the assigned location group) is at.
Ownership type is defaulted to corporate dedicated for custom enrollment.
* If a DEP device is enrolled using the legacy DEP enrollment method and is reset without unenrolling/deleting the device from console, when the enrollment process is started on the device again and if it goes through custom enrollment, a new device record is created and the old device record is deleted. This is because for the enrollment using the custom DEP web view, we do not get the UDID until the checkin.
* Supported authentication methods are basic/directory authentication, single and two factor token authentication and SAML.
* If you have specified a platform for an enrollment token, it's not supported and can use the token to enroll a device with any platform.
* If the end user kicks off the custom enrollment and closes the web view between the device record creation and the profile delivery and then initiates the custom enrollment again, you might see duplicate device records with the older one showing "Enrollment in progress". This is because we do not have the UDID to tie these two records. We have added a purge job to clean up these records which cleans records over the last 30 days. There will also be multiple device enrollment staging records since we create a staging record everytime the web view is loaded.
* A new enrollment mode has been added. In the mobileManagement.DeviceEnrollmentStaging table, the mode for custom enrollment will be CustomDep.
* Remember custom enrollment is applicable only for iOS 13+ and macOS 10.15+ devices only.
* TOU will be picked from the final OG context decided post authentication.

## Database changes

* New column added to dbo.DeviceExtendedProperties. The column IsCustomDepEnrolled is used to identify a device that has enrolled using the custom enrollment. This is also the column that we depend on to purge the enrollment in progress records.
* New column added to deviceProfile.MDMEnrollmentProgram. The column EnableCustomWebView is used to identify if the admin has enabled custom enrollment for the dep profile.
Demo videos
