# Mammotion GeoJSON Map Plugin

A Lovelace resource that renders GeoJSON mowing areas on the map with area names and zone labels for Mammotion mowers.

## Installation via HACS

[![Open your Home Assistant instance and open a repository inside the Home Assistant Community Store.](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=mikey0000&repository=ha-mammotion-geojson-map-plugin&category=plugin)

Or manually:

1. Open HACS → three-dot menu (⋮) → **Custom repositories**
2. Add `https://github.com/mikey0000/ha-mammotion-geojson-map-plugin` with category **Dashboard**
3. Find **Mammotion GeoJSON Map Plugin** and click **Download**
4. add the following to the map card (ha-map-card) url: /hacsfiles/ha-mammotion-geojson-map-plugin/geojson.js

## Plugin options

Set these under the geojson plugin's `options` in your `ha-map-card` config:

| Option | Default | Description |
| --- | --- | --- |
| `entity_id` | – | The mower's `lawn_mower.*` entity. |
| `rotation_deg` | `0` | Rotate the rendered GeoJSON by this many degrees. |
| `rotation_origin_lat` / `rotation_origin_lon` | auto (centroid) | Optional rotation origin. |
| `erase_by` | `"progress"` | Passed to `get_mow_progress_geojson`. |
| `geojson_max_points` | `3000` | Caps the main GeoJSON (boundaries/zones/paths) to roughly this many positions by subsampling. Dense `path` geometry can cause slowdowns or freezes on some browsers; thinning it keeps render cost bounded. Set `0` to disable thinning. |
| `mow_path_max_points` | `1500` | Caps the mow-path/coverage geometry to roughly this many positions by subsampling, so render cost stays bounded as coverage grows. Set `0` to disable thinning and render the full path. |
| `show_mow_path` | `true` | Set `false` to skip the mow-path/coverage layer entirely (boundaries, zones, dock and mower marker still render). |

Example:

```yaml
type: custom:map-card
entities:
  - entity: device_tracker.luba_xxxxxxxx_luba_xxxxxxxx
plugins:
  - name: geojson
    url: /hacsfiles/ha-mammotion-geojson-map-plugin/geojson.js
    options:
      entity_id: lawn_mower.luba_xxxxxxxx
      mow_path_max_points: 1500
```

## Requirements

The **Mammotion** integration must be installed and at least one mower must have a synced map.
