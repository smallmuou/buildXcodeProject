buildXcodeProject
=================

build xcode project for distribute without source code

Usage
-----------------
>usage: $0 [-h] [-v] [-o output] project
>
>OPTIONS
>   -h       Display usage
>   -v       Display version information
>   -o       Set output directory


How to distribute iOS APP to Apple store(without apple developer id)
-----------------
###Way1:Join to developer team

From Apple Q&A : https://developer.apple.com/library/ios/qa/qa1763/_index.html

*  Join to developer team
*  Create a new distribution certificate according to Requesting Signing Identities. If the team distribution certificate already exists, it must be revoked and recreated by the build engineer according to Re-Creating Certificates and Updating Related Provisioning Profiles.
*  Create a distribution profile using the steps in Creating Store Provisioning Profiles.
*  Download and install the distribution provisioning profile by dragging it onto the Xcode or iTunes icons on the dock.
*  Define a Bundle Identifier in Xcode that is compatible with the App ID for the app using the steps in Setting the Bundle ID.
*  Assign the distribution provisioning profile to the 'Release' Code Signing Identity with the Xcode project Target level Build Settings.
*  Depending on your intended distribution method, follow the steps in Submitting Your App or Beta Testing your iOS App respectively.

###Way2:Static library or Framework

###Way3:Copy binary files to xcode project
*   Using buildXcodeProject.sh to build project
*   Remove all files from xcode project like .h .m .xib .png(except Info.plist, .lproj)
*   Add 'build' to xcode project
*   Change the bundle id, code sign
*   Rebuild project with xcode, and it will reproduct the .app with new distribute cer
*   Distribute app with xcode (build archive)
