# 🧬 Hybrid Genome Assembly

Combining short-read and long-read data for improved genome assembly.

---

## 🧪 Tool: [Unicyler](https://github.com/rrwick/unicycler)
Designed for hybrid assembly using both short and long reads.

---

## 🚀 Hybrid Assembly

```bash
unicycler \
-1 input_R1.fastq.gz \
-2 input_R2.fastq.gz \
-l nanopore_reads.fastq \
-o output_directory/ \
-t 30
```

## ⚙️ Key Parameters
- <code>-1</code> → Short R1 reads
- <code>-2</code> → Short R2 reads
- <code>-l</code> → Long reads 
- <code>-o</code> → Output directory
- <code>-t</code> → Number of threads

## 💡 Notes
- Combines accuracy of short reads with long-range information
- Produces more complete and contiguous assemblies
- Particularly useful for bacterial and small genomes
