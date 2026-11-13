# GAPS Globe data: instructions for AI assistants

This repository publishes **GAPS Globe** (https://haps-lab.github.io/gaps-globe/), a website made by the Hazardous Air Pollutants (HAPs)
Laboratory that shows measurements of persistent organic pollutants and other contaminants in outdoor air from the
**GAPS** (Global Atmospheric Passive Sampling) and **GAPS-Megacities** networks, since 2005. GAPS Globe v2.1,
data version 2026-11-12.

The website itself is one HTML file with the data packed inside; do not try to read it. The same data are here as
plain CSV files in the folder `data/`: 38,258 measurements (19,058 detected) from 1,264 samples at 132 sites; 12 campaigns (2005, 2006, 2007, 2008, 2009, 2011, 2013, 2014, 2015, 2017, 2018, 2023); 112 compounds and sums in 10 families.

If a person sent you here, they want to explore these data with you: counts, summaries, comparisons, tables and
plots. **Read this whole file before you answer**, then follow it.

## How to work

1. **Pick the files the question needs** (table under "Files"):
   - **About a site** (when, how often, what was measured): `data/site-overview.csv`, one row per site. Often
     enough on its own.
   - **About samples or what was measured where and when:** the per-campaign files `data/samples/samples_<campaign>.csv`
     and `data/coverage/coverage_<campaign>.csv` (small), or the whole `data/samples.csv` and `data/coverage.csv`
     if you load them with code.
   - **Concentrations:** the measurement files, one per compound family (the largest split by campaign), in
     `data/measurements/`. These are large: load them with code.
   - **Sites, compounds, methods and papers:** the reference tables.
2. **Open the files** from `https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/` followed by the file path, for example `https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/site-overview.csv`.
   `https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/index.json` lists every file with its rows and size.
3. **Use code when you can** (a Python or similar tool): load the CSV files and compute counts, summaries and plots
   with code, not by reading and counting rows by eye. If you cannot run code, work only from the small files (all
   under 30 kB), say that your numbers are read rather than computed, and keep the question small.
4. **Count carefully** (see "Counting" below): every replicate is a sample; a sample can belong to several families;
   counts cover published campaigns only.
5. **Follow the data rules** (under "How the data work"), above all: a non-detect has no value; concentrations are
   in pg/m³; sums are already computed; these are individual measurements, not trends.
6. **Answer plainly.** Say which files and filters you used. Do not present trends, causes or health effects as
   findings: these are measurements for exploration; trend analyses are in the peer-reviewed publications. If the
   data cannot answer the question, say so rather than guessing.
7. **Credit the data** in your answer: say the numbers come from GAPS Globe (data version 2026-11-12), give the
   licence (CC BY-NC 4.0) and the citation (under "Licence and citation"), and the publications behind the data
   used: the column "Published in" of the measurement files, or, when you used only the summaries, the DOIs in
   `data/campaigns-and-methods.csv` for the campaigns, networks and families you counted (full references in
   `data/publications.csv`).

## If something fails

- **A file does not open:** try the same path on the website, `https://haps-lab.github.io/gaps-globe/data/...`, then on GitHub,
  `https://github.com/HAPs-Lab/gaps-globe/blob/main/data/...`. Check the file name in `index.json`.
- **Your tool cuts files short** (web-reading tools often stop at about 40,000 characters): use the small files
  (`site-overview.csv`, the per-campaign files under `data/samples/` and `data/coverage/`, the reference tables), which
  are all under 30 kB. Never answer from a file you could only read in part without saying so.
- **You need concentrations but cannot load the measurement files:** ask the person to download just the selection
  they need from the website's Download page (https://haps-lab.github.io/gaps-globe/#/download; a few compounds, sites or campaigns make a small
  file) and attach it, then work from that file.
- **You can read web pages, but your code tool has no internet access** (common: the files open in the chat but
  cannot be loaded into your code): do not ask the person to clone the repository or run code themselves. Answer
  what you can from the small files, which you can read directly. For concentrations or plots, ask the person to
  download just the selection they need from the website's Download page (https://haps-lab.github.io/gaps-globe/#/download; for example one
  compound and one site, all campaigns), as CSV or Excel, and attach it here; then load that file with your code tool.
