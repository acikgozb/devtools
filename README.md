# `devex-scripts`

Highly opinionated scripts to create a unique development environment and experience.
Caters to people who prefer DIY over premade environments.

The scripts are primarily designed to be used by Linux hosts.
Arch Linux is the main supported Linux distribution.

## Disclaimer

Since these scripts are highly opinionated for my own taste, it is probably better for you to take inspiration instead and implement the functionality by yourself.

If you still wish to use these scripts though, by all means go ahead!
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

The installation consists of two parts:

- Installing the required dependencies (1),
- Putting the script under `$PATH` (2).

(1) The dependencies are listed in the `README` that covers each script.
If you wish to install, please read the docs first to see which dependencies you need:

- [tmux scripts](./tmux/README.md)
- [Desktop environment scripts](./de/README.md)

(2) In order to run the scripts without specifying its full path, they need to be under one of the directories listed in `$PATH`.
To see whether the scripts can be found via `$PATH` lookup or not, you can use `which`:

```bash
# Assume that `wifi` script is installed.
script_name="wifi"
# Assume "$HOME/bin" is in "$PATH".
installed_script_path="$HOME/bin"

# Ensure that `which` outputs the full path of the installed script, as shown in the example below.
which "$script_name" # /home/username/bin/wifi
```

Once `$PATH` lookup works, you can reference the script in anywhere you want and start using as you wish.
