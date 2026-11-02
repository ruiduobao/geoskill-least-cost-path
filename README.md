# Least Cost Path (geoskill-least-cost-path)

> Cost distance computation + Dijkstra back-links + path extraction, outputting the least-cost path

---

## 1. Overview

Based on a cost raster, Dijkstra computes the minimum accumulated cost distance and back-links from the source point to the whole grid (8-neighborhood, diagonal weighted by √2); the least-cost path is then traced back from the target point. Outputs a cost distance raster and a path GeoJSON.

## 3. Quick Start

```bash
pip install -r requirements.txt
python geoskill-least-cost-path.py --bbox 116 39 117 40 --synthetic --output-dir ./out
```

## 4. CLI Parameters

Run `python <skill>.py --help` for the full list. Common parameters:

| Parameter | Type | Description |
|---|---|---|
| `--bbox` | `float[4]` | WGS84 bounding box `min_lon min_lat max_lon max_lat` |
| `--input` | `path` | Local input file (GeoJSON/GeoTIFF/etc.) |
| `--output-dir` | `path` | Output directory (default `./output`) |
| `--synthetic` | `flag` | Use synthetic data instead of real input |
| `--quiet` | `flag` | Suppress non-essential stdout |

## 5. Input / Output

| File | Format | Description |
|---|---|---|
| `cost_distance.tif` | GeoTIFF/GeoJSON/JSON | Primary output |
| `least_cost_path.geojson` | GeoTIFF/GeoJSON/JSON | Primary output |
| `output-manifest.json` | JSON | Run manifest |

## 6. Technical Principle

- Dijkstra cost distance
- Back-links (backlink)
- Path extraction and cost accounting

## 8. License

MIT License. See [`LICENSE`](./LICENSE) for full text.

---

> 中文完整版：[references/SKILL.zh-CN.md](references/SKILL.zh-CN.md)
