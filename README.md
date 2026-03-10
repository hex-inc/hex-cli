# Hex CLI

![GitHub Release](https://img.shields.io/github/v/release/hex-inc/hex-cli)

> [!IMPORTANT]
> **Early Beta** — This project is in very early beta. Expect significant breaking changes as it matures.

The official command-line interface for [Hex](https://hex.ai), designed for data people and their agents. Every command supports structured JSON output and consistent, composable patterns — making it a natural fit for AI agents, automation pipelines, and programmatic workflows, in addition to interactive use.

## Installation

### Shell installer (recommended)

```sh
curl -sSL https://raw.githubusercontent.com/hex-inc/hex-cli/main/install.sh | sh
```

To install to a custom location:

```sh
curl -sSL https://raw.githubusercontent.com/hex-inc/hex-cli/main/install.sh | sh -s -- --prefix ~/.local
```

### Homebrew

Coming soon...

## Getting started

### Authenticate

```sh
hex auth login
```

This opens a browser-based OAuth flow and stores your credentials securely in your system keyring.

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
| `hex auth`        | Manage authentication (`login`, `logout`, `status`)                       |
| `hex projects`    | Manage projects (`list`, `get`, `create`, `open`)                         |
| `hex run`         | Execute a project and wait for completion                                 |
| `hex runs`        | Manage project runs (`list`, `status`, `cancel`)                          |
| `hex cells`       | Manage project cells (`list`, `get`, `create`, `update`, `delete`, `run`) |
| `hex collections` | Browse collections (`list`, `get`)                                        |
| `hex connections` | Browse data connections (`list`, `get`)                                   |
| `hex groups`      | Manage workspace groups (`list`, `get`, `create`, `delete`)               |
| `hex users`       | Browse workspace users (`list`, `get`)                                    |
| `hex profile`     | Manage environment profiles (`list`, `add`, `use`, `remove`, `current`)   |
| `hex config`      | Manage CLI configuration (`list`, `get`, `set`, `path`)                   |
| `hex logs`        | View CLI logs                                                             |

Run `hex --help` or `hex <command> --help` for detailed usage.

## Global flags

```
--api-url <URL>     Override API base URL (env: HEX_API_URL)
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

You can also set JSON as the default output format for a profile:

```sh
hex config set output_format json
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
