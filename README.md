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
