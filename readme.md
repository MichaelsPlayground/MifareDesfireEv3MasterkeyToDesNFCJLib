# Mifare DESFire EV3 Masterkey to DES using NFCjLib

## Purpose of the app

This app has a limited use case: it changes the Master Application Key ("MAK") from a default **AES key** to a default **DES key**.

The default AES key is 16 bytes long and filled with 16 0x00 values, the default DES key is filled with 8 * 0x00 values.

```plaintext
default AES-Key: 00000000000000000000000000000000
default DES-Key: 0000000000000000
```

The key is **changed immediately after tapping without any further confirmation** the tag to the NFC reader, so be careful if you 
really want to change the key. The app is just checking that the "old" MAK is of type AES and then authenticates the Master 
Application with the default AES key: If the authentication is success the key is changed.

This app is useful to reset the tag to factory settings but the change depends on the master application settings: if the configuration 
is frozen no change is possible.

## Library used for this app

This app is using the NFCjLib library from **Desfire Tools for Android** available on GitHub here:
https://github.com/skjolber/desfire-tools-for-android.

It was written by Thomas Skjølberg ("skjolber") and this one is the best available source for accessing 
NXP's Mifare DESFire tags. 

About the license situation: The library itself has no dedicated license information but the library is a combination of 2 sub 
libraries with own licenses:
- nfcjlib - [Modified BSD License (3-clause BSD)](https://github.com/skjolber/desfire-tools-for-android/blob/master/nfcjlib/LICENSE)
- libfreefare - [LGPL 3.0 with classpath exception](https://github.com/skjolber/desfire-tools-for-android/blob/master/libfreefare/LICENSE)
- everything else - [Apache 2.0](http://www.apache.org/licenses/LICENSE-2.0.html)

## License of this app

This app is under [Apache 2.0 license](license.md)

## Background informtion

If you are trying to get basic information's about the DESFire tag the first contact point is the manufacturer's datasheet, available here:
- DESFire EV1 MF3ICDX21_41_81_SDS: https://www.nxp.com/docs/en/data-sheet/MF3ICDX21_41_81_SDS.pdf
- DESFire EV2 MF3DX2_MF3DHX2_SDS: https://www.nxp.com/docs/en/data-sheet/MF3DX2_MF3DHX2_SDS.pdf
- DESFire EV3 MF3D(H)x3: https://www.nxp.com/docs/en/data-sheet/MF3DHx3_SDS.pdf
- DESFire EV3 Quick start guide: https://www.nxp.com/docs/en/application-note/AN12753.pdf
- DESFire EV3 feature and functionality comparison to other MIFARE DESFire products: https://www.nxp.com/docs/en/application-note/AN12752.pdf

Unfortunately the 3 main datasheets are shortened by the manufacturer and the full datasheets are available under **Non disclosure agreements (NDA)** only. 
As I'm using a "ready to use" library no NDA breach was done.

Another fine piece of information is the **NXP MIFARE DESFire EV1 Protocol** available here: https://github.com/revk/DESFireAES/blob/master/DESFire.pdf. 
This is a short overview about most of the DESFire EV1 commands and error codes.

## About this app: 
It is developed using Android Studio version Giraffe | 2022.3.1 Patch 1 and is running on SDK 21 to 33 (Android 13) (tested on 
Android 8 and 13 with real devices).  


