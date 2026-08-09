# Ampbase Homebrew Tap

Homebrew formula for the **Ampbase supervisor** — the agent that runs on your
hosts, connects them to [Ampbase](https://ampbase.io), applies configuration,
and reports health.

## Install

```sh
brew install ampbase-io/tap/ampbase
```

That installs `ampbase`, a signed and notarized universal binary covering both
Apple Silicon and Intel.

## Enroll

Installing the binary does not connect it to anything. Enroll it against one of
your channels:

```sh
sudo ampbase enroll --key <agent-key> --endpoint <opamp-endpoint>
```

Add `--user` to enroll without `sudo`, as a per-user LaunchAgent instead of a
system LaunchDaemon.

Your channel's get-started page has this command with the key and endpoint
already filled in — copy it from there rather than assembling it by hand.

## Linux

This tap is macOS-only. On Linux, use the installer:

```sh
curl -fsSL https://ampbase.io/install.sh | sh
```

It serves per-architecture builds and drops a systemd unit where systemd is
present.

## Documentation

- [Install the supervisor](https://ampbase.io/docs/install-supervisor)
- [Supervisor reference](https://ampbase.io/docs/supervisor-reference)
- [Quickstart](https://ampbase.io/docs/quickstart)

## About this repository

`Formula/ampbase.rb` is **generated**. Each supervisor release renders it from a
template and pushes it here, pinning the version and the SHA-256 of the exact
artifact published at `https://ampbase.io/releases/`. Edits made directly to the
formula are overwritten by the next release — change the template in the Ampbase
repository instead.

The formula deliberately declares no `service` block. `ampbase enroll` installs
and manages the launchd job; a second manager writing its own copy would leave a
host with two competing definitions of one service.

## License

The Ampbase supervisor is proprietary software licensed under the Ampbase Cloud
Service Agreement. Full terms at [ampbase.io/terms](https://ampbase.io/terms).
