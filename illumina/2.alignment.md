# 🧬 Illumina Alignment

Alignment of short-read Illumina sequencing data to a reference genome.

---

## 🧪 Tools
- [BWA MEM](https://bio-bwa.sourceforge.net/) for alignment
- [Samtools](https://www.htslib.org/) for BAM conversion and sorting

---

## 🚀 Single Sample (Paired-End)

```bash
bwa mem -t 20 reference.fasta input_R1.fastq.gz input_R2.fastq.gz | \
samtools view -bS | \
samtools sort -o output_sorted.bam -@ 20
```

## 🔁 Multiple Samples (Loop)

```bash
for sample in $(ls *_R1.fastq.gz | sed 's/_R1.fastq.gz//'); do
  bwa mem -t 20 reference.fasta ${sample}_R1.fastq.gz ${sample}_R2.fastq.gz | \
  samtools view -bS | \
  samtools sort -o ${sample}_sorted.bam -@ 20
done
```

## ⚙️ Key Parameters
- <code>-t 20</code> → Number of threads
- <code>mem</code> → Recommended algorithm for Illumina reads
- <code>samtools sort</code> → Produces sorted BAM for downstream analysis

## 💡 Notes
- Ensure reference genome is indexed before running BWA
- Output BAM file is required for variant calling and QC
- Works for WGS, WES, and targeted sequencing data
