# Build Ravencoin on macOS (Apple Silicon)

This guide describes how to build Ravencoin on macOS systems with Apple Silicon (M1, M2, M3, etc.).

## 1. Prerequisites

Install the necessary dependencies using [Homebrew](https://brew.sh):

```bash
brew install automake libtool boost miniupnpc openssl@1.1 pkg-config protobuf qt libevent qrencode
```

## 2. Prepare Build System

Generate the configuration files:

```bash
./autogen.sh
```

## 3. Configure

Configure the build. You must explicitly verify and set the paths to Homebrew libraries, as they are located in `/opt/homebrew` on Apple Silicon.

```bash
./configure \
  --with-gui=qt5 \
  --with-boost=/opt/homebrew \
  --with-boost-libdir=/opt/homebrew/lib \
  LDFLAGS="-L/opt/homebrew/opt/openssl@1.1/lib -L/opt/homebrew/opt/berkeley-db@4/lib -L/opt/homebrew/opt/qt@5/lib -L/opt/homebrew/lib" \
  CPPFLAGS="-I/opt/homebrew/opt/openssl@1.1/include -I/opt/homebrew/opt/berkeley-db@4/include -I/opt/homebrew/opt/qt@5/include -I/opt/homebrew/include" \
  PKG_CONFIG_PATH="/opt/homebrew/opt/openssl@1.1/lib/pkgconfig:/opt/homebrew/opt/qt@5/lib/pkgconfig:/opt/homebrew/opt/libevent/lib/pkgconfig"
```

## 4. Build

Compile the binaries (using all available CPU cores):

```bash
make -j$(sysctl -n hw.ncpu)
```

## 5. Result

The binaries will be available in the `src` directory:

- `src/ravend`
- `src/raven-cli`
- `src/qt/raven-qt`
