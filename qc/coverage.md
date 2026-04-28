# 📊 Coverage Analysis

Assessment of sequencing depth and coverage across the genome.

---

## 🧪 Tools
- [Samtool](https://www.htslib.org/)
- [Mosdepth](https://github.com/brentp/mosdepth)

Used to evaluate alignment coverage and sequencing depth.

---

## 🚀 Basic Coverage (Samtools)

```bash
samtools coverage input.bam
```

## 🧬 Mpileup Coverage Output

```bash
samtools mpileup -BQ0 -d 100000 -a -A -f reference.fasta input.bam > coverage.txt
```

## ⚡ Mosdepth Coverage

```bash
mosdepth -t 20 sample_name input.bam
```

## 🎯 Targeted Coverage (BED Regions)

```bash
mosdepth -t 20 -n -x -b regions.bed sample_name input.bam
```

## 📈 Extract Coverage Metrics

```bash
grep -P "total\t10\t" sample_name.mosdepth.region.dist.txt
grep -P "total\t20\t" sample_name.mosdepth.region.dist.txt
```

## 💡 Notes

- Coverage depth is critical for variant calling accuracy
- Use targeted BED files for exome or panel data
- Mosdepth provides fast and efficient coverage calculations
