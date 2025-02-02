# Rope Climbing AR Guide

A mobile AR prototype that overlays a climbing route onto a real rock face. A moderator anchors the route on the wall, then hands the phone to a climber, who sees only the route.

Built with Unity 6 and AR Foundation (ARCore / ARKit) as a university project.

## How it works

**Moderator mode**

1. Scan the wall until AR planes are detected.
2. Tap two points on the wall to place anchors: the start of the route and a second reference hold.
3. The selected route, a 3D polyline traced from a scan of the rock, gets translated, scaled and rotated so its first two points line up with the two anchors.
4. Use the **Rotation** slider to turn the route around the axis between the two anchors until it fits the wall.
5. **Switch model** cycles through the available routes; **Remove All Anchors** starts over.

**Evaluation mode**

Switching to evaluation mode hides the moderator UI and all plane and feature-point visualizations, so the climber sees only the camera feed and the route. A six-finger tap switches back to moderator mode.

## Project layout

| Path | Contents |
| --- | --- |
| `Assets/Scenes/Anchors/Anchors.unity` | Main scene with the route guide |
| `Assets/ModeManager.cs` | Switches between moderator and evaluation mode; cycles routes |
| `Assets/Scripts/Runtime/PathManager.cs` | Fits a route polyline to two anchors and handles rotation |
| `Assets/Scripts/Runtime/ARPlaceAnchor.cs` | Places anchors from raycast hits and passes them to the path manager |
| `Assets/Environments/`, `Assets/Import/` | Scanned rock models and routes |
| `Assets/*_sim_environment.prefab`, `Assets/rock_simulated_environment.prefab` | XR Simulation environments for testing in the editor |

## Running it

1. Open the project in **Unity 6000.0.26f1** (with Android and/or iOS build support).
2. Build to an ARCore (Android) or ARKit (iOS) device. `Anchors` is the only scene in the build settings, so the app starts straight into the guide.
3. To try it in the editor, enable **XR Simulation** under *Project Settings → XR Plug-in Management* and pick one of the rock environments in the XR Environment view.

## Credits

Based on Unity's [AR Foundation Samples](https://github.com/Unity-Technologies/arfoundation-samples) (6.0.3), which provides the UI and AR scaffolding. All sample scenes and assets the guide doesn't use have been removed. The sample code is licensed under the Unity Companion License; see [LICENSE.md](LICENSE.md).
