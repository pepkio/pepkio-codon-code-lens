# pepkio-codon-code-lens

Python client for the Pepkio [codon-code-lens](https://www.pepkio.com/tools/codon-code-lens) tool.

## Installation

```bash
pip install pepkio-codon-code-lens
```

## Usage

### Python API

```python
from pepkio_codon_code_lens import PepkioClient

client = PepkioClient(api_key="your_api_key")

# Get manifest
manifest = client.get_manifest()

# Run tool
result = client.run(
    input_data={
        "tab": "translate",
        "genetic_code": 1,
        "sequence": "ATGGTGAGCAAGGGCGAGGAGCTGTTCACCGGGGTGGTGCCCATCCTGGTCGAGCTGGACGGCGACGTAAACGGCCACAAGTTC",
        "frame": "all",
        "display_format": "compact",
    }
)
print(result.status)
print(result.result)
```

### CLI

```bash
# Get manifest
pepkio-codon-code-lens manifest

# Run example from manifest
pepkio-codon-code-lens run --example translate_gfp_fragment

# Run with JSON input
pepkio-codon-code-lens run --input-json '{"tab":"translate","sequence":"ATGGCC"}'
```
