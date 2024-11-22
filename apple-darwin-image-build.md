### 构建aarch64-apple-ios-cross Docker Image

[https://github.com/cross-rs/cross-toolchains](https://github.com/cross-rs/cross-toolchains)

- Clone项目
```
git clone https://github.com/cross-rs/cross
cd cross
git submodule update --init --remote
```

- 获取MacSdk
[https://github.com/joseluisq/macosx-sdks](https://github.com/joseluisq/macosx-sdks)
已知问题，  SDK < 10.16 或者 SDK >= 13.0 无法构建成功， 建议使用12.3

- 将sdk放置cross-toolchains/docker/[some-dir]下
- 构建
```
cargo build-docker-image aarch64-apple-darwin-cross \
  --build-arg 'MACOS_SDK_DIR=[some-dir]' \
  --build-arg 'MACOS_SDK_FILE=MacOSX12.3.sdk.tar.xz'
```

### 生成Mac OS SDK

[https://github.com/tpoechtrager/osxcross](https://github.com/tpoechtrager/osxcross)




