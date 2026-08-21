<!-- markdownlint-disable -->
<p align="center">
  <a href="https://github.com/lupaxa-miscellaneous-toolbox">
    <img src="https://raw.githubusercontent.com/the-lupaxa-project/brand-assets/master/logos/organisations/miscellaneous-toolbox/readme-logo.png" alt="Project Logo" width="256"/><br/>
  </a>
</p>
<h3 align="center">
  The Lupaxa Miscellaneous Toolbox<br />
  Part of The Lupaxa Project
</h3>

<br />

# lupaxa-favicon-generator

Generate a modern favicon set from one source image (PNG, JPEG, WebP, or SVG):
PNG sizes, `favicon.ico`, Apple touch icon, PWA icons (including maskable),
`site.webmanifest`, optional HTML link snippet, and `favicon.svg` when the
source is SVG.

Built for documentation and product sites used by The Lupaxa Project.

## Features

- One source image → full favicon / PWA icon set
- Formats: PNG, JPEG, WebP, and SVG (SVG needs system Cairo)
- Outputs: 16/32 PNG, multi-size ICO, Apple touch 180×180, 192/512 and
  maskable 512 icons, webmanifest, optional HTML snippet
- CLI flags for fit mode, padding, theme/background colours, and name metadata
- Fully typed, linted, formatted, and tested
- MkDocs documentation included

## Installation

### From PyPI

```bash
pip install lupaxa-favicon-generator
```

### From source (development mode)

```bash
pip install -e ".[dev]"
```

The console command is `favicon-generator`.

SVG input also requires the system Cairo library (`brew install cairo` on
macOS or `apt install libcairo2` on Debian/Ubuntu).

## CLI quick start

```bash
favicon-generator --help
favicon-generator --version
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

Default output directory: `./favicons`.

You can also run the CLI as a module:

```bash
python -m lupaxa.favicon_generator --help
python -m lupaxa.favicon_generator logo.png
```

## Requirements

- Python 3.10+
- Runtime dependencies: `Pillow`, `cairosvg`
- System Cairo for SVG input

## Documentation

Online documentation:

[Documentation](https://favicon-generator.thelupaxaproject.org/)

Source repository:

[GitHub](https://github.com/lupaxa-miscellaneous-toolbox/favicon-generator)

### Serve docs locally

From a clone of the repository:

```bash
make mkdocs-serve
```

Then open the local URL printed by MkDocs in your browser.

## Development

Clone the repository and install with Make:

```bash
make init                # first-time makefile-skills checkout
make python-install-dev  # editable install with [dev]
make python-check        # lint, type-check, and test
```

<a href="https://github.com/the-lupaxa-project">
    <img src="https://raw.githubusercontent.com/the-lupaxa-project/brand-assets/master/logos/components/footer-for-child-orgs.svg" alt="The Lupaxa Project Footer" width="100%" />
</a>
