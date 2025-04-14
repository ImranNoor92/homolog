🧬 Ideal Pipeline Based on Your Aims
Here’s a refined strategy aligned with your grant:

🧱 Step 1: Build a Custom HMM Library
Use Pfam + any manually aligned JRF-containing capsid proteins (from PDB, literature, etc.)

Include: Picornaviridae, Caliciviridae, CtenDNAV-II, Parvoviruses, etc.

🔍 Step 2: Use hmmscan on Large Datasets
Search Swiss-Prot, UniProt viral proteins, and (eventually) IMG/VR

Filter for matches to JRF domains

🧪 Step 3: Structural Filtering
Use ChimeraX, DALI, or TM-align to superpose capsid proteins that passed HMMER

Extract interface residues from T=3 trimers (using FMDV, Norovirus, CtenDNAV-II)

🧠 Step 4: Design VP3 Variants
Map trimeric motifs onto AAV VP3

Use AlphaFold to fold each variant

Use ProteinMPNN to refine backbone/interface

Use MD / coarse-grained simulations to test assembly potential
