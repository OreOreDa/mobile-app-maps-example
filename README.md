# Maps application

React Native application for Maps

## Installation

First, install the dependencies:
```
npm install
```

Then get a Google Maps API key:

Go to https://developers.google.com/maps/documentation/ios-sdk/get-api-key and https://developers.google.com/maps/documentation/android-api/signup to get your keys for both iOS and Android.

Make sure that Google Maps Android API and Google Maps SDK for iOS are enabled for the current project.
https://console.developers.google.com/apis/library/maps-android-backend.googleapis.com/
https://console.developers.google.com/apis/library/maps-ios-backend.googleapis.com

### iOS

Run the following commnands:
```
cd ios
pod install
```

After that, use `.xcworkspace`, not `.xcproject`.

Insert Google Maps API key in AppDelegate.m

### Android

Insert Google Maps API key in AndroidManifest.xml
