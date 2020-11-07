# genome-grist - map Illumina metagenomes to GenBank genomes

<a href="https://pypi.org/project/genome-grist/"><img alt="PyPI" src="https://badge.fury.io/py/genome-grist.svg"></a>
<a href="https://github.com/dib-lab/pybbhash/blob/latest/LICENSE.txt"><img alt="License: 3-Clause BSD" src="https://img.shields.io/badge/License-BSD%203--Clause-blue.svg"></a>

## In brief

`genome-grist` is a toolkit to do the following:

1. download a metagenome
2. process it into trimmed reads, and make a [sourmash signature](https://sourmash.readthedocs.io/)
3. search the sourmash signature with 'gather' against sourmash databases, e.g. all of genbank
4. download the matching genomes from genbank
5. map all metagenome reads to genomes using minimap - `map_reads` and `extract_mapped_reads`
6. extract matching reads iteratively based on gather, successively eliminating reads that matched to previous gather matches - `extract_gather`
7. run mapping on “leftover” reads to genomes - `map_gather`
9. summarize all mapping results for comparison and graphing - `summarize_gather`

## Why the name `grist`?

In the sourmash family of names (sourmash, wort, distillerycats, etc.)

NOT:
https://en.wikipedia.org/wiki/Grist_(computing)

THIS:
https://en.wikipedia.org/wiki/Grist

## Installation

The command:
```
python -m pip install genome-grist
```
will install the latest version. Plase use python3.7 or later. We suggest
using an isolated conda environment.

## Quick start:

Run the following three commands.

First, download SRA sample HSMA33MX, trim reads, and build a sourmash
signature:
```
genome-grist process HSMA33MX smash_reads
```

Next, run sourmash signature against genbank:
```
genome-grist process HSMA33MX smash_reads
```
(NOTE, this depends on the latest genbank genomes and won't work for most
people just yet; for now, use cached results from the repo:
```
cp tests/test-data/HSMA33MX.x.genbank.gather.csv outputs/genbank/
touch outputs/genbank/HSMA33MX.x.genbank.gather.out
```
)

Finally, download the reference genomes, map reads and produce a summary
report:
```
genome-grist process HSMA33MX summarize
```

## Full set of top-level `process` targets

- download_reads
- trim_reads
- smash_reads
- gather_genbank
- download_matching_genomes
- map_reads
- summarize

## Support

genome-grist is alpha-level software. Please be patient and kind :).

Please ask questions and add comments
[by filing github issues](https://github.com/dib-lab/genome-grist/issues).

CTB Nov 7, 2020
