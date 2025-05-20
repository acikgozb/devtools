# `devtools`

Highly experimental and opinionated scripts that are used to create a unique development environment and experience.
Caters to people who prefer DIY over premade environments.

The scripts are primarily designed for Arch Linux hosts, but most of them should work in pretty much all Linux distributions (excluding the scripts under `arch` directory).

## Disclaimer

There are some important facts about these scripts which should be mentioned before moving on:

- This repository is thought as a playground, so most of the scripts are at PoC stage, meaning that they are intentionally kept non customizable.
Basically, I try to fix my problem as fast as possible in here, and then create a separate version for each which extends the functionality with a better structure to iterate upon.

- The non PoC version of these scripts can be found below:
    - [`hpm` (for `power`)](https://github.com/acikgozb/hpm)
    - [`wl` (for `wifi`)](https://github.com/acikgozb/wl)

- The scripts are designed for my own needs, so some of them might not fit your use cases.

Overall, the main goal of this repository is to help inspire others just as how I took inspiration.
Sharing is caring, right?

If you still wish to use these PoC scripts though, by all means go ahead!
Please let me know how it goes.

## Demos

### `fzfw`

<details>
    <video src="https://github.com/user-attachments/assets/d563ec74-f575-402f-8576-352bcac1a86a"></video>
</details>

### `wifi`

<details>
    <video src="https://github.com/user-attachments/assets/4f94b83a-36b5-4eb2-8c4e-a999335082d9"></video>
</details>

### `bluetooth`

<details>
    <video src="https://github.com/user-attachments/assets/3b22d8ad-81cf-4d21-a569-1735cc44db67"></video>
</details>

### `power`

<details>
    <img src="https://github.com/user-attachments/assets/97d85bc1-5a9c-4c04-b8a6-ac01d5a7b0ae" />
</details>

## Installation

Here are the steps to install any script in this repository:

- Installing the required dependencies (1).
- Cloning this repository (2).
- Putting the script under `$PATH` (3).

(1) The dependencies are listed in the `README` that covers each script.
If you wish to install, please read the docs first to see which dependencies you need:

- [tmux scripts](./tmux/README.md)
- [Zellij scripts](./zellij/README.md)
- [Desktop environment scripts](./de/README.md)
- [Arch Linux scripts](./arch/README.md)

If you miss some of the dependencies, install them with the package manager of your choice.

(2) Next, clone the repository to the place you want.

```bash
git clone git@github.com:acikgozb/devtools.git /repo/clone/path
```

(3) In order to run the scripts without specifying its full path, they need to be under one of the directories listed in `$PATH`.
I'd recommend symlinking the scripts under a directory listed in `$PATH` to not deal with copying them on each update or to keep `$PATH` clean:

```bash
# Change to a directory under $PATH.
cd /dir/under/path

# Create a soft link with either the default name or a custom one.
ln -s ../rel/path/to/the/script ./script-name

# Check if the script can be picked up via a $PATH lookup.
which script-name  # /dir/under/path/script-name

# If the full path of the script can be seen with `which`,
# you can reference the script in anywhere you want and
# start using as you wish.
script-name
```
