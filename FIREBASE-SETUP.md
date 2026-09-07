# FileDrop Firebase integration

This static project is configured only for the existing **FileDrop** Firebase
web app (`filedrop-24b64`). Its public web configuration is stored in
`control/gs-firebase.js`; no Firebase Admin SDK credential or private key is
used or required.

## Service used

Only **Realtime Database** is used. It synchronizes overlay theme state at:

```
gs-production/{private-room-id}/overlays/{overlay-name}
```

Authentication, Cloud Firestore, Cloud Storage, Cloud Functions, and Firebase
Analytics are not called by this project.

## One required Console setting

The supplied FileDrop Realtime Database URL is configured in the shared module:

```
https://filedrop-24b64-default-rtdb.asia-southeast1.firebasedatabase.app
```

Open `control/setup.html` on the deployed site, choose a private room ID, and
save to generate streamer links.

The code accepts only a FileDrop Realtime Database URL and only the supplied
FileDrop app ID/key/project ID, preventing an old GS Overlay or another Firebase
project configuration from being used.

For deployment, restrict rules to the `gs-production` tree and the people who
need to run the event. The app has no Authentication flow, so do not leave
global public read/write rules enabled after testing. A secure rule design needs
an authentication model before it can be deployed; none was supplied with this
static project.
