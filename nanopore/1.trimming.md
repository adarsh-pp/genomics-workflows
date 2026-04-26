# 🧬 Nanopore Read Trimming

This section covers basic environment setup and management using Conda for bioinformatics workflows.

---


## Tool: [Porechop](https://github.com/rrwick/porechop)
Removes adapters and chimeric reads from Nanopore FASTQ files

---

## 🚀 Single Sample

```bash
porechop-runner.py -i input.fastq.gz -o output_trimmed.fastq.gz -t 30
```

## 🔁 Multiple Samples (Loop - 1)

```bash
for file in *.fastq.gz; do
  base=$(basename "$file" .fastq.gz)
  porechop-runner.py -i "$file" -o "${base}_trimmed.fastq.gz" -t 30
done
```

## 🔁 Multiple Samples (Loop - 2)

```bash
for i in $(ls *.fastq.gz | sed 's/.fastq.gz//'| sort | uniq);
  do echo $i
  porechop-runner.py -i $i".fastq.gz" -o $i"_trimmed.fastq.gz" -t 30 --format fastq.gz
done
```
