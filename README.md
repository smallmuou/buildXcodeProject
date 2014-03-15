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

*  Add the build engineer to the development team with the role of Admin through the Member Center. For more information on defining team roles, see Managing Your Team. The Admin role is required to manage the team distribution certificate.
*  If the distribution build will be submitted to the App Store, add the build engineer to the team users on iTunes Connect with the role of Technical User. This allows the build engineer to log into iTunes Connect with their own credentials while submitting the app. Skip this step if the build is being used for Ad Hoc beta testing. For more info about the Technical User role in iTunes Connect, see Managing Users in the iTunes Connect Developer Guide.
*  Create a new distribution certificate according to Requesting Signing Identities. If the team distribution certificate already exists, it must be revoked and recreated by the build engineer according to Re-Creating Certificates and Updating Related Provisioning Profiles.
*  Create a distribution profile using the steps in Creating Store Provisioning Profiles.
*  Download and install the distribution provisioning profile by dragging it onto the Xcode or iTunes icons on the dock.
*  Define a Bundle Identifier in Xcode that is compatible with the App ID for the app using the steps in Setting the Bundle ID.
*  Assign the distribution provisioning profile to the 'Release' Code Signing Identity with the Xcode project Target level Build Settings.
*  Depending on your intended distribution method, follow the steps in Submitting Your App or Beta Testing your iOS App respectively.

###Way2:Static library or Framework
*   Add static library target using xcode.
*   Add source code to the target.
*   Build static library target, and it will product .a
*   Add .a to the app target, and remove the source code.
*   Rebuild the app target, and will product the .app file.(Need -ObjC)
*   Distribute app with xcode (build archive)

###Way3:Copy binary files to xcode project
*   Using buildXcodeProject.sh to build project
*   Remove all files from xcode project like .h .m .xib .png(except Info.plist, .lproj)
*   Add 'build' to xcode project
*   Change the bundle id, code sign
*   Rebuild project with xcode, and it will reproduct the .app with new distribute cer
*   Distribute app with xcode (build archive)
