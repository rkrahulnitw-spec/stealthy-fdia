# Time-Series Vulnerability Assessment of Stealthy AC FDIA — interactive dashboard

Worst-case stealthy false-data injection attacks searched at **every one of the 8,760 hours**
of a standard IEEE RTS year, on the **IEEE-14** and **IEEE-30** benchmark grids.
None of the ~16,700 attacks was detected by the grid's chi-square bad-data test.

**Live site:** https://rkrahulnitw-spec.github.io/fdia-grid-dashboard/

M.Tech Major Project, NIT Warangal · supervisor Prof. Altaf Q. H. Badar.
Extends A. Sikkewal (IEEE SEFET 2026), which studied a single load snapshot.

## What this repo is

A **static export** of the project's React + FastAPI dashboard. Every API response has
been pre-computed to JSON so the whole app runs with no server. Per-hour grid states are
chunked one file per day, so scrubbing to an hour downloads ~250 KB rather than the lot.

Regenerate with:

    python scripts/export_static_site.py
    VITE_STATIC=1 BASE=/fdia-grid-dashboard/ npm run build

## Data

Load: IEEE RTS-GMLC (Barrows et al., *IEEE Trans. Power Systems* 35(1), 2020).
Networks: IEEE 14-bus and 30-bus test cases, UW Power Systems Test Case Archive, via MATPOWER.

## Note

IEEE-14's figures are being recomputed with a more thorough search; they will improve.
IEEE-30's are final.
