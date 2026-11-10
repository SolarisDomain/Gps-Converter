# GPS Converter for Android

This is an Android Studio project wrapping a fully local HTML/JavaScript coordinate converter in an Android WebView.

## Build the APK
1. Install Android Studio (or Android SDK + Gradle).
2. Open this folder as an Android Studio project.
3. Allow Gradle sync; install Android SDK Platform 35 and Build Tools when prompted.
4. Select **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
5. The debug APK will be at `app/build/outputs/apk/debug/app-debug.apk`.

## Install on your phone
Copy `app-debug.apk` to the Android phone, open it, and allow installation from that file manager when Android asks. Launch **GPS Converter**. Tap **Use My Live Device GPS** and grant location permission when prompted.

## Build without Android Studio (GitHub Actions)
Push this project to a GitHub repository. The included workflow builds a debug APK and attaches it to the workflow run as an artifact.

## Offline behavior
The app's HTML, CSS, and JavaScript are packaged in `app/src/main/assets/index.html`; no web server, CDN, or internet connection is needed. GPS requires Android location services and permission but coordinate conversion works offline.

## Important coordinate accuracy notes
- UTM and ECEF use WGS84 formulas.
- The MGRS output in this first Android build is a simplified grid formatter and should be independently checked before survey, navigation, emergency, or other safety-critical use. The input parser does not claim full MGRS decoding.
- Plus Code output is a lightweight 10-digit pair-code implementation; verify the result with an authoritative Open Location Code implementation before relying on it.
- What3words is not implemented. The original `W3W-GRID` routine was only a geohash-derived placeholder and was not a genuine What3words conversion.
- UTM zone edge exceptions (Norway/Svalbard) are not specially handled.
