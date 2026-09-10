# Metro map

The pipeline overview metro map is generated from `assets/metro_map.mmd` using [nf-metro](https://github.com/pinin4fjords/nf-metro). If you add or rename pipeline steps, update the `.mmd` source and regenerate the images:

```bash
pip install 'nf-metro>=0.5.4' cairosvg

# Static SVG + PNG
nf-metro render assets/metro_map.mmd \
  -o docs/images/nf-core-rnaseq_metro_map.svg \
  -o docs/images/nf-core-rnaseq_metro_map_dark.png \
  -o docs/usage/differential_expression_analysis/img/nf-core-rnaseq_metro_map.svg

# Static light-mode PNG (mmd defaults to style dark)
nf-metro render assets/metro_map.mmd --mode light \
  -o docs/images/nf-core-rnaseq_metro_map_light.png

# Animated SVG (used in manifest + README)
nf-metro render assets/metro_map.mmd --animate \
  -o docs/images/nf-core-rnaseq_metro_map_animated.svg

# Ensure trailing newlines on SVGs (required by pre-commit)
for f in docs/images/nf-core-rnaseq_metro_map.svg \
         docs/images/nf-core-rnaseq_metro_map_animated.svg; do
  sed -i '' -e '$a\' "$f"
done
```
