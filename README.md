# 🧬 Docking Pose Robustness and Interaction Analysis Pipeline

This repository provides a reproducible computational workflow for evaluating docking pose robustness, spatial localization, and residue-level interaction patterns of small molecules targeting the interdomain cleft of hnRNPA1 UP1.

The pipeline is implemented in Google Colab and supports comparative analysis of blind (large-grid) and site-focused (small-grid) docking results.

---

## 🔍 Overview

This workflow was developed to:

* Assess robustness of docking results against grid-size effects
* Quantify ligand localization within a predefined binding region
* Characterize spatial clustering of docking poses
* Evaluate ligand–protein interaction patterns at residue level

Importantly, docking is used here for **structural hypothesis evaluation**, not ligand selection.

---

## ⚙️ Key Features

### 1. Docking Pose Localization

* Ligand poses are parsed from AutoDock Vina `.pdbqt` outputs
* Center-of-mass (COM) of each pose is computed
* Distance to the interdomain cleft centroid is calculated

### 2. Pocket Occupancy Analysis

* Poses within a defined threshold (≤ 8 Å) are considered proximal
* Enables quantitative comparison between blind and focused docking

### 3. Spatial Clustering (DBSCAN)

* Density-based clustering applied to COM coordinates
* Parameters:

  * `eps = 3.5 Å`
  * `min_samples = 2`
* Identifies dominant binding clusters and spatial dispersion

### 4. Ligand–Pocket Contact Analysis

* Contact fraction defined as:

  > fraction of ligand atoms within 4.5 Å of pocket atoms
* Provides interaction density per docking pose

### 5. Contact Variability

* Standard deviation of contact fraction across poses
* Used as a proxy for interaction consistency

### 6. Residue-wise Contact Mapping

* Frequency of contacts computed for residues 88–101
* Enables identification of key interaction hotspots
* Supports mechanistic interpretation of ligand binding

---

## 🧪 Input Files

* Protein structure (PDBQT format)

  * Example: `6dcl_prpared.pdbqt`

* Docking outputs (AutoDock Vina):

  * Blind docking (large grid)
  * Site-focused docking (interdomain cleft)

Example:

```
161671_large_grid.pdbqt
161671_Site_focused_grid.pdbqt
```

---

## 📊 Output Analyses

The pipeline generates:

* COM-based distance distributions
* Pocket occupancy percentages
* DBSCAN clustering summaries
* PCA visualization of pose clustering
* Contact fraction boxplots
* Contact variability metrics
* Residue-wise interaction heatmaps

---

## 🧠 Interpretation Guidelines

This workflow supports:

* Identification of consistent binding regions
* Comparison of ligand interaction patterns
* Evaluation of spatial and interaction-level robustness

It does **not** aim to:

* Predict binding affinity
* Validate docking accuracy experimentally
* Establish definitive binding specificity

Instead, it provides **multi-metric structural evidence** to support downstream analysis (e.g., MD simulations).

---

## 📌 Binding Region Definition

* Target site: **Interdomain cleft of hnRNPA1 UP1**
* Residues analyzed: **88–101**

---

## 🚀 Usage

1. Open the notebook in Google Colab
2. Upload:

   * receptor `.pdbqt`
   * docking output files
3. Run all cells sequentially

---

## 🔗 Repository Link

GitHub: https://github.com/romenmeitei/SMA

---

## 📄 Citation

If you use this workflow, please cite the associated manuscript (under preparation).

---

## ⚠️ Notes

* Results depend on docking quality and input structures
* Thresholds (distance, contact cutoff) are empirically chosen
* Interpretation should be combined with complementary analyses

---

## 👨‍🔬 Author

Dr. L. Romen Meitei
Regional Institute of Medical Sciences (RIMS), Imphal

---

## 📬 Contact

For questions or collaboration:

* GitHub Issues
* or direct communication via institutional contact

---
