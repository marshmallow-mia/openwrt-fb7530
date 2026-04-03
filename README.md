# openwrt-fb7530

Builds a ready-to-flash OpenWrt image for the **AVM Fritzbox 7530** using the [openwrt-imagebuilder-action](https://github.com/izer-xyz/openwrt-imagebuilder-action).

## Device

| Field | Value |
|-------|-------|
| Device | AVM Fritzbox 7530 |
| Target | `ipq40xx/generic` |
| Profile | `avm_fritz7530` |
| OpenWrt page | https://openwrt.org/toh/avm/avm_fritz_box_7530 |

## Build

The GitHub Actions workflow (`.github/workflows/build.yml`) runs automatically on every push to `main`, or can be triggered manually from the **Actions** tab.

### Configuration

Edit [`config`](config) to change:

| Variable | Description |
|----------|-------------|
| `image` | ImageBuilder image (target-subtarget, e.g. `ipq40xx-generic`) |
| `profile` | Device profile (e.g. `avm_fritz7530`) |
| `openwrt_version` | OpenWrt release version |
| `packages` | Space-separated list of packages to add (prefix with `-` to remove) |
| `disabled_services` | Space-separated list of services to disable at boot |
| `debug` | Set to `true` for verbose build output |

### Custom files

Place any files you want included in the image under `files/` (e.g. `files/etc/config/network`). The directory is passed to the ImageBuilder via the `files` parameter.

### Releases

After a successful build the workflow creates a GitHub Release tagged `v<openwrt_version>-<run_number>` and attaches all generated firmware files from the `bin/` directory.

## Flashing

Follow the official OpenWrt instructions for flashing the Fritzbox 7530:
https://openwrt.org/toh/avm/avm_fritz_box_7530
