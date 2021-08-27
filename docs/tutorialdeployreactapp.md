# How to Deploy react native app by fastlance + firebase + telegram bot

## Install and setup environment

- [Setup CI/CD](setupcicdenv.md)

## How to deploy react native app.

!> Note: You go to root project and Use must run `yarn ios` and `yarn android` to compiler all the file, before run script build apk or ipa.

1. Change version app:

Android:
- Goto your project/android/app/build.gradle and change version(`versionCode`, `versionName`) for an app:
```
 defaultConfig {
        applicationId "com.xxx.xxx"
        minSdkVersion rootProject.ext.minSdkVersion
        targetSdkVersion rootProject.ext.targetSdkVersion
        versionCode 1
        versionName "1.0.0"
    }
```

iOS:
- Goto your project/ios/fastlance/Fastfile and change version(`version_number`) for an app:
```
  increment_version_number(
  version_number: "1.0.0",
  xcodeproj: "#{root_path}/ios/xxx.xcodeproj"
 )
```
!> Note: You must change the app version because if the current app is the same as the version of the previous app. We cannot upload a new build.

2. Change release note:

Android:
Goto root project/android/fastlane/Fastfile and fine the keyword: `release_notes` to change release note:
```
release_notes:'Fix bug something...'
```

iOS:
Goto root project/ios/fastlane/Fastfile and fine the keyword: `release_notes` to change release note:
```
release_notes:'Fix bug something...'
```

?> Note: This step is optional

2. Go to root project and run command line to start CI/CD for the deploy your app by automation:
```
yarn android:beta && yarn ios:beta
```

Now, let your CI/CD deploy your app to firebase and auto-notify with QC by Telegram. You can track CI/CD progress in your terminal.
