# 🧬 Sequence Similarity Search with BLAST

Search for sequence similarity against reference sequences or databases.

---

## 🧪 Tool: [Blast](https://www.ncbi.nlm.nih.gov/books/NBK279690/)

Used for comparing nucleotide or protein sequences.

## 🚀 Basic BLASTn (Sequence vs Sequence)

```bash
blastn -query query.fasta -subject reference.fasta -out output.txt -outfmt 6
```

## 🧬 BLASTn with Custom Output Fields

```bash
blastn \
-query query.fasta \
-subject reference.fasta \
-out output.txt \
-outfmt "6 qseqid sseqid pident length mismatch gapopen qstart qend sstart send evalue bitscore"
```

## 🌐 BLAST against Database (e.g. nt)

```bash
blastn \
-query query.fasta \
-db /path/to/blast_db \
-out output.txt \
-outfmt 6 \
-num_threads 30
```

## 🧬 Protein Search (BLASTp)

```bash
blastp \
-query protein.fasta \
-db /path/to/protein_db \
-out output.txt \
-outfmt 6 \
-num_threads 30
```

## 📊 Common Output Columns

- <code>qseqid</code> → Query sequence ID
- <code>sseqid</code> → Subject sequence ID
- <code>pident</code> → Percent identity
- <code>length</code> → Alignment length
- <code>evalue</code> → Statistical significance
- <code>bitscore</code> → Alignment score

## 💡 Notes

- <code>-outfmt 6</code> gives tabular output (easy to parse)
- Use appropriate database depending on analysis (nt, nr, custom)
- Adjust <code>evalue</code> threshold for sensitivity
