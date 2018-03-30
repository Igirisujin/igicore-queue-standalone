# igicore - Queue [Standalone Edition]
Standalone queue system for FiveM servers.

This resource allows players to connect to your server while it's full and queue until there is an available slot.

[![License](https://img.shields.io/github/license/Igirisujin/igicore-queue-standalone.svg)](LICENSE)
[![Release Version](https://img.shields.io/github/release/Igirisujin/igicore-queue-standalone.svg)](https://github.com/Igirisujin/igicore-queue-standalone/releases)

# Download and Installation
Downloads can be found on the [Releases](https://github.com/Igirisujin/igicore-queue-standalone/releases/latest) page.
Follow the instructions on the release on how to install.

# Config
Use the `igi_config_path` to define the path to the queue settings YAML file. This can be a full path or the path relative to where you launch the server from (e.g. where your startserver.sh is).

```lua
sv_maxclients = 32      # Default FiveM convar for max connected players

set igi_config_path "resources/[IgiCore]/igicore-queue/queueSettings.yml"  # Path to the config file relative to where you launch the server
```

## YAML Config File
The release zip contains an example for the queueSettings.yml file. This file allows you to specify the disconnect grace period and player priority for players on your server.

`PriorityPlayers` is a list of players with a custom priority value (Anyone not in this list will default to Priority = 100) 
`DisconnectGrace` is how long in seconds a player can disconnect from the queue and keep their spot until they reconnect.
`MaxClients` is also an extra value you can specify to override what the queue thinks the server's max client limit is. (By default, this will be read from the sv_maxclients convar in your server.cfg). Useful for debugging purposes.

Example file:
```yml
PriorityPlayers:  # List of players with a custom priority value (Anyone not in this list will default to Priority = 100)
    - SteamId:  1100001056a8b25 # Igi
      Priority: 10  # Lower number == higher priority

    - SteamId:  1100001056a8b13
    - Priority: 50

    # ... More players here

DisconnectGrace: 30 # In seconds
```


# Development
Clone this repo inside your FiveM server's ``resources`` directory and build the project in Visual Studio 2017.

Edit your ``server.cfg`` file to include the following line below in your existing configuration:

```lua
start igicore-queue
```
