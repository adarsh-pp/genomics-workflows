# 🧬 Variant Calling with Bcftools

Variant calling and filtering from aligned sequencing data.

---

## 🧪 Tool: [Bcftools](https://samtools.github.io/bcftools/bcftools.html)
Variant calling and filtering from aligned sequencing data.

---

## 🚀 Variant Calling

```bash
# Single sample
bcftools mpileup -Ou -f reference.fasta input.bam | \
bcftools call -mv -Oz -o variants.vcf.gz

# Multiple samples
for sample in *.bam; do
  bcftools mpileup -Ou -f reference.fasta "$sample" | \
  bcftools call -mv -Oz -o "${sample%.bam}.vcf.gz"
done

# Pooled variant calling
bcftools mpileup -Ou -f reference.fasta -b bam_list.txt | \
bcftools call -mv -Oz -o pooled_variants.vcf.gz
```

## ⚙️ Variant Filtering

Filter based on depth and quality.

```bash
bcftools filter -i 'DP>20 && QUAL>30' \
-Oz -o filtered.vcf.gz variants.vcf.gz
```

## 🧬 Extract Variants by Region

```bash
bcftools view -R regions.txt input.vcf.gz -o output_filtered.vcf
```

## 💡 Notes

- <code>DP</code> → Read depth
- <code>QUAL</code> → Variant quality score
- Adjust thresholds based on dataset and study design
- Output VCF can be used for annotation and downstream analysis
- Used for both nanopore, illumina, and Onso data
