# Pepkio Codon Code Lens

Container image bundling the Codon Code Lens CLI for multi-table genetic sequence translation, ORF discovery, codon usage bias profiling, and peptide property calculation via the Pepkio API.

# What It Does

The image runs `pepkio-codon-code-lens`, a client for the Pepkio Codon Code Lens REST API. It performs 6-frame nucleotide translations, evaluates non-standard genetic code tables, detects open reading frames (ORFs), computes Relative Synonymous Codon Usage (RSCU), and calculates peptide physicochemical properties ($MW$, $pI$, GRAVY).

Typical workflows include translating mitochondrial or bacterial contigs with non-standard genetic codes, screening open reading frames in unannotated transcriptomic reads, diagnosing rare codon bottlenecks in heterologous expression, and designing site-directed mutagenesis primers. Calculator logic runs on Pepkio servers; provide a network connection and API key for `run` commands.

# Features

- Multi-table NCBI genetic code translation (Table 1 Standard, Table 2 Vertebrate Mitochondrial, Table 6 Ciliate, Table 11 Bacterial/Plastid, etc.)
- 6-frame translation across forward (+1, +2, +3) and reverse-complement (-1, -2, -3) frames
- Open reading frame (ORF) detection with configurable minimum length and stop codon handling
- Codon usage bias analytics including RSCU and position-specific GC content ($GC_1, GC_2, GC_3$)
- Protein physicochemical profiling: molecular weight ($MW$), isoelectric point ($pI$), net charge, and GRAVY
- Named manifest examples (`translate_gfp_fragment`, `back_translate_short_peptide`, `codon_table_standard_m`, etc.)
- Manifest inspection without an API key

# Quick Start

```bash
docker pull pepkio/codon-code-lens:0.1.0
docker run --rm -e PEPKIO_API_KEY="your-key" pepkio/codon-code-lens:0.1.0 \
  pepkio-codon-code-lens run --example translate_gfp_fragment
```

Manifest only (no API key):

```bash
docker run --rm pepkio/codon-code-lens:0.1.0 \
  pepkio-codon-code-lens manifest --examples
```

Set `PEPKIO_API_BASE_URL` to override the API host (default: `https://tools.pepkio.com`). Create an API key with **tools:run** scope at https://www.pepkio.com/account/api-keys.

# Quick Example

```bash
docker run --rm -e PEPKIO_API_KEY="$PEPKIO_API_KEY" pepkio/codon-code-lens:0.1.0 \
  pepkio-codon-code-lens run --input-json \
  '{"tab":"translate","genetic_code":1,"sequence":"ATGGTGAGCAAGGGCGAGGAGCTGTTC","frame":"all"}'
```

# Typical Use Cases

- 6-frame translation of raw cDNA or sequencing reads in containerized bioinformatic pipelines
- Identifying coding regions in organellar genomes using alternative translation tables
- Evaluating rare codon frequency and translation bottlenecks before gene synthesis
- Validating mutated sequences in automated CI/CD molecular biology workflows
- Calculating theoretical molecular weights and $pI$ values for proteomics workflows

# Scientific Background

The standard genetic code (NCBI Table 1) assigns 64 triplet codons to 20 standard amino acids and 3 termination signals. Alternative genetic codes (e.g. NCBI Tables 2, 6, 11) reassign stop codons or utilize alternative start codons (e.g. GTG, TTG). Relative Synonymous Codon Usage (RSCU) evaluates codon bias normalized against equal usage expectations.

# Web Application

For researchers who prefer a graphical interface, an interactive web version is available.

Web Application: https://www.pepkio.com/tools/codon-code-lens

The web UI adds interactive 6-frame translation maps, interactive codon frequency charts, highlighted rare codons, sequence file uploads, and shareable permalinks.

# Documentation and Resources

GitHub Repository (source and Dockerfile): https://github.com/pepkio/pepkio-codon-code-lens

Web Application: https://www.pepkio.com/tools/codon-code-lens

# About Pepkio

Pepkio (https://www.pepkio.com/) develops software tools and bioinformatics solutions for life science researchers, including laboratory calculators and analysis services (https://www.pepkio.com/cro).

A semantic, AI-native version of this document in the K2F format is available at https://k2f.dev (https://k2f.dev/v/d8b866ce5ed5da3d2d3d248f01ec55210bee83bbfd5e98036b458f4059fb87c3)
