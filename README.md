Systemic Risk and Financial Contagion in the Nigerian Banking Sector
A Multi-Regime Network Analysis of the Five Domestic Systemically Important Banks (2008–2024)


Samuel Babatunde Folorunsho Ajakaiye --MScFE Candidate WorldQuant University

What this project does
This research estimates a time-varying DCC-GARCH interconnectedness network with Delta CoVaR edge weights for the five Nigerian domestic systemically important banks (D-SIBs) — First Bank, GTBank/GTCO, Zenith, Access, and UBA — and tests a fiscal transmission channel linking Brent crude oil prices, monthly Federation Account Allocation Committee (FAAC) disbursements, and CBN external reserves to banking-system connectedness. Five binary institutional controls (the 2009–2011 interbank guarantee, AMCON operations, the multi-window FX regime, COVID-19 forbearance, and the June 2023 FX unification) correct for government intervention bias in observable stress signals.

Repository structure
```
├── ngx_data_validation.ipynb     Data preparation: loads raw price CSVs, splices
│                                 predecessor/successor tickers, computes log returns,
│                                 and produces a data-quality report
├── data/
│   └── raw/                      Raw daily price CSVs for the five banks (source: Investing.com)
├── output/
│   ├── prices_spliced.csv        Continuous close-price panel, five banks
│   ├── returns_log.csv           Daily log-return panel (input to the GARCH stage)
│   └── data_quality_report.txt   Coverage, gaps, zero-return runs, corporate-action flags
└── requirements.txt              Python dependencies
```

How to run Repo

Clone or download this repository.
Install dependencies: `pip install -r requirements.txt` (Python 3.10+).
Open `ngx_data_validation.ipynb` in Jupyter, VS Code, or Google Colab and run all cells from top to bottom. The notebook reads from `data/raw/` using relative paths and rewrites the three files in `output/`.
Expected result: a common (all-bank) sample of 3,151 daily return observations spanning 2012-03-07 to 2024-12-31, and a data-quality report matching the copy committed in `output/`.

Data sources
Series	Source	Status
Daily equity prices, five D-SIBs (2012–2024)	Investing.com (NGX-listed equities)	Collected and validated
Daily equity prices, predecessor tickers (2008–2012)	Nigerian Exchange (NGX) historical data service	Requested (academic licence)
Monthly FAAC disbursements	FAAC / National Bureau of Statistics publications	Next stage
Brent crude oil prices	U.S. EIA / FRED	Next stage
CBN external reserves	Central Bank of Nigeria statistics database	Next stage

Ticker continuity: GUARANTY→GTCO (2021 holdco restructuring), ACCESS→ACCESSCORP (2022 holdco; Diamond Bank merger 2019), and FIRSTBANK→FBNH→FIRSTHOLDCO are spliced into single continuous series per bank, with the return on each transition date excluded.

Model scope boundary statement

The committed scope of this research, as agreed with the course instructor, comprises: (1) the DCC-GARCH / Delta CoVaR network with eigenvector centrality rankings compared across four pre-specified regime periods; (2) the FAAC fiscal transmission channel tested by Granger causality within a distributed-lag VAR; and (3) the five institutional dummy controls.
The following are explicitly designated future work and are not implemented here: the bank-level crude-oil loan exposure panel, the parallel-market FX premium early-warning variable, Hidden Markov Model endogenous regime detection, and maximum-entropy robustness checks. A stated limitation follows from the first exclusion: without the oil-exposure panel, common factor exposure and bilateral contagion cannot be fully separated, and the results are interpreted accordingly.
Known data limitations: the common sample begins in March 2012 pending the NGX historical data purchase for 2008–2012; NGX equities exhibit thin trading (10–15% zero-return days) and daily price limits (±10%) that censor extreme single-day returns; one candidate unadjusted corporate action (UBA, 2016-03-30) is under verification against NGX disclosures.

Project status

[x] Data acquisition and validation (five banks, 2012–2024)
[ ] NGX historical extension (2008–2012) — requested
[ ] Univariate GARCH(1,1) estimation per bank
[ ] DCC estimation and Delta CoVaR network construction
[ ] Regime-period centrality comparison
[ ] FAAC transmission channel VAR and Granger causality tests
[ ] Institutional dummy augmentation
[ ] Final report and presentation

Contact
samuel@teledinamik.com.ng
