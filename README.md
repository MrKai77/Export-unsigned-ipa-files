# Making a unsigned ipa file from Xcode
>A short tutorial on making unsigned ipa files from Xcode!

## xcodeproj file
>Here's how to make an unsigned ipa file with a xcodeproj file. 
1. Open Terminal and write: `xcodebuild archive -project`.
2. Drag the xcodeproj file into the terminal.
3. Write ` -scheme ` and then write the scheme of the project that you want to compile.
4. Finally, write  `-archivePath unsigned.xcarchive -configuration Release CODE_SIGN_IDENTITY="" CODE_SIGNING_REQUIRED=NO CODE_SIGNING_ALLOWED=NO` and press `enter` to execute the command. This will generate a `unsigned.xcarchive` file in your current working directory (usually `~/`).
5. In Finder, find the `unsigned.xcarchive` and right click -> `Show Package Contents`.
6. Inside the `unsigned.xcarchive`, enter the `Products/` folder.
7. There will be a folder named `Applications`. Rename that to `Payload`.
8. Then, right click the `Payload` folder and click on `Compress "Payload"`.
9. Finally, rename the `Payload.zip` to `<APPNAME>.ipa`, with `<APPNAME>` replaced with the app's name (alternatively, you can leave it at `Payload.ipa`).
