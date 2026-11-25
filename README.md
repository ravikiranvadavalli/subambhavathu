# Subambhavathu Android app (WebView wrapper)

This Android Studio project packages the existing live website `https://subambhavathu.in/` as an Android app. It keeps the website's PHP/MySQL forms and current maroon/gold/cream visual identity; it does not duplicate the backend or database.

## Included
- Android app label and package: `Subambhavathu` / `com.subambhavathu.app`
- Android WebView loading the HTTPS website
- JavaScript, DOM storage and cookies enabled for existing site workflows
- File chooser support for website registration uploads
- Android back button navigation
- External HTTPS, telephone and email links handed to Android
- No cleartext HTTP; external hosts are not loaded inside the app

## Build APK in Android Studio (Windows)
1. Install Android Studio (current stable) and open this folder (`SubambhavathuAndroid`).
2. Allow Android Studio to install Android SDK Platform 35 and Build Tools when prompted.
3. Use JDK 17 or newer (Android Studio's bundled JBR is recommended).
4. Wait for Gradle Sync to finish.
5. Select **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
6. The debug APK will be created at `app/build/outputs/apk/debug/app-debug.apk`.
7. Copy that APK to your Android phone and install it. For wider distribution, create a signed release APK using **Build > Generate Signed Bundle / APK**.

## Important integration note
The supplied PHP source has public enquiry forms, purohit/service-provider registration and an admin dashboard. It does not implement a customer sign-in/account area or customer booking-history page. Therefore this first app opens the existing site and its working enquiry flow; it does not claim customer accounts or booking history are connected. Those features require PHP/MySQL backend development first.

## Website requirement
The website must remain online and have a valid HTTPS certificate. This app is an online client, not an offline copy of the PHP/MySQL server.

## Build APK without installing Android Studio on your computer (GitHub cloud build)
This project includes `.github/workflows/build-apk.yml` so GitHub's hosted runner can build the APK using Java 17, Android SDK 35 and Gradle 8.9.

1. Create a free GitHub account and a new repository named `SubambhavathuAndroid`.
2. Upload the contents of this project folder (including the hidden `.github` folder) to the repository. Make sure `settings.gradle`, `build.gradle`, `app/` and `.github/` are at the repository root.
3. Open the repository's **Actions** tab and select **Build Subambhavathu APK**.
4. Click **Run workflow** and wait for the run to finish successfully.
5. Open the completed workflow run, scroll to **Artifacts**, and download `Subambhavathu-debug-apk`. Extract it to get `app-debug.apk`.
6. Transfer the APK to your Android phone and install it. Android may ask you to allow installation from that file manager/browser.

This produces a debug APK for testing. It is not a Play Store-signed release. The website must remain online and accessible over HTTPS.
