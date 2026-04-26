# 🧬Illumina Read Trimming

Quality control and adapter trimming for short-read Illumina sequencing data.

---

## Tool: [TrimGalore](https://github.com/felixkrueger/trimgalore)

Performs adapter trimming and quality filtering. Internally uses Cutadapt and FastQC.

---

## 🚀 Single Sample (Paired-End)

```bash
trim_galore -q 30 --length 20 --fastqc --phred33 --paired input_R1.fastq.gz input_R2.fastq.gz -o output_dir/
```

## 🔁 Multiple Samples (Loop)

```bash
for sample in $(ls *_R1.fastq.gz | sed 's/_R1.fastq.gz//'); do
  trim_galore -q 30 --length 20 --fastqc --phred33 \
  --paired ${sample}_R1.fastq.gz ${sample}_R2.fastq.gz \
  -o output_dir/
done
```

## ⚙️ Key Parameters

- <code>-q 30</code> → Trim low-quality bases (Phred < 30)
- <code>--length 20</code> → Discard reads shorter than 20 bp
- <code>--fastqc</code> → Run QC after trimming
- <code>--paired</code> → For paired-end reads

## 💡 Notes

- Recommended preprocessing step before alignment
- Improves mapping quality and downstream analysis
- Ensure correct pairing of R1 and R2 files
- Poor quality reads can affect alignment and variant calling
- Standard step in all Illumina pipelines
