# Maps application

React Native application for Maps

## Installation

First, install the dependencies:
```
yarn install
```

Then get a Google Maps API key:

Go to https://developers.google.com/maps/documentation/ios-sdk/get-api-key and https://developers.google.com/maps/documentation/android-api/signup to get your keys for both iOS and Android.

Make sure that Google Maps Android API and Google Maps SDK for iOS are enabled for the current project.
https://console.developers.google.com/apis/library/maps-android-backend.googleapis.com/
https://console.developers.google.com/apis/library/maps-ios-backend.googleapis.com

### iOS

Create a `Podfile` in `ios` as below:

~~~
target 'replay' do
  rn_path = '../node_modules/react-native'
  rn_maps_path = '../node_modules/react-native-maps'

  # See http://facebook.github.io/react-native/docs/integration-with-existing-apps.html#configuring-cocoapods-dependencies
  pod 'yoga', path: "#{rn_path}/ReactCommon/yoga/yoga.podspec"
  pod 'React', path: rn_path, subspecs: [
    'Core',
    'CxxBridge',
    'DevSupport',
    'RCTActionSheet',
    'RCTAnimation',
    'RCTGeolocation',
    'RCTImage',
    'RCTLinkingIOS',
    'RCTNetwork',
    'RCTSettings',
    'RCTText',
    'RCTVibration',
    'RCTWebSocket',
  ]

  # React Native third party dependencies podspecs
  pod 'DoubleConversion', :podspec => "#{rn_path}/third-party-podspecs/DoubleConversion.podspec"
  pod 'glog', :podspec => "#{rn_path}/third-party-podspecs/glog.podspec"
  pod 'Folly', :podspec => "#{rn_path}/third-party-podspecs/Folly.podspec"

  # react-native-maps dependencies
  pod 'react-native-maps', path: rn_maps_path
  pod 'react-native-google-maps', path: rn_maps_path
  pod 'GoogleMaps'
  pod 'Google-Maps-iOS-Utils'
end

post_install do |installer|
  installer.pods_project.targets.each do |target|
    if target.name == 'react-native-google-maps'
      target.build_configurations.each do |config|
        config.build_settings['CLANG_ENABLE_MODULES'] = 'No'
      end
    end
    if target.name == "React"
      target.remove_from_project
    end
  end
end
~~~

Then run the following commnands:
```
cd ios
pod install
```

Do NOT run `react-native link` command for react-native-maps.
After that, use `.xcworkspace`, not `.xcproject`.

Insert Google Maps API key in AppDelegate.m

### Android

Do NOT run `react-native link` command for react-native-maps.

Insert Google Maps API key in AndroidManifest.xml
