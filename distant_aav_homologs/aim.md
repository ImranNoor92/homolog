# Specific Aim 2: Design and Test Candidates from Uncultured Viral Genomes

## Objective
Design and test novel AAV capsid protein candidates by mining uncultured viral genomes, focusing on naturally occurring T=3 capsids within the *Parvoviridae* family. This approach aims to circumvent the limitation in Specific Aim 1, where T=3-forming regions in distant relatives may not efficiently promote T=3 architecture in AAVs.

---

## Rationale
While Specific Aim 1 explores T=3-compatible regions from distant viruses, this aim focuses on **closer relatives to AAV**, such as members of the *Parvoviridae* family. We hypothesize that **uncultured parvoviruses with unusually large genomes** may naturally encode T=3 capsid proteins. By identifying and modeling these candidates, we can create **better-adapted T=3 capsids** for AAV engineering.

This strategy builds upon successful discoveries from the Luque Lab, which previously identified novel small capsids (T=1 and T=3) in tailed phages not observed in isolated viruses.

---

## Strategy Overview

### 1. **Database Mining**
- Download the **IMG/VR database** of uncultured viral genomes from the **DOE Joint Genome Institute (JGI)**.
- Select **genomes >6 kb** from the **Parvoviridae** family.

### 2. **Taxonomic Classification and ORF Prediction**
- Run the **VIRify** pipeline for classification at the **genus and family levels** (expected ~86.6% accuracy).
- Identify **open reading frames (ORFs)** using **Prodigal** (primary) and **Glimmer** (supplementary, for eukaryotic viruses).

### 3. **Functional Annotation**
- Annotate ORFs using **hmmscan** against the **Pfam** database.
- Select sequences containing hits to **single jelly roll capsid domains**.

### 4. **Structure Prediction and Assembly**
- Use **RoseTTAFold** and **AlphaFold** to predict the **3D structures** of candidate capsid proteins.
- Apply **AlphaFold-Multimer** to model **trimeric assemblies**.
- Arrange trimeric tiles into **T=1 and T=3 capsid architectures**.

### 5. **Theoretical Biophysical Evaluation**
- Analyze predicted capsid assemblies using **biophysical simulations** (from C.1.2 in Specific Aim 1).
- Identify stable T=3 candidates and the **key edge fragments** responsible for T=3 assembly.

### 6. **Structural Comparison with AAV2**
- Compare uncultured capsid trimeric tiles with **AAV2 trimers** using **ChimeraX matchmaking**.
- Identify AAV2 protein regions requiring integration of **T=3-enabling fragments**.

### 7. **Candidate Design and Testing**
- Define a **design library** of AAV2-based capsid protein variants.
- Refine and prioritize **at least 20 candidates** using methods from Specific Aim 1 (C.1.2 and C.1.3).

---

## Goal
Develop and test a set of **≥20 engineered AAV capsid variants** that incorporate T=3-enabling motifs from uncultured *Parvoviridae* genomes, yielding larger, more stable capsids suitable for therapeutic applications.

---

## Tools & Pipelines
- IMG/VR database (DOE JGI)
- VIRify pipeline (taxonomic annotation)
- Prodigal & Glimmer (ORF prediction)
- ViPhOG & Pfam (functional annotation)
- RoseTTAFold & AlphaFold (structure prediction)
- AlphaFold-Multimer (trimer modeling)
- ChimeraX (structural alignment)
- Custom biophysical modeling tools (as per Specific Aim 1)

---

## Deliverables
- Filtered and annotated list of uncultured parvoviral capsid proteins
- Predicted structures for monomers and trimers
- T=3 AAV2 variants with rationally designed modifications
- Experimental validation-ready sequence constructs

---


Raw Text 
Specific Aim 1: 
Design and test candidates from capsid protein homologs known to form T=3
capsids. The capsid proteins in AAV and viruses in the Parvoviridae family share a protein fold (the jelly roll
fold) with viruses that form T=3 capsids. Some of these distant relatives have been observed to transition
from T=1 to T=3 capsids. We will use structural homology to incorporate amino acid mutations in the AAV
capsid protein to favor the formation of T=3 capsid. We will computationally design at least 200 capsid protein
variants. We will apply the classical nucleation theory of virus capsids to identify the protein variants predicted
to favor T=3 architectures over T=1 capsids. We will then apply transient dynamics theory to narrow down the
candidates that assemble the T=3 capsids efficiently within expected cellular timescales. Finally, we will apply
coarse-grained molecular dynamics to assess the stability of the top candidates. We will select for validation
at least 20 capsid protein variants among those more likely to form T=3 capsids theoretically. The vectors
produced will be screened for capsid size, titer, genomic packing, and infectivity. The priority will be identifying
vectors forming capsid sizes around 40 nm.


Specific Aim 2: 
Design and test candidates mining uncultured viral genomes bioinformatically.
T=3 capsids have not been observed among isolates of AAV variants or viruses in the Parvoviridae family,
but they could exist among uncultured viruses. To this end, we will mine uncultured viral genomes
bioinformatically to identify capsid proteins among unusually large genomes of parvoviruses that could form
T=3 capsids naturally. The proteins will be folded bioinformatically. Sequence and structural homology will be
used to introduce mutations in the AAV capsid for candidates forming T=3 capsids. We will then apply the
same biophysical selection methods and empirical validation strategy described in Specific Aim 1.

This README captures the scope, rationale, and detailed plan of execution for Specific Aim 2 and will guide both computational and experimental phases of candidate development.

