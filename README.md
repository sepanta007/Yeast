# Yeast

* [Overview](#overview)
* [Dataset](#dataset)
* [Methodology](#methodology)
* [Conclusion](#conclusion)
* [Requirements](#requirements)
* [Usage](#usage)
* [Acknowledgments](#acknowledgments)
* [Licence](#licence)
* [Contributors](#contributors)

## Overview

This project focuses on the analysis of the yeast protein localization dataset using various statistical and machine learning techniques. The objective is to explore the data, apply appropriate clustering and dimensionality reduction methods, and interpret the results to gain insights into the factors influencing protein localization within a cell.

## Dataset

The dataset contains 10 distinct classes representing different cellular localizations:

- **CYT** (cytosolic or cytoskeletal) : 463 instances
- **NUC** (nuclear) : 429 instances
- **MIT** (mitochondrial) : 244 instances
- **ME3** (membrane protein, no N-terminal signal) : 163 instances
- **ME2** (membrane protein, uncleaved signal) : 51 instances
- **ME1** (membrane protein, cleaved signal) : 44 instances
- **EXC** (extracellular) : 37 instances
- **VAC** (vacuolar) : 30 instances
- **POX** (peroxisomal) : 20 instances
- **ERL** (endoplasmic reticulum lumen) : 5 instances

## Methodology

### 1. Exploratory Data Analysis (EDA)

- **Boxplots** : Analyzed the distribution of numeric variables, revealing significant heterogeneity except for `erl` and `pox`. Many outliers (aberrant values) were observed beyond the minimum and maximum thresholds.

### 2. Principal Component Analysis (PCA)

- **Supplementary variables** : `erl` and `pox` as supplementary quantitative variables, `localization_site` as a supplementary qualitative variable.
- **Results** : Six main dimensions were generated, explaining significant variance in the dataset. `mcg` and `gvh` showed high contributions (cos² values), indicating their significant role in defining the main components. `vac` and `alm` also contributed but to a lesser extent.
- **Interpretation** : The coordinates of individuals in the principal component space showed significant dispersion, with specific profiles emerging in relation to the analyzed variables.

### 3. Clustering analysis

#### 3.1 Dendrogram with Ward's method

- **Agglomerative coefficient** : Achieved a high coefficient of 0.99, indicating strong clustering structure.

#### 3.2 K-means clustering

- **Indices used** :
    - **Calinski-Harabasz** : Optimal with 2 clusters.
    - **Davies-Bouldin** : Optimal with 10 clusters, matching the initial number of classes.
    - **Silhouette** : Optimal with 2 clusters.
    - **Dunn** : Optimal with 5 clusters.
- **Normalized Mutual Information (NMI)** :
    - Calinski-Harabasz : 0.1033
    - Davies-Bouldin : 0.2279
    - Silhouette : 0.1033
    - Dunn : 0.1950
- **Selection** : Davies-Bouldin was chosen due to the alignment with the original 10 classes and the highest NMI score.
- **Cluster purity** : Achieved an approximate purity index of 0.35, indicating good separation and compactness.

### 4. Detailed report

A detailed summary of the PCA results and other analyses can be found in the file `yeast.pdf`.

## Conclusion

The project successfully applied PCA and K-means clustering to the yeast protein localization dataset, revealing significant insights into the factors influencing protein localization. The Davies-Bouldin index proved to be the most effective for this dataset, providing clusters that closely matched the original classes.

## Requirements

- Jupyter notebook
- R
- Libraries : `corrplot`, `cluster`, `clusterCrit`, `moments`, `funtimes`, `ggplot2`, `FactoMineR`, `factoextra`

## Usage

1. Install the required libraries.
2. Open the Jupyter notebook and run the cells sequentially.
3. Review the detailed results in the `Yeast.pdf` file.

## Acknowledgments

This project was conducted as part of the "Numerical Data Processing" course, using the [yeast protein localization dataset](https://archive.ics.uci.edu/dataset/110/yeast) and applying techniques learned throughout the course.

## Licence

This project is licensed under the [MIT](https://github.com/sepanta007/Yeast/blob/master/LICENSE) License.

## Contributors

* [Sepanta Farzollahi](https://github.com/sepanta007)
* [Hagop Hannachian](https://github.com/hagop-h)
* [Jean-Baptiste Hochet](https://github.com/jbhochet)