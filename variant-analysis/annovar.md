# 🧬 Variant Annotation with ANNOVAR

Annotation of genetic variants using multiple genomic databases.

---

## 🧪 Tool: [ANNOVAR](https://annovar.openbioinformatics.org/en/latest/)
Used for functional annotation of variants from VCF or AVINPUT format.

---

## 🚀 Annotate VCF File

```bash
perl /path/to/annovar/table_annovar.pl input.vcf /path/to/humandb/ \
-buildver hg38 \
-out output_prefix \
-protocol refGeneWithVer,cytoBand,dbnsfp47a,exac03,gnomad41_exome,gnomad41_genome,1000g2015aug_all,1000g2015aug_afr,1000g2015aug_eur,1000g2015aug_amr,1000g2015aug_eas,1000g2015aug_sas,avsnp151,clinvar_20240917 \
-operation gx,r,f,f,f,f,f,f,f,f,f,f,f,f \
-xref /path/to/gene_xref.txt \
-remove -nastring . -polish -vcfinput
```

## 🔁 Convert VCF to ANNOVAR Format (AVINPUT)
Required when genotype-level information is needed.

```bash
for file in *_filtered.vcf; do
  base=$(basename "$file" _filtered.vcf)
  perl /path/to/annovar/convert2annovar.pl \
  -format vcf4 \
  -withzyg \
  --includeinfo "$file" \
  -outfile ${base}.avinput
done
```

## 🔁 Annotate AVINPUT Files

```bash
for file in *.avinput; do
  base=$(basename "$file" .avinput)
  perl /path/to/annovar/table_annovar.pl "$file" /path/to/humandb/ \
  -buildver hg38 \
  -out "$base" \
  -protocol refGeneWithVer,cytoBand,dbnsfp47a,exac03,gnomad41_exome,gnomad41_genome,1000g2015aug_all,1000g2015aug_afr,1000g2015aug_eur,1000g2015aug_amr,1000g2015aug_eas,1000g2015aug_sas,avsnp151,clinvar_20240917 \
  -operation gx,r,f,f,f,f,f,f,f,f,f,f,f,f \
  -xref /path/to/gene_xref.txt \
  -remove -nastring . -polish -otherinfo
done
```

## ⚙️ Key Parameters

- <code>-buildver</code> hg38 → Reference genome version
- <code>-protocol</code> → Annotation databases used
- <code>-operation</code> → Type of annotation (gene-based, region-based, filter-based)
- <code>-xref</code> → Gene cross-reference file
- <code>-polish</code> → Improves annotation consistency

## 💡 Notes
- Requires pre-downloaded ANNOVAR databases <code>(humandb/)</code>
- Use AVINPUT format when genotype information is required
- Output includes functional, population frequency, and clinical annotations
