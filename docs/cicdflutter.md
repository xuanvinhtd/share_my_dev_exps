# Template script to setup CI-CD with firebase

## Template Script

?> This is a template script, use mus change something to apply your project.

### Android

[fastfile_android_flutter.rb](_snippets/cicd/fastfile_android_flutter.rb.md ':include')

### iOS

[fastfile_ios_flutter.rb](_snippets/cicd/fastfile_ios_flutter.rb.md ':include')

## How to use

### Install Setup CI-CD
- Required: ruby 2.7.2
- Required: MacOS

1. Install Bundle by command below:
```
gem install bundler
```

2. Install fastlane + firebase by run command below:
```
bundle install
```

### How to use CI-CD to deploy app to the firebase?

1. Change the release note in Android vs iOS project.
    - Goto root project/android/fastlane/Fastfile and change the release note at 38 line:
    Ex:
    ```
    release_note = "Fixed something"
    ```

    - Goto root project/ios/fastlane/Fastfile and change the release note at 35 line:
    Ex:
    ```
    release_note = "Fixed something"
    ```

2. Run script to auto build and deploy app:
    - Open terminal and goto root project/
    - Run script below:
    Note: Must change build_name vs build_number before run this script below!
    
    ```
    cd android && bundle exec fastlane deploy_dev_app_to_firebase build_name:1.0.0 build_number:1 && cd .. && cd ios && bundle exec fastlane deploy_dev_app_to_firebase build_name:1.0.0 build_number:1 && cd ..
    ```