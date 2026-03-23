# Hex CLI

![GitHub Release](https://img.shields.io/github/v/release/hex-inc/hex-cli)

```
███╗ ███╗████████╗███╗ ███╗
███║ ███║███╔═███║╚███╗███╔╝
█████████║████████║ ╚█████╔╝
███╔══███║███╔════╝ ███╔███╗
███║ ███║███║ ███╗███╔╝ ███╗
███║ ███║████████║███║ ███║
╚══╝ ╚══╝╚═══════╝╚══╝ ╚══╝
```

> [!IMPORTANT]
> **Early Beta** — This project is in very early beta. Expect significant breaking changes as it matures.

The official command-line interface for [Hex](https://hex.ai), designed for data people and their agents. Every command supports structured JSON output and consistent, composable patterns — making it a natural fit for AI agents, automation pipelines, and programmatic workflows, in addition to interactive use.

## Installation

### Homebrew (recommended)

Make sure to install hex from the hex-inc Homebrew tap:

`brew install hex-inc/hex-cli/hex`

### Shell installer

```sh
curl --proto '=https' --tlsv1.2 -LsSf https://github.com/hex-inc/hex-cli/releases/latest/download/hex-installer.sh | sh
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
-p, --profile <NAME>  Select profile (env: HEX_PROFILE)
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
