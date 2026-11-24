# JSON Structure

Only the fields used by the notebook are shown.

```
data
├── item
│   └── slots[0]
│       └── frame_urls[]            URL of each video frame image
└── annotations[]                   one entry per annotated frame
    └── frames
        └── "<frame number>"
            └── skeleton
                └── nodes[]         10 joints
                    ├── name        e.g. "1_Neck"
                    ├── x           pixel x in the 1280x720 frame
                    └── y           pixel y in the 1280x720 frame
```

## Example

```json
{
  "frames": {
    "2609": {
      "skeleton": {
        "nodes": [
          { "name": "0_Nose", "x": 404.37, "y": 167.25 },
          { "name": "1_Neck", "x": 395.28, "y": 215.57 }
        ]
      }
    }
  }
}
```

## Linking Annotations to Images

The frame number key inside `frames` is used as the index into `item.slots[0].frame_urls`, so each set of keypoints can be drawn on its own frame.

## Bone Connections

The node order in the JSON is not the same as the body order, so the notebook rearranges it with `line_Sequence = [0,1,2,4,7,9,6,3,5,8]` before drawing lines between joints.
