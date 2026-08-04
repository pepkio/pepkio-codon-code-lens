# pepkio-codon-code-lens

A Python client for programmatic 6-frame sequence translation, NCBI genetic code table mapping, open reading frame (ORF) discovery, and relative synonymous codon usage (RSCU) analytics.

# What It Does

`pepkio-codon-code-lens` provides Python bindings and a command-line interface to evaluate DNA and RNA sequences. It translates nucleotide data across all 6 reading frames using canonical and non-canonical NCBI genetic code tables, calculates position-specific GC content ($GC_1, GC_2, GC_3$) and codon bias metrics, detects candidate open reading frames, and estimates protein physicochemical parameters.

# Features

- **NCBI Genetic Code Tables**: Supports standard (Table 1) and non-standard genetic codes (e.g., mitochondrial, ciliate, and bacterial/archaeal tables).
- **6-Frame Translation**: Computes forward (+1, +2, +3) and reverse-complement (-1, -2, -3) reading frames.
- **ORF Discovery**: Identifies coding regions with customizable minimum length and start/stop codon criteria.
- **Codon Bias Analytics**: Calculates absolute codon counts, relative frequencies, Relative Synonymous Codon Usage (RSCU), and position-specific GC content.
- **Protein Property Prediction**: Predicts molecular weight, isoelectric point ($pI$), molar extinction coefficient, net charge at pH 7.4, and GRAVY hydropathicity scores.
- **Automation Interfaces**: Synchronous and asynchronous Python client API alongside a CLI for pipeline integration.

# Installation

Install the package via `pip`:

```bash
pip install pepkio-codon-code-lens
```

# Quick Example

```python
from pepkio_codon_code_lens import PepkioClient

with PepkioClient() as client:
    # 6-frame translation with NCBI Table 1 (Standard Code)
    result = client.run({
        "tab": "translate",
        "genetic_code": 1,
        "sequence": "ATGGTGAGCAAGGGCGAGGAGCTGTTCACCGGGGTGGTGCCCATCCTGGTCGAGCTGGACGGCGACGTAAACGGCCACAAGTTC",
        "frame": "all",
        "display_format": "compact"
    })
    
    print("Status:", result.status)
    print("Forward Frame 1:", result.result.get("translate", {}).get("frame_plus_1"))
```

# Typical Use Cases

- **Recombinant Gene Design**: Evaluate host-specific codon bias and rare codon frequency before gene synthesis for heterologous expression in *E. coli* or yeast.
- **Organellar Genome Translation**: Translate mitochondrial or plastid genomic sequences using non-canonical NCBI translation tables.
- **Transcriptome Annotation**: Identify functional open reading frames across unannotated de novo transcriptomic contigs.
- **Synonymous Mutation Analysis**: Screen synonymous codon swaps to modify restriction sites while preserving primary amino acid sequences.

# Scientific Background

Translating nucleotide sequences into amino acid sequences requires mapping 64 triplet codons to 20 standard amino acids and stop signals. While most nuclear genomes use the standard genetic code (NCBI Table 1), organellar genomes and certain microorganisms utilize alternative codes where canonical stop codons encode amino acids (e.g., UGA encoding Tryptophan in vertebrate mitochondria). Codon usage bias describes the non-uniform frequency of synonymous codons in a genome, measured quantitatively by Relative Synonymous Codon Usage (RSCU).

# Web Application

For researchers who prefer a graphical interface, an interactive web version is available.

Web Application: https://www.pepkio.com/tools/codon-code-lens

The web application includes interactive visual codon maps, side-by-side frame comparisons, downloadable worksheets, and shareable analysis links.

# Documentation and Resources

GitHub Repository: https://github.com/pepkio/pepkio-codon-code-lens

Web Application: https://www.pepkio.com/tools/codon-code-lens

# About Pepkio

Pepkio (https://www.pepkio.com/) develops software tools and bioinformatics solutions for life science researchers, including laboratory calculators and analysis services (https://www.pepkio.com/cro).

# Keywords

* codon code lens
* genetic code table
* 6 frame translation
* open reading frame
* ORF finder
* codon usage bias
* RSCU calculator
* NCBI genetic codes
* reverse complement translation
* protein physicochemical properties
* isoelectric point calculator
* molecular weight prediction
* sequence translation python
* codon optimization
* heterologous gene expression
* mitochondrial genetic code
* GC content calculator
* GC1 GC2 GC3
* amino acid translation
* synonymous codon usage
* bioinformatics python package
* peptide property calculator
* GRAVY score calculator
* recombinant protein expression
* reading frame analysis
* 6 frame dna translation python
* ncbi genetic code table translator
* relative synonymous codon usage rscu
* open reading frame orf finder python
* reverse complement sequence translator
* protein molecular weight and pi calculator
* codon usage bias analysis tool
* organellar genome sequence translation
* position specific gc content calculator
* host codon adaptation checker
