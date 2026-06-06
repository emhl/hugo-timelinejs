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
if you want you can change [some options](https://timeline.knightlab.com/docs/options.html) from the shortcode parameter as well. currently availible are:
- `data`: Path to JSON Object containing the Data
- `height`: The height of the timeline
- `width`: The width of the timeline.
- `hashBookmark`: If set to true, TimelineJS will update the browser URL each time a slide advances, so that people can link directly to specific slides,
