# CPP Toolchain

## Shared CI infrastructure for C++ libraries

This repository contains the shared CI infrastructure used by the **Thoth** and **Hermes** C++ libraries.

It provides the Linux Docker image and the reusable Linux and Windows GitHub Actions workflows used to build and test
the libraries with the same CI flow on both platforms.

| Component      | Reference / Platform                      |
|----------------|-------------------------------------------|
| GCC            | `16.2` / Linux                            |
| MSVC           | Visual Studio 2022 (`VS 17.x`) / Windows  |
| CMake          | `3.31.6` / Linux image                    |
| Ninja          | Linux and Windows                         |
| ccache         | Linux and Windows                         |
| NVIDIA/stdexec | `nvhpc-26.05`                             |
| GoogleTest     | `v1.15.2`                                 |
| zlib           | `v1.3.1`                                  |
| CPM            | `v0.43.1`                                 |
| OpenSSL        | Linux                                     |
| liburing       | Linux                                     |

The reusable workflows use the platform-specific toolchain, configure the consumer project with CMake, compile it with
Ninja and ccache, and run its CTest suite. Linux jobs run inside the Docker image, while Windows jobs use MSVC and the
Windows-native dependencies.
