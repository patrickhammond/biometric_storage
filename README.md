# biometric_storage

[![Pub](https://img.shields.io/pub/v/biometric_storage?color=green)](https://pub.dev/packages/biometric_storage/)

Encrypted file store, **optionally** secured by biometric lock 
for Android, iOS and MacOS. 

Meant as a way to store small data in a hardware encrypted fashion. E.g. to 
store passwords, secret keys, etc. but not massive amounts
of data.

On android uses androidx uses KeyStore and on iOS LocalAuthentication with KeyChain.

Check out [AuthPass Password Manager](https://authpass.app/) for a app which 
makes heavy use of this plugin.

## Versions

* Use 0.2.x for legacy plugin format for iOS and android support.
* Use 0.3.x-beta for the new platforms pubspec format which also supports mac OS.

## Getting Started

### Android
* Requirements:
  * Android: API Level >= 23
  * MainActivity must extend FlutterFragmentActivity
  * Theme for the main activity must use `Theme.AppCompat` thme.
    (Otherwise there will be crases on Android < 29)
    For example: 
    
    **AndroidManifest.xml**:
    ```xml
    <activity
    android:name=".MainActivity"
    android:launchMode="singleTop"
    android:theme="@style/LaunchTheme"
    ```

    **xml/styles.xml**:
    ```xml
        <style name="LaunchTheme" parent="Theme.AppCompat.NoActionBar">
        <!-- Show a splash screen on the activity. Automatically removed when
             Flutter draws its first frame -->
        <item name="android:windowBackground">@drawable/launch_background</item>

        <item name="android:windowNoTitle">true</item>
        <item name="android:windowActionBar">false</item>
        <item name="android:windowFullscreen">true</item>
        <item name="android:windowContentOverlay">@null</item>
    </style>
    ```

### iOS

https://developer.apple.com/documentation/localauthentication/logging_a_user_into_your_app_with_face_id_or_touch_id

* include the NSFaceIDUsageDescription key in your app’s Info.plist file
* Requires at least iOS 9

### Mac OS

* include the NSFaceIDUsageDescription key in your app’s Info.plist file
* enable keychain sharing and signing. (not sure why this is required. but without it
    You will probably see an error like: 
    > SecurityError, Error while writing data: -34018: A required entitlement isn't present.
* Requires at least Mac OS 10.12

## Resources

* https://developer.android.com/topic/security/data
* https://developer.android.com/topic/security/best-practices

