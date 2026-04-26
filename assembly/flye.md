# 🧬 Genome Assembly with Flye

De novo assembly of long-read sequencing data using Flye.

---

## 🧪 Tool: [Flye](https://github.com/mikolmogorov/Flye)
Used for assembling genomes from Nanopore or other long-read sequencing data.

---

## 🚀 Standard Assembly (Nanopore Reads)

```bash
flye --nano-raw input.fastq --out-dir assembly_output/ --threads 30
```

## 🧬 Assembly with Scaffolding

```bash
flye --nano-raw input.fastq --scaffold --out-dir assembly_output/ --threads 30
```

## 🧬 Metagenome Mode

```bash
flye --nano-raw input.fastq --meta --out-dir assembly_meta/ --threads 30
```

## ⚙️ Key Parameters

- <code>--nano-raw</code> → Input Nanopore reads
- <code>--scaffold</code> → Enables scaffolding
- <code>--meta</code> → For metagenomic datasets
- <code>--threads</code> → Number of CPU threads

## 💡 Notes

- Designed for long-read sequencing data
- Produces high-contiguity assemblies
- Requires sufficient coverage for optimal results

