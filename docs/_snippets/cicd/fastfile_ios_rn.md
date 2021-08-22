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

default_platform(:ios)

def root_path
  Dir.pwd.sub(/.*\Kfastlane/, '').sub(/.*\Kandroid/, '').sub(/.*\Kios/, '').sub(/.*\K\/\//, '')
end

lane :sh_on_root do |options|
  command = options[:command]
  sh("cd #{root_path}/ios && #{command}")
end

platform :ios do
  desc "Deploy [Dev] Con Voi to Firebase"
  lane :beta do
    install_provisioning_profile(path: "#{root_path}/ios/provisioning/adhoc_con_voi.mobileprovision")

    update_project_provisioning( 
     xcodeproj: "con_voi.xcodeproj",
     target_filter: "con_voi", 
     profile: "#{root_path}/ios/provisioning/adhoc_con_voi.mobileprovision",
  )
  update_project_team( # Set the right team on your project
   teamid: "CGP8PQM2AF"
  )

  sh_on_root(command: "pod install")

  increment_version_number(
  version_number: "1.0.0",
  xcodeproj: "#{root_path}/ios/con_voi.xcodeproj"
 )

  build_app(
  export_method: "ad-hoc",
  export_options:"#{root_path}/ios/ExportOptions.plist",
  build_path: "./builds",
  output_directory: "./builds",
  output_name: "con_voi.ipa",
)

    firebase_app_distribution(
      app: "1:624924003232:ios:b812939bf96551fa4c72c5",
      firebase_cli_token:'1//0gAdo2QgpwDUKCgYIARAAGBASNwF-L9IrSqaoWGhdVLM_rCQvL_OrkCTr3VFCehnfipx3RvCAEflu22iqR9OmKNTBbKAl4Duy8-M',
      testers:'vinh.hx@hikotech.io',
      groups: "HIKO-Tester",
      release_notes: "Menu, Login, Register UI/FUNC - Please only test on phone - UI on Ipad/Table not ready!",
      android_artifact_path: "#{root_path}/ios/builds/con_voi.ipa"
    )
  end
end
```