# 🧰 FASTQ Processing Utilities

Common operations for handling and manipulating FASTQ files.

---

## 🧪 Tools
- [Seqtk](https://github.com/lh3/seqtk)
- [Samtools](https://www.htslib.org/)

Used for extracting, converting, and processing sequencing reads.

## 🚀 Extract Reads by ID

```bash
seqtk subseq input.fastq read_ids.txt > extracted_reads.fastq
```

## 🧬 Extract Paired-End Reads

```bash
# Single sample
seqtk subseq input_R1.fastq.gz read_ids.txt > extracted_R1.fastq
seqtk subseq input_R2.fastq.gz read_ids.txt > extracted_R2.fastq

# Multiple samples
for sample in $(cat sample_list.txt); do
  seqtk subseq ${sample}_R1.fastq.gz ids.txt > ${sample}_R1_extracted.fastq
  seqtk subseq ${sample}_R2.fastq.gz ids.txt > ${sample}_R2_extracted.fastq
done
```

## 🔄 Convert FASTQ to FASTA

```bash
seqtk seq -a input.fastq > output.fasta
```

## 🔢 Count Reads in FASTQ

```bash
zcat input.fastq.gz | wc -l
```

## 🧬 Convert BAM to FASTQ

```bash
samtools fastq input.bam > output.fastq
```

## 💡 Notes

- FASTQ files store sequencing reads with quality scores
- Useful for filtering, subsetting, and format conversion
- Ensure paired-end reads remain synchronized
