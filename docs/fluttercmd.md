# Getting Started

## Template Project Environment

- environment:
    Flutter sdk: ">=2.7.0 <3.0.0"
- Xcode 12.4
- Android 3.6
- Ruby 2.7.2
- Pod 1.10.1

## Run Template Project

1. Start a iOS/Android simulator
2. Run below commannds on the terminal

```
flutter clean & flutter pub get
// Development
flutter run --flavor dev -t lib/main_dev.dart
// Staging
flutter run --flavor stg -t lib/main_stg.dart
// Product
flutter run --flavor pro -t lib/main_pro.dart
```

## Build Template Project

1. Run the below commannds on the terminal

### Android
#### Build APK with mode release

```
// Development
flutter clean && flutter build apk --flavor dev -t lib/main_dev.dart --release
// Staging
flutter clean && flutter build apk --flavor stg -t lib/main_stg.dart --release
// Product
flutter clean && flutter build apk --flavor pro -t lib/main_pro.dart --release
```

#### Build AAB with mode debug

```
// Development
flutter clean && flutter build appbundle --flavor dev -t lib/main_dev.dart --debug
// Staging
flutter clean && flutter build appbundle --flavor stg -t lib/main_stg.dart --debug
// Product
flutter clean && flutter build appbundle --flavor pro -t lib/main_pro.dart --debug
```

#### Build APK with mode debug

```
// Development
flutter clean && flutter build apk --flavor dev -t lib/main_dev.dart --debug
// Staging
flutter clean && flutter build apk --flavor stg -t lib/main_stg.dart --debug
// Product
flutter clean && flutter build apk --flavor pro -t lib/main_pro.dart --debug
```

#### Build Bundle with mode debug/release

Like with the above commands, we need to change "apk" to "bundle"

### iOS

#### Build iOS with mode debug

```
flutter build ios --debug --flavor dev
flutter build ios --debug --flavor stg
flutter build ios --debug --flavor pro
```

#### Build iOS with mode release

```
flutter build ios --release --flavor dev
flutter build ios --release --flavor stg
flutter build ios --release --flavor pro
```

## Features

- Structure project for Flutter
- Config evironment(Dev,Prod)
- Setup multiple language(vn, en) & Sample
- Setup Light/Dart Theme
- Logic code used BLOC & Sample
- Core network use Dio & Sample
- Core Sqlite & Sample
- Show the log
- Setup Lint Rules by Google rules
- Step CI/CD

## Plugins

- Flutter 2.0.6
- intl: ^0.17.0
- equatable: ^2.0.2
- flutter_bloc: ^7.0.1
- dio: ^4.0.0
- pretty_dio_logger: ^1.1.1
- cached_network_image: ^3.0.0
- sqflite_sqlcipher: ^2.0.0
- crypto: ^3.0.1
- pedantic: ^1.11.0

## Upgrading the Flutter
### SDK

```
flutter upgrade
```
### packages

```
flutter pub upgrade
```

## Install Flutter vs Create App on macOS

