# NoisyDiffusion - Privacy Preserving Synthetic Gene Expression Data Generation

Generating synthetic gene expression data has the potential to advance computational biology and health research by enabling broader access to data. However, creating synthetic data that is both highly faithful to the original and useful from a biological perspective while also ensuring privacy is a significant challenge. While diffusion models are powerful generative tools, their application to sensitive genomic data requires careful consideration of privacy implications, especially regarding their susceptibility to memorisation and membership inference attacks (MIAs). This project presents NoisyDiffusion: a conditional diffusion model designed to generate synthetic gene expression data while incorporating mechanisms for differential privacy to mitigate MIAs.

As this project is part of the **CAMDA 2025 - Health Privacy Challenge**, it was evaluated on the TCGA-COMBINED and TCGA-BRCA datasets. NoisyDiffusion demonstrated strong utility, with classifiers trained on its synthetic data achieving high accuracy (e.g., 96.92% on TCGA-COMBINED) and AUPR, rivaling top non-private baselines (Multivariate, CVAE) and significantly outperforming other generative models, including those with explicit DP (DP-CVAE, CTGAN).

Crucially, for privacy, Membership Inference Attack (MIA) AUCs were close to 0.5, suggesting good resilience and performance comparable to the Multivariate baseline. This work demonstrates that diffusion models can effectively generate high-quality, privacy-respecting synthetic genomic data, offering a promising pathway for advancing research while safeguarding sensitive information.

## Results

### TCGA-BRCA — per-split results

| Split | accuracy_synthetic | avg_pr_macro_synthetic | accuracy_real | avg_pr_macro_real | feature_overlap_count | feature_overlap_proportion | MMD_score | discriminative_score | distance_to_closest | distance_to_closest_base |
|------:|-------------------:|-----------------------:|--------------:|------------------:|----------------------:|--------------------------:|----------:|---------------------:|--------------------:|--------------------------:|
| 1 | 0.7569 | 0.7250 | 0.8394 | 0.7658 | 16 | 0.3265 | 0.014285 | 0.617128 | 26.0795 | 24.1028 |
| 2 | 0.7431 | 0.7512 | 0.8670 | 0.8204 | 18 | 0.3830 | 0.012269 | 0.638554 | 25.4180 | 23.6720 |
| 3 | 0.7936 | 0.8219 | 0.8945 | 0.9415 | 15 | 0.3125 | 0.010425 | 0.627353 | 25.7810 | 24.3472 |
| 4 | 0.8165 | 0.7702 | 0.8624 | 0.8536 | 17 | 0.3696 | 0.006728 | 0.553247 | 23.6742 | 23.9720 |
| 5 | 0.7788 | 0.7241 | 0.8848 | 0.9065 | 25 | 0.5102 | 0.011040 | 0.584094 | 24.8320 | 23.9976 |
| **average** | **0.77778** | **0.75848** | **0.86962** | **0.85756** | **18.20** | **0.38036** | **0.010949** | **0.604075** | **25.15694** | **24.01832** |

### TCGA-COMBINED — per-split results

| Split | accuracy_synthetic | avg_pr_macro_synthetic | accuracy_real | avg_pr_macro_real | feature_overlap_count | feature_overlap_proportion | MMD_score | discriminative_score | distance_to_closest | distance_to_closest_base |
|------:|-------------------:|-----------------------:|--------------:|------------------:|----------------------:|--------------------------:|----------:|---------------------:|--------------------:|--------------------------:|
| 1 | 0.9665 | 0.9843 | 0.9746 | 0.9895 | 60 | 0.6122 | 0.005442 | 0.691777 | 22.4321 | 23.2451 |
| 2 | 0.9792 | 0.9900 | 0.9827 | 0.9966 | 61 | 0.6703 | 0.005874 | 0.678634 | 22.1188 | 23.3086 |
| 3 | 0.9769 | 0.9917 | 0.9792 | 0.9907 | 56 | 0.6087 | 0.003896 | 0.685234 | 23.8200 | 23.1524 |
| 4 | 0.9664 | 0.9898 | 0.9826 | 0.9949 | 54 | 0.6000 | 0.005244 | 0.714078 | 22.5898 | 23.1367 |
| 5 | 0.9572 | 0.9855 | 0.9664 | 0.9909 | 59 | 0.6344 | 0.004437 | 0.726804 | 23.2322 | 23.4071 |
| **average** | **0.96924** | **0.98826** | **0.97710** | **0.99252** | **58.00** | **0.62512** | **0.004979** | **0.699305** | **22.83858** | **23.24998** |


