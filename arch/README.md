# Scripts for Arch Linux

The scripts in this group are mainly geared towards adding simple functionality on top of a barebones Arch Linux installation.

## `aurora`

**Dependencies**: `makepkg, gnupg, git`

_WARNING_: `aurora` is a DIY AUR helper script that is highly experimental and intentionally non customizable.

It's development is done based on current needs and the main goal is definitely not to replace widely used tools.
Therefore, if you want a fully fledged AUR helper, please check out the tools like `yay`.

### Usage

`aurora` provides the following functionalities:

- Installing a package (with or without an `validpgpkeys` entry)

#### Installing a package

Assuming that `aurora` is on `$PATH`:

```bash
# Mulitple packages can be installed as expected.
aurora install [package]...
```

Here is how the installation works:

- The AUR branch of a given package is cloned under `$HOME/lib/aur/<package>`.
- `makepkg` is used to build the package first to understand whether key acquisition is needed.
- (Optional) If the build process outputs a signature file, `aurora` tries to acquire it automatically.
- `aurora` installs the package via `makepkg`, which eventually calls `pacman`.

Basically, the steps are more or less the same that are listed on [Arch Wiki](https://wiki.archlinux.org/title/Arch_User_Repository#Installing_and_upgrading_packages).
