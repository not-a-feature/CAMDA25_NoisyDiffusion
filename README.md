# NoisyDiffusion - Privacy Preserving Synthetic Gene Expression Data Generation

Generating synthetic gene expression data has the potential to advance computational biology and health research by enabling broader access to data. However, creating synthetic data that is both highly faithful to the original and useful from a biological perspective while also ensuring privacy is a significant challenge. While diffusion models are powerful generative tools, their application to sensitive genomic data requires careful consideration of privacy implications, especially regarding their susceptibility to memorisation and membership inference attacks (MIAs). This project presents NoisyDiffusion: a conditional diffusion model designed to generate synthetic gene expression data while incorporating mechanisms for differential privacy to mitigate MIAs.

As this project is part of the **CAMDA 2025 - Health Privacy Challenge**, it was evaluated on the TCGA-COMBINED and TCGA-BRCA datasets. NoisyDiffusion demonstrated strong utility, with classifiers trained on its synthetic data achieving high accuracy (e.g., 96.9% on TCGA-COMBINED) and AUPR, rivaling top non-private baselines (Multivariate, CVAE) and significantly outperforming other generative models, including those with explicit DP (DP-CVAE, CTGAN).

Crucially, for privacy, Membership Inference Attack (MIA) AUCs were close to 0.5, suggesting good resilience and performance comparable to the Multivariate baseline. This work demonstrates that diffusion models can effectively generate high-quality, privacy-respecting synthetic genomic data, offering a promising pathway for advancing research while safeguarding sensitive information.

## Results

### TCGA-BRCA — per-split results

| Split | accuracy_synthetic | avg_pr_macro_synthetic | accuracy_real | avg_pr_macro_real | feature_overlap_count | feature_overlap_proportion | MMD_score | discriminative_score | distance_to_closest | distance_to_closest_base |
|------:|-------------------:|-----------------------:|--------------:|------------------:|----------------------:|--------------------------:|----------:|---------------------:|--------------------:|--------------------------:|
| 1 | 0.7569 | 0.7251 | 0.8761 | 0.9000 | 18 | 0.3913 | 0.015825 | 0.641604 | 20.7196 | 24.2979 |
| 2 | 0.7890 | 0.7657 | 0.8761 | 0.8150 | 19 | 0.4222 | 0.007425 | 0.618504 | 23.4020 | 23.9873 |
| 3 | 0.8119 | 0.8298 | 0.9128 | 0.9647 | 20 | 0.4348 | 0.012824 | 0.679659 | 21.3375 | 23.6054 |
| 4 | 0.7661 | 0.7945 | 0.8165 | 0.8653 | 20 | 0.4348 | 0.015297 | 0.607662 | 20.8944 | 24.2450 |
| 5 | 0.7465 | 0.6854 | 0.8433 | 0.8434 | 21 | 0.4468 | 0.015439 | 0.648447 | 21.1993 | 23.9869 |
| **average** | **0.7741** | **0.7601** | **0.8650** | **0.8777** | **19.60** | **0.4260** | **0.013362** | **0.639175** | **21.5106** | **24.0245** |

### TCGA-COMBINED — per-split results

| Split | accuracy_synthetic | avg_pr_macro_synthetic | accuracy_real | avg_pr_macro_real | feature_overlap_count | feature_overlap_proportion | MMD_score | discriminative_score | distance_to_closest | distance_to_closest_base |
|------:|-------------------:|-----------------------:|--------------:|------------------:|----------------------:|--------------------------:|----------:|---------------------:|--------------------:|--------------------------:|
| 1 | 0.9711 | 0.9882 | 0.9792 | 0.9932 | 60 | 0.6977 | 0.006159 | 0.683935 | 22.1786 | 23.1698 |
| 2 | 0.9653 | 0.9779 | 0.9757 | 0.9933 | 62 | 0.6739 | 0.005128 | 0.754717 | 22.6649 | 23.2381 |
| 3 | 0.9618 | 0.9828 | 0.9699 | 0.9843 | 54 | 0.6506 | 0.008264 | 0.736902 | 21.3483 | 23.3183 |
| 4 | 0.9676 | 0.9858 | 0.9792 | 0.9927 | 61 | 0.6703 | 0.005091 | 0.736119 | 22.7231 | 23.3630 |
| 5 | 0.9792 | 0.9904 | 0.9850 | 0.9956 | 61 | 0.6559 | 0.007162 | 0.718464 | 21.7794 | 23.2716 |
| **average** | **0.9690** | **0.9850** | **0.9778** | **0.9918** | **59.60** | **0.6697** | **0.006361** | **0.726027** | **22.1389** | **23.2722** |


