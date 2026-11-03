# Maryland early voting: the night before Election Day 2026

An Election Day update to Capital News Service's coverage of mail-in and early in-person voting before Maryland's Nov. 3, 2026 general election. It reruns the original story's analysis with the comparison point moved from one week out to **the night before Election Day**.

**The original story and its repo:** [Marylanders vote earlier in 2026](https://cnsmaryland.org/2026/10/30/marylanders-vote-earlier-in-2026/) · [dlanderm-dal/md-early-voting-2026](https://github.com/dlanderm-dal/md-early-voting-2026). That repo's README explains the data, definitions and methods, and all of them still apply. This one covers only what changed.

## The graphic

[**Election Eve: Early voting spikes in Maryland**](https://dlanderm-dal.github.io/md-early-voting-2026-election-day/table_1_stacked_bars_d3.html) (D3, `table_1_stacked_bars_d3.html`): mail-in, early in-person and combined votes by party, the night before Election Day, 2022 vs. 2026.

| | Nov. 7, 2022 | Nov. 2, 2026 | Change |
|---|---|---|---|
| Mail-in ballots received (by 6 p.m.) | 399,319 | 417,417 | +4.5% |
| Early in-person votes (all eight days) | 381,972 | 604,396 | +58.2% |
| Combined | 781,291 | 1,021,813 | +30.8% |

Embed it the same way as the original story's D3 charts:

```html
<iframe class="cns-d3" src="https://dlanderm-dal.github.io/md-early-voting-2026-election-day/table_1_stacked_bars_d3.html" title="Election Eve: Early voting spikes in Maryland" width="100%" height="640" style="border:0;width:100%;display:block" scrolling="no" loading="lazy"></iframe>
```

The update's other three graphics are published in Flourish, and their uploads are in `output/`:

| Graphic | Flourish | Upload |
|---|---|---|
| Who accounts for the jump in early voting in Maryland? (table) | [30791371](https://public.flourish.studio/visualisation/30791371/) | `methods_party_change_flourish.csv` |
| Marylanders increasingly utilizing methods of voting before election day (line chart, now 16 to 1 days before Election Day) | [30791347](https://public.flourish.studio/visualisation/30791347/) | `early_voting_time_domain_graphic.csv` |
| Congressional districts all see spike in early in-person voting | [30791335](https://public.flourish.studio/visualisation/30791335/) | `in_person_congressional_flourish.csv` |

## What changed

- **Comparison point: the night before Election Day.** The mail-in reports are as of 6 p.m. on Nov. 7, 2022, Nov. 4, 2024 and Nov. 2, 2026. Early in-person voting was over by then, so those numbers cover all eight days (Oct. 27 to Nov. 3, 2022, Oct. 24 to 31, 2024, and Oct. 22 to 29, 2026).
- **The line chart runs to the night before.** It now covers 16 to 1 days before Election Day; the original stopped at 5. After early voting ends, the early in-person line holds at its final total.
- **New 2026 data.**
  - `direct-download/nov_3_1.43pm/`: the State Board of Elections' mail-in and early-voting reports, downloaded from its website at 1:43 p.m. on Nov. 3, 2026. The mail-in report is as of Nov. 2, 2026.
  - `skipjack_download/`: the board's county mail-in reports for Oct. 28 to Nov. 2, 2026, from [Skipjack](https://github.com/NewsAppsUMD/skipjack)'s archive of State Board of Elections reports (`archives/sbe/campaign_stats/GG26`). Each `_provenance.json` file records the board URL the report came from and when Skipjack fetched it. Each spreadsheet's SHA-256 checksum matches the one recorded there, and the Nov. 2 file is identical to the board download in `direct-download/`.
- **Earlier data, copied from the original repo.** `from_full_pia/` holds the original repo's files under their original folder names, from `Press Reports-selected/`, `direct-download/` and `supplemental_reports/`. It adds four 2022 reports (Nov. 4 to 7) and four 2024 reports (as of Nov. 1 to 4) from the same public records release. The line chart needs them now that it runs to 1 day out.

## How the numbers are built

`election_day_update.Rmd` is the original story's `early_voting_factcheck_self.Rmd`, with these changes:

- every file is read from this repo,
- the comparison dates are moved to the night before Election Day,
- the line chart runs to 1 day out,
- a last chunk writes graphic 1's data into the D3 page.

[`CHANGES_vs_full_pia.md`](CHANGES_vs_full_pia.md) lists every line that differs from the original Rmd and why. Run the chunks in order from this folder in R or RStudio. It needs the `tidyverse`, `janitor`, `readxl` and `jsonlite` packages, and writes every table to `output/`.

**Rounding.** The popups' "change in share of votes" (percentage points) is the difference of the two years' shares after rounding to one decimal, as in the original story. It can differ by 0.1 point from the change calculated from the unrounded counts. For example, Democrats' share of combined votes was 63.985% in 2022 and 64.046% in 2026: the popup says 0.0 points, and the unrounded change is +0.06.

## Credits

- Graphics and analysis: David Landerman, Capital News Service
- Source: [Maryland State Board of Elections](https://elections.maryland.gov/press_room/index.html); 2022 and 2024 figures obtained through a public records request
- Oct. 28 to Nov. 2, 2026 mail-in reports: [Skipjack](https://github.com/NewsAppsUMD/skipjack), NewsAppsUMD
- Oct. 26, 2022 mail-in report: Derek Willis, University of Maryland, College Park (see the original repo)
