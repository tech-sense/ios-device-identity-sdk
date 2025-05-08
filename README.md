# SenseOS - iOS SDK 

Sense is a device intelligence and identification tool. This tool collects a comprehensive set of attributes unique to a device or browser, forming an identity that will help businesses.

## Requirements
    * iOS 12.0 or above
    * Swift version 5.0 and above

### Step 1 - Installation
```
pod 'SenseOS', '~> 0.0.2'
pod update
```
### Step 2 - Import SDK
```
import SenseOS
```
To initialize the SDK add the below line of code.

```
    func initiateSense(){
        let senseOsConfig = SenseOSConfig()
        senseOsConfig.allowGeoLocation = false // true or false
        SenseOS.initSDK(senseOsConfig: senseOsConfig, withDelegate: self)
    }

```
#### Sense Config Information

If you pass allowGeoLocation as true in above config means, it will return Device Location Information in Sense Details.

### Step 3 - Implement  Delegate Method
Use the below code to obtain the Device result.
```
extension ViewController: SenseOSDelegate{
    func onFailure(message: String) {
        // Failure Callback.
    }
    func onSuccess(data: [String : Any]) {
        // Success Callback
    }
}
```
### Step 4 - Get Device Info
By call the following delegate to receive the device info shown below.
```
 SenseOS.getSenseDetails(withDelegate: self)
```
### Step 5 - Location Permission (optional)
You have to add this permission in Info.plist to get Device Location Information.

```
<key>NSLocationWhenInUseUsageDescription</key>
<string>This app needs access to your location to provide location-based services.</string>
<key>NSLocationAlwaysAndWhenInUseUsageDescription</key>
<string>Location access is required for enhanced app functionality.</string>
<key>NSLocationWhenInUseUsageDescription</key>
<string>Require to get user location</string>
```