- **You cannot open web addresses at all:** tell the person plainly. They can download the data themselves from the
  website's Download page (https://haps-lab.github.io/gaps-globe/#/download: choose compounds, sites and campaigns, then Excel or CSV) and attach
  the file to the conversation; it has the same columns as the files here, with a README sheet.
- **Something in the data looks wrong or is missing:** report it as it is, and point the person to the contacts on
  the website's About page (https://haps-lab.github.io/gaps-globe/#/about). Never fill gaps with invented or substituted values.

## Counting

- **Samples:** one row of `samples.csv` is one sample. Replicate samplers deployed together (Replicate A, B, C) are
  separate samples; say so when replicates are in the count. A PUF and a SIP disk deployed together are separate
  samples too. "How many times was a site sampled" is answered with the number of samples, and how many campaigns
  (and replicate samplers) they come from.
- **Families:** a sample can be analysed for several compound families. In `coverage.csv`, "Samples" counts the
  samples of one site, campaign and family, so never add it up across families: to count samples, use
  `samples.csv` or `site-overview.csv`.
- **Compounds:** "Compounds measured" counts individual compounds, not sums.
- **Years:** "Campaign" is a label for the sampling year; a few samples of a campaign start in the previous December.
  For "between 2005 and 2015", count by Campaign unless the person asks about deployment dates, and say which you used.
- **Published campaigns only:** a campaign missing from a site may have been sampled but not yet published. Say that
  your counts cover the published data in these files.

## Files

