```ruby
# Have an easy way to get the root of the project
def root_path
  Dir.pwd.sub(/.*\Kfastlane/, '').sub(/.*\Kandroid/, '').sub(/.*\Kios/, '').sub(/.*\K\/\//, '')
end

# Have an easy way to run flutter tasks on the root of the project
lane :sh_on_root do |options|
  command = options[:command]
  sh("cd #{root_path} && #{command}")
end

# Tasks to be reused on each platform flow
lane :fetch_dependencies do
  sh_on_root(command: "flutter pub get")
end

default_platform(:ios)

platform :ios do
  desc "Deploy Dev app to Firebase distribution"
  lane :deploy_dev_app_to_firebase do |options|
    sh_on_root(command: "flutter clean")
    fetch_dependencies
    
    update_code_signing_settings(
    use_automatic_signing: false,
    path: "#{root_path}/ios/Runner.xcodeproj",
    team_id: "CGP8PQM2AF"
    )

    install_provisioning_profile(path: "#{root_path}/ios/provisioning/slots_adhoc.mobileprovision")

    build_number = options[:build_number]
    build_name = options[:build_name]
    release_note = "Test Deploy"

    sh_on_root(command: "flutter build ipa --release --no-sound-null-safety --flavor prod --build-name=#{build_name} --build-number=#{build_number} --export-options-plist=ios/ExportOptions_firebase.plist")

    firebase_app_distribution(
      app: "1:623458129219:ios:4734f81443cf10c5984bf6", 
      firebase_cli_token:'1//0gAdo2QgpwDUKCgYIARAAGBASNwF-L9IrSqaoWGhdVLM_rCQvL_OrkCTr3VFCehnfipx3RvCAEflu22iqR9OmKNTBbKAl4Duy8-M',
      testers:'vinh.hx@hikotech.io',
      groups: "HIKO-Tester",
      release_notes: release_note,
      ipa_path: "#{root_path}/build/ios/ipa/base_architecture.ipa",
    )
  end
end
```