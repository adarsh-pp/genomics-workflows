# 🧬 Genome Assembly with SPAdes

De novo assembly of short-read sequencing data using SPAdes.

---

## 🧪 Tool: [SPAdes](https://github.com/ablab/spades)
Used for assembling genomes from Illumina short-read data.

---

## 🚀 Standard Assembly

```bash
spades.py -1 input_R1.fastq.gz -2 input_R2.fastq.gz -t 30 -o assembly_output/
```

## 🔁 Multiple Samples (Loop)

```bash
for sample in $(ls *_R1.fastq.gz | sed 's/_R1.fastq.gz//'); do
  spades.py \
  -1 ${sample}_R1.fastq.gz \
  -2 ${sample}_R2.fastq.gz \
  -t 30 \
  -o ${sample}_assembly/
done
```

## 🧬 Plasmid Assembly Mode

```bash
plasmidspades.py \
-1 input_R1.fastq.gz \
-2 input_R2.fastq.gz \
-t 30 \
-o plasmid_assembly/
```

## 🧬 Metaplasmid Assembly

```bash
metaplasmidspades.py \
-1 input_R1.fastq.gz \
-2 input_R2.fastq.gz \
-t 20 \
-o metaplasmid_assembly/
```

## ⚙️ Advanced Assembly (Custom k-mers)

```bash
spades.py \
-1 input_R1.fastq.gz \
-2 input_R2.fastq.gz \
-t 30 \
-k 21,33,55,77 \
--careful \
-o assembly_output/
```

## 💡 Notes
- Designed for Illumina short-read data
- <code>--careful</code> reduces mismatches and indels
- k-mer sizes can be adjusted based on genome size and read length
- Output includes contigs and scaffolds
