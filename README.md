# Config variables for React Native apps

Module to expose config variables to your javascript code in React Native, supporting both iOS and Android.

## Usage

Create a new file `env.json` in the root of your React Native app:

```
{
  "development": {
    "ENV": "development",
    "API_URL": "http://example.development",
    ...
  },
  "staging": {
    "ENV": "staging",
    "API_URL": "http://example.staging",
    ...
  },
  "production": {
    "ENV": "production",
    "API_URL": "http://example.production",
    ...
  }
}
```

Then access variables defined there from your app:

```js
import Config from 'react-native-config'

Config.API_URL  // 'http://example.development'
Config.ENV  // 'development'
```

### iOS

Read variables declared in `env.js` from your Obj-C classes like:

```objective-c
// import header
#import "ReactNativeConfig.h"

// then read individual keys like:
NSString *apiUrl = [ReactNativeConfig envFor:@"API_URL"];

// or just fetch the whole config
NSDictionary *config = [ReactNativeConfig env];
```

They're also available for configuration in `Info.plist`, by appending `__RN_CONFIG_` to their name:

```
__RN_CONFIG_API_URL
```

Note: Requires specific setup (see below) and a `Product > Clean` is required after changing the values to see the updated values.

### Different environments

Before you want to complie the code, you run the script react-native [run-android | run-ios]. Now you can run "react-native-config [run-android | run-ios] <ENV>". ENV is the enviroments you want to get configs. 

Example: react-native-config run-ios staging.
```js
import Config from 'react-native-config'

Config.API_URL  // 'http://example.staging'
Config.ENV  // 'staging'
```

By default ENV is development


## Setup

Install the package:

```
$ npm install react-native-config --save
```

Link the library:

```
$ react-native link react-native-config
```
