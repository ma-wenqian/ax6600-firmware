# Firmware-Layer Patches

Use this directory for adjustments that should be applied after the source tree is checked out but before build validation:

- package tweaks
- feed-side fixes
- product-level file overrides

Do not place source fork history here. If a change must be carried long-term against upstream source, move it to `ax6600-source`.

## Feed Package Patches

Feed package patches are organized as: `feed-packages/<feed-name>/<package-name>/*.patch`

Example: `feed-packages/packages/netdata/0001-disable-cloud-aclk.patch`

Supported feed names:
- `packages` (immortalwrt/packages)
- `luci` (immortalwrt/luci)
- `routing` (openwrt/routing)
- `telephony` (openwrt/telephony)
- `video` (openwrt/video)

## Active Patches

### netdata

- `0001-disable-cloud-aclk.patch`: Disable Netdata Cloud (ACLK) to fix protobuf/absl API incompatibility
  - Issue: absl::LogMessageFatal constructor signature changed in newer versions
  - Solution: Disable cloud feature (--disable-cloud) which requires problematic protobuf code
