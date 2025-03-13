# Desktop Environment Scripts

The scripts in this group are mainly geared towards providing minimal desktop environment modules.

The modules are implemented for Wayland compositors only, and Rofi is used to provide a basic UI to the user.
Therefore, the scripts depend on having the following dependencies on the host:

- `wayland`
- `rofi-wayland`

## UI

- The Rofi menus that are used in these scripts do not override user configurations or themes.

- The navigation between the menus are pretty minimal.
  By default, it is possible to exit from the UI by pressing `ESC`, regardless of wherever the user currently is.
  Special commands are used in some scripts to re-execute the selected action (e.g. rescanning WiFi networks or available Bluetooth devices).

Please read the sections below to understand the dependencies used by each script and the provided actions.

## `power`

**Dependencies**: `systemd`

`power` script allows users to terminate the `$USER` session, restart or shutdown the system entirely.

## `wifi`

**Dependencies**: `nmcli`

`wifi` script utilizes `nmcli` to allow users to manage their WiFi connections through a simple UI.

Here are the available actions:

- Turn off/on WiFi: Self explanatory.

- Connect to a network: This action makes `wifi` scan the available networks.
  Upon a successful scan, the signal strengths and network names are shown on the menu.
  If the selected network is not a known network (a previously connected network), `wifi` asks for the password and then tries to connect.
  If the selected network is a known network, then `wifi` connects to it without asking for the password.
  Regardless of whether the connection is established or not, the user is redirected back to the main menu.

- Disconnect from the network (_network name_): This action makes `wifi` disconnect from the previously connected network.
  It is only shown if the user is connected to a network.
  `wifi` does not delete the connection from the known connection list during this action, therefore it is possible to automatically connect back to the network later without using `wifi` (e.g. after the initial boot).

Informative messages are shown when a redirect happens to notify the user about the result of the selected action.

## `bluetooth`

**Dependencies**: `bluetoothctl`

Similar to `wifi` script, `bluetooth` utilizes `bluetoothctl` to allow users to manage their Bluetooth connections through a simple UI.

Here are the available actions:

- Enable/Disable bluetooth: Self explanatory.

- Scan devices: This action makes `bluetooth` scan the available devices.
  Upon a successful scan, the devices are shown on the menu.
  If nothing is found after a scan, then the user is redirected back to the main menu.
  Once a device is selected from the list, then `bluetooth` tries to trust the device first, and then connect to it.
  Regardless of whether the connection is established or not, the user is redirected back to the main menu.

- Disconnect from device(s): This action allows users to disconnect from their devices.
  Once this action is selected, then the connected devices are shown on the menu.
  Selecting a device triggers `bluetooth` to disconnect from it.
  Once the action is completed, the user is redirected back to the main menu.

Informative messages are shown when a redirect happens to notify the user about the result of the selected action.

### Non-Supported Cases

Right now, `bluetooth` script can only connect to devices that does not require a PIN code (e.g. earphones).
**Trying to establish a connection to a device that requires a PIN code will result in an error.**

This will be handled in a future commit.
