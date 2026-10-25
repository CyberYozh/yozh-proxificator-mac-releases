# YozhProxificator for Mac — downloads

<!-- Delete this comment and the paragraph "Before version 1.0.0" under it when 1.0.0 is published. -->

**Before version 1.0.0.** There is no public release yet: GitHub marks no release here as "Latest", and the download
link below does not work yet. Test builds are in the pre-release
[acceptance](https://github.com/CyberYozh/yozh-proxificator-mac-releases/releases/tag/acceptance); they are for testing,
not for general use. Download the newest image from it, `YozhProxificator-X.Y.Z.dmg`.

YozhProxificator sends the traffic of your Mac, or of the apps you choose, through proxies.

## Download

From version 1.0.0 on, this link always gives the latest release:
**[YozhProxificator.dmg](https://github.com/CyberYozh/yozh-proxificator-mac-releases/releases/latest/download/YozhProxificator.dmg)**

Requirements: a Mac with Apple silicon, macOS 15 or later.

The download is a disk image. It holds the app and a shortcut to the Applications folder, nothing else. Open the image
and drag YozhProxificator to Applications, or open the app from the image: it offers to move itself there.
The app updates itself from this repository; updates are signed, and automatic checks can be turned off in its
settings.

## Check what you downloaded

Each public release, `vX.Y.Z` (from 1.0.0 on), has a file `SHA256SUMS` with the SHA-256 of its files. Download it into
the folder where the image is, then run, in Terminal, in that folder:

    shasum -a 256 -c SHA256SUMS --ignore-missing

A test build in the release `acceptance` has a file `SHA256SUMS-X.Y.Z` of its own instead: download that one beside the
image and put its name in the command.

The image is signed with Developer ID and notarized by Apple. Put the name of your file in place of
`YozhProxificator.dmg`:

    spctl -a -t open --context context:primary-signature -v YozhProxificator.dmg

It answers `accepted` and `source=Notarized Developer ID`.

## Source code

YozhProxificator is free software under the GNU GPL v3, with no warranty. Each public release `vX.Y.Z` (from 1.0.0 on)
and each test build in the release `acceptance` carries the complete source of what it ships:

- `yozh-proxificator-mac-X.Y.Z-source.tar.gz` — the app, its system component and the build scripts;
- `yozh-xray-<commit>-source.tar.gz` — the proxy engine, a fork of Xray-core, at the commit the build pins (`<commit>`
  is the first twelve characters of that commit);
- `sparkle-<version>-source.tar.gz` — the update framework.

## The update feeds

The app reads a feed — a list of versions, with the images and notes they point to — to find out whether a newer
version exists. There are two feeds, each in a release of its own; `updates` appears with the first public release,
1.0.0:

- `acceptance` is a pre-release with the internal test builds (0.9.x) and their feed, not for general use. Each build
  comes with its source archives and its own `SHA256SUMS-X.Y.Z`; an engine or framework archive that several builds
  share is stored once. The test builds read this feed, and 1.0.0 is published into it as well, so they move on to the
  public feed with it.
- `updates` is the feed of the public releases. It is for the app, not for download; the source of each version in it
  is in that version's release `vX.Y.Z`.

## How to uninstall

1. In the app's **Settings → All traffic**, press **Remove component**.
2. Move the app to the Trash.
3. If programs stay offline, open **Yozh Unblock** from Applications. If the network is gone after the removal, run
   `sudo /Library/PrivilegedHelperTools/com.cyberyozh.proxyficator/yozh-helper restore` in Terminal.
