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

- The AUR branch of a given package is cloned under `$AURORA_LIB_PATH/<package>`.
- `makepkg` is used to build the package first to understand whether key acquisition is needed.
- (Optional) If the build process outputs a signature file, `aurora` tries to acquire it automatically.
- `aurora` installs the package via `makepkg`, which eventually calls `pacman`.

Basically, the steps are more or less the same that are listed on [Arch Wiki](https://wiki.archlinux.org/title/Arch_User_Repository#Installing_and_upgrading_packages).

#### Environment variables

Here are the environment variables that `aurora` uses for `aurora install`:

`AURORA_LIB_PATH`

This variable is used to define the clone path for the packages.

By default, it is set to `$HOME/.local/lib`.

Users can either define this in their shell configuration files (e.g. `.bashrc`, `.zshrc`) or provide the variable before running the command, like shown below:

```bash
# 1 - export can be done either in the current shell instance, or in the configuration files.
$ export AURORA_LIB_PATH="/path/for/your/packages"
$ aurora install package1 package2

# 2 - provide the variable before the command.
$ AURORA_LIB_PATH="/path/for/your/packages" aurora install package1 package2
```
