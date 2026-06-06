# TimelineJS Hugo Shortcode

## Installation

You need to have [Hugo](https://gohugo.io) installed and an existing Hugo site config

## using Hugo Modules (preferred)
Setup your site to [use Hugo Modules](https://gohugo.io/hugo-modules/use-modules/)

get this module
```sh
hugo mod get github.com/emhl/hugo-timelinejs
```

add this to your hugo.toml or config.toml:
```toml
[module]
[[module.imports]]
    path = 'github.com/emhl/hugo-timelinejs'
```

## using git

- clone this repo into your themes folder or add it as a submodule.
- add `hugo-timelinejs` to the list of themes in your config

## Usage

You can create a data file in the `assets` directory. This module supports the original [JSON specification](https://timeline.knightlab.com/docs/json-format.html) as well as a custom `YAML` format.

### Concise YAML Format

Use YAML for a cleaner authoring experience. The module automatically transpiles YAML files to the required JSON.

See the [YAML Format Documentation](docs/YAML_FORMAT.md) for available fields and examples.

### Embedding

Embed the timeline with the shortcode:
```hugo
{{< timelinejs "timelines/history.yaml" >}}
```
or for JSON:
```hugo
{{< timelinejs "timelines/example.json" >}}
```

### Additional options
If you want you can change [some options](https://timeline.knightlab.com/docs/options.html) from the shortcode parameters as well. Currently available are:
- `data`: Path to the JSON or YAML file containing the timeline data (relative to `assets/`).
- `height`: The height of the timeline (default: `600px`).
- `width`: The width of the timeline (default: `100%`).
- `hashBookmark`: If set to `true`, TimelineJS will update the browser URL each time a slide advances, allowing direct links to specific slides.
- `lang`: The language code for the UI (e.g., `de`, `fr`, `es`). Defaults to the current Hugo page language. Over 60 locale definitions are included in the module.
- `font`: The name of a built-in font combination (e.g., `Amatic-Andika`, `Bevan-PontanoSans`). 
- `theme`: The name of a built-in theme (e.g., `dark`, `contrast`).

*Note: While the `font` and `theme` parameters are supported, the corresponding CSS files are not bundled by default to keep the module lightweight. If you wish to use them, ensure you provide the necessary CSS files in your site's `static/` directory.*