-[Tutorial](https://flutter.dev/docs/get-started/install/macos)
- Create app by command:

```
flutter create my_app
cd my_app
flutter runs
```

## Setup CI/CD with Firebase, Fastlane, Testflight, GitHub Action

### Setup
- Install rbenv to manage multiple Ruby version.

```
brew install rbenv
```

Check sheet for [rbenv](https://devhints.io/rbenv)

- Install bundle - Bundler provides a consistent environment for Ruby projects by tracking and installing the exact gems and versions that are needed..)

```
gem install bundler
```

- Install Fastlane on MacOS - [Tutorial](https://docs.fastlane.tools/)
- Install firebase for Android - [Tutorial](https://firebase.google.com/docs/app-distribution/android/distribute-fastlane)
- Install firebase for iOS - [Tutorial](https://firebase.google.com/docs/app-distribution/ios/distribute-fastlane)

- Note: If not permission, you must add 'sudo' first the commands.

## Init with new project
You must go to root of android/ios finder of your project to run the below commands:
- Add gem file:

```
bundle init
```

- Open gem file to add ruby version for this project

```
ruby "=2.7.2" # It compatible with fastlane version
```

Note: If your mac have not ruby 2.7.2, you use rbenv to install it and set this project use this ruby version(rbenv local 2.7.2)
- Add fastlane:

```
fastlane init
```

- Add firebase distribution and authenticate, get ci token

```
bundle exec fastlane add_plugin firebase_app_distribution
bundle exec fastlane run firebase_app_distribution_login
```

- Setup github action
- create file workflow/main.yml(view in source)

- Setup `json_key_file` on Google play console to upload file to release
- Setup p8 file on Apple Develop account to upload file to release/Testflight
- Add trigger in fastlane file

## Init with old project
- Just install version ruby in Gem file by rbenv
- Go to android/ios directory and run command bellow:

```
bundle install
```
## Run
- Trigger when we start run github action
- Push code to github and see GitHubAction run it on cloud(github)
- You can run script on local to auto build + test + deploy app(AppStore/TestFlight/GoogleConsole, Firebase)

- Note:
=> Android:
    - Setup keystore vs properties key
=> iOS:
    - Setup file provisioning vs Cer
    - You must get file ExportOptions.plist to genarate file ipa.
    - When you export  api file by buld type(appstore/add-hoc/development/), in finder of ipa file which you just export, you can see file ExportOptions.plist for each build type
    - Get this file and setup in fastlane to automate export ipa file.
    - Use the p8 key that generate from appstoreconnect web.(Use authentiate with appstoreconnect, to release app)


### Trigger to start run github action
- Only start run gihub action when push code to branch name: deploy_app_to_firebase

Note: Before you merge and push code to the branch(deploy_app_to_firebase), you must setting "build_number,build_name, release_note" in main.yml file. If you need them change:

```
options: '{"build_number": "1", "build_name": "1.0.3", "release_note": "Test add parameter"}'
```

## Example script to run local

##### iOS

- Deploy iOS Dev App to firebase Distribution:

```
bundle exec fastlane deploy_dev_app_to_firebase
```

- Deploy iOS Prod App to firebase Distribution:

```
bundle exec fastlane deploy_pro_app_to_firebase
```

- Deploy iOS Prod App to TestFlight:

```
bundle exec fastlane deploy_pro_app_to_testflight
```

- Deploy iOS Prod App to AppStore:

```
bundle exec fastlane deploy_pro_app_to_appstore
```

Note: If setup testflight authentication, should flow [here](https://sarunw.com/posts/using-app-store-connect-api-with-fastlane-match/)

##### Andriod

- Deploy APK of Dev App to firebase Distribution:

```
bundle exec fastlane deploy_dev_app_to_firebase
```

- Deploy APK of Prod App to firebase Distribution:

```
bundle exec fastlane deploy_prod_app_to_firebase
```


### Sample Code
- We have 2 env:
    1. Your device(MacOS, Win..) - Local
    2. Your cloud(Github, Travis, Aws...) - Cloud
- We can view exsample in source at file:
    1. .github/workfolow/main.yml
    2. android/Gemfile
    3. android/Fastlane/...
    4. ios/Gemfile
    5. ios/Fastlane/...

Note: If build fail the iOS on Cloud: ' The Xcode project defines schemes: dev' -> Use must set checked "share scheme" for eache scheme(stg, dev) to buld app by command line.

### More
- Check KeyStore in file apk or AppBundle
APK file:

```
keytool -printcert -jarfile app.apk
```

ABB file:

```
keytool -printcert -jarfile app.aab user_id
```
### Clean Flutter Project

```
flutter clean
flutter pub cache repair && 
flutter clean && flutter packages get
```
### Error Pod


```
1. flutter clean
rm -Rf ios/Pods
rm -Rf ios/.symlinks
rm -Rf ios/Flutter/Flutter.framework
rm -Rf ios/Flutter/Flutter.podspec
2. Remove Podfile
rm ios/Podfile
3. Run App
flutter pub get && flutter run --flavor dev -t lib/main_dev.dart
```

### Genarate KeyStore

```
keytool -genkey -v -keystore CastDiceFree.jks -storepass cdfree20210504 -alias CastDiceFreeKey -keypass 20200504 -keyalg RSA -keysize 2048 -validity 10000
```

## Reference
- [Flutter website](https://flutter.dev/)
- [Flutter Plugin website](https://pub.dev/)

## Copyright & License

This open source project authorized by Vinh Ho.X(hoxuanvinhuit93@gmail.com), and the license is MIT.
