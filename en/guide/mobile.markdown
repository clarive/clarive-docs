---
title: Mobile App Delivery
index: 4000
---

Clarive supports deploying to both the Apple App Store and Google Play Store using their corresponding APIs and
a library/command-line tool called **Fastlane**, which is bundled in the Clarive Mobile plugin.

### Publishing the App to the Store

Publishing an app to a mobile store, such as Apple's and Google's, involves a number of steps that you need to plan well
before implementing.

- Maintain the store profile.
- Sign the app code with certificates.
- Maintain push notification profiles.
- Create application screenshots.
- Build, test and deploy the app.

### Signing and Maintaining Certificates

You have to plan running `PRE` step where code is signed using the organizational certificate
[Resources](/concepts/resource) with a [Rule](/concepts/rule).

### Accessing the Store

For each store, we recommend using a different set of libraries that need to be installed separately in the Clarive
server.

#### Apple Store

The Clarive App Store feature relies on the (Ruby) Spaceship library.

**Spaceship** exposes both the Apple Developer Center and the iTunes Connect API.

This fast and powerful API powers parts of Clarive, and can be leveraged for more advanced Clarive features.

`https://idmsa.apple.com`

- Used to authenticate and call up a valid session.

`https://developerservices2.apple.com`

- Provides a detailed list of all available provisioning profiles.
- Returns the devices, certificates and apps for each of the profiles.
- Registers new devices.

`https://developer.apple.com`

- Lists all devices, certificates, apps and app groups.
- Creates new certificates, provisioning profiles and apps.
- Disables/enables services on apps and assigns them to app groups.
- Deletes certificates and apps.
- Repairs provisioning profiles.
- Downloads provisioning profiles.
- Team selection.

`https://itunesconnect.apple.com`

- Manages apps.
- Manages beta testers.
- Submits updates for review.
- Manages app metadata.

`https://du-itc.itunesconnect.apple.com`

- Uploads icons, screenshots, trailers etc.

#### Google Play Store

Clarive also supports deployment to the Google Play store.

Setup consists of setting up your Google Developer Service Account:

- Open the *Google Play Developer Console*.
- Select *Settings* tab, followed by the *API access* tab.
- Click the *Create Service Account* button and follow the *Google Play Developer Console* link in the dialog.
- Click *Create credentials* and select *Service account*.
- Select *JSON* as the Key type and click *Create*.
- Make a note of the name of the *JSON file* downloaded to your computer, and close the dialog.
- Back on the *Google Play Developer Console*, click *Done* to close the dialog.
- Click on *Grant Access* for the newly added service account.
- Choose *Release Manager* from the *Role* dropdown menu and click *Send Invitation* to close the dialog.
