# Specific Aim 2: Design and Test Candidates from Uncultured Viral Genomes

This README outlines a detailed breakdown of the workflow to design and test capsid candidates from uncultured viral genomes, focusing on the identification and engineering of T=3 AAV capsid variants.

---

## Step 1: Database Acquisition and Preparation

### 1. Download IMG/VR database
- Obtain the IMG/VR database from the US Department of Energy Joint Genome Institute (JGI).
- Verify the latest version of the database and confirm metadata availability.

### 2. Filter Uncultured Viral Genomes
- Extract viral genomes belonging to the *Parvoviridae* family.
- Select only genomes larger than 6 kb for further analysis.

---

## Step 2: Taxonomic Classification and Initial Annotation

### 3. Run VIRify Pipeline
- Process the viral genomes using the VIRify pipeline to classify them at genus and family levels.
- Validate the classification accuracy (expected ~86.6%).

### 4. Extract Open Reading Frames (ORFs)
- Use Prodigal to predict ORFs in the uncultured viral genomes.
- Cross-check with Glimmer, which is more accurate for eukaryotic viruses.

### 5. Annotate ORFs Using Hidden Markov Models (HMMs)
- Scan ORFs against the Pfam (protein family) database using `hmmscan`.
- Identify genomes containing single jelly roll capsid protein domains.

---

## Step 3: Structural Modeling of Candidate Capsid Proteins

### 6. Extract Capsid Protein Sequences
- Retrieve protein sequences of putative capsid genes from selected genomes.

### 7. Fold Capsid Proteins Using AI-Based Predictors
- Use RoseTTAFold and AlphaFold to predict the 3D structures of candidate capsid proteins.

### 8. Generate Trimeric Capsid Protein Tiles
- Use AlphaFold-Multimer to model trimeric assemblies of candidate capsid proteins.
- Generate T=1 and T=3 capsid architectures using these tiles.

---

## Step 4: Computational Analysis of Structural Stability

### 9. Assess Stability of Predicted T=3 Capsids
- Apply theoretical biophysical methods (from Specific Aim 1, Section C.1.2) to analyze stability.
- Identify stable candidates for T=3 capsids.

### 10. Determine Edge Protein Fragments in Trimers
- Locate structural regions at the edges of the trimeric capsid proteins that influence assembly.

---

## Step 5: Structural Comparison with AAV2 Capsid

### 11. Align Trimers from Uncultured and AAV2 Capsids
- Compare trimeric capsid proteins from uncultured viruses vs. AAV2 capsid proteins.
- Use ChimeraX matchmaking for structural alignment.

### 12. Identify Key Regions for T=3 Capsid Assembly
- Detect sequence motifs or structural features in uncultured capsid proteins that promote T=3 formation.
- Define the specific AAV2 capsid regions that require modification to incorporate these motifs.

### 13. Generate a Library of Candidate Protein Designs
- Create a design library incorporating structural elements from uncultured capsids into AAV2 sequences.

---

## Step 6: Refinement and Selection of Best Candidates

### 14. Refine Candidates Using Computational Filtering
- Apply theoretical stability assessments (as described in C.1.2 of Specific Aim 1).
- Prioritize at least 20 strong candidates based on stability and structural compatibility.

### 15. Prepare for Experimental Validation
- Follow C.1.3 methods from Specific Aim 1 to test the best candidates in vitro.
- Design expression and assembly experiments for the modified AAV capsids.

---

## Step 7: Experimental Validation (If Included in This Aim)

### 16. Express and Purify Selected Capsid Variants
- Clone the top 20 candidate sequences into expression vectors.
- Express in a suitable host system (e.g., HEK293 cells).
- Purify the assembled capsid proteins.

### 17. Assess In Vitro Capsid Formation and Stability
- Use electron microscopy (EM) and biophysical methods to confirm T=3 capsid formation.
- Perform differential scanning fluorimetry (DSF) or SEC-MALS to assess capsid stability.

### 18. Compare Engineered AAV Capsids with Wild-Type AAV2
- Determine if modified AAV capsids retain or improve packaging efficiency and infectivity.

---

## Final Output and Analysis

### 19. Summarize Results and Select Final Variants
- Rank candidates based on stability, folding accuracy, and AAV2 structural compatibility.
- Select final T=3 engineered capsid proteins for further development.

### 20. Prepare Manuscript and Report Findings
- Document findings and prepare a publication or research report.
- Discuss the implications of natural T=3 capsids in parvoviruses and AAV capsid engineering.

---

This breakdown ensures every step is manageable, leading to the successful identification, design, and testing of novel T=3 AAV capsid variants from uncultured viral genomes.

