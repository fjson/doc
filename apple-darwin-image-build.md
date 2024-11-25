## Rust在windows上编译aarch64-apple产物

- 使用cross-rs
[https://github.com/cross-rs/cross?tab=readme-ov-file](https://github.com/cross-rs/cross?tab=readme-ov-file)

- 创建Cross.toml文件

```
[target.aarch64-apple-darwin]
image = "ghcr.io/cross-rs/aarch64-apple-darwin-cross:local"
```

- 构建
```shell
cross build --target aarch64-apple-darwin --release
```

### 构建aarch64-apple-darwin-cross Docker Image

[https://github.com/cross-rs/cross-toolchains](https://github.com/cross-rs/cross-toolchains)

- Clone项目
```shell
git clone https://github.com/cross-rs/cross
cd cross
git submodule update --init --remote
```

- 获取MacSdk
[https://github.com/joseluisq/macosx-sdks](https://github.com/joseluisq/macosx-sdks)
已知问题，  SDK < 10.16 或者 SDK >= 13.0 无法构建成功， 建议使用12.3

- 将sdk放置cross-toolchains/docker/[some-dir]下
- 构建Image
```shell
cargo build-docker-image aarch64-apple-darwin-cross \
  --build-arg 'MACOS_SDK_DIR=[some-dir]' \
  --build-arg 'MACOS_SDK_FILE=MacOSX12.3.sdk.tar.xz'
```

### 生成Mac OS SDK

[https://github.com/tpoechtrager/osxcross](https://github.com/tpoechtrager/osxcross)




