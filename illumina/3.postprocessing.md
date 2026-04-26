# 🧬 Illumina Post-processing

Post-alignment processing steps for Illumina sequencing data before variant calling.

---

## 🧪 Tools
- [Picard](https://broadinstitute.github.io/picard/) for duplicate marking and read group handling
- [Samtools](https://www.htslib.org/) for indexing

---

## 🚀 Mark Duplicates

Removes PCR duplicates to reduce bias in variant calling.

```bash
# Single sample
picard MarkDuplicates \
INPUT=input_sorted.bam \
OUTPUT=dedup.bam \
METRICS_FILE=metrics.txt \
REMOVE_DUPLICATES=true \
CREATE_INDEX=true

# Multiple samples
for sample in $(ls *_sorted.bam | sed 's/_sorted.bam//'); do
  picard MarkDuplicates \
  INPUT=${sample}_sorted.bam \
  OUTPUT=${sample}_dedup.bam \
  METRICS_FILE=${sample}_metrics.txt \
  REMOVE_DUPLICATES=true \
  CREATE_INDEX=true
done
```

## 🧬 Add or Replace Read Groups

Required for tools like GATK.

```bash
# Single sample
picard AddOrReplaceReadGroups \
INPUT=dedup.bam \
OUTPUT=dedup_RG.bam \
RGID=id \
RGLB=library \
RGPL=platform \
RGSM=sample \
RGPU=unit

# Multiple samples
for sample in $(ls *_dedup.bam | sed 's/_dedup.bam//'); do
  picard AddOrReplaceReadGroups \
  INPUT=${sample}_dedup.bam \
  OUTPUT=${sample}_dedup_RG.bam \
  RGID=${sample} \
  RGLB=${sample}_lib \
  RGPL=ILLUMINA \
  RGSM=${sample} \
  RGPU=${sample}_unit
  
  samtools index ${sample}_dedup_RG.bam
done
```

## 💡 Notes

- Duplicate removal improves variant calling accuracy
- Read groups are essential for GATK workflows
- Always index BAM files after processing
