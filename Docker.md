# Build docker images

## example build

1. Verify current or wanted stable versions!

   - `binutils`

       https://ftp.debian.org/debian/pool/main/b/binutils/

   - `crosstool-ng` and related `gcc` versions:

       https://github.com/crosstool-ng/crosstool-ng/tags

       https://github.com/crosstool-ng/crosstool-ng/releases

2. build the image

    ```sh
    export HOST_TRIPLE=armv6-rpi-linux-gnueabihf
    export BINUTIL_VERSION=2.43.1-5
    export CT_NG_TAG=crosstool-ng-1.27.0
    export GCC_VERSION=14-2
    export RELEASE_VERSION=1.0.0

    docker build \
    --tag       docker-arm-cross-toolchain:${HOST_TRIPLE}-${GCC_VERSION}-${RELEASE_VERSION} \
    --build-arg BUILDPLATFORM=x86_64 \
    --build-arg HOST_TRIPLE=${HOST_TRIPLE} \
    --build-arg BINUTIL_VERSION=${BINUTIL_VERSION} \
    --build-arg GCC_VERSION=${GCC_VERSION} \
    --build-arg CT_NG_TAG=${CT_NG_TAG} \
    .
    ```
