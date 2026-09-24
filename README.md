<p align="center">
    <a href="https://github.com/lupaxa-miscellaneous-toolbox">
        <img src="https://raw.githubusercontent.com/the-lupaxa-project/brand-assets/master/logos/organisations/miscellaneous-toolbox/readme-logo.png" alt="Organisation Logo" />
    </a>
</p>

<h1 align="center">Favicon Generator</h1>

Generate a modern favicon set from one source image (PNG, JPEG, WebP, or SVG):

- `favicon-16x16.png`, `favicon-32x32.png`
- `favicon.ico` (16, 32, 48)
- `apple-touch-icon.png` (180×180)
- `icon-192.png`, `icon-512.png`, `icon-maskable-512.png`
- `site.webmanifest`
- `favicon-links.html` (optional HTML snippet)
- `favicon.svg` when the source is SVG

## Install

Python 3.10 or newer. The PyPI package name is `lupaxa-favicon-generator`.
The console command is `favicon-generator`.

SVG input also needs the system Cairo library (`brew install cairo` on macOS,
or `apt install libcairo2` on Debian/Ubuntu).

```bash
python -m pip install lupaxa-favicon-generator
```

From a clone, for development:

```bash
python -m pip install -e ".[dev]"
```

## Use

```bash
favicon-generator --help
favicon-generator logo.png
favicon-generator logo.svg \
  --output-dir site/assets/favicons \
  --prefix /assets/favicons/ \
  --name "My App" \
  --short-name "App" \
  --theme-colour "#0A0A0A" \
  --background-colour "#0A0A0A" \
  --background "#0A0A0A" \
  --padding 0.05
```

The same commands work as a module:

```bash
python -m lupaxa.favicon_generator --help
python -m lupaxa.favicon_generator logo.png
```

Default output directory: `./favicons`.

For Apple touch icons, prefer a non-transparent `--background` so iOS does not
composite onto an unexpected fill. Maskable icons use an opaque white fill
when `--background` is transparent.

### Useful Flags

| Flag                                       | Purpose                           |
| :----------------------------------------- | :-------------------------------- |
| `--fit contain\|cover\|stretch`            | How the source fills each canvas. |
| `--no-ico` / `--no-html` / `--no-manifest` | Skip optional outputs.            |
| `--overwrite`                              | Replace existing files.           |

Use `--help` for the full option list.

## Testing

```bash
make init
make python-install-dev
make python-check
```

Or without Make:

```bash
python -m pip install -e ".[test]"
pytest
```

Coverage for `lupaxa.favicon_generator` is reported by default. Optional Cairo
SVG integration tests run when marked and skip if native Cairo is unavailable:

```bash
pytest -m cairo
```

## Documentation

The published guide is at
<https://favicon-generator.thelupaxaproject.org/>.

Site Markdown lives in `mkdocs/`.

```bash
python -m pip install -r requirements.txt
make mkdocs-serve
```

`make mkdocs-build` builds the site. A strict build is `python -m mkdocs build --strict`.

<a href="https://github.com/the-lupaxa-project">
    <img src="https://raw.githubusercontent.com/the-lupaxa-project/brand-assets/master/logos/components/footer-for-child-orgs.svg" alt="The Lupaxa Project Footer" width="100%" />
</a>
