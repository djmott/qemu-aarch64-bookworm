# qemu-aarch64-bookworm

Docker images for QEMU ARM64 (aarch64) emulation and application runtime on Debian Bookworm.

## Images

| Image | Purpose |
|-------|---------|
| **qemu-builder** | QEMU user-mode emulator for running/building aarch64 binaries on x86_64. Includes cross-compilation toolchain. |
| **runtime** | Slim application runtime with non-root user. |

## Build Locally

Build in order (base image first):

```bash
# 1. QEMU builder (base image - build first)
docker build -f Dockerfile.base -t qemu-builder .

# 2. Runtime
docker build -f Dockerfile.vcpkg -t runtime .
```

## Pull from GHCR

After pushing to GitHub, images are available at:

```
ghcr.io/<owner>/qemu-aarch64-bookworm-qemu-builder:latest
ghcr.io/<owner>/qemu-aarch64-bookworm-runtime:latest
```

Example (replace `opensource` with your org/user):

```bash
docker pull ghcr.io/opensource/qemu-aarch64-bookworm-qemu-builder:latest
docker pull ghcr.io/opensource/qemu-aarch64-bookworm-runtime:latest
```

## GitHub Actions

The workflow builds and pushes both images to GHCR on:

- Push to `main` or `master`
- Push of version tags (`v*`, e.g. `v1.0.0`)

Tags: `latest`, `sha-<short-sha>`, and the version tag when applicable.
