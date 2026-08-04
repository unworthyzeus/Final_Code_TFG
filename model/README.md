# Final Try 80 checkpoint

`best_model.pt` is the `try80_joint_huge_pathloss_finetune` checkpoint used by
the final joint Try 80 model. It predicts attenuation, delay spread, and
angular spread from the same prior-anchored network.

The checkpoint was compared against the other final Try 80 candidates on the
complete official test split: 2,590 maps from 14 held-out cities. Building
pixels were excluded from all metrics. Every file was evaluated with the same
code, labeled dataset, calibrations, masks, batch size, and DirectML device.

| Checkpoint | Attenuation RMSE [dB] | Delay spread RMSE [ns] | Angular spread RMSE [deg] | Joint score |
|---|---:|---:|---:|---:|
| Previously published | 1.7623 | 26.9043 | 11.7855 | 12.7800 |
| Cluster finetune | 1.6947 | **26.6882** | 11.5302 | 12.5837 |
| Final finetune | **1.6737** | 26.6888 | **11.5141** | **12.5589** |

The joint score is the Try 80 selection metric:
`attenuation RMSE + 0.30 * delay spread RMSE + 0.25 * angular spread RMSE`.
The final finetune has the lowest joint test score. It contains 26,862,938
parameters and uses the `base_width=128`, `K=3` Try 80 model configuration.

## Integrity

- Size: 322,553,518 bytes
- SHA-256: `0c245de7d7d090d12563d17dc5c3d2e1de9ed96c32debc8461e15cac7a7c9e25`

The same checksum is available in `SHA256SUMS.txt`.
