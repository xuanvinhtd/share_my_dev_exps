# Collection of the command line when work with react native project (Updating...)

## Run app with simulator

 1. iOS:
- Get list of name iOS simulator in your MacOS by command line:

  ```
  xcrun simctl list devices
  ```

- Run app with simulator name:

```
react-native run-ios --simulator="iPhone 6s"
react-native run-ios --simulator="iPhone 8 Plus"
react-native run-ios --simulator="iPad Pro (12.9-inch) (4th generation)"
eact-native run-ios --simulator="iPhone 11 Pro Max"
emulator -avd Samsung_Galaxy_Tab_S6_Lite_API_30
emulator -avd Pixel_XL_API_30
```

2. Android:

- Get list of name Android simulator in your MacOS by command line:

```
emulator -list-avds
```

Start android simulator with simulator name: emulator -avd [your avd name]

```
ex: emulator -avd Pixel_4_XL_API_30
```

After that run your app on simulator: `react-native run-android` to install and run your app on simulators that already started

In Case, pull new code and get error, you should `clean project` và `install package` again by command:

- Open Terminal, to root project.
- Run command: 

```
watchman watch-del-all && 
rm -rf node_modules/ &&
yarn cache clean &&
yarn install && cd ios && pod install && cd ..  &&
yarn start -- --reset-cache
```

!> Note: When pull code, If have more new UI or new package, you should run above command.


```
yarn clean:android && yarn clean:ios && watchman watch-del-all && rm -rf node_modules/ && yarn cache clean && yarn install && cd ios && pod install && cd .. && react-native link && yarn start -- --reset-cache
```


?> Updating....