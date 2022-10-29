# Exporting an unsigned `.ipa` file from Xcode
Follow steps 1️⃣,2️⃣ & 3️⃣ to successfully make an unsigned `.ipa` file!

### 1️⃣ Listing Schemes of a Project

#### `.xcodeproj` File
* Open Terminal and write `xcodebuild -list -project <XCODEPROJ>`, then replace the `<XCODEPROJ>` with your `.xcodeproj` file and execute the command.

#### `.xcworkspace` File
* Open Terminal and write `xcodebuild -list -workspace <XCWORKSPACE>`, then replace the `<XCWORKSPACE>` with your `.xcworkspace` file and execute the command.

### 2️⃣ Making a `.xcarchive` of your Project

#### `.xcodeproj` File
* In Terminal, write `xcodebuild archive -project <XCODEPROJ> -scheme <SCHEME> -archivePath unsigned.xcarchive -configuration Release CODE_SIGN_IDENTITY="" CODE_SIGNING_REQUIRED=NO CODE_SIGNING_ALLOWED=NO` where `<XCODEPROJ>` and `<SCHEME>` are replaced with the xcodeproj file and scheme name respectively.* Then, execute the command.  

#### `.xcworkspace` File
* In Terminal, write `xcodebuild -workspace <XCWORKSPACE> -scheme <SCHEME> -configuration Release clean archive -archivePath unsigned.xcarchive CODE_SIGN_IDENTITY=”” CODE_SIGNING_REQUIRED=NO CODE_SIGNING_ALLOWED=NO`  where `<XCWORKSPACE>` and `<SCHEME>` are replaced with the xcworkspace file and scheme name respectively.* Then, execute the command.  

> *If the scheme contains spaces, make sure to use quotes!

### 3️⃣ Making the `.ipa` File

1. First, find the `unsigned.xcarchive` file you created in step 2 and click `Show Package Contents` to enter it.
2. Enter the `Products` folder and rename the `Applications` folder to `Payload`.
3. Click on `Compress "Payload"` to make a zip file of the folder.
4. Finally, rename the `Payload.zip` to `<APPNAME>.ipa`, where `<APPNAME>` is the app's name.

### 🎉 Congratulations, you have successfully created a unsigned `.ipa` file of your app!

⭐️ If you thought this was helpful, please fork & star this repository!
