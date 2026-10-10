# Measuring Orthographic Depth via Information Compression and Alignment

A paper proposing a fast, unsupervised way to quantify how transparently a writing system encodes its language's pronunciation, across 25 languages.

Orthographic depth is how far spelling departs from sound. Spanish and Finnish are shallow; English and French are deep. The method compares each language's native spelling with a phonemic IPA transcription of the same text:

- compress the spelling, the IPA, and the two concatenated with gzip, and compare the ratios (computed on character counts so UTF-8 byte length doesn't bias the result)
- compute a normalized Levenshtein distance between the two forms as an alignment cost
- min-max normalize both metrics so languages can be compared directly

The data is one 3 to 5 sentence paragraph per language, with transcriptions from Wiktionary or standard references. Shallow orthographies such as Italian, Spanish and Swahili come out low, and deep ones such as English, Chinese, Tibetan and Khmer come out high. Korean scores deeper than its reputation suggests, which the paper attributes to phonological rules that Hangul doesn't write down.

## Files

- `Measuring_Orthographic_Depth_via_Information_Compression_and_Alignment.pdf`: the compiled paper
- `orthographic_depth.tex`: the LaTeX source
- `refs.bib`: bibliography
- `depth_plot.pdf`: the figure used in the paper
- `sources/`: reference papers cited in the work

## Building

```bash
pdflatex orthographic_depth.tex
bibtex orthographic_depth
pdflatex orthographic_depth.tex
pdflatex orthographic_depth.tex
```

The source uses `natbib`, `longtable`, `booktabs` and `hyperref`.
