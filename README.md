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

## Make Zed recognize the bare `hosts` filename

`/etc/hosts` has no extension, so Zed needs an explicit hint. Add to `~/.config/zed/settings.json`:

```json
{
  "file_types": {
    "Hosts": ["hosts", "**/etc/hosts", "**/private/etc/hosts"]
  }
}
```

Reload the file (or restart Zed) and the `Hosts` language will be applied.

## Local testing

`/etc/hosts` is read-only without `sudo`. To preview highlighting without editing the real file, copy it:

```sh
cp /etc/hosts ~/hosts-preview.hosts
zed ~/hosts-preview.hosts
```

The `.hosts` suffix matches `path_suffixes` in `languages/hosts/config.toml` and triggers the language without any settings change.

## License

MIT — see [LICENSE](./LICENSE).
