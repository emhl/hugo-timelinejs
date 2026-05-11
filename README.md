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

you need to crate a json file in the assets directory that follows the [specification](https://timeline.knightlab.com/docs/json-format.html)

and then you can embed it with the shortcode
```hugo
{{< timelinejs "timelines/example.json" >}}
```

### Additional options
if you want you can change [some options](https://timeline.knightlab.com/docs/options.html) from the shortcode parameter as well. currently availible are:
- `data`: Path to JSON Object containing the Data
- `height`: The height of the timeline
- `width`: The width of the timeline.
- `hashBookmark`: If set to true, TimelineJS will update the browser URL each time a slide advances, so that people can link directly to specific slides,
