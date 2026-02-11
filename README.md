# FishyWebRTC Transport

WebRTC transport for [FishNet](https://github.com/FirstGearGames/FishNet) networking. Enables **WebGL clients** to connect to dedicated servers via WebRTC DataChannels with HTTP signaling.

Forked from [cakeslice/FishyWebRTC](https://github.com/cakeslice/FishyWebRTC) with FishNet 4.6.18 compatibility fixes.

## Prerequisites

- **Unity 6000.2+**
- **FishNet 4.6.18+** (installed in Assets)
- `com.unity.webrtc` 3.0.0-pre.7 (auto-installed as dependency)

## Installation

### Option A: Local Package (recommended for development)

1. Copy `com.skillcade.fishy-webrtc/` into your project's `Packages/` folder
2. Add to `Packages/manifest.json`:
   ```json
   "com.skillcade.fishy-webrtc": "file:com.skillcade.fishy-webrtc"
   ```

### Option B: Import .unitypackage

1. Install `com.unity.webrtc` 3.0.0-pre.7 via Package Manager (Add by name: `com.unity.webrtc`)
2. Double-click the `.unitypackage` file → Import All

### Option C: From Tarball

1. Package Manager → **Add package from tarball** → select `.tgz` file

## Setup

`ENABLE_WEBRTC` is **automatically defined** when `com.unity.webrtc` is detected (via asmdef `versionDefines`). No manual scripting defines needed.

1. Add the `FishyWebRTC` component to your NetworkManager GameObject
2. Configure ICE servers (STUN/TURN) in the Inspector
3. Set signaling address and port

### Edgegap Deployment

For Edgegap, configure at runtime before `StartConnection()`:
```csharp
var transport = GetComponent<FishyWebRTC>();
transport.SetHTTPS(true);
transport.SetNoClientPort(true);
transport.SetClientAddress("your-server.edgegap.net");
```

## License

Based on [cakeslice/FishyWebRTC](https://github.com/cakeslice/FishyWebRTC) — MIT License.
