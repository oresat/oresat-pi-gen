# OreSat Pi Gen

Fork of [RPi-Distro/pi-gen], the repo for building Raspberry Pi OS images.

This is used to build custom Raspberry Pi OS images for OreSat projects.

## Branches

- `default`: Holds this README as guide on how to use the repo. Shares no
  history with other branches.
- `master`: Local copy of the `master` branch from pi-gen, used to build the
  arm32 Pi OS image. Should be keep in sync with pi-gen to easily merge
  into `oresat-` branches, otherwise treated as readonly.
- `arm64`: Local copy of the `arm64` branch from pi-gen, used to build the
  arm64 Pi OS image. Should be keep in sync with pi-gen to easily merge
  into `oresat-` branches, otherwise treated as readonly.
- `oresat-hgs`: The branch to build a custom image for OreSat Live handheld
  ground station.

## How this repo works

- Each branch is used to build a specific raspi image, checkout a specific
  branch if you want to build that image.
- Only merge `master` or `arm64` into an `oresat-` branch other do not merge
  branches together.
- On `oresat-*` branches, only add to stageX directories, changing the
  `README.md`, `scripts/`, etc will problaby cause merge conficts in the
  future when the latest versions of master or `arm64` are `merged` into those
  branches.
- See the `README.md` in `master` branch for explinaton of the pi-gen build
  process and stage system.

## Build a Custom OreSat image

Install build dependencies. **Note:** The follow is for Debian Linux, change as
need for other Linux distros.

```bash
$ sudo apt install coreutils quilt parted qemu-user-static debootstrap \
zerofree zip dosfstools libarchive-tools libcap2-bin grep rsync xz-utils file \
git curl bc qemu-utils kpartx gpg pigz
```

Checkout the branch for image. **Note:** Change `oresat-hgs` as needed.

```bash
$ git checkout oresat-hgs
```

Build the image.

```bash
$ ./build.sh -c config
```

[RPi-Distro/pi-gen]: https://github.com/RPi-Distro/pi-gen
