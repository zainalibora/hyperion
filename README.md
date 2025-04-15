# hyperion &nbsp; [![bluebuild build badge](https://github.com/tj5miniop/hyperion/actions/workflows/build.yml/badge.svg)](https://github.com/tj5miniop/hyperion/actions/workflows/build.yml)

# NOTE - THIS IMAGE SHOULDN'T BE USED (YET) AS A DAILY-DRIVING OPERATING SYSTEM, IT IS CURRENTLY IN A PROTOTYPING PHASE.

## Hyperion - A fedora COSMIC-based atomic desktop, meant for gaming, including many tweaks from Bazzite/Nobara/CachyOS. More details to come

## Why not use Bazzite? 

Bazzite is a great atomic desktop which provides an awesome 'just-works' experience for gamers.
I was originally basing Hyperion off of Bazzite, but I was getting many conflicts with packages, files, etc. I'm basing off of the official Fedora COSMIC ATOMIC spin, which should be released alongside Fedora 42.


See the [BlueBuild docs](https://blue-build.org/how-to/setup/) for quick setup instructions for setting up your own repository based on this template.

After setup, it is recommended you update this README to describe your custom image.

## Installation

> [!WARNING]  
> [This is an experimental feature](https://www.fedoraproject.org/wiki/Changes/OstreeNativeContainerStable), try at your own discretion.

To rebase an existing atomic Fedora installation to the latest build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/tj5miniop/hyperion:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/tj5miniop/hyperion:latest
  ```
- Reboot again to complete the installation
  ```
  systemctl reboot
  ```

The `latest` tag will automatically point to the latest build. That build will still always use the Fedora version specified in `recipe.yml`, so you won't get accidentally updated to the next major version.

## ISO

If build on Fedora Atomic, you can generate an offline ISO with the instructions available [here](https://blue-build.org/learn/universal-blue/#fresh-install-from-an-iso). These ISOs cannot unfortunately be distributed on GitHub for free due to large sizes, so for public projects something else has to be used for hosting.

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/tj5miniop/hyperion
```
