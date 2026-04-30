# zed-hosts

Syntax highlighting for `/etc/hosts` files in the [Zed](https://zed.dev) editor.

Highlights:

- Full-line and inline `#` comments
- IPv4 and IPv6 addresses (as numbers)
- Hostnames (as variables)

The grammar lives in a sibling repository: [`tree-sitter-hosts`](https://github.com/vlasikhin/tree-sitter-hosts).

## Installation

### From the Zed extensions panel

Once published: open the command palette → `zed: extensions` → search for **Hosts** → Install.

### As a dev extension

1. Clone this repository.
2. In Zed, open the command palette → `zed: install dev extension`.
3. Select the cloned `zed-hosts/` directory.

Zed will fetch the grammar from `tree-sitter-hosts` at the pinned revision and compile it.

## File matching

`path_suffixes = ["hosts"]` (defined in `languages/hosts/config.toml`) already matches any path ending in `hosts`, including `/etc/hosts` and `/private/etc/hosts`. No extra configuration is needed for the standard case.

If you want to apply the language to other filenames (e.g. `Hostfile`, `hosts.bak`, custom paths), add a `file_types` override to `~/.config/zed/settings.json`:

```json
{
  "file_types": {
    "Hosts": ["Hostfile", "**/custom/path/hosts.*"]
  }
}
```

## License

MIT — see [LICENSE](./LICENSE).
