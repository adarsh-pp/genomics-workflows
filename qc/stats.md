# 📊 Alignment Statistics

Summary statistics for aligned sequencing data.

---

## 🧪 Tool: [Samtool](https://www.htslib.org/)
Used to assess alignment quality and read statistics from BAM files.

---

## 🚀 Basic Alignment Statistics

```bash
samtools flagstat input.bam
```

## 🔁 Multiple Samples (Loop)

```bash
for file in *.bam; do
  echo "$file"
  samtools flagstat "$file"
done
```

## 📊 Chromosome-wise Read Counts

```bash
samtools idxstats input.bam | awk '$1 != "*" {print $1, $3}' | awk '{if($2!=0) print $0}' > chr_read_counts.txt
```

## 🧬 Primary Mapped Reads Only

```bash
samtools view -F 0x904 input.bam | awk '{print $3}' | sort | uniq -c | awk '{print $2, $1}' > primary_chr_counts.txt
```

## 💡 Notes
- <code>flagstat</code> provides summary of mapped, unmapped, and duplicate reads
- <code>idxstats</code> gives chromosome-level distribution
- Filtering flags helps focus on high-quality alignments
