# Stealthy FDIA — Time-Series Vulnerability Assessment of Power Grids

**Live dashboard → https://rkrahulnitw-spec.github.io/stealthy-fdia/**

Worst-case *stealthy* false-data injection attacks searched at **every one of the 8,760 hours**
of a standard IEEE RTS year, on the **IEEE-14** and **IEEE-30** benchmark grids.
**None of the ~16,700 attacks was detected** by the grid's chi-square bad-data test.

M.Tech Major Project, NIT Warangal · supervisor Prof. Altaf Q. H. Badar.
Extends A. Sikkewal (IEEE SEFET 2026), which studied a single load snapshot.

## The finding

Attack damage has **two opposite regimes**:

| | IEEE-14 | IEEE-30 |
|---|---|---|
| valid stealthy attacks | 8,346 / 8,760 | 8,360 / 8,760 |
| **caught by the detector** | **0** | **0** |
| worst extra losses | +2.26 MW (+31%) | **+4.91 MW (+42%)** |
| worst extra cost | +$1,867/h | +$1,784/h |
| extra cost over the year | $1.51 M | $0.82 M |

Physical **loss** damage happens only near the annual peak. **Economic** damage is broad,
year-round, and largest at *light* load — the attack shifts generation off cheap units onto
expensive ones without raising losses at all. A single-snapshot study cannot show this.

## What this repo is

A **static export** of the project's React + FastAPI dashboard. Every API response is
pre-computed to JSON, so the whole app runs with no server. Per-hour grid states are chunked
one file per day, so scrubbing to an hour downloads ~250 KB rather than the full 90 MB.

Regenerate:

    python scripts/export_static_site.py
    VITE_STATIC=1 BASE=/stealthy-fdia/ npm run build

## Data

Load: IEEE RTS-GMLC (Barrows et al., *IEEE Trans. Power Systems* 35(1), 2020).
Networks: IEEE 14-bus and 30-bus test cases, UW Power Systems Test Case Archive, via MATPOWER.

## Status

**IEEE-30 is final and complete** — all 8,760 hours.

**IEEE-14 is mid-revision.** Its hours are being re-searched with the same, more thorough
method IEEE-30 received; its worst case rises from +2.26 to at least +2.84 MW, so every
IEEE-14 number here will improve. 17 of its 8,760 hourly grid states were being recomputed
when this snapshot was generated and are absent from the Grid-model scrubber — the app
falls back to the nearest available hour and says so. IEEE-30 has no gaps.
