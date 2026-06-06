# TimelineJS Options

The `timelinejs` shortcode supports the following options from the official [TimelineJS documentation](https://timeline.knightlab.com/docs/options.html).

All options should be passed using **snake_case**.

## General Options

| Option | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `data` | String | (Required) | Path to your JSON or YAML data file relative to `assets/`. Can also be passed as the first positional argument. |
| `width` | String | `100%` | Width of the timeline. |
| `height` | String | `600px` | Height of the timeline. |
| `language` | String | Page language | [Language code](https://github.com/NUKnightLab/TimelineJS3/tree/master/src/js/language/locale) for the interface. |
| `font` | String | (Default) | Name of a supported font set. |
| `theme` | String | (Default) | Name of a supported theme. |
| `hash_bookmark` | Boolean | `false` | If `true`, the URL hash will be updated to reflect the current slide. |
| `start_at_end` | Boolean | `false` | If `true`, the timeline will start at the last slide. |
| `start_at_slide` | Number | `0` | The index of the slide to start on. |
| `track_resize` | Boolean | `true` | If `true`, the timeline will resize when the window resizes. |
| `debug` | Boolean | `false` | If `true`, TimelineJS logs verbose messages to the browser console. |
| `use_bc` | Boolean | `false` | If `true`, uses "BC/AD" instead of negative numbers for years before 0. |
| `base_class` | String | (Empty) | A class name to add to the timeline's outer container. |
| `default_bg_color` | String | (Empty) | Default background color for slides. |
| `layout` | String | (Default) | Navigation layout (`landscape` or `portrait`). |

## Navigation Options

| Option | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `timenav_position` | String | `bottom` | Position of the navigation (`top` or `bottom`). |
| `timenav_height` | Number | `150` | Height of the navigation in pixels. |
| `timenav_height_percentage` | Number | `25` | Height of the navigation as a percentage of the total height. |
| `timenav_height_min` | Number | `150` | Minimum height of the navigation in pixels. |
| `timenav_mobile_height_percentage` | Number | `40` | Height of the navigation on mobile devices. |
| `scale_factor` | Number | `2` | How many screens wide the timeline should be. |
| `optimal_tick_width` | Number | `100` | Optimal distance between major ticks in pixels. |
| `dragging` | Boolean | `true` | Whether to allow mouse-dragging navigation in the timeline. |
| `touch_dragging` | Boolean | `true` | Whether to allow touch-swipe navigation on mobile. |
| `marker_height_min` | Number | `30` | Minimum height for markers in the navigation. |
| `marker_width_min` | Number | `100` | Minimum width for markers in the navigation. |
| `marker_padding` | Number | `5` | Padding between markers. |

## Animation & Interaction

| Option | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `duration` | Number | `1000` | Animation duration in milliseconds. |
| `ease` | String | `TL.Ease.easeInOutStrong` | Easing function for animations. |
| `initial_zoom` | Number | `2` | Initial zoom level. |
| `zoom_sequence` | Array | `[0.5, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]` | Comma-separated list of zoom levels (e.g., `"1, 2, 5"`). |

## Analytics

| Option | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `ga_property_id` | String | (Empty) | Google Analytics property ID. |
| `track_events` | Array | `['back_to_start', 'nav_next', 'nav_previous', 'zoom_in', 'zoom_out']` | Comma-separated list of events to track. |

## Example

```markdown
{{< timelinejs 
    data="timelines/my-story.yaml" 
    height="500px" 
    hash_bookmark="true" 
    timenav_position="top" 
    scale_factor=3
    language="de"
    dragging="false"
>}}
```
