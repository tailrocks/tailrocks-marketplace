# tailrocks-marketplace

Claude Code plugin marketplace for tailrocks tools.

## Installation

In Claude Code:

```text
/plugin marketplace add tailrocks/tailrocks-marketplace
```

## Available Plugins

| Plugin | Description |
|---|---|
| [rust-best-practices](https://github.com/tailrocks/rust-best-practices) | Rust engineering skills for writing, reviewing, refactoring, and documenting idiomatic Rust code. |

## Install a Plugin

After adding the marketplace:

```text
/plugin install rust-best-practices@tailrocks-marketplace
```

## Local Development

Validate the marketplace manifest locally:

```sh
claude plugin validate .
```

The marketplace installs `rust-best-practices` from
`https://github.com/tailrocks/rust-best-practices.git`, so installation through
the marketplace works after that repository is published.

To test the plugin before publishing, load the plugin repo directly:

```sh
claude --plugin-dir ../rust-best-practices
```

## License

Apache-2.0
