# @adrianha/react-native-midtrans

## Getting started

`$ npm install @adrianha/react-native-midtrans --save`

### Manual installation

#### iOS using Cocoapods

1. Navigate to ios/
2. Run `pod install`

#### iOS

1. In XCode, in the project navigator, right click `Libraries` ➜ `Add Files to [your project's name]`
2. Go to `node_modules` ➜ `@adrianha/react-native-midtrans` and add `ReactNativeMidtrans.xcodeproj`
3. In XCode, in the project navigator, select your project. Add `libReactNativeMidtrans.a` to your project's `Build Phases` ➜ `Link Binary With Libraries`
4. Run your project (`Cmd+R`)

#### Android

1. Open up `android/app/build.gradle`

Add this.

```
repositories {
    jcenter()
    // Add the midtrans repository into the list of repositories
    maven { url "http://dl.bintray.com/pt-midtrans/maven" }
    maven { url "https://jitpack.io" }
}
```

2. In `android/app/build.gradle`

Add this line 

```
// For using the Midtrans Sandbox
implementation 'com.midtrans:uikit:1.23.0-SANDBOX' // change the number to the latest version
// For using the Midtrans Production
implementation 'com.midtrans:uikit:1.23.0' // change the number to the latest version
```

For see the version. https://github.com/veritrans/veritrans-android/releases

## Usage

1. Create Midtrans instance

```javascript
import Midtrans from '@adrianha/react-native-midtrans';

const midtrans = new Midtrans({
  clientKey: 'CLIENT_KEY',
  baseUrl: 'BASE_URL',

  /** iOS only: Midtrans.ENVIRONMENT_SANDBOX | Midtrans.ENVIRONMENT_PRODUCTION */
  environment: Midtrans.ENVIRONMENT_SANDBOX,

  /** android only */
  colorTheme: {
    primaryColor: '#000000',
  },
});
```

2. Pay with SNAP token

```javascript
try {
  const result = await midtrans.startPaymentWithSnapToken('SNAP_TOKEN');
  console.log({ result });
} catch (e) {
  console.log(e);
}
```
