# YAML Format Documentation

This module allows you to define timelines using a concise YAML format, which is automatically transpiled to the official TimelineJS JSON format.

**Key simplifications:**
- **Flattened Text:** Use `headline` and `text` directly on the slide object.
- **Smart Dates:** Use `date` (start) and `end` (end). Supports Hugo date objects, "YYYY-MM-DD" strings, or just "YYYY".
- **Simple Media:** Use `media` for just the URL, or as a map for full options (`url`, `caption`, `credit`, etc.).
- **Simple Background:** Use `background` for just the URL/color, or as a map.
## Slide Structure (Title, Events, and Eras)

Every slide (whether it's the `title` slide, an item in `events`, or an item in `eras`) supports the following fields in the concise format:

| Field | Description | JSON Equivalent |
| :--- | :--- | :--- |
| `headline` | The slide title (HTML supported). | `text.headline` |
| `text` | The body text of the slide (HTML supported). | `text.text` |
| `date` | The start date. Supports Hugo date objects, "YYYY-MM-DD" strings, or "YYYY". | `start_date` |
| `end` | The end date. Same format as `date`. | `end_date` |
| `media` | A URL string (shortcut) or a full Map (see Media section). | `media` |
| `background` | A URL/Color string (shortcut) or a full Map. | `background` |
| `group` | (Events only) Used to group events visually. | `group` |
| `display_date` | A string to override how the date is displayed. | `display_date` |

## Date Handling

The `date` and `end` fields are "smart". You can provide:
- **A Date Object:** `2023-10-25` (YAML native date)
- **A String:** `"2023-10-25"` or `"2023"`
- **A Full Map:** If you need specific granularity like `hour` or `minute`:
  ```yaml
  date:
    year: 2023
    month: 10
    day: 25
    hour: 14
  ```

## Media Handling

You can use a simple string for the URL:
```yaml
media: "https://youtu.be/..."
```
Or a map for full control:
```yaml
media:
  url: "https://example.com/image.jpg"
  caption: "An amazing photo"
  credit: "John Doe"
  alt: "Alternative text"
```

## Background Handling

You can use a simple string for a color or image URL:
```yaml
background: "#ff0000"
# OR
background: "https://example.com/bg.jpg"
```
Or a map:
```yaml
background:
  url: "https://example.com/bg.jpg"
  color: "#333333"
```

## Precision Dates (Hours, Minutes, Seconds)

The parser automatically extracts time components if you provide a full ISO string or a Hugo date object:

```yaml
# ISO String with time
date: "2023-10-25T14:30:00Z"

# Hugo/YAML Date object
date: 2023-10-25 14:30:00
```

The transpiler will convert these into the `hour`, `minute`, and `second` fields required by TimelineJS.

## Specification Coverage

The YAML transpiler is a "smart wrapper" over the official spec. It covers nearly everything by passing through unknown fields directly.

### Simplified Fields (The "Magic" ones)
These fields are transformed from a flat structure to the nested JSON structure:
- `headline`, `text` → `text: { headline, text }`
- `date`, `end` → `start_date`, `end_date` (with automatic parsing)
- `media` → `media: { url: "..." }` (if string)
- `background` → `background: { url: "..." }` (if string)

### Direct Pass-through Fields
Any field not listed above is passed through **exactly as defined**. This means you can use official JSON fields directly:
- `display_date`, `group`, `unique_id`, `autofocus`, etc.

### Top-Level Fields
Supported top-level fields:
- `events` (Array), `title` (Object), `eras` (Array), `scale` (String: "human" or "cosmological").

## Example File (`assets/timelines/example.yaml`)

```yaml
title:
  headline: "Concise Timeline"
  text: "Built with Hugo"
  date: 2020

events:
  - date: 2021-01-01
    end: 2021-12-31
    headline: "The First Year"
    text: "A lot happened."
    media: "https://example.com/year1.mp4"
    group: "Phase 1"

  - date: 2022-06-15
    headline: "Midpoint"
    background: "blue"
    group: "Phase 2"

eras:
  - date: 2021
    end: 2022
    headline: "The Early Days"
```
