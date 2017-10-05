# aframe-teleport-controls

Teleport component

![Screenshot](https://github.com/fernandojsg/aframe-teleport-controls/raw/master/teleport.png)

## Properties

| Property    | Description                     | Default Value    |
| --------    | -----------                     | -------------    |
| cameraRig       | Selector of the camera Rig to teleport         |    |
| type       | Type of teleport: line or parabolic         | parabolic   |
| aimEvent       | Event to listen to start aiming (For example `trackpaddown`)         |    |
| teleportEvent       | Event to listen to teleport (For example `trackpadup`)         |    |
| collisionEntities | Selector of the meshes used to check the collisions. If no value provided a plane Y=0 is used |  |
| hitEntity | Entity used to show at the hitting position. If no value provided a cylinder will be used as default. |           |
| hitCylinderColor | Color used for the default `hitEntity` primitives | #99ff99          |
| hitCylinderRadius | Radius used for the default `hitEntity` primitives | 0.25          |
| hitCylinderHeight | Height used for the default `hitEntity` primitives | 0.3 |
| curveHitColor | Color used for the curve when hit the mesh | #99ff99          |
| curveMissColor | Color used for the curve when it doesn't hit anything | #ff0000          |
| curveNumberPoints | Number of points used in the curve | 30          |
| curveLineWidth | Line width of the curve | 0.025          |
| curveShootingSpeed | Curve shooting speed, as bigger value, farther distance. | 5          |
| defaultPlaneSize | Default plane size | 100 |
| maxLength | Max length of the ray when using type=line teleport | 10 |
| landingNormal | Normal vector to detect collisions with the `collisionEntity` | (0, 1, 0)          |
| landingMaxAngle | Angle threshold (in degrees) used together with `landingNormal` to detect if the mesh is so steep to jump to it. | 45          |

### Usage

#### Browser Installation

Install and use by directly including the [browser files](dist):

There are two ways to use it: using a camera rig or not. I strongly recommend using a camera rig as the following example:

```html
<head>
  <title>My A-Frame Scene</title>
  <script src="https://aframe.io/releases/0.7.0/aframe.min.js"></script>
  <script src="https://rawgit.com/fernandojsg/aframe-teleport-controls/master/dist/aframe-teleport-controls.min.js"></script>
</head>

<body>
  <a-scene>
    <a-entity id="cameraRig">
      <!-- camera -->
      <a-entity camera wasd-controls look-controls></a-entity>
      <!-- hand controls -->
      <a-entity id="left-hand" teleport-controls="cameraRig: #cameraRig"></a-entity>
      <a-entity id="right-hand" teleport-controls="cameraRig: #cameraRig"></a-entity>
    </a-entity>
  </a-scene>
</body>
```

To use this component with Gear VR, you need to add `gearvr-controls`:

```html
  <a-scene>
    <a-entity id="cameraRig">
      <a-camera />
      <a-entity
        teleport-controls="cameraRig: #cameraRig"
        gearvr-controls
       />
    </a-entity>
  </a-scene>
```

You can also use the trigger button instead of trackpad button by adding `button: trigger`.

For Daydream, replace `gearvr-controls` by `daydream-controls`.

If you use [aframe-environment-component](https://github.com/feiss/aframe-environment-component) > 1.0.0
and want to teleport on the generated ground, on the hills, you can
specify `collisionEntities: .environmentGround`. You can also add `.environmentDressing` if you want to teleport on the dressing like the mushrooms.
On Gear VR, it can be very slow with the curved line. Use `maxLength: 200; type: line;` in this case.


#### NPM Installation

Install via NPM:

```bash
npm install aframe-teleport-controls
```

Then register and use.

```js
require('aframe-teleport-controls');
```
