```ruby
# This file contains the fastlane.tools configuration
# You can find the documentation at https://docs.fastlane.tools
#
# For a list of all available actions, check out
#
#     https://docs.fastlane.tools/actions
#
# For a list of all available plugins, check out
#
#     https://docs.fastlane.tools/plugins/available-plugins
#

# Uncomment the line if you want fastlane to automatically update itself
# update_fastlane

def root_path
  Dir.pwd.sub(/.*\Kfastlane/, '').sub(/.*\Kandroid/, '').sub(/.*\Kios/, '').sub(/.*\K\/\//, '')
end

default_platform(:android)

platform :android do
  desc "Runs all the tests"
  lane :test do
    gradle(task: "test")
  end

  desc "Deploy [Dev] Con Voi to Firebase"
  lane :beta do
    gradle(task: 'clean')
    gradle(task: 'assemble', 
      build_type: 'release',
      properties: {
        "versionCode" => 1,
        "versionName" => "1.0.0",
    })

    firebase_app_distribution(
      app: "1:624924003232:android:3caac97ae4af35894c72c5",
      firebase_cli_token:'1//0gAdo2QgpwDUKCgYIARAAGBASNwF-L9IrSqaoWGhdVLM_rCQvL_OrkCTr3VFCehnfipx3RvCAEflu22iqR9OmKNTBbKAl4Duy8-M',
      testers:'vinh.hx@hikotech.io',
      groups: "HIKO-Tester",
      release_notes: "Menu, Login, Register UI/FUNC - Please only test on phone - UI on Ipad/Table not ready!",
      android_artifact_path: "#{root_path}/android/app/build/outputs/apk/release/app-release.apk"
    )
  end

  desc "Deploy a new version to the Google Play"
  lane :deploy do
    gradle(task: "clean assembleRelease")
    upload_to_play_store
  end
end
```