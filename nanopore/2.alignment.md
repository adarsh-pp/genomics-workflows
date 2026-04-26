# 🧬 Nanopore Alignment

Alignment of long-read Nanopore sequencing data to a reference genome.

---

## 🧪 Tools
- [Minimap2](https://github.com/lh3/minimap2)
- [Samtools](https://www.htslib.org/)

---

## Single Sample

```bash
minimap2 -ax map-ont -t 30 reference.fasta input.fastq.gz | \
samtools view -bS | \
samtools sort -o output_sorted.bam -@ 20
```

## Mutliple Samples (Loop)

```bash
# Method1
for sample in *.fastq.gz; do
  minimap2 -ax map-ont -t 30 reference.fasta "$sample" | \
  samtools view -bS | \
  samtools sort -o "${sample%.fastq.gz}_sorted.bam" -@ 20
done

# Method2
for i in `ls *.fastq | sed s"/.fastq//"`; do
  echo $i
  minimap2 -ax map-ont -t 30 reference.fasta $i".fastq" | \
  samtools view -bS | \
  samtools sort -o $i"_sorted.bam" -@ 20
done
```

## ⚙️ Large Reference Genome (Optional)

```bash
minimap2 -ax map-ont --split-prefix tmp_prefix reference.fasta input.fastq.gz | \
samtools view -bS | \
samtools sort -o output_sorted.bam -@ 20
```

## Notes

- <code>map-ont</code> preset is optimized for Nanopore reads
- Output BAM is sorted and ready for downstream analysis
- Use <code>--split-prefix</code> for large genomes to improve performance
