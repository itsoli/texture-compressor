# Texture Compressor

[![npm version](https://badge.fury.io/js/texture-compressor.svg)](https://badge.fury.io/js/texture-compressor)

CLI tool for texture compression using ASTC, ETC, PVRTC and S3TC in a KTX container.

## Sponsor

[![BTC](https://img.shields.io/badge/BTC-3JK7LX5JsSYTKja16eGmDtjKfyTexVwB8z-f5f5f5?logo=bitcoin)](https://blockchain.com/btc/address/3JK7LX5JsSYTKja16eGmDtjKfyTexVwB8z)

[![ETH](https://img.shields.io/badge/ETH-0xDd324578a724Af06B9c39E3351C3627Cb85D85cA-f5f5f5?logo=ethereum)](https://blockchain.com/eth/address/0xDd324578a724Af06B9c39E3351C3627Cb85D85cA)

[![DASH](https://img.shields.io/badge/DASH-XpwH46HxvfNsvtopc4734vSdQdjhounzX7-f5f5f5?logo=dash)](https://explorer.dash.org/insight/address/XpwH46HxvfNsvtopc4734vSdQdjhounzX7)

[![LTC](https://img.shields.io/badge/LTC-METUJrwmejUVFGdrzgVU6i6f1jxxyrKRTc-f5f5f5?logo=litecoin)](https://live.blockcypher.com/ltc/address/METUJrwmejUVFGdrzgVU6i6f1jxxyrKRTc/)

## Installation

Make sure you have [Node.js](http://nodejs.org/) installed.

```sh
 $ npm install texture-compressor
```

## Live demo

[Live demo](https://timvanscherpenzeel.github.io/texture-compressor/)

## Documentation

[Supported devices table](docs/SUPPORTED_DEVICES_TABLE.md)

[Supported parameters](docs/SUPPORTED_PARAMETERS.md)

[Recommended parameters](docs/RECOMMENDED_PARAMETERS.md)

## CLI Usage

### ASTC

```sh
$ node ./bin/texture-compressor -i input/example.png -t astc -c ASTC_4x4 -q astcmedium -o output/example-astc.ktx -y -m -vb
```

### ETC

```sh
$ node ./bin/texture-compressor -i input/example.png -t etc -c ETC2_RGB -q etcfast -o output/example-etc.ktx -y -m -vb
```

### PVRTC

```sh
$ node ./bin/texture-compressor -i input/example.png -t pvrtc -c PVRTC1_2 -q pvrtcnormal -o output/example-pvrtc.ktx -y -m -vb
```

### S3TC

```sh
$ node ./bin/texture-compressor -i input/example.png -t s3tc -c DXT1 -q normal -o output/example-s3tc.ktx -y -m -vb
```

## Module usage

```js
const { pack } = require('./dist/cli/lib/index');

pack({
  type: 'astc',
  input: 'input/example.png',
  output: 'output/example-astc.ktx',
  compression: 'ASTC_4x4',
  quality: 'astcmedium',
  verbose: true,
}).then(() => console.log('done!'));
```

## Flags

### Required

    -i, --input [example: ./input/example.png] [required]
    -o, --output [example: ./output/example.ktx] [required]
    -t, --type [example: astc, etc, pvrtc, s3tc] [required]
    -c, --compression [example: ASTC_4x4, ETC2_RGB, PVRTC1_2, DXT1] [required]
    -q, --quality [example: astcmedium, etcfast, pvrtcnormal, normal] [required]

### Optional

    -vb, --verbose [true / false, default: false] [not required]

    -rs, --square ['no', '-', '+', default: +] [not required]
    -rp, --pot ['no', '-', '+', default: +] [not required]
    -m, --mipmap [true / false, default: false] [not required]
    -y, --flipY [tue / false, default: false] [not required]

### Tool flags

Tool flags are not processed by `texture-compressor` but rather directly by the binary you are targeting itself.

For example adding `--flags ["usesourceformat DXT1A" "alphaThreshold 200"]` will pass `usesourceformat DXT1A` and `alphaThreshold 200` directly to `Crunch`.

Please be aware that these flags are tool specific and can therefore not be directly applied to the other binaries.

    -f, --flags ["flag value" "flag value"] [not required]

To find tool specific flags please refer to the manuals of [ASTC](http://cdn.imgtec.com/sdk-documentation/PVRTexTool.User+Manual.pdf), [ETC](http://cdn.imgtec.com/sdk-documentation/PVRTexTool.User+Manual.pdf), [PVRTC](http://cdn.imgtec.com/sdk-documentation/PVRTexTool.User+Manual.pdf), [S3TC](https://github.com/BinomialLLC/crunch/blob/235946f7a1cf8b9c97e8bf0e8062d5439a51dec7/crunch/crunch.cpp#L70-L181).

## License

My work is released under the [MIT license](https://raw.githubusercontent.com/TimvanScherpenzeel/texture-compressor/master/LICENSE).

This repository distributes multiple binary tools for Windows, Mac and Linux.
This product includes components of the PowerVR™ SDK from Imagination Technologies Limited.

- [astcenc](https://raw.githubusercontent.com/ARM-software/astc-encoder/master/license.txt)
- [PVRTexToolCLI](https://community.imgtec.com/developers/powervr/sdk-end-user-licence-agreement/)
- [crunch](https://raw.githubusercontent.com/BinomialLLC/crunch/master/license.txt)
