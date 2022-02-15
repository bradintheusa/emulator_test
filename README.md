# test_app

Start the emulator

```
cd emulator
firebase emulators:start --export-on-exit=emulatorData --import=emulatorData
```

Start and android emulator

```
emulator -avd Nexus_5X_API_28
```

Run the app
```
cd test_app
flutter run
```

Run the flutter app and everything should work flawlessly. Now shut down the android emulator and connect a real android device. Restart the app.

The app wont work. I get this error

```
W/Firestore(30266): (24.0.1) [OnlineStateTracker]: Could not reach Cloud Firestore backend. Backend didn't respond within 10 seconds
W/Firestore(30266):
W/Firestore(30266): This typically indicates that your device does not have a healthy Internet connection at the moment. The client will operate in offline mode until it is able to successfully connect to the backend.

══╡ EXCEPTION CAUGHT BY WIDGETS LIBRARY ╞═══════════════════════════════════════════════════════════
The following StateError was thrown building StreamBuilder<DocumentSnapshot<Object?>>(dirty, state:
_StreamBuilderBaseState<DocumentSnapshot<Object?>, AsyncSnapshot<DocumentSnapshot<Object?>>>#a193b):
Bad state: cannot get a field on a DocumentSnapshotPlatform which does not exist
```

Now if this line is commented out the physical device runs fine.

```
FirebaseFirestore.instance.useFirestoreEmulator("localhost", 8080);
```

Any help would be appreciated.


If I use more emulator services I get similar errors. this is from another app.

```
An Observatory debugger and profiler on Nexus 5X is available at: http://127.0.0.1:62536/y_wW9MBDpnc=/
D/vndksupport(  851): Loading /vendor/lib64/hw/android.hardware.graphics.mapper@2.0-impl.so from current namespace instead of sphal namespace.
D/vndksupport(  851): Loading /vendor/lib64/hw/gralloc.msm8992.so from current namespace instead of sphal namespace.
E/flutter (  851): [ERROR:flutter/lib/ui/ui_dart_state.cc(209)] Unhandled Exception: [firebase_auth/unknown] com.google.firebase.FirebaseException: An internal error has occurred. [ Failed to connect to /10.0.2.2:9099 ]
E/flutter (  851): #0      MethodChannelFirebaseAuth.signInAnonymously (package:firebase_auth_platform_interface/src/method_channel/method_channel_firebase_auth.dart:423:7)
```
