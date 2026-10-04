# DINOv2 Visual Analysis of Tokyo Covered Shopping Streets (Arcades)

## Overview

This notebook explores whether **self-supervised visual features (DINOv2)** can reveal typological patterns across Tokyo's covered shopping streets (*shōtengai* / arcades) — a central subject of my PhD research in urban/landscape design.

Instead of manually classifying arcades by pre-defined categories (material, era, width, etc.), this project tests a **bottom-up, feature-driven approach**: let a pretrained vision model describe what it "sees," and look for structure in that description.

## Data

- **Source**: Google Street View images
- **Scope**: ~6,000 images sampled along Tokyo's covered shopping streets (arcades)
- **Collection environment**: Google Colab

## Method (current stage)

1. **Feature extraction** — Each street-view image is passed through a pretrained **DINOv2** (self-supervised Vision Transformer) backbone to obtain a **768-dimensional embedding** per image. DINOv2 requires no manual labels, which makes it well suited to a dataset with no existing typological annotations.
2. **Colour-space analysis** — In parallel, basic **RGB-based colour statistics** are extracted per image, as a lightweight, interpretable complement to the high-dimensional DINOv2 features (e.g. checking whether colour alone separates arcades as well as learned visual features do).
3. **Clustering & visualisation** — The 768-dim embeddings are reduced and clustered to produce a visual map of the dataset, used to inspect whether visually/structurally similar arcades group together.

**Status**: This is the first half of a larger pipeline. Feature extraction, colour analysis, and cluster visualisation are complete; **similarity search / retrieval is not yet implemented** (see Next Steps).

## Output

- Cluster visualisation of the ~6,000-image dataset in DINOv2 feature space
- Preliminary comparison between DINOv2-based grouping and RGB-based grouping

## Tech Stack

- Python, Google Colab
- PyTorch
- DINOv2 (`facebookresearch/dinov2`)
- (Downstream analysis — clustering/visualisation libraries — to be documented as the pipeline is finalised)

## Why this matters for my research

Tokyo's covered shopping streets are usually studied through qualitative, case-by-case observation. This project is an attempt to complement that with a **quantitative, image-based typology** — grouping arcades by *how they visually present themselves* rather than by administrative category alone.

## Next Steps

- Extend from pure visual similarity (DINOv2) toward **multimodal (text + image) semantic search**, so arcades could be queried by natural-language description rather than only by reference image — bringing this closer to a text-to-image retrieval system over a domain-specific photo archive.
- Formalise the colour-analysis comparison and document the clustering method/parameters used.
- Package the feature-extraction step as a reusable script rather than a single notebook.

## Author

Chaoya zhang — PhD candidate, Open and Environmental Systems, Keio University. Research focus: Tokyo's covered shopping streets. Background in landscape architecture (Sichuan University).
