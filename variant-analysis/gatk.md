# 🧬 Variant Calling with GATK

Variant calling using GATK for germline and somatic analysis.

---

## 🧪 Tool: [GATK](https://gatk.broadinstitute.org/hc/en-us)
Widely used toolkit for high-quality variant discovery.

---

## ⚙️ Create Reference Dictionary (Required)

```bash
picard CreateSequenceDictionary \
R=reference.fasta \
O=reference.dict
```

## 🚀 Germline Variant Calling (HaplotypeCaller)

```bash
# Single sample
gatk HaplotypeCaller \
-R reference.fasta \
-I input.bam \
-O output.vcf

# Multiple samples
for sample in *.bam; do
  gatk HaplotypeCaller \
  -R reference.fasta \
  -I "$sample" \
  -O "${sample%.bam}.vcf"
done
```

## 🧬 Somatic Variant Calling (Mutect2)

```bash
gatk Mutect2 \
-R reference.fasta \
-I tumor.bam \
-I normal.bam \
-O somatic.vcf
```

## 💡 Notes

- Requires properly formatted BAM (sorted, indexed, with read groups)
- Reference genome must be indexed (<code>.fai</code> and <code>.dict</code>)
- HaplotypeCaller → germline variants
- Mutect2 → somatic variants
