# Mammotion GeoJSON Map Plugin

A Lovelace resource that renders GeoJSON mowing areas on the map with area names and zone labels for Mammotion mowers.

## Installation via HACS

[![Open your Home Assistant instance and open a repository inside the Home Assistant Community Store.](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=mikey0000&repository=ha-mammotion-geojson-map-plugin&category=plugin)

Or manually:

1. Open HACS → three-dot menu (⋮) → **Custom repositories**
2. Add `https://github.com/mikey0000/ha-mammotion-geojson-map-plugin` with category **Dashboard**
3. Find **Mammotion GeoJSON Map Plugin** and click **Download**
4. add the following to the map card (ha-map-card) url: /hacsfiles/ha-mammotion-geojson-map-plugin/geojson.js

## Requirements

The **Mammotion** integration must be installed and at least one mower must have a synced map.
