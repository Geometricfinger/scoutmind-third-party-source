# ScoutMind: third-party open-source components and their source code

ScoutMind for Windows, sold through the Microsoft Store, includes some open-source programs made by other people. Their licences give you the right to get their complete source code. This repository provides that source.

**ScoutMind's own code is not open source.** This repository contains only the third-party components listed below, their licence texts, and records of exactly how each shipped binary was built.

## What ScoutMind includes, and where to get its source

| ScoutMind version | Component inside the app | Licence | Binary (SHA-256) | Complete corresponding source (release) |
|---|---|---|---|---|
| 1.0.100.0 | `ffmpeg.exe`: FFmpeg `N-126435-gf93cd72dde-20260906`, a static Windows build by [BtbN/FFmpeg-Builds](https://github.com/BtbN/FFmpeg-Builds) (build-scripts commit `8267213e26c1031621e6e1210fe3aa4867214f6a`) | GPL version 3 or later | `5f0118f94a7e92d01a86ea07ed533dee9cb45789d135a4365e98cefec3ca8847` | [`ffmpeg-N-126435-gf93cd72dde-win64-gpl`](../../releases/tag/ffmpeg-N-126435-gf93cd72dde-win64-gpl) |
| 1.0.119.0 and 2.0 | `ffmpeg.exe`: FFmpeg `n9.0.2-10-g51c4a23d74-20260926` (FFmpeg commit `51c4a23d74ac2fbf2fb066e0ce274a966a16da23`), a static Windows build by BtbN/FFmpeg-Builds (build-scripts commit `58cc05f33c20e3ead0ce876b72531ab482d0f981`) | GPL version 3 or later | `b04aa739de5b1d3e89b1c9fe4862be81d6dbb61558decee0d68cdc85b03eb511` | [`ffmpeg-n9.0.2-10-g51c4a23d74-win64-gpl-9.0`](../../releases/tag/ffmpeg-n9.0.2-10-g51c4a23d74-win64-gpl-9.0) |
| 1.0.100.0, 1.0.119.0 and 2.0 | `cv2/opencv_videoio_ffmpeg490_64.dll`: OpenCV's FFmpeg video plugin (FFmpeg 4.4.4 with libvpx and libaom), shipped inside `opencv-python-headless` 4.9.0.80 | LGPL version 2.1 or later (OpenCV itself is Apache-2.0) | `969a3219854b6b654a7e5a89ccdb87f3cc143af5e43858eea0ad9275237ea406` | [`opencv-videoio-ffmpeg490_64-4.9.0.80`](../../releases/tag/opencv-videoio-ffmpeg490_64-4.9.0.80) |

Each release holds a single `.tar` archive and its `.sha256` file. Inside each archive you'll find:
- the pinned source of every library that went into that binary;
- the build scripts and toolchain sources;
- the licence texts;
- a `manifest.json`;
- a `SHA256SUMS` file covering every file;
- a README explaining how the binary was built.

The `manifests/` folder here has the same records, so you can read them without downloading the archive.

## Checking a download

```
shasum -a 256 -c <archive>.tar.sha256
tar -xf <archive>.tar
cd <archive-folder> && shasum -a 256 -c SHA256SUMS
```

To check that a ScoutMind installation contains the binary listed above, compute the SHA-256 of `ffmpeg.exe` or `opencv_videoio_ffmpeg490_64.dll` in the app's install folder and compare it with the table.

## Your rights

- The GPL and LGPL texts are in [`LICENSES/`](LICENSES/).
- These components keep their own licences, and nothing in ScoutMind's terms of sale limits your rights under them.
- For the LGPL-licensed OpenCV FFmpeg plugin, you may modify it and use your modified version with ScoutMind, and you may reverse-engineer the parts of ScoutMind needed to debug such modifications.
- `ffmpeg.exe` is a separate program that ScoutMind runs. You may use, study, change and share it under the GPL.

## Availability

- This source stays available here for at least three years after the last ScoutMind version that includes each binary was distributed.
- If a download stops working, email **coulsonlane@gmail.com**. We'll provide the same source at no charge beyond the cost of physically delivering it.
