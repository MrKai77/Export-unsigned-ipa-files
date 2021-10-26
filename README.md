# Making a unsigned ipa file from Xcode

### 1. Listing Schemes of a Project

#### Xcodeproj File
* Open Terminal and write: `xcodebuild -list -project ` and drag the xcodeproj file into the terminal and press `enter` to execute the command.

#### Xcworkspace File
* Open Terminal and write: `xcodebuild -list -workspace ` and drag the xcworkspace file into the terminal and press `enter` to execute the command.

### 2. Making a Xcarchive of your Project

#### Xcodeproj File
* Open Terminal and write: `xcodebuild archive -project <XCODEPROJ> -scheme <SCHEME> -archivePath unsigned.xcarchive -configuration Release CODE_SIGN_IDENTITY="" CODE_SIGNING_REQUIRED=NO CODE_SIGNING_ALLOWED=NO` with `<XCODEPROJ>` and `<SCHEME>` replaced with the xcodeproj file and scheme name respectively. 

#### Xcworkspace File
* Open Terminal and write: `xcodebuild -workspace <XCWORKSPACE> -scheme <SCHEME> -configuration Release clean archive -archivePath unsigned.xcarchive CODE_SIGN_IDENTITY=”” CODE_SIGNING_REQUIRED=NO CODE_SIGNING_ALLOWED=NO`  with `<XCWORKSPACE>` and `<SCHEME>` replaced with the xcworkspace file and scheme name respectively. 

### 3. Making the Ipa File

1. First, find the `unsigned.xcarchive` file you created in step 2 and `Show Package Contents` to enter it.
2. Enter the `Products` folder and rename the `Applications` folder to `Payload`.
3. Click on `Compress "Payload"` to make a zip file of the folder.
4. Finally, rename the `Payload.zip` to `Payload.ipa`.

### Congratulations, you have successfully created a unsigned ipa file of your app!
>Sideload the unsigned ipa file with Altstore or Sideloadly on a jailed iDevice!  
>Alternatively, install it with AppSync Unified on a jailbroken iDevice!
