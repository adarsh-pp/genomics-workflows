# 🧬 Variant Annotation with SnpEff

Annotating genetic variants to predict their functional impact.

---

## 🧪 Tools: [SnpEff](https://pcingola.github.io/SnpEff/)
Used to annotate variants based on genomic features (genes, transcripts, coding regions).
Following commands are for SnpEff version3

---

## 🏗️ Build SnpEff Database

Download the reference genome (.fa) and genes (.gff) files. Create a new species/strain specific directory in snpEff/data and copy the files here.
Rename the files to sequences.fa and genes.gff. Next edit the snpEff.config file and add a new entry for the specific strain added
```text
Example:
#E.coli_BL21
E.coli_BL21.genome : E.coli_BL21
```
Then run the following command in the SnpEff directory
```bash
java -jar snpEff.jar build -c snpEff.config -gff3 -v genome_name
```

## 🚀 Annotate Variants

```bash
java -jar snpEff.jar eff -c snpEff.config -no-downstream -no-upstream genome_name variants.vcf.gz -o txt > annotated_snpeff.txt
```

## 💡 Notes

- Ensure correct genome database is used
- Custom genomes require database building
- Output can be further processed for downstream analysis
