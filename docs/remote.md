# Remote

Snout supports a remote control interface using OSC, allowing you to control various features of the application remotely.
A binary (`snout-remote`) is provided that can be used to control Snout. Although any application that can send OSC messages will do.

## Configuration

Add the following to your `config.toml` file:

```toml
[control]
listen = "127.0.0.1:9500"
```

## `snout-remote` usage

### Setting face bounds

To set the bounds of a face shape, run the following command:

```sh
snout-remote face-bounds <shape> <lower> <upper>
```

The name of the `<shape>` is case sensitive, a list of all shapes can be found [below](#available-face-shapes)

An example for setting the bounds of a shape can be found below.

```sh
snout-remote face-bounds "MouthLeft" 0.4 1.0
```


### Face auto calibration

You can auto calibrate the lower bounds of all face shapes using the `face-calibrate` command.
This will take a 100 frames worth of data (about 3 seconds at 30fps) and use it to determine the lower bounds of the face shapes.

Make sure to keep a neutral face through the calibration cycle.

Bounds set through the auto calibration process are *not* saved persistently.

You can add the `-v` flag when launching `snout-cli` to see the set bounds and apply them permanently in the configuration file.

```sh
snout-remote face-calibrate
```

## API

### Set face bounds

Set the bounds of the face.

```
/snout/face/bounds <shape> <lower> <upper>
```

### Start face auto calibration

Start the auto calibration process for the face.

```
/snout/face/calibrate
```

## Available face shapes

- cheekPuffLeft
- cheekPuffRight
- cheekSuckLeft
- cheekSuckRight
- jawOpen
- jawForward
- jawLeft
- jawRight
- noseSneerLeft
- noseSneerRight
- mouthFunnel
- mouthPucker
- mouthLeft
- mouthRight
- mouthRollUpper
- mouthRollLower
- mouthShrugUpper
- mouthShrugLower
- mouthClose
- mouthSmileLeft
- mouthSmileRight
- mouthFrownLeft
- mouthFrownRight
- mouthDimpleLeft
- mouthDimpleRight
- mouthUpperUpLeft
- mouthUpperUpRight
- mouthLowerDownLeft
- mouthLowerDownRight
- mouthPressLeft
- mouthPressRight
- mouthStretchLeft
- mouthStretchRight
- tongueOut
- tongueUp
- tongueDown
- tongueLeft
- tongueRight
- tongueRoll
- tongueBendDown
- tongueCurlUp
- tongueSquish
- tongueFlat
- tongueTwistLeft
- tongueTwistRight
