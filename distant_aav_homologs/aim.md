# 📌 Specific Aim 2: Design and Test Candidates from Uncultured Viral Genomes

## Objective
Design and test novel AAV capsid protein candidates by mining uncultured viral genomes, focusing on naturally occurring T=3 capsids within the *Parvoviridae* family. This approach aims to circumvent the limitation in Specific Aim 1, where T=3-forming regions in distant relatives may not efficiently promote T=3 architecture in AAVs.
---
While Specific Aim 1 explores T=3-compatible regions from distant viruses, this aim focuses on **closer relatives to AAV**, such as members of the *Parvoviridae* family. We hypothesize that **uncultured parvoviruses with unusually large genomes** may naturally encode T=3 capsid proteins. By identifying and modeling these candidates, we can create **better-adapted T=3 capsids** for AAV engineering.

This strategy builds upon successful discoveries from the Luque Lab, which previously identified novel small capsids (T=1 and T=3) in tailed phages not observed in isolated viruses.
---

This workflow outlines the computational and structural bioinformatics steps required to identify, model, and validate potential T=3 capsid-forming proteins from uncultured viral genomes (focused on Parvoviridae).

---

## 🧬 Step 1: Database Acquisition and Preparation

### 1.1 Download IMG/VR Database
- Go to the [JGI IMG/VR portal](https://img.jgi.doe.gov/cgi-bin/vr/main.cgi).
- Download the latest **uncultured viral genome (UViG)** dataset.
- Confirm inclusion of:
  - Genome FASTA files
  - Annotation files (metadata, taxonomy, host prediction, etc.)

### 1.2 Filter for Target Genomes
- **Filter genomes** belonging to the *Parvoviridae* family.
- **Select only genomes** where:
  - `length > 6,000 bp`
  - `lineage = Parvoviridae` (from metadata or taxonomic classification)

---

## 💾 Step 2: Taxonomic Classification and ORF Annotation

### 2.1 Run the VIRify Pipeline
- Use [VIRify](https://github.com/EBI-VIRify/VIRify) (Docker or Singularity) to classify and annotate genomes:
  - Input: FASTA files from Step 1.2
  - Output: Genus/family level taxonomy with ~86.6% accuracy
  - Dependencies: Prodigal, ViPhOG database

### 2.2 ORF Prediction
#### 2.2.1 Run Prodigal
- Command: `prodigal -i input.fasta -a output_proteins.faa -d output_nucleotides.fna -o output.gbk -f gbk`
- Flags: use `-p meta` for metagenomes.

#### 2.2.2 Run Glimmer (complement Prodigal)
- Especially useful for eukaryotic viral genes.
- Use [Glimmer3](https://ccb.jhu.edu/software/glimmer/):
  - Train a model (if needed).
  - Compare Glimmer results to Prodigal for consistency.

### 2.3 Functional Annotation via HMMs
#### 2.3.1 Run HMMScan
- Use [HMMER v3.3+](http://hmmer.org/) with Pfam database:
  ```bash
  hmmscan --domtblout pfam_hits.out Pfam-A.hmm proteins.faa
  ```

#### 2.3.2 Filter for Jelly Roll Domains
- Search for Pfam domains associated with **single jelly roll** (e.g., PF00729, PF00910).
- Retain genomes that:
  - Have **at least one hit** to a jelly roll domain.
  - Contain **capsid-like ORFs** of ~400–800 amino acids.

---

## 🧠 Step 3: Structure Prediction and Trimer Modeling

### 3.1 Extract and Format Protein Sequences
- From filtered genomes, extract ORFs corresponding to putative capsid genes.
- Format as FASTA: `>genome_id_ORF_id\nSEQUENCE`

### 3.2 Predict Monomer Structures
#### 3.2.1 Run AlphaFold and RoseTTAFold
- For each capsid gene:
  - Use **ColabFold**, **AlphaFold2 local**, or **RoseTTAFold** to fold structures.
  - Save `.pdb` and confidence metrics (pLDDT).

### 3.3 Predict Trimeric Assemblies
#### 3.3.1 Run AlphaFold-Multimer
- Input 3x monomer sequences (identical) in FASTA.
- Confirm:
  - **Inter-chain contacts** (interface RMSD, pDockQ)
  - **Correct folding of trimer**

#### 3.3.2 Construct T=1 and T=3 Tiles
- Arrange trimeric units into **icosahedral symmetries**:
  - Use **custom scripts** or tools like **pyCapsid**, **ChimeraX**.

---

## 🧪 Step 4: In Silico Capsid Stability & Comparative Design

### 4.1 Biophysical Screening (as in Specific Aim 1)
- Assess theoretical assembly using:
  - **Classical nucleation theory**
  - **Coarse-grained simulations** (e.g., MARTINI for capsomers)

### 4.2 Identify Assembly-Favoring Fragments
- From trimers, extract **interface residues**.
- Label interface "edges" that enable T=3 contacts.

---

## 🔬 Step 5: Structural Alignment with AAV2

### 5.1 Trimeric Alignment
- Use **ChimeraX Matchmaker**:
  - Align AAV2 trimer vs. uncultured virus trimer
  - Identify RMSD and interface similarity

### 5.2 Identify Transferable Regions
- Note **sequence motifs** and **loops** unique to uncultured T=3 trimers.
- Map those regions to corresponding **AAV2 sites**.

---

## 🧱 Step 6: Candidate Library Generation

### 6.1 Design AAV2 Variants
- Swap T=3-associated fragments from uncultured trimers into AAV2.
- Maintain:
  - Surface exposure
  - Symmetry constraints
  - Tolerable insert size

### 6.2 Final Computational Screening
- Fold designed AAV2 chimeras.
- Filter based on:
  - Fold quality
  - Predicted multimer assembly
  - Stability metrics

---

## 🧬 Step 7: Optional Experimental Validation (if applicable)

### 7.1 Clone and Express Top Variants
- Design constructs using **Gibson assembly** or **Golden Gate**.
- Express in **HEK293T** or **Sf9** cells.

### 7.2 Validate Assembly
- Methods:
  - **TEM**
  - **SEC-MALS**
  - **DSF**
  - **Native PAGE**

---

## 📊 Step 8: Final Selection and Reporting

### 8.1 Rank and Report Candidates
- Metrics to include:
  - Folding accuracy (pLDDT)
  - RMSD vs AAV2
  - Trimer assembly scores
  - Theoretical T=3 favorability

### 8.2 Prepare Research Output
- Format results for:
  - Internal reports
  - Figures for manuscripts
  - Supplementary tables with structural and taxonomic data



---

## Rationale


---

## **Raw Text**
## **Specific Aim 2:**
Design and test candidates mining uncultured viral genomes bioinformatically.
T=3 capsids have not been observed among isolates of AAV variants or viruses in the Parvoviridae family,but they could exist among uncultured viruses. To this end, we will mine uncultured viral genomesbioinformatically to identify capsid proteins among unusually large genomes of parvoviruses that could formT=3 capsids naturally. The proteins will be folded bioinformatically. Sequence and structural homology will beused to introduce mutations in the AAV capsid for candidates forming T=3 capsids. We will then apply thesame biophysical selection methods and empirical validation strategy described in Specific Aim 1.

