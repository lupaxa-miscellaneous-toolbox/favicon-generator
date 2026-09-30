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
```

Default output directory: `./favicons`. Use `--overwrite` if that directory
already contains generated files you want replaced.

The same commands work as a module:

```bash
python -m lupaxa.favicon_generator --help
python -m lupaxa.favicon_generator logo.png
```

### SVG and Site Paths

SVG input is rasterised with cairosvg and also copied to `favicon.svg` in the
output directory. Use `--prefix` so the HTML snippet and `site.webmanifest`
point at the correct public path (for example `assets/favicons/` or
`/favicons/`). `--name` / `--short-name` feed the web manifest.

```bash
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

### Fit, Background, and Padding

| Flag                            | Notes                                                 |
| :------------------------------ | :---------------------------------------------------- |
| `--fit contain\|cover\|stretch` | How the source fills each canvas (`contain` default). |
| `--background`                  | Canvas fill: `transparent`, CSS name, or hex.         |
| `--padding`                     | Fractional padding `0.0`–`0.45`.                      |

For Apple touch icons, prefer a non-transparent `--background` so iOS does not
composite onto an unexpected fill. Maskable icons use an opaque white fill
when `--background` is transparent.

### Skipping Optional Outputs

```bash
favicon-generator logo.png --no-ico --no-html
favicon-generator logo.png --output-dir favicons --overwrite
```

| Flag            | Effect                            |
| :-------------- | :-------------------------------- |
| `--no-ico`      | Skip `favicon.ico`.               |
| `--no-html`     | Skip the HTML snippet.            |
| `--no-manifest` | Skip `site.webmanifest`.          |
| `--overwrite`   | Replace existing generated files. |

## CLI Options

Run `favicon-generator --help` for the authoritative list from your installed
version.

| Option                | Default                  | Description                             |
| :-------------------- | :----------------------- | :-------------------------------------- |
| `source`              | *(required)*             | Source image: PNG, JPEG, WebP, or SVG.  |
| `-o` / `--output-dir` | `favicons`               | Output directory.                       |
| `--fit`               | `contain`                | `contain`, `cover`, or `stretch`.       |
| `--background`        | `transparent`            | Canvas background.                      |
| `--padding`           | `0`                      | Fractional padding `0.0`–`0.45`.        |
| `--theme-colour`      | `#FFFFFF`                | `theme-color` / manifest `theme_color`. |
| `--background-colour` | same as `--theme-colour` | Manifest `background_color`.            |
| `--name`              | source stem or `App`     | Manifest name.                          |
| `--short-name`        | same as `--name`         | Manifest `short_name`.                  |
| `--prefix`            | *(empty)*                | URL prefix for HTML and manifest.       |
| `--html-file`         | `favicon-links.html`     | HTML snippet filename.                  |
| `--no-manifest`       | off                      | Skip `site.webmanifest`.                |
| `--no-html`           | off                      | Skip HTML snippet.                      |
| `--no-ico`            | off                      | Skip `favicon.ico`.                     |
| `--overwrite`         | off                      | Replace existing files.                 |

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

<a href="https://github.com/the-lupaxa-project">
    <img src="https://raw.githubusercontent.com/the-lupaxa-project/brand-assets/master/logos/components/footer-for-child-orgs.svg" alt="The Lupaxa Project Footer" width="100%" />
</a>
