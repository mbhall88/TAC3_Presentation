+++
weight = 30
+++
{{% section %}}

# Presentation Overview

1. What have I been doing for the last 12 months?
2. Executive Summary
3. **Progress Report**
4. Discussion

---

# Chapter 1

### Variant discovery in genome graphs

Develop algorithms and software for variant discovery using bacterial genome graphs, building on work of a previous student in the lab.

<progress class="chapter1-progress" max="100" value="90"></progress> </br>90%

---

### Pan-genome

Bacterial genomes are incredibly diverse.

<img src="images/pangenome.jpg"  height="350" width="500" style="border: none;">

In an "open" pan-genome, such as *Salmonella enterica*, two individuals could share as little as 16% of their genes

---

### The single-reference problem

<img src="images/single-ref.png"  height="550" width="550" style="border: none;">

---

### Genome graphs

-   Uses a population reference graph (PRG) instead of a single, linear reference
-   PRG represents variation seen within a population
-   Two forms - local and pan-PRG

<img src="images/build-prg.png"  height="300" width="700" style="border: none;">

---

### Nanopore sequencing

<img src="images/nanopore.png"  height="400" width="600" style="border: none;">

Variant calling in its infancy (`medaka`, `nanopolish`, and Clair), but no extensive
benchmark has been completed (for Mtb)

---

### Genome Graphs + Nanopore

`Pandora` - pan-genome inference and **genotyping** with long-noisy or short-accurate reads from Rachel Colquhoun.

<img src="images/pandora.png"  height="400" width="700" style="border: none;">

---

### `pandora map`

Infer consensus sequence for a *single* sample and genotype with respect to this consensus sequence

<img src="images/pandora-no-denovo.png"  height="400" width="1000" style="border: none;">

---

### `pandora compare`

Infer consensus sequence for a *collection* of samples and genotype with respect to this consensus sequence

<img src="images/pandora-compare.png"  height="200" width="1000" style="border: none;">

---

## Limitation

`pandora` can only genotype based on variation within the graph

---

## Solution

The work in my first chapter outlines a method for removing this limitation and provides
an analysis of the gain in recall and precision by incorporating *de novo* variant discovery
into the `pandora` workflow.

---

### What have I done?


{{% fragment %}}Implement *de novo* variant discovery module within `pandora` (~1325/~3500 lines of source/test code){{% /fragment %}}
{{% fragment %}}Built evaluation framework (~1250/~3500 lines of source/test code){{% /fragment %}}
{{% fragment %}}Built a `snakemake` pipeline of ~3500 lines of codes to orchestrate the entire evaluation and simulations.{{% /fragment %}}

---

# Variant discovery in a genome graph

---

#### Step 1: Finding candidate regions

<img src="images/find-candidate.png"  height="500" width="1000" style="border: none;">

---

#### Step 2: Enumerating paths through candidate regions

<img src="images/pandora-denovo.png"  height="520" width="1000" style="border: none;">

---

# Evaluation

---

## Empirical data

-   The main focus of both `pandora` and *de novo* evaluation
-   Use `pandora` to show the benefit of the genome graph approach
-   20 *E. coli* samples from different phylogroups
-   Compare to other variant callers - `snippy`, `samtools`, `medaka`, and `nanopolish` - using a variety of references

---

## Empirical data

Difficulty in evaluating is "truth"

-   Align each pair of genomes to get differences
-   Construct truth panel from these differences
-   Augment reference with variants and map truth panel
-   Calculate recall and precision

---

### Assessing variants

<img src="images/evaluation.png"  height="520" width="1000" style="border: none;">

---

### Effect of basecalling model

<img src="images/basecall_model.png"  height="550" width="1100" style="border: none;">

---

### Precision

<img src="images/precision.png"  height="550" width="1100" style="border: none;">

---

### Recall

<img src="images/recall.png"  height="550" width="1100" style="border: none;">

---

### Outstanding work

-   Release preprint and submit paper (this month 🤞)
-   Direct integration of *de novo* variants back into PRG
-   Some refinement of genotyping as a part of Chapters 2 & 3



{{% /section %}}
