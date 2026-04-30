# 🧬 Taxonomic Classification with Kraken2

Classification of sequencing reads into taxonomic groups using k-mer-based matching.

---

## 🧪 Tool: [Kraken2](https://github.com/DerrickWood/kraken2)

Fast and accurate classification of reads against reference databases.

## 🚀 Single Sample (Single-End / Nanopore)

```bash
kraken2 \
--db /path/to/database/ \
input.fastq.gz \
--report kraken_report.txt \
--output kraken_output.txt \
--threads 10
```

## 🧬 Paired-End Reads (Illumina)

```bash
kraken2 \
--db /path/to/database/ \
--gzip-compressed \
--paired input_R1.fastq.gz input_R2.fastq.gz \
--report sample_report.txt \
--output sample_output.txt \
--threads 10
```

## 🔁 Multiple Samples (Loop)

```bash
for sample in $(ls *_R1.fastq.gz | sed 's/_R1.fastq.gz//'); do
  kraken2 \
  --db /path/to/database/ \
  --gzip-compressed \
  --paired ${sample}_R1.fastq.gz ${sample}_R2.fastq.gz \
  --report ${sample}_report.txt \
  --output ${sample}_output.txt \
  --threads 10
done
```

## 📊 Add Header to Report (Optional)

```bash
echo -e "Percentage\tReads_covered\tReads_assigned\tRank_code\tNCBI_tax_id\tScientific_name" | \
cat - kraken_report.txt > final_report.txt
```

## 🧬 Extract Unclassified Reads

```bash
awk '$3 == 0 {print $2}' kraken_output.txt > unmapped_read_ids.txt
```

## 💡 Notes

- Requires pre-built Kraken2 database
- Works with both short and long reads
- Output includes classification and taxonomic assignment
- Useful for metagenomics and contamination analysis
