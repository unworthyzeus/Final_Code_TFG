# Final Try 80 checkpoint

`best_model.pt` is the `try80_joint_huge_pathloss_finetune` checkpoint used by
the final joint Try 80 model. It predicts attenuation, delay spread, and
angular spread from the same prior-anchored network.

The checkpoint was compared against the previously published Try 80 file on
the complete official test split: 2,590 maps from 14 held-out cities. Building
pixels were excluded from all metrics. Both files were evaluated with the same
code, labeled dataset, calibrations, masks, batch size, and DirectML device.

| Checkpoint | Attenuation RMSE [dB] | Delay spread RMSE [ns] | Angular spread RMSE [deg] |
|---|---:|---:|---:|
| Published checkpoint | 1.7623 | 26.9043 | 11.7855 |
| `try80_joint_huge_pathloss_finetune` | **1.6947** | **26.6882** | **11.5302** |

The replacement improves all three test RMSE values. The checkpoint contains
26,862,938 parameters and uses the `base_width=128`, `K=3` Try 80 model
configuration.

## Integrity

- Size: 322,553,518 bytes
- SHA-256: `fd1c71bd3eaa9b2386ac5e6dc076a27aeee677a6cbb289510ce38eaa1a03a3a2`

The same checksum is available in `SHA256SUMS.txt`.
