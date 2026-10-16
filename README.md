# ScoutMind: third-party open-source components and their source code

ScoutMind for Windows, sold through the Microsoft Store, includes some open-source programs made by other people. ScoutMind for Mac (beta, Apple silicon) includes the same kinds of programs; see the second table. Their licences give you the right to get their complete source code. This repository provides that source.

**ScoutMind's own code is not open source.** This repository contains only the third-party components listed below, their licence texts, and records of exactly how each shipped binary was built.

## What ScoutMind includes, and where to get its source

| ScoutMind version | Component inside the app | Licence | Binary (SHA-256) | Complete corresponding source (release) |
|---|---|---|---|---|
| 1.0.100.0 | `ffmpeg.exe`: FFmpeg `N-126435-gf93cd72dde-20260906`, a static Windows build by [BtbN/FFmpeg-Builds](https://github.com/BtbN/FFmpeg-Builds) (build-scripts commit `8267213e26c1031621e6e1210fe3aa4867214f6a`) | GPL version 3 or later | `5f0118f94a7e92d01a86ea07ed533dee9cb45789d135a4365e98cefec3ca8847` | [`ffmpeg-N-126435-gf93cd72dde-win64-gpl`](../../releases/tag/ffmpeg-N-126435-gf93cd72dde-win64-gpl) |
| 1.0.119.0 and 2.0 | `ffmpeg.exe`: FFmpeg `n9.0.2-10-g51c4a23d74-20260926` (FFmpeg commit `51c4a23d74ac2fbf2fb066e0ce274a966a16da23`), a static Windows build by BtbN/FFmpeg-Builds (build-scripts commit `58cc05f33c20e3ead0ce876b72531ab482d0f981`) | GPL version 3 or later | `b04aa739de5b1d3e89b1c9fe4862be81d6dbb61558decee0d68cdc85b03eb511` | [`ffmpeg-n9.0.2-10-g51c4a23d74-win64-gpl-9.0`](../../releases/tag/ffmpeg-n9.0.2-10-g51c4a23d74-win64-gpl-9.0) |
| 1.0.100.0, 1.0.119.0 and 2.0 | `cv2/opencv_videoio_ffmpeg490_64.dll`: OpenCV's FFmpeg video plugin (FFmpeg 4.4.4 with libvpx and libaom), shipped inside `opencv-python-headless` 4.9.0.80 | LGPL version 2.1 or later (OpenCV itself is Apache-2.0) | `969a3219854b6b654a7e5a89ccdb87f3cc143af5e43858eea0ad9275237ea406` | [`opencv-videoio-ffmpeg490_64-4.9.0.80`](../../releases/tag/opencv-videoio-ffmpeg490_64-4.9.0.80) |

## ScoutMind for Mac (beta, Apple silicon): components and source

| ScoutMind version | Component inside the app | Licence | Checksum (SHA-256) | Complete corresponding source (release) |
|---|---|---|---|---|
| 2.0 Mac beta | `bin/ffmpeg`: FFmpeg 7.1 with x264, a static build made from source on a Mac (a separate program that ScoutMind runs) | GPL version 2 or later | `5d390684fc6567b0fe70699a8ed6822a38fb0bba01148f7b9e8e21dfaeb1fb42` (before Apple code signing; the copy inside the app is re-signed, so its checksum differs, and `manifest.json` in the archive records the build) | [`ffmpeg-7.1-mac-arm64-gpl-x264`](../../releases/tag/ffmpeg-7.1-mac-arm64-gpl-x264) |
| 2.0 Mac beta | OpenCV's FFmpeg libraries inside `opencv-python-headless` 4.9.0.80 (custom build `1scoutmindlgpl1`, wheel SHA-256 `fd8898bfdc69b08151841f16e1b8b2b80af6dc6fbb0bff94c991bacf92c68ee3`): `libavcodec.61.19.100.dylib` (`ba535aa1637822c4427cf56f2a0374affdf3cb1603185c3caf5ca86cf27e1f23`), `libavformat.61.7.100.dylib` (`6112d502005fb11148d9113b898598aa3e10f7029b0e196c76501aeecefe8081`), `libavutil.59.39.100.dylib` (`6298762da5d8f77d6c7687b23f6b2bf8024232253a8bf2b89c4815209c1af097`), `libswresample.5.3.100.dylib` (`c58d51e420f2f040564f0cbd8ca2e72bad42f55b26fa96dd80d612d13aafb481`), `libswscale.8.3.100.dylib` (`b03d09e67ba1515e13b79e0eb180e495224bec44bc54567c117e69cf66171e33`) | LGPL version 2.1 or later (OpenCV itself is Apache-2.0) | as listed in the previous column (as shipped in the wheel, before Apple code signing) | [`opencv-ffmpeg-libs-4.9.0.80-mac-arm64`](../../releases/tag/opencv-ffmpeg-libs-4.9.0.80-mac-arm64) |

The Mac releases hold a single `.zip` archive and its `.sha256` file. The same two archives also travel inside the app, under `ScoutMind.app/Contents/Resources/third_party/`. The libraries are separate files inside the app (`ScoutMind.app/Contents/Frameworks/cv2/__dot__dylibs/` for the OpenCV FFmpeg libraries and `Contents/Frameworks/bin/ffmpeg` for the program); ScoutMind does not check them when it runs.

For the Mac beta, the same rights apply as for Windows: you may modify the LGPL-licensed FFmpeg libraries and use your modified version with ScoutMind, and you may reverse-engineer the parts of ScoutMind needed to debug such modifications. The beta is signed with a local (ad hoc) signature and is not Apple-notarized, so macOS may ask you to sign the app again after you replace a file.

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
