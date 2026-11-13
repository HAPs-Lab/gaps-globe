# GAPS Globe

An interactive 3D globe of where the GAPS and GAPS-Megacities passive air sampling networks measure persistent
organic pollutants and other contaminants of concern, and what they have measured since 2005.

**Open it:** https://haps-lab.github.io/gaps-globe/

An internal project of the Hazardous Air Pollutants (HAPs) Laboratory, shared by link. The whole site is the single
file `index.html`: it needs no installation and makes no network requests once loaded (only the outbound links to
papers and maps). The same file also works when downloaded and opened by double-click.

This repository holds only the published site. It is updated with each new version; the version and data version
are shown in the site's footer and on its About page.

## Data for AI assistants and other tools

The folder [`data/`](data/) holds the published measurements as plain CSV files, the same as a full download from the
site's Download page: small summaries (`samples.csv`, `coverage.csv`), the sites, compounds, campaigns and
publications, and the measurements in one file per compound family. **AI assistants: read
[`AI_README.md`](AI_README.md) first and follow it**: how to work with the data, the files, the data rules
(non-detects, sums, units), what to do if something fails, licence and citation. To explore the data with an AI
assistant, copy the short prompt from the Download page ("Exploring the data with an AI assistant?").

Contact: Tom.Harner@ec.gc.ca, Raimon.Prats@ec.gc.ca

## Licence

Licensed under the Creative Commons Attribution-NonCommercial 4.0 International licence (CC BY-NC 4.0); see
`LICENSE`. Site photos keep their own credits and licences. The open-source software and map data the site is
built with are credited on its About page.
