
FROM gcc:16.2-trixie

LABEL org.opencontainers.image.source="https://github.com/NotRiemannCousin/cpp-toolchain"
LABEL org.opencontainers.image.description="Shared Linux CI toolchain image (GCC 16.2) for Thoth and Hermes"

ARG CMAKE_VERSION=3.31.6

RUN apt-get update && apt-get install -y --no-install-recommends \
        ninja-build \
        ccache \
        liburing-dev \
        libssl-dev \
        pkg-config \
        git \
        curl \
        ca-certificates \
        gdb \
        lcov \
        gcovr \
    && rm -rf /var/lib/apt/lists/*

RUN curl -fsSL \
        "https://github.com/Kitware/CMake/releases/download/v${CMAKE_VERSION}/cmake-${CMAKE_VERSION}-linux-x86_64.sh" \
        -o /tmp/cmake-installer.sh \
    && sh /tmp/cmake-installer.sh --skip-license --prefix=/usr/local \
    && rm /tmp/cmake-installer.sh

ENV CPM_SOURCE_CACHE=/opt/cpm-cache
ENV CCACHE_DIR=/opt/ccache
RUN mkdir -p "${CPM_SOURCE_CACHE}" "${CCACHE_DIR}"

COPY shared/cpm-warmup/CMakeLists.txt /tmp/warmup/CMakeLists.txt
RUN cd /tmp/warmup \
    && curl -fsSL https://github.com/cpm-cmake/CPM.cmake/releases/download/v0.43.1/get_cpm.cmake -o get_cpm.cmake \
    && cmake -S . -B build -G Ninja \
    && rm -rf /tmp/warmup/build

WORKDIR /workspace
