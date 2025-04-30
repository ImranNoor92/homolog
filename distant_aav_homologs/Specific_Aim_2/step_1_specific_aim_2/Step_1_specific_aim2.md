# 📝 Step 1 Workflow: Database Acquisition and Preparation

This document details the full procedure to obtain and filter uncultured viral genomes for identifying candidate capsid proteins from the Parvoviridae family that may form T=3 capsids.

---

## 📚 1.1 Access and Download IMG/VR Database

### What is IMG/VR?
The IMG/VR (Integrated Microbial Genomes & Viral) database from the U.S. Department of Energy JGI provides uncultured viral genomes from metagenomic samples.

- **Portal**: https://img.jgi.doe.gov/vr/
- **Data access**: https://genome.jgi.doe.gov/portal/IMG_VR/IMG_VR.download.html

### Files to Download
| File | Description |
|------|-------------|
| `IMGVR_all_nucleotides-high_confidence.fna.gz` | Genomic sequences (FASTA) |
| `IMGVR_all_proteins-high_confidence.faa.gz` | Predicted proteins (from Prodigal) |
| `IMGVR_all_Sequence_information-high_confidence.tsv` | Metadata table |
| `IMGVR_Host_information-high_confidence.tsv` | Optional: predicted hosts |

### Download with `wget`
```bash
wget -c https://ftp.microbio.me/pub/IMGVR/IMGVR_all_nucleotides-high_confidence.fna.gz
wget -c https://ftp.microbio.me/pub/IMGVR/IMGVR_all_proteins-high_confidence.faa.gz
wget -c https://ftp.microbio.me/pub/IMGVR/IMGVR_all_Sequence_information-high_confidence.tsv
```

Unzip:
```bash
gunzip IMGVR_all_nucleotides-high_confidence.fna.gz
gunzip IMGVR_all_proteins-high_confidence.faa.gz
```

---

## 🔎 1.2 Filter for Target Genomes

Goal: Select viral genomes that:
- Belong to **Parvoviridae**
- Are **longer than 6,000 bp**

### Python Script for Filtering
```python
import pandas as pd

metadata = pd.read_csv("IMGVR_all_Sequence_information-high_confidence.tsv", sep="\t")
filtered = metadata[(metadata["Lineage"].str.contains("Parvoviridae", na=False)) &
                    (metadata["Sequence Length"] > 6000)]
filtered.to_csv("filtered_parvoviridae_6kb.tsv", sep="\t", index=False)

with open("parvoviridae_ids.txt", "w") as f:
    for gid in filtered["IMGVR ID"]:
        f.write(f"{gid}\n")
```

### Extract Sequences with `seqkit`
```bash
seqkit grep -f parvoviridae_ids.txt IMGVR_all_nucleotides-high_confidence.fna > parvo_filtered.fna
seqkit grep -f parvoviridae_ids.txt IMGVR_all_proteins-high_confidence.faa > parvo_filtered.faa
```

Install `seqkit`: `conda install -c bioconda seqkit`

---

## 📁 1.3 Organize Project Structure
```bash
project_root/
├── data/
│   ├── raw/
│   ├── filtered/
├── scripts/
├── logs/
├── output/
```

---

## 📊 1.4 Summary Stats (Optional)
```python
print("Number of genomes:", len(filtered))
print("Avg. genome length:", filtered["Sequence Length"].mean())
print("Unique sources:", filtered["Sample"].nunique())
```

---

## 👌 Output from Step 1
| File | Purpose |
|------|---------|
| `parvo_filtered.fna` | Filtered genome FASTA (Parvoviridae, >6 kb) |
| `parvo_filtered.faa` | Filtered protein FASTA |
| `filtered_parvoviridae_6kb.tsv` | Filtered metadata table |
| `parvoviridae_ids.txt` | Genome ID list |

---

## 📖 References and Tools
- IMG/VR Portal: https://img.jgi.doe.gov/vr/
- Direct FTP: https://ftp.microbio.me/pub/IMGVR/
- seqkit: https://bioinf.shenwei.me/seqkit/
- IMG/VR User Guide: https://img.jgi.doe.gov/docs/vr/IMG_VR_UserGuide.pdf


