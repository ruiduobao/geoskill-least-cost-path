---
name: geoskill-least-cost-path
description: '成本距离计算+Dijkstra回溯链接+路径提取，输出最小成本路径'
---

# 最小成本路径 | Least Cost Path

Using a cost raster, computes the minimum cumulative cost distance and backlinks from the source to the whole grid with Dijkstra (8-neighborhood, diagonal weighted by √2), then traces back from the target point to extract the least-cost path. Outputs a cost-distance raster and the path as GeoJSON.

## Core Algorithm / 核心算法

- Dijkstra cost distance
- Backlinks
- Path extraction and cost accounting

## Dependencies / 依赖

```bash
pip install numpy rasterio scipy
```

## Usage / 使用方法

### Example 1 (synthetic data, offline)

```bash
python geoskill-least-cost-path.py --bbox 116.0 39.0 117.0 40.0 --synthetic --output-dir ./out
```

### Example 2 (specified area + quiet mode)

```bash
python geoskill-least-cost-path.py --bbox 121.0 31.0 122.0 32.0 --synthetic --output-dir ./out2 --quiet
```

### Example 3 (real input)

```bash
python geoskill-least-cost-path.py --input <your data file> --output-dir ./out3
```

### Example 4 (tiny-area boundary test)

```bash
python geoskill-least-cost-path.py --bbox 116.39 39.90 116.40 39.91 --synthetic --output-dir ./out4 --quiet
```

## Output / 输出

| File | Format | Description |
|---|---|---|
| `cost_distance.tif` | GeoTIFF/GeoJSON/JSON | Primary output |
| `least_cost_path.geojson` | GeoTIFF/GeoJSON/JSON | Primary output |
| `output-manifest.json` | JSON | Run manifest |

## Data Source / 数据源 / Source

- Synthetic mode: locally generates physically consistent simulated data; no external data source.
- Real mode: reads local input files; no network requests.

## Privacy / 隐私声明 / Privacy

- Runs fully offline by default; makes no network requests.
- `--synthetic` mode reads no external data.
- All computation is done locally; no user data is uploaded.

## License / License

MIT

---

> 中文完整版：需要时再读 [references/SKILL.zh-CN.md](references/SKILL.zh-CN.md)，不要默认全量加载。
