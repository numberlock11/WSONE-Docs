---
id: version-1907-Register_Managed_Google_Accounts
title: Managed Google Accounts
custom_edit_url: https://github.com/numberlock11/WSONE-Docs/blob/master/docs/Google/Register_Managed_Google_Accounts.md
original_id: Register_Managed_Google_Accounts
---

> Before proceeding with registration, review ["Choosing a Registration Method"](https://numberlock11.github.io/WSONE-Docs/docs/Google/Android_UEM_Overview#choosing-a-registration-method) in the Android UEM Overview page to ensure you're selecting the right registration method for your use case.

In order to manage Android devices, Workspace ONE must be registered as your UEM provider with Google. When using Managed Google Accounts, this is a simple process that can be completed in a few minutes.

## Best Practices

* You'll need a @gmail.com account to complete registration using the Managed Google Accounts method. We recommend creating a separate @gmail.com account that will be used strictly for registration and will not be associated with any user. The Google account cannot be associated with a GSuite domain.
* Complete the registration at your highest organization group (should be of type 'Customer'). Registering at the highest organization group will allow you to use the same registration across all your use cases instead of maintaining multiple UEM registrations with Google.

## Registering Workspace ONE UEM for Android Management

1. Navigate to Groups & Settings > All Settings > Devices & Users > Android > Android EMM Registration.

![](Screenshots/AndroidEMMRegistration.png)

2. Click 'Register with Google'
3. You will be redirected to a Google page to register your organization. Sign in with the @gmail.com account created for management, and enter your organization name. You should already see Workspace ONE listed as your EMM provider. Google will ask you to optionally fill details about your privacy officers. Agree to the Google agreement and click 'Confirm'.

> Ensure that the correct Google account is used for registration. If you already logged into the Chrome browser using your personal Google account, the Google sign in page will use that account upon redirect. Consider using a private browsing window to ensure you are using the correct Google account.

4. You will be redirected back to the Workspace ONE UEM Settings page and registration is completed. You can confirm that registration is successful by using the 'Test Connection' button.

## Removing the Registration

> Before proceeding, be aware that removing the registration is not recommended for active deployments and can lead to loss of management functionality on enrolled devices.

1. Navigate to Groups & Settings > All Settings > Devices & Users > Android > Android EMM Registration.
2. Click 'Clear Settings' at the bottom of the page.
