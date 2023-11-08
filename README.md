# A spectrum of nonsense-mediated mRNA decay efficiency along the degree of mutational constraint

## Overview
A landmark study has proposed several factors on nonsense-mediated mRNA decay (NMD) efficiency using matched genome and transcriptome data of human cancer but was highly affected by random variance caused in measuring the NMD efficiency. In this study, using a more precise, allele-specific expression-based measure of NMD efficiency, a more accurate NMD efficiency model was developed. Combining this model with the public germline variant database stratified by allele frequency, we showed a spectrum of NMD efficiency, from common variants to somatic variants in the cancer genome. The spectrum in NMD efficiency was also evident from the change in the gene-level mutational constraint measured by the loss-of-function observed/expected upper bound fraction (LOEUF). Based on the clear association observed between the NMD efficiency and LOEUF, we propose that NMD may be a key player in shaping the landscape of gene-level mutational constraint.

## Software requirements

### Hardware requirements
The provided code requires only a standard computer with enough RAM to support the in-memory operations.

### Software requirements

This package is supported for macOS, Windows, and Linux. The package has been tested on the following systems:
- macOS: Monterey(12.4)
- Windows10


### Python Dependencies
The provided code mainly depends on the Python scientific stacks.

```
NumPy
pandas
scikit-learn
scipy
pickle
```

## Installation guide
### Install from pip
To install all the requirements, run the following command:
```
python -m pip install -r requirements.txt
```

### Install from conda
If you install the Anaconda Distribution, you will already have hundreds of packages installed. If you need to install a package, use
```
conda install <package-name>
```

## Demo and Instructions for use
We provide related codes through Jupyter Notebooks. To try it:
```
jupyter notebook
```

Run demo.ipynb through Jupyter Notebooks. Funtions predict_NMD_efficiency and predict_NMD_efficiency_df aims to predict NMD efficiency for a single and a list of data.

```
def predict_NMD_efficiency(EJC_55_500:int, downstream_exon_count:int, last_exon:int,
                           PTC_to_start_codon:int, dist_to_stop_codon:int, PTC_exon_length:int,
                           PTC_to_intron:int, upstream_exon_count:int, cDNAcnt:int, 
                           mRNA_half_life:float, c50nt_to_last_EJ:int, LOEUF:float) -> float:
```

train.ipynb and analysis.ipynb are also provided for further information.

