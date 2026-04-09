# Hex CLI

![GitHub Release](https://img.shields.io/github/v/release/hex-inc/hex-cli)

<pre>
███╗  ███╗████████╗███╗  ███╗
███║  ███║███╔═███║╚███╗███╔╝
█████████║████████║ ╚█████╔╝ 
███╔══███║███╔════╝ ███╔███╗ 
███║  ███║███║ ███╗███╔╝ ███╗ 
███║  ███║████████║███║  ███║
╚══╝  ╚══╝╚═══════╝╚══╝  ╚══╝
</pre>

The official command-line interface for [Hex](https://hex.ai), designed for data people and their agents. Every command supports structured JSON output and consistent, composable patterns — making it a natural fit for AI agents, automation pipelines, and programmatic workflows, in addition to interactive use.

## Installation

### Homebrew (recommended)

Make sure to install hex from the hex-inc Homebrew tap:

`brew install hex-inc/hex-cli/hex`

### Shell installer

```sh
curl -fsSL https://hex.tech/install.sh | bash
```

## Getting started

### Authenticate

```sh
hex auth login
```

This opens a browser-based OAuth flow and stores your credentials securely in your system keyring.

To authenticate against multiple workspaces, use named profiles:

```sh
hex auth login --profile staging -H https://staging.hex.tech/
hex auth switch staging
```

### Run a project

```sh
hex run <project-id>
```

### List your projects

```sh
hex projects list
```

## Commands

| Command           | Description                                                               |
| ----------------- | ------------------------------------------------------------------------- |
| `hex auth`        | Manage authentication (`login`, `logout`, `status`, `switch`, `token`)    |
| `hex projects`    | Manage projects (`list`, `get`, `create`, `open`)                         |
| `hex run`         | Execute a project and wait for completion                                 |
| `hex runs`        | Manage project runs (`list`, `status`, `cancel`)                          |
| `hex cells`       | Manage project cells (`list`, `get`, `create`, `update`, `delete`, `run`) |
| `hex collections` | Browse collections (`list`, `get`)                                        |
| `hex connections` | Browse data connections (`list`, `get`)                                   |
| `hex groups`      | Manage workspace groups (`list`, `get`, `create`, `delete`)               |
| `hex users`       | Browse workspace users (`list`, `get`)                                    |
| `hex config`      | Manage CLI configuration (`list`, `get`, `set`, `path`)                   |
| `hex logs`        | View CLI logs                                                             |

Run `hex --help` or `hex <command> --help` for detailed usage.

## Global flags

```
--profile <NAME>  Select profile (env: HEX_PROFILE)
--json              Output as JSON
-q, --quiet         Suppress non-essential output
-v, --verbose       Show verbose output
--no-color          Disable colored output
```

## Configuration

Configuration is stored in `~/.config/hex/config.toml`. You can set configuration options using the `hex config` command.

### Credentials

Credentials are stored in your system keyring (Apple Keychain on macOS, Secret Service on Linux). If a keyring is unavailable, they fall back to `~/.config/hex/credentials.json`.

## JSON output

All commands support `--json` for machine-readable output, making it easy to integrate with scripts and CI pipelines:

```sh
hex projects list --json | jq '.[0].name'
```

## Uninstall

Remove the binary from wherever it was installed:

```sh
rm "$(which hex)"
```

To also remove configuration and credentials:

```sh
rm -rf ~/.config/hex
```

## License
Copyright © 2026 Hex Technologies, Inc. All rights reserved. This CLI tool and its source code are proprietary to Hex Technologies, Inc. and are provided solely for use by Authorized Users that have accepted the Hex Service Agreement as can be found at https://learn.hex.tech/docs/legal/hex-service-agreement or have entered into a separate, valid written agreement with Hex Technologies, Inc., governing their use of Hex's products and services. No other use, copying, modification, or distribution of this CLI tool is permitted. If you have not affirmatively accepted the terms of the Hex Service Agreement or do not currently have such an active agreement with Hex Technologies, you are not authorized to use, access, or download this software.