# EXT_gpu_compressed_texture

## Contributors

- DeepKolos, [@deepkolos](https://github.com/deepkolos)

## Status

Draft

## Dependencies

Written against the glTF 2.0 spec.

## Overview

This extension allows glTF models to use gpu compressed texture which is decode from `basisu` and optionally encode by `zstd`. A client that doesn't support the gpu compressed texture format provided by the extensions, will fallback to orignal img(`png/jpg`).

## glTF Schema Updates

The `EXT_gpu_compressed_texture` extension is added to the `textures` node and specifies a `astc,bc7,dxt,pvrtc,etc1` property that points to the index of the `buffers` node. and the `compress` property is specify what compress algo is used. for example `0` is none compressed, and `1` is compressed by `zstd`.

```json
"textures": [
    {
        "source": 0,
        "extensions": {
            "EXT_gpu_compressed_texture": {
                "astc": 1,
                "bc7": 2,
                "dxt": 3,
                "pvrtc": 4,
                "etc1": 5,
                "width": 2048,
                "height": 2048,
                "hasAlpha": 0,
                "compress": 1
            }
        }
    }
],
"buffers": [
    { "name": "buffer", "byteLength": 207816, "uri": "buffer.bin" },
    { "name": "image3.astc", "byteLength": 48972, "uri": "image3.astc.bin" },
    { "name": "image3.bc7", "byteLength": 50586, "uri": "image3.bc7.bin" },
    { "name": "image3.dxt", "byteLength": 10686, "uri": "image3.dxt.bin" },
    { "name": "image3.pvrtc", "byteLength": 21741, "uri": "image3.pvrtc.bin" },
    { "name": "image3.etc1", "byteLength": 22360, "uri": "image3.etc1.bin" },
]
```

this extension not support glb for now.

### JSON Schema

[glTF.EXT_gpu_compressed_texture.schema.json](schema/glTF.EXT_gpu_compressed_texture.schema.json)

## Known Implementations

implement for three.js and cli tools [gltf-gpu-compressed-texture](https://github.com/deepkolos/gltf-gpu-compressed-texture)
