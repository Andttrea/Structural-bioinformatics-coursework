# Structural Bioinformatics: Protein Structure Prediction and Comparison

**Repository maintained by:** Andrea Villarruel García   
**Course:** Structural Bioinformatics Algorithms — Dr. Bruno Contreras

## Overview

This repository documents a collection of hands-on exercises from an undergraduate structural bioinformatics course. The activities explore how computational tools can be used to **predict, assess, align, and interpret protein structures**.

Rather than presenting a single research pipeline, the repository brings together four complementary exercises: prediction and validation of a protein structure with AlphaFold 2, modeling a transcription factor–DNA complex with AlphaFold 3, structural comparisons using Foldmason and Python, and an introduction to protein folding through Foldit.

## Projects

### 1. CD300H: Tertiary structure prediction and validation

**Tools:** AlphaFold 2 (via ColabFold), SAVES, SWISS-MODEL Structure Assessment

Using the [CD300H protein sequence](estructura_terciaria/A0A0K2S4Q6.fasta) from UniProt, this exercise generated a predicted protein structure with ColabFold and assessed it using complementary structural-quality tools.

The evaluation examined stereochemical geometry, sequence–structure compatibility, and model-quality estimates. The recorded assessments included an **ERRAT quality factor of 70.44**, a **VERIFY3D result of FAIL**, a **MolProbity score of 3.38**, and a **global QMEANDisCo estimate of 0.46 ± 0.06**. These mixed results emphasize why a predicted structure should be evaluated rather than treated as experimentally validated.

![CD300H structural assessment](estructura_terciaria/swiss_model_resuts/structure.png)

[Methods and files](estructura_terciaria/README.md) · [Results and interpretation](estructura_terciaria/Results.md)

### 2. NANOG: Protein–DNA complex modeling with AlphaFold 3

**Tools:** AlphaFold 3, SWISS-MODEL Structure Assessment, MolProbity, QMEANDisCo

This exercise examined the transcription factor **NANOG**, a regulator of pluripotency, in a predicted complex with a DNA sequence. Two input configurations were compared:

- **Full-length NANOG**, including regions beyond the DNA-binding domain.
- **A trimmed NANOG sequence** focused on the DNA-binding homeodomain.

The saved AlphaFold 3 prediction inputs and model files are available in the repository. Comparing the two configurations provided an opportunity to investigate how the included protein region influences global structural-quality measures.

| Model | MolProbity score | Global QMEANDisCo |
|---|---:|---:|
| Trimmed NANOG | 1.68 | 0.67 ± 0.11 |
| Full-length NANOG | 2.60 | 0.42 ± 0.05 |

These values are reported from the project’s structure-assessment outputs. They suggest more favorable *global assessment metrics* for the trimmed model; they do not, on their own, establish experimental accuracy or validate a DNA-binding mechanism.

| Trimmed NANOG–DNA model | Full-length NANOG–DNA model |
|:---:|:---:|
| ![Trimmed NANOG–DNA structure](estructura_cuarternaria/swiss_model/NANOG_trimmed/structure.png) | ![Full-length NANOG–DNA structure](estructura_cuarternaria/swiss_model/NONOG_full/structure.png) |

[Methods and files](estructura_cuarternaria/README.md) · [Results and interpretation](estructura_cuarternaria/Results.md)

### 3. Structural alignments, sequence identity, and RMSD

**Tools:** CATH, Foldseek/Foldmason, Python

This exercise explored structural similarity among protein domains selected from a CATH superfamily. Foldmason was used for structure-based sequence alignment and comparison, followed by pairwise analysis of two selected structure pairs.

An **instructor-provided Python structural-superposition script** was adapted to calculate and report sequence identity alongside root-mean-square deviation (RMSD). The original script is credited to **Bruno Contreras-Moreira** in the source code.

| Structure pair | Reported sequence identity | Reported RMSD |
|---|---:|---:|
| 2JUH model 2 vs. 2AJE model 6 | 79.38% | 10.61 Å |
| 2ROH model 20 vs. 2ROH model 1 | 71.88% | 25.10 Å |

The values illustrate how sequence identity and structural-superposition metrics offer different perspectives on similarity. RMSD interpretation depends on the alignment and atom correspondences used.

![Foldmason alignment](superposiciones/foldmason.png)

[Methods and files](superposiciones/README.md) · [Results and interpretation](superposiciones/results/Results.md) · [Adapted Python script](superposiciones/src/indentity_rmsd.py)

### 4. Exploring protein folding with Foldit

**Tool:** Foldit

An introductory interactive exercise explored structural features involved in protein folding, including backbone geometry, side-chain packing, steric clashes, and hydrophobic interactions.

[Exercise overview](fold_it/README.md) · [Reflection and screenshots](fold_it/foldit_reporte.md)

## Skills demonstrated

| Area | Techniques and tools |
|---|---|
| Structure prediction | Using AlphaFold 2/ColabFold and AlphaFold 3 to obtain predicted structural models |
| Model assessment | Interpreting MolProbity, Ramachandran plots, QMEANDisCo, SAVES, and VERIFY3D |
| Structural bioinformatics | Using CATH and Foldseek/Foldmason to explore structural relationships |
| Programming | Adapting Python code for sequence-identity calculation and structural comparisons |
| Scientific reasoning | Comparing alternative models and recognizing the limitations of computational confidence and structural-similarity metrics |

## Repository organization

```text
.
├── estructura_terciaria/    # CD300H: AlphaFold 2 and structural validation
├── estructura_cuarternaria/ # NANOG–DNA: AlphaFold 3 model comparison
├── superposiciones/        # Foldmason and Python structural comparisons
├── fold_it/                # Interactive folding exercise
└── README.md               # Overview of the course activities
```

Each activity contains its own documentation and, where available, saved outputs, figures, and detailed interpretation.

## Scope and acknowledgments

This is a **coursework portfolio**, not a newly developed protein-structure prediction algorithm or a single validated software pipeline. The AlphaFold, Foldmason, and structure-validation tools were used as existing scientific resources. The structural-superposition Python script was based on teaching material provided by **Dr. Bruno Contreras-Moreira**, with an added sequence-identity calculation as documented in the exercise.

The predictions and reported quality metrics should be interpreted as computational results, not experimental confirmation of molecular structure or function.Repository dedicated to notes for the course Structural Bioinformatics Algorithms taught by Dr. Bruno Contreras.
