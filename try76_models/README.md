# Try 76 trained expert checkpoints

This directory contains the 12 best Try 76 checkpoints used by the
distribution-first GMM U-Net path-loss model. There is one checkpoint for each
combination of six morphology classes and the LoS or NLoS receiver region.

The files are stored as regular Git blobs, not Git LFS objects. Each checkpoint
is 43,633,198 bytes and contains the selected epoch, model state, optimizer
state, model configuration, and validation score.

## Checkpoints

- `dense_block_highrise_los.pt`
- `dense_block_highrise_nlos.pt`
- `dense_block_midrise_los.pt`
- `dense_block_midrise_nlos.pt`
- `mixed_compact_lowrise_los.pt`
- `mixed_compact_lowrise_nlos.pt`
- `mixed_compact_midrise_los.pt`
- `mixed_compact_midrise_nlos.pt`
- `open_sparse_lowrise_los.pt`
- `open_sparse_lowrise_nlos.pt`
- `open_sparse_vertical_los.pt`
- `open_sparse_vertical_nlos.pt`

The architecture, evaluation code, experiment configurations, and full Try 76
documentation are available in the
[Try 76 source directory](https://github.com/unworthyzeus/TFGAllProgress_Tries_and_Attempts/tree/main/TFGSeventySixthTry76).

## Loading a checkpoint

```python
import torch

from src.model_try76 import Try76Model, Try76ModelConfig

checkpoint = torch.load(
    "try76_models/open_sparse_lowrise_los.pt",
    map_location="cpu",
    weights_only=False,
)
model = Try76Model(Try76ModelConfig(**checkpoint["model_cfg"]))
model.load_state_dict(checkpoint["model"])
model.eval()
```

Use the corresponding Try 76 YAML and evaluation script for preprocessing,
height conditioning, topology routing, and LoS or NLoS masking. SHA-256 hashes
are listed in `SHA256SUMS.txt`.
