# Metro map

The pipeline overview metro map is generated from `assets/metro_map.mmd` using [nf-metro](https://github.com/pinin4fjords/nf-metro). If you add or rename pipeline steps, update the `.mmd` source and regenerate the images:

```bash
pip install 'nf-metro>=0.5.4' cairosvg

# Static SVG + PNG
nf-metro render assets/metro_map.mmd \
  --diamond-style symmetric \
  -o docs/images/nf-core-rnaseq_metro_map.svg \
  -o docs/images/nf-core-rnaseq_metro_map.png
  -o docs/usage/differential_expression_analysis/img/nf-core-rnaseq_metro_map.png

# Animated SVG (used in manifest + README)
nf-metro render assets/metro_map.mmd \
  --animate --diamond-style symmetric \
  -o docs/images/nf-core-rnaseq_metro_map_animated.svg

# Ensure trailing newlines on SVGs (required by pre-commit)
for f in docs/images/nf-core-rnaseq_metro_map.svg \
         docs/images/nf-core-rnaseq_metro_map_animated.svg; do
  sed -i '' -e '$a\' "$f"
done
```
