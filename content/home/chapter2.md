+++
weight = 40
+++
{{% section %}}

# Chapter 2

### Applications to *M. tuberculosis* Nanopore variant calling

Benchmark Nanopore versus Illumina SNP calling and show our algorithms meet the needs of clinical and public health users.

<progress class="chapter2-progress" max="100" value="66"></progress>
</br>66%

---

## TB and Public Health

-   \#1 cause of death by a single pathogen
-   Public health requirements for TB diagnostics are resistance prediction, species identification, and **clustering of genomes**.
-   Requirements currently met with Illumina
-   Reasons to consider switching to Nanopore: cost, location of burden, speed

---

## Genetic clustering

The first step towards clustering a set of genomes is determining a distance matrix.

-   ~~Feeding aligned genomes into a phylogenetic tree-building tool~~
-   Counting SNP differences and clustering based on these

---

## Chapter Aims

*M. tuberculosis* public health applications

-   ~~Species identification~~
-   Prediction of drug resistance
-   Epidemiological clustering of sample

**How can `pandora` be used to improve these requirements?**

**Show that Nanopore sequencing is now capable of performing these tasks**

---

## Dataset

Same isolate DNA extraction sequenced on both Illumina and Nanopore

-   119 samples from Madagascar (35 PacBio)
-   83 samples from South Africa
-   20 samples from Birmingham

**150 samples after QC** (7 PacBio)

---

## What have I done?

-   Prepared data (i.e. basecalling, file system organisation etc.)
-   Quality control
-   Assembly benchmark
-   Train ONT basecalling model
-   Baseline Illumina and Nanopore variant calls
-   `pandora` variant calls (in progress)

---


## Baseline variant analysis

#### Variant truth sets

-   Illumina - COMPASS, PHE pipeline based on `samtools` with filters
-   Nanopore - `bcftools` with filters

Baseline Illumina/Nanopore concordance, using PacBio as a validation (where we have it)

---

## Baseline concordance

Call rate: what % of true ALTs does `bcftools` make a REF/ALT call

Concordance: what % of true ALTs does `bcftools` genotype agree with truth

---

### Baseline concordance

<img src="images/alt_concordance.png"  height="550" width="1100" style="border: none;">

---

### Baseline distance

<img src="images/dotplot.png"  height="550" width="1100" style="border: none;">

---

### Baseline distance

<img src="images/close_dotplot.png"  height="550" width="1100" style="border: none;">

---

### Validation

<img src="images/baseline_truth.png" height="450"  style="border: none;">

---

## What's left to do?

- Finish `pandora` variant calling and compare with other callers
- Clustering of samples

---

### `pandora` Variant Calling

**Using two PRGs of varying complexity:**

-   Call SNPs and indels with `pandora`
-   How does complexity of PRG affect concordance and computational cost
-   Reproduce same analysis from baseline

---

### Clustering

-   Use distance matrices and linear equation to define Nanopore SNP threshold
-   Cluster based on this threshold and see how concordant with Illumina
-   Does multi-sample analysis improve clustering?


{{% /section %}}
