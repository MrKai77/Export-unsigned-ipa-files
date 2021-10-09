# Making a unsigned ipa file from Xcode
>A short tutorial on making unsigned ipa files from Xcode!

## 1. Listing Schemes of a Project
>Before you start the archive process, I reccomend finding the scheme of your project.

### Xcodeproj File
* Open Terminal and write: `xcodebuild -list -project ` and drag the xcodeproj file into the terminal and press `enter` to execute the command.

### Xcworkspace File
* Open Terminal and write: `xcodebuild -list -workspace ` and drag the xcworkspace file into the terminal and press `enter` to execute the command.

## Xcodeproj File
>Here's how to make an unsigned ipa file with a xcodeproj file. 
1. Open Terminal and write: `xcodebuild archive -project`.
2. Drag the xcodeproj file into the terminal.
3. Write ` -scheme ` and then write the scheme of the project that you want to compile.
4. Finally, write `-archivePath unsigned.xcarchive -configuration Release CODE_SIGN_IDENTITY="" CODE_SIGNING_REQUIRED=NO CODE_SIGNING_ALLOWED=NO` and press `enter` to execute the command. This will generate a `unsigned.xcarchive` file in your current working directory (usually `~/`).
5. In Finder, find the `unsigned.xcarchive` and right click -> `Show Package Contents`.
6. Inside the `unsigned.xcarchive`, enter the `Products/` folder.
7. There will be a folder named `Applications`. Rename that to `Payload`.
8. Then, right click the `Payload` folder and click on `Compress "Payload"`.
9. Finally, rename the `Payload.zip` to `<APPNAME>.ipa`, with `<APPNAME>` replaced with the app's name (alternatively, you can leave it at `Payload.ipa`).

Here's the full terminal command for more advanced users:  
`xcodebuild archive -project <XCODEPROJ> -scheme <SCHEME> -archivePath unsigned.xcarchive -configuration Release CODE_SIGN_IDENTITY="" CODE_SIGNING_REQUIRED=NO CODE_SIGNING_ALLOWED=NO`  
Make sure to replace `<XCODEPROJ>` and `<SCHEME>` with the xcodeproj file and scheme respectively!

## Xcworkspace File
>Here's how to make an unsigned ipa file with a xcworkspace file. 
1. Open Terminal and write: `xcodebuild -workspace `.
2. Drag the xcworkspace file into the terminal.
3. Write ` -scheme ` and then write the scheme of the project that you want to compile.
4. Finally, write ` -configuration Release clean archive -archivePath unsigned.xcarchive CODE_SIGN_IDENTITY=”” CODE_SIGNING_REQUIRED=NO CODE_SIGNING_ALLOWED=NO` and press `enter` to execute the command. This will generate a `unsigned.xcarchive` file in your current working directory (usually `~/`).
5. In Finder, find the `unsigned.xcarchive` and right click -> `Show Package Contents`.
6. Inside the `unsigned.xcarchive`, enter the `Products/` folder.
7. There will be a folder named `Applications`. Rename that to `Payload`.
8. Then, right click the `Payload` folder and click on `Compress "Payload"`.
9. Finally, rename the `Payload.zip` to `<APPNAME>.ipa`, with `<APPNAME>` replaced with the app's name (alternatively, you can leave it at `Payload.ipa`).

Here's the full terminal command for more advanced users:  
`xcodebuild -workspace <XCWORKSPACE> -scheme <SCHEME> -configuration Release clean archive -archivePath unsigned.xcarchive CODE_SIGN_IDENTITY=”” CODE_SIGNING_REQUIRED=NO CODE_SIGNING_ALLOWED=NO`  
Make sure to replace `<XCWORKSPACE>` and `<SCHEME>` with the xcodeproj file and scheme respectively!
