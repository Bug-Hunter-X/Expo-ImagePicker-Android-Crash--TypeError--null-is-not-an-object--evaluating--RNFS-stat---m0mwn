# Expo ImagePicker Android Crash: TypeError: null is not an object (evaluating 'RNFS.stat')

This repository demonstrates a bug in Expo's ImagePicker on Android.  After selecting an image, the app intermittently crashes with a `TypeError: null is not an object (evaluating 'RNFS.stat')` error. This appears to be related to how ImagePicker interacts with the underlying RNFS library.

## Reproducing the Bug

1. Clone this repository.
2. Run `npm install` or `yarn install`.
3. Run the app on an Android emulator or device.
4. Attempt to select an image using the ImagePicker.
5. The app may crash with the aforementioned error.  The crash is not consistent; sometimes it works, sometimes it crashes.

## Potential Causes

The root cause might involve:

* **Asynchronous operations:** Race conditions in the handling of the selected image and the RNFS file system operations.
* **Permissions:** Though less likely, temporary permission issues could lead to the `null` reference.
* **Expo and RNFS Version Compatibility:** A compatibility problem between Expo's ImagePicker implementation and the version of RNFS used.

## Solution (bugSolution.js)

The solution involves adding robust error handling and potentially using a different approach for accessing the image's URI.