| File | Rows | Size | What it holds |
| --- | --- | --- | --- |
| [data/site-overview.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/site-overview.csv) | 132 | 17 kB | One row per site: its published campaigns with the number of samples in each, the total, and the families measured. Start here for questions about a site: when, how often, what. |
| [data/samples.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/samples.csv) | 1,264 | 158 kB | One row per sample: site, campaign, dates, temperature, the families and number of compounds measured. Whole file, for tools that run code. |
| [data/coverage.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/coverage.csv) | 1,493 | 94 kB | One row per site, campaign and family: samples, compounds measured, results and detected results (sums not counted). Whole file, for tools that run code. |
| https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/samples/samples_<campaign>.csv (12 files: 2005, 2006, 2007, 2008, 2009, 2011, 2013, 2014, 2015, 2017, 2018, 2023) | 7-193 each | up to 27 kB | samples.csv, one file per campaign (small enough to read whole). |
| https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/coverage/coverage_<campaign>.csv (12 files: 2005, 2006, 2007, 2008, 2009, 2011, 2013, 2014, 2015, 2017, 2018, 2023) | 7-292 each | up to 19 kB | coverage.csv, one file per campaign (small enough to read whole). |
| [data/sites.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/sites.csv) | 132 | 19 kB | The sites with published measurements: codes, names, country, network, type, status, coordinates. |
| [data/compounds.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/compounds.csv) | 112 | 26 kB | The compounds: family, names, code, CAS, molecular weight, log KOA, sum members, Stockholm Convention status. |
| [data/campaigns-and-methods.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/campaigns-and-methods.csv) | 47 | 8 kB | One row per campaign, network and family: sampler, analytical technique, sampling-rate method, recalculation, publications. |
| [data/publications.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/publications.csv) | 16 | 7 kB | The publications behind the data, then the papers on the sampling method. |
| [data/measurements/PCB_2005.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/measurements/PCB_2005.csv) | 1,292 | 222 kB | Measurements of Polychlorinated Biphenyls (PCB), campaign 2005. |
| [data/measurements/PCB_2006.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/measurements/PCB_2006.csv) | 1,016 | 177 kB | Measurements of Polychlorinated Biphenyls (PCB), campaign 2006. |
| [data/measurements/PCB_2007.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/measurements/PCB_2007.csv) | 1,354 | 239 kB | Measurements of Polychlorinated Biphenyls (PCB), campaign 2007. |
| [data/measurements/PCB_2009.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/measurements/PCB_2009.csv) | 1,384 | 248 kB | Measurements of Polychlorinated Biphenyls (PCB), campaign 2009. |
| [data/measurements/PCB_2011.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/measurements/PCB_2011.csv) | 1,376 | 251 kB | Measurements of Polychlorinated Biphenyls (PCB), campaign 2011. |
| [data/measurements/PCB_2014.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/measurements/PCB_2014.csv) | 1,536 | 277 kB | Measurements of Polychlorinated Biphenyls (PCB), campaign 2014. |
| [data/measurements/PBDE.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/measurements/PBDE.csv) | 3,603 | 712 kB | Measurements of Polybrominated Diphenyl Ethers (PBDE), all published campaigns. |
| [data/measurements/NBFR.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/measurements/NBFR.csv) | 3,915 | 732 kB | Measurements of Novel Brominated Flame Retardants (NBFR), all published campaigns. |
| [data/measurements/OPE.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/measurements/OPE.csv) | 4,275 | 944 kB | Measurements of Organophosphate Esters (OPE), all published campaigns. |
| [data/measurements/DP.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/measurements/DP.csv) | 1,632 | 309 kB | Measurements of Dechlorane Plus and Related Compounds (DP), all published campaigns. |
| [data/measurements/OCP_2005.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/measurements/OCP_2005.csv) | 1,815 | 331 kB | Measurements of Organochlorine Pesticides (OCP), campaign 2005. |
| [data/measurements/OCP_2006.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/measurements/OCP_2006.csv) | 1,637 | 300 kB | Measurements of Organochlorine Pesticides (OCP), campaign 2006. |
| [data/measurements/OCP_2007.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/measurements/OCP_2007.csv) | 1,958 | 362 kB | Measurements of Organochlorine Pesticides (OCP), campaign 2007. |
| [data/measurements/OCP_2009.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/measurements/OCP_2009.csv) | 1,903 | 358 kB | Measurements of Organochlorine Pesticides (OCP), campaign 2009. |
| [data/measurements/OCP_2011.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/measurements/OCP_2011.csv) | 1,892 | 360 kB | Measurements of Organochlorine Pesticides (OCP), campaign 2011. |
| [data/measurements/OCP_2014.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/measurements/OCP_2014.csv) | 2,112 | 399 kB | Measurements of Organochlorine Pesticides (OCP), campaign 2014. |
| [data/measurements/CP.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/measurements/CP.csv) | 46 | 9 kB | Measurements of Chlorinated Paraffins (CP), all published campaigns. |
| [data/measurements/nPFAS.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/measurements/nPFAS.csv) | 1,516 | 330 kB | Measurements of Neutral (Volatile) PFAS (nPFAS), all published campaigns. |
| [data/measurements/PFAA.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/measurements/PFAA.csv) | 2,664 | 563 kB | Measurements of Perfluoroalkyl Acids (PFAA), all published campaigns. |
| [data/measurements/VMS.csv](https://raw.githubusercontent.com/HAPs-Lab/gaps-globe/main/data/measurements/VMS.csv) | 1,332 | 272 kB | Measurements of Volatile Methyl Siloxanes (VMS), all published campaigns. |

All files are CSV: UTF-8 (with a byte-order mark), comma-separated, one header row, full stop as the decimal mark,
dates as YYYY-MM-DD. Families with measurement files: PCB (Polychlorinated Biphenyls), PBDE (Polybrominated Diphenyl Ethers), NBFR (Novel Brominated Flame Retardants), OPE (Organophosphate Esters), DP (Dechlorane Plus and Related Compounds), OCP (Organochlorine Pesticides), CP (Chlorinated Paraffins), nPFAS (Neutral (Volatile) PFAS), PFAA (Perfluoroalkyl Acids), VMS (Volatile Methyl Siloxanes).

## How the data work

- **Published campaigns only.** A measurement is included only if its campaign (for its network and compound family)
  has at least one peer-reviewed publication (column "Published in"). Campaigns not yet published are shown on the
  website but are not in these files, so a missing year is not necessarily a year without sampling.
- **One row per sample and compound.** A sample is one passive air sampler deployed at one site, usually for about
  three months (columns Deployed, Retrieved, Days); a few deployments were much longer (up to about 15 months), as
  recorded. "Campaign" is a label, not a date.
- **Valid results only:** flagged in the database as detected or below the detection limit, and quantitative.
- **Not detected:** "Detected" is No and the concentration is blank. A non-detect is never a number: do not
  substitute zero or a fraction of the LOQ unless the person asks for it, and then say so. The LOQ column gives the
  sample's limit of quantification for context; some detected values lie below it.
- **Units:** concentrations and LOQs in pg/m³ of air (picograms per cubic metre), rounded to 4 and 3 significant
  figures; temperatures in °C. Concentrations span several orders of magnitude: use a logarithmic axis in plots.
- **Sums** ("Sum of members" Yes, e.g. ΣPCB) are computed by GAPS Globe for a sample only when every member compound
  has a valid result: the total of the detected members (non-detects count as zero), or not detected when no member
  is detected. They are not values reported in the publications. Never add a sum to its own members.
- **Replicates:** samplers deployed together share a Sample ID and are told apart by "Replicate" (A, B).
- **Samplers:** PUF (polyurethane foam) and SIP (sorbent-impregnated PUF) disks deployed together are separate
  samples with their own Sample ID.
- **Recalculated:** where Yes, concentrations were recalculated with updated sampling rates and may differ from the
  original publication (method in campaigns-and-methods.csv).
- **Joining files:** "Site code (ECCC)" links the measurement, sample and coverage files to sites.csv; "Compound
  code" to compounds.csv; Campaign, Network and Family to campaigns-and-methods.csv; the DOIs in "Published in" to
  publications.csv.

## Columns of the measurement files

| Column | Meaning |
| --- | --- |
| Sample ID | Sample identifier: site code, quarter, year and sampler type. Replicates share an ID. |
| Replicate | A or B for replicate samples deployed together; blank otherwise. |
| Sampler | PUF: polyurethane foam disk. SIP: sorbent-impregnated PUF disk. |
| Site code (ECCC) | Site code used by Environment and Climate Change Canada. |
| Site name | Site name. |
| Country | Country of the site. |
| Network | GAPS or GAPS-Megacities. |
| Campaign | Sampling campaign (a label, not a date: see Deployed and Retrieved). |
| Quarter | Quarter of the campaign in which the sampler was deployed. |
| Deployed | Date the sampler was deployed (YYYY-MM-DD). |
| Retrieved | Date the sampler was retrieved (YYYY-MM-DD). |
| Days | Days of deployment. |
| Mean air temperature (°C) | Mean air temperature over the deployment; blank if not available. |
| Family | Compound family (abbreviation; names in the Compounds sheet). |
| Compound | Compound name. |
| Compound code | Compound code used in the database. |
| CAS | CAS Registry Number; blank for sums and where not available. |
| Sum of members | Yes for sums computed by GAPS Globe from member compounds (see the data rules). |
| Detected | Yes if flagged as detected in the database; No if below the detection limit (not detected). |
| Concentration (pg/m³) | Concentration in air; blank when not detected (never a number for a non-detect). |
| LOQ (pg/m³) | The sample's limit of quantification (LOQ) as reported in the database, for context; blank for sums and where not reported. Some detected values lie below it. |
| Published in | DOI(s) of the publication(s) that report this campaign; separated by semicolons. |
| Recalculated | Yes if concentrations were recalculated with updated sampling rates after publication. |

## Licence and citation

Shared under the Creative Commons Attribution-NonCommercial 4.0 International licence (CC BY-NC 4.0,
https://creativecommons.org/licenses/by-nc/4.0/): free to use and adapt for non-commercial purposes, with credit.

**Cite as:** Hazardous Air Pollutants (HAPs) Laboratory. GAPS Globe, version v2.1, data version 2026-11-12. Please cite also the publications listed for the measurements used (column "Published in";
full references in publications.csv).

**Disclaimer:** GAPS Globe is an independent project of the HAPs Laboratory. It is not an official product of, or endorsed by, Environment and Climate Change Canada or any other organizations. Values shown may differ from original publications where concentrations were recalculated. For authoritative values, consult the cited publications.
