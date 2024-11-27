# macOS Docker Environment

This repository contains a `docker-compose.yaml` file to set up and run a macOS environment inside a Docker container using the [macOS](https://github.com/dockur/macos) project. This setup allows you to run macOS within a container for development and testing purposes.

## Features

- macOS virtualized using Docker.
- Configurable environment options for RAM, CPU cores, and disk size.
- Persistent storage for maintaining the container's state.
- SSH and web UI access to the macOS instance.
- Optimized setup instructions for installing and using Xcode.

## Setup Instructions

1. Start the container:
   ```bash
   docker-compose up -d
   ```

2. Follow the instructions at [macOS](https://github.com/dockur/macos).

## Xcode Setup

1. **Install Xcode**:
   - If possible, install Xcode from the macOS App Store.
   - If you're unable to log in to the App Store within the container:
     1. Download Xcode from the [Apple Developer Portal](https://developer.apple.com/download/all/).
     2. Install Xcode and move it to the default `/Applications` directory.

2. **Run Xcode at least once**:
   - This ensures that it completes its initial setup.

3. **Install Xcode Command Line Tools**:
   - Open a terminal in the macOS container and run:
     ```bash
     xcode-select --install
     ```

4. The disk space should be at least 50GB to account for:
   - Environment (macOS, Xcode, tools): ~42GB.
   - Build caches and other files.

## Persistent Data

The `./macos_storage` directory is mounted to the container at `/storage`. This allows you to persist the state of the container, enabling you to recreate the container without losing data.

## Troubleshooting

- **Cannot log in to the App Store**:
  - This is a known issue in virtualized macOS environments. Use the Apple Developer Portal to download Xcode as a workaround.

- **Performance issues**:
  - Adjust `RAM_SIZE` and `CPU_CORES` in the `docker-compose.yaml` file based on your system's available resources.

## For additional configuration and optimizations refer to

- [macOS](https://github.com/dockur/macos)
- [Docker-OSX](https://github.com/sickcodes/Docker-OSX)
- [macOS Optimizations](https://github.com/sickcodes/osx-optimizer)
