
<p align="center">
  <img alt="react-native-ble-plx" src="logo.png" />
</p>

React Native Bluetooth Low Energy library using [RxBluetoothKit](https://github.com/Polidea/RxBluetoothKit) and [RxAndroidBle](https://github.com/Polidea/RxAndroidBle) as it's backend libraries.

Example apps are available in [Google Play](https://play.google.com/store/apps/details?id=com.polidea.sniffator) and [App Store](https://itunes.apple.com/us/app/sniffator/id1147266354?ls=1&mt=8)!

[![GooglePlay](googleplay.png)](https://play.google.com/store/apps/details?id=com.polidea.sniffator) [![AppStore](appstore.png)](https://itunes.apple.com/us/app/sniffator/id1147266354?ls=1&mt=8)

---

[![NPM](https://nodei.co/npm/react-native-ble-plx.png?downloads=true)](https://nodei.co/npm/react-native-ble-plx/)

---

## Recent Changes

**0.4.0**
- Renamed `Device.uuid` to `Device.id`, `Service.deviceUUID` to `Service.deviceID`, `Characteristic.deviceUUID` to `Characteristic.deviceID`
- Updated to Swift 3.0
- Documentation was moved to ./doc folder and now is generated by ESDoc.

## Documentation

Checkout ./doc folder or visit site: .

## Configuration & Installation

**iOS:**
* Add `react-native-ble-plx` to a project as a dependency in `package.json` file.
  For example `"react-native-ble-plx": "Polidea/react-native-ble-plx"` will install
  latest version from Polidea's Github repository.
* Make sure that you have [Carthage](https://github.com/Carthage/Carthage) installed on your system.
* Execute `npm install` to fetch and install a library.
* Open iOS project located in `./ios` folder.
* Move `BleClient.xcodeproj` located in `.node_modules/react-native-ble-plx/ios`
  using drag & drop to `Libraries` folder in your project.
* In general settings of a target add `libBleClient.a` to Linked Frameworks and Libraries.
* In `Build Settings`/`Search Paths`/`Framework search paths` add path: `$(SRCROOT)/../node_modules/react-native-ble-plx/ios/BleClientManager/Carthage/Build/iOS`.  
* In `Build Settings`/`Build Options`/`Always Embed Swift Standard Libraries` set to `Yes`.
* In `Build Phases` click on top left button and add `New Run Script Phase`. 
  * Shell command: `/usr/local/bin/carthage copy-frameworks`
  * Input Files:
    * `$(SRCROOT)/../node_modules/react-native-ble-plx/ios/BleClientManager/Carthage/Build/iOS/BleClientManager.framework`
    * `$(SRCROOT)/../node_modules/react-native-ble-plx/ios/BleClientManager/Carthage/Build/iOS/RxSwift.framework`
    * `$(SRCROOT)/../node_modules/react-native-ble-plx/ios/BleClientManager/Carthage/Build/iOS/RxBluetoothKit.framework`
* Minimal supported version of iOS is 8.0

**Android**:
* Add `react-native-ble-plx` to a project as a dependency in `package.json` file.
  For example `"react-native-ble-plx": "Polidea/react-native-ble-plx"` will install
  latest version from Polidea's Github repository.
* Execute `npm install` to fetch and install a library.
* Open Android project located in `./android` folder.
* In `settings.gradle` add following lines:
```
include ':react-native-ble-plx'
project(':react-native-ble-plx').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-ble-plx/android')
```
* In `build.gradle` of `app` module add following dependency:
```
dependencies {
   ...
   compile project(':react-native-ble-plx')
   ...
```
* Additionaly make sure that min SDK version is at least 18:
```
android {
    ...
    defaultConfig {
        minSdkVersion 18
        ...
```

* In `MainApplication.getPackages` import and add BleModule package:
```
import com.polidea.reactnativeble.BlePackage;
...

public class MainApplication extends Application implements ReactApplication {
    ...

    @Override
    protected List<ReactPackage> getPackages() {
      return Arrays.<ReactPackage>asList(
        new MainReactPackage(),
        new BlePackage()
      );
}
```
* In `AndroidManifest.xml` add Bluetooth permission and update or remove `<uses-sdk/>`:
```
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    ...
    <uses-permission android:name="android.permission.BLUETOOTH" />

    <uses-sdk
        android:minSdkVersion="18"
        ...
```
