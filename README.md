<div align="center">

<img src="./.github/assets/yakuyomi-logo.png" alt="MTYOMI" width="80"/>

# MTYOMI

**On-device AI translation manga reader.**

[English](README.md) | [中文](README_zh.md)

[![License: GPL-3.0](https://img.shields.io/badge/License-GPL--3.0-0877d2?labelColor=27303D)](LICENSE-YAKUYOMI.md)
[![Release](https://img.shields.io/github/v/release/joyeli/Yakuyomi?include_prereleases&label=Download&labelColor=27303D)](https://github.com/joyeli/Yakuyomi/releases/latest)

</div>

MTYOMI is a [mihon](https://github.com/mihonapp/mihon) fork that translates manga as you download or read — Japanese to Traditional Chinese by default, any language pair you set. **Detection, OCR and text removal run on-device** (all three models on NCNN, CPU only). Only **translation** calls a cloud LLM. **Night reading** darkens the page itself, also on-device. The engine lives in a separate repo, [yakuyomi-engine](https://github.com/joyeli/yakuyomi-engine), pulled in as a submodule.

<div align="center">
<img src="./.github/assets/showcase.png" alt="Box-fill vs MTYOMI inpainting" width="100%"/>
<br>
<sub><b>Text over art (hair, faces, backgrounds) is where overlay / box-fill translation fails.</b> MTYOMI erases the original, reconstructs the art (3), then typesets the translation back in (4).</sub>
</div>

See [README_zh.md](README_zh.md) for the full feature guide (translation, night reading, capture, reader, library, browse).

## Download

Grab the latest **signed APK** from the [Releases page](https://github.com/joyeli/Yakuyomi/releases/latest). Most phones want `arm64-v8a`; use `universal` if unsure.

## Building

```sh
git clone --recurse-submodules https://github.com/joyeli/Yakuyomi.git
cd Yakuyomi
./gradlew :app:assembleDebug
```

The engine is wired in via Gradle composite build (`includeBuild`). It compiles native code and needs NDK `28.2.13676358` and CMake `3.22.1`. Use JDK 17+. If you already cloned without `--recurse-submodules`, run `git submodule update --init --recursive`.

## License

**GPL-3.0** — see [LICENSE-YAKUYOMI.md](LICENSE-YAKUYOMI.md).
