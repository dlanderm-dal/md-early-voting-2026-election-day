# Every difference from the published Rmd

Compare `full_pia/early_voting_factcheck_self.Rmd` (left, the published story) with `election_day_update/election_day_update.Rmd` (right). There are **87 differences**, and every one is listed below, grouped by why it changed. Line numbers are the **right-hand file's** (the left file's are in brackets).

Nothing in `full_pia` was changed. All the code that isn't listed here is identical, character for character. Every mail-in report, including the six from Skipjack, goes through the same read-and-clean code as in the published Rmd.

| Group | Differences |
|---|---|
| 1. The top of the file | 3 |
| 2. The comparison point: the night before Election Day | 26 |
| 3. Where each file is read from | 40 |
| 4. Time domain graphic: the added 2022 and 2024 reports | 2 |
| 5. Time domain graphic: 2026's last six days, from Skipjack | 1 |
| 6. Time domain graphic: everything else that changed for 16 to 1 days out | 14 |
| 7. The new last chunk: the D3 charts | 1 |

## 1. The top of the file

**Line 2** [left: 2]: Title and date of this copy.

Was:
```r
title: "early_voting_factcheck_self"
```
Now:
```r
title: "election_day_update"
```

**Line 4** [left: 4]: Title and date of this copy.

Was:
```r
date: "2026-10-29"
```
Now:
```r
date: "2026-11-03"
```

**Line 7–21** [left: none, added]: New note at the top saying what this copy is and the three changes.

Added:
```r

<!--
ELECTION DAY UPDATE (Nov. 3, 2026): a copy of full_pia/early_voting_factcheck_self.Rmd, the published story's Rmd,
with three changes (everything else is the same code):
  1. Comparison point = the night before Election Day: Nov. 7, 2022 / Nov. 4, 2024 / Nov. 2, 2026 (mail-in reports as of 6 PM).
     Early in-person voting was over by then, so those are all eight days.
  2. Every file comes from this folder: full_pia's files are copied into from_full_pia/ (same folder names as in
     full_pia's Press Reports-selected/, direct-download/ and supplemental_reports/), today's SBE download is in
     direct-download/nov_3_1.43pm/, and the 2026 mail-in days Oct. 28 to Nov. 2 come from skipjack_download/
     (the SBE "Absentees Sent and Returned by County" spreadsheets as archived by Skipjack,
     github.com/NewsAppsUMD/skipjack, archives/sbe/campaign_stats/GG26; read with the same code as every other day).
  3. The time domain graphic now runs 16 to 1 days before Election Day (was 16 to 5), and a last chunk puts the
     new numbers into the two D3 charts in this folder.
full_pia is published: nothing here reads from or writes to it. Everything is written to this folder's output/.
-->
```

## 2. The comparison point: the night before Election Day

**Line 32** [left: 17]: Dates and wording: the night before Election Day (Nov. 7, 2022 and Nov. 2, 2026) instead of one week before (Nov. 1, 2022 and Oct. 27, 2026).

Was:
```r
# First Goal Early Voting Totals by Method-Mail-in, Early-in person, and combined. As of One week before election day.
```
Now:
```r
# First Goal Early Voting Totals by Method-Mail-in, Early-in person, and combined. As of the night before election day.
```

**Line 37** [left: 22]: Dates and wording: the night before Election Day (Nov. 7, 2022 and Nov. 2, 2026) instead of one week before (Nov. 1, 2022 and Oct. 27, 2026).

Was:
```r
# One week before election day is Nov. 1, 2022 and Oct. 27, 2026
```
Now:
```r
# The night before election day is Nov. 7, 2022 and Nov. 2, 2026 (mail-in reports as of 6 PM); early in-person voting had ended (Nov. 3, 2022 and Oct. 29, 2026)
```

**Line 40** [left: 25]: 2022 mail-in report: as of Nov. 7, 2022 (the night before Election Day), was Nov. 1, 2022 (one week before).

Was:
```r
mail_2022_raw <- read_excel("Press Reports-selected/2022/GG22/11-1-2022/Absentees Sent and Returned by County.xlsx", col_names = FALSE)
```
Now:
```r
mail_2022_raw <- read_excel("from_full_pia/11-7-2022/Absentees Sent and Returned by County.xlsx", col_names = FALSE)   # as of Nov. 7, 2022 6 PM
```

**Line 41** [left: 26]: 2026 mail-in report: today's SBE download, as of Nov. 2, 2026 (the night before Election Day), was the Oct. 27, 2026 download.

Was:
```r
mail_2026_raw <- read_excel("direct-download/oct_28_2.14pm/Absentees_Sent_and_Returned_by_County(4).xlsx", col_names = FALSE)
```
Now:
```r
mail_2026_raw <- read_excel("direct-download/nov_3_1.43pm/Absentees_Sent_and_Returned_by_County(4).xlsx", col_names = FALSE)   # as of Nov. 2, 2026 6 PM (downloaded Nov. 3)
```

**Line 44** [left: 29]: 2022 early in-person file: the last one, all 8 days (early voting ended Nov. 3, 2022), was the Nov. 1, 2022 file (6 days).

Was:
```r
in_person_early_2022 <- read_csv("Press Reports-selected/2022/GG22/11-1-2022/EarlyVoting RAW data.csv")
```
Now:
```r
in_person_early_2022 <- read_csv("from_full_pia/11-3-2022/EarlyVoting RAW data.csv")          # all 8 days (early voting ended Nov. 3, 2022)
```

**Line 45** [left: 30]: 2026 early in-person file: today's download, all 8 days (early voting ended Oct. 29, 2026), was the Oct. 27, 2026 download (6 days).

Was:
```r
in_person_early_2026 <- read_csv("direct-download/oct_28_2.14pm/EarlyVoting_RAW_data.csv")
```
Now:
```r
in_person_early_2026 <- read_csv("direct-download/nov_3_1.43pm/EarlyVoting_RAW_data.csv")     # all 8 days (early voting ended Oct. 29, 2026)
```

**Line 52** [left: 37]: Dates and wording: the night before Election Day (Nov. 7, 2022 and Nov. 2, 2026) instead of one week before (Nov. 1, 2022 and Oct. 27, 2026).

Was:
```r
mail_2022_as_of <- mail_2022_raw[[4]][3]               # save the text in row 3, column 4 of the raw sheet ("As of: November 1, 2022 6 PM")
```
Now:
```r
mail_2022_as_of <- mail_2022_raw[[4]][3]               # save the text in row 3, column 4 of the raw sheet ("As of: November 7, 2022 6 PM")
```

**Line 62** [left: 47]: Dates and wording: the night before Election Day (Nov. 7, 2022 and Nov. 2, 2026) instead of one week before (Nov. 1, 2022 and Oct. 27, 2026).

Was:
```r
         as_of = str_remove(as_of, fixed(" 6 PM")),    #   step 2: delete " 6 PM", leaving "November 1, 2022"
```
Now:
```r
         as_of = str_remove(as_of, fixed(" 6 PM")),    #   step 2: delete " 6 PM", leaving "November 7, 2022"
```

**Line 63** [left: 48]: Dates and wording: the night before Election Day (Nov. 7, 2022 and Nov. 2, 2026) instead of one week before (Nov. 1, 2022 and Oct. 27, 2026).

Was:
```r
         as_of = mdy(as_of))                           #   step 3: read "November 1, 2022" as a real date (2022-11-01); no |> because the pipe ends here
```
Now:
```r
         as_of = mdy(as_of))                           #   step 3: read "November 7, 2022" as a real date (2022-11-07); no |> because the pipe ends here
```

**Line 66** [left: 51]: Dates and wording: the night before Election Day (Nov. 7, 2022 and Nov. 2, 2026) instead of one week before (Nov. 1, 2022 and Oct. 27, 2026).

Was:
```r
mail_2026_as_of <- mail_2026_raw[[5]][3]               # save the text in row 3, column 5 of the raw sheet ("As of: October 27, 2026 6 PM")
```
Now:
```r
mail_2026_as_of <- mail_2026_raw[[5]][3]               # save the text in row 3, column 5 of the raw sheet ("As of: November 2, 2026 6 PM")
```

**Line 77** [left: 62]: Dates and wording: the night before Election Day (Nov. 7, 2022 and Nov. 2, 2026) instead of one week before (Nov. 1, 2022 and Oct. 27, 2026).

Was:
```r
         as_of = mdy(as_of))                           #   date step 3: read it as a date (2026-10-27); the pipe ends here
```
Now:
```r
         as_of = mdy(as_of))                           #   date step 3: read it as a date (2026-11-02); the pipe ends here
```

**Line 98** [left: 83]: Early voting is over: 8 of 8 days (was 6), so the files run through Nov. 3, 2022 and Oct. 29, 2026.

Was:
```r
# How far each file goes: count the early voting days that have any votes (6 in both files)
```
Now:
```r
# How far each file goes: count the early voting days that have any votes (8 in both files: early voting is over)
```

**Line 103** [left: 88]: Early voting is over: 8 of 8 days (was 6), so the files run through Nov. 3, 2022 and Oct. 29, 2026.

Was:
```r
in_person_early_as_of_2022 <- mdy("October 27, 2022") + in_person_early_days_2022 - 1   # Oct. 27 + 5 more days = Nov. 1, 2022
```
Now:
```r
in_person_early_as_of_2022 <- mdy("October 27, 2022") + in_person_early_days_2022 - 1   # Oct. 27 + 7 more days = Nov. 3, 2022
```

**Line 104** [left: 89]: Early voting is over: 8 of 8 days (was 6), so the files run through Nov. 3, 2022 and Oct. 29, 2026.

Was:
```r
in_person_early_as_of_2026 <- mdy("October 22, 2026") + in_person_early_days_2026 - 1   # Oct. 22 + 5 more days = Oct. 27, 2026
```
Now:
```r
in_person_early_as_of_2026 <- mdy("October 22, 2026") + in_person_early_days_2026 - 1   # Oct. 22 + 7 more days = Oct. 29, 2026
```

**Line 240** [left: 225]: Dates and wording: the night before Election Day (Nov. 7, 2022 and Nov. 2, 2026) instead of one week before (Nov. 1, 2022 and Oct. 27, 2026).

Was:
```r
            `As of` = if_else(year == 2022, "Nov. 1, 2022", "Oct. 27, 2026"),   #   K: typed in: one week before each Election Day
```
Now:
```r
            `As of` = if_else(year == 2022, "Nov. 7, 2022", "Nov. 2, 2026"),    #   K: typed in: the night before each Election Day
```

**Line 241** [left: 226]: Early voting is over: 8 of 8 days (was 6), so the files run through Nov. 3, 2022 and Oct. 29, 2026.

Was:
```r
            `Early voting day` = "Day 6 of 8") |>                               #   L: typed in
```
Now:
```r
            `Early voting day` = "Day 8 of 8") |>                               #   L: typed in (early voting is over)
```

**Line 414** [left: 399]: Early voting is over: 8 of 8 days (was 6), so the files run through Nov. 3, 2022 and Oct. 29, 2026.

Was:
```r
  mutate(as_of_2022 = in_person_early_as_of_2022,                                #   the date each early voting file runs through (Nov. 1, 2022)
```
Now:
```r
  mutate(as_of_2022 = in_person_early_as_of_2022,                                #   the date each early voting file runs through (Nov. 3, 2022)
```

**Line 415** [left: 400]: Early voting is over: 8 of 8 days (was 6), so the files run through Nov. 3, 2022 and Oct. 29, 2026.

Was:
```r
         as_of_2026 = in_person_early_as_of_2026,                                #   (Oct. 27, 2026)
```
Now:
```r
         as_of_2026 = in_person_early_as_of_2026,                                #   (Oct. 29, 2026)
```

**Line 416** [left: 401]: Early voting is over: 8 of 8 days (was 6), so the files run through Nov. 3, 2022 and Oct. 29, 2026.

Was:
```r
         early_voting_day = str_c("Day ", in_person_early_days_2026, " of 8"),   #   "Day 6 of 8"
```
Now:
```r
         early_voting_day = str_c("Day ", in_person_early_days_2026, " of 8"),   #   "Day 8 of 8"
```

**Line 469** [left: 454]: Dates and wording: the night before Election Day (Nov. 7, 2022 and Nov. 2, 2026) instead of one week before (Nov. 1, 2022 and Oct. 27, 2026).

Was:
```r
            `As of 2022 (popup)` = "Nov. 1, 2022",
```
Now:
```r
            `As of 2022 (popup)` = "Nov. 7, 2022",
```

**Line 470** [left: 455]: Dates and wording: the night before Election Day (Nov. 7, 2022 and Nov. 2, 2026) instead of one week before (Nov. 1, 2022 and Oct. 27, 2026).

Was:
```r
            `As of 2026 (popup)` = "Oct. 27, 2026",
```
Now:
```r
            `As of 2026 (popup)` = "Nov. 2, 2026",
```

**Line 502** [left: 487]: Dates and wording: the night before Election Day (Nov. 7, 2022 and Nov. 2, 2026) instead of one week before (Nov. 1, 2022 and Oct. 27, 2026).

Was:
```r
            `As of` = if_else(year == 2022, "Nov. 1, 2022", "Oct. 27, 2026"),      #   K
```
Now:
```r
            `As of` = if_else(year == 2022, "Nov. 7, 2022", "Nov. 2, 2026"),       #   K: the night before Election Day
```

**Line 503** [left: 488]: Early voting is over: 8 of 8 days (was 6), so the files run through Nov. 3, 2022 and Oct. 29, 2026.

Was:
```r
            `Early voting day` = "Day 6 of 8",                                     #   L
```
Now:
```r
            `Early voting day` = "Day 8 of 8",                                     #   L
```

**Line 533** [left: 518]: Comment: 2026 early voting is over, so all 8 days.

Was:
```r
# 2026: in_person_early_2026 from the first import chunk (days 1-6 so far)
```
Now:
```r
# 2026: in_person_early_2026 from the first import chunk (all 8 days)
```

**Line 1124** [left: 953]: Comment: 2026 early voting is over, so all 8 days.

Was:
```r
# 2026: days 1-6 so far
```
Now:
```r
# 2026: all 8 days
```

**Line 1132** [left: 961]: Comment: there are no empty days left to drop (the code is unchanged).

Was:
```r
  filter(votes > 0)                                                   # drop days 7 and 8: no votes yet
```
Now:
```r
  filter(votes > 0)                                                   # drop any day with no votes (none now: early voting is over)
```

## 3. Where each file is read from

Every one of these is the **same file** the published Rmd read, now copied into this folder. `from_full_pia/` keeps full_pia's own folder names, so `Press Reports-selected/2022/GG22/10-28-2022/` becomes `from_full_pia/10-28-2022/`. The 2024 and 2026 folders work the same way, and so do `supplemental_reports/` and `direct-download/oct_28_2.14pm/`. The code on these lines is otherwise unchanged.

| Line (right) [left] | Was | Now |
|---|---|---|
| 333 [318] | `supplemental_reports/2026_GG_representativeincongressbydistrict_candidatelist.csv` | `from_full_pia/supplemental_reports/2026_GG_representativeincongressbydistrict_candidatelist.csv` |
| 334 [319] | `supplemental_reports/US_Congressional_Districts_2022.geojson` | `from_full_pia/supplemental_reports/US_Congressional_Districts_2022.geojson` |
| 531 [516] | `Press Reports-selected/2022/GG22/11-3-2022/EarlyVoting RAW data.csv` | `from_full_pia/11-3-2022/EarlyVoting RAW data.csv` |
| 532 [517] | `Press Reports-selected/2024/PG24/EV_SDR_End_11012024/EarlyVoting RAW data.csv` | `from_full_pia/EV_SDR_End_11012024/EarlyVoting RAW data.csv` |
| 557 [541] | `Press Reports-selected/2022/GG22/10-23-2022/Absentees Sent and Returned by County_10_23_2022.xlsx` | `from_full_pia/10-23-2022/Absentees Sent and Returned by County_10_23_2022.xlsx` |
| 567 [551] | `Press Reports-selected/2022/GG22/10-24-2022/Absentees Sent and Returned by County_10_24_2022.xlsx` | `from_full_pia/10-24-2022/Absentees Sent and Returned by County_10_24_2022.xlsx` |
| 577 [561] | `Press Reports-selected/2022/GG22/10-25-2022/Absentees Sent and Returned by County_10_25_2022.xlsx` | `from_full_pia/10-25-2022/Absentees Sent and Returned by County_10_25_2022.xlsx` |
| 587 [571] | `supplemental_reports/absentee_ballots_20221027.xlsx` | `from_full_pia/supplemental_reports/absentee_ballots_20221027.xlsx` |
| 597 [581] | `Press Reports-selected/2022/GG22/10-27-2022/Absentees Sent and Returned by County_10_27_2022.xlsx` | `from_full_pia/10-27-2022/Absentees Sent and Returned by County_10_27_2022.xlsx` |
| 607 [591] | `Press Reports-selected/2022/GG22/10-28-2022/Absentees Sent and Returned by County.xlsx` | `from_full_pia/10-28-2022/Absentees Sent and Returned by County.xlsx` |
| 617 [601] | `Press Reports-selected/2022/GG22/10-29-2022/Absentees Sent and Returned by County.xlsx` | `from_full_pia/10-29-2022/Absentees Sent and Returned by County.xlsx` |
| 627 [611] | `Press Reports-selected/2022/GG22/10-30-2022/Absentees Sent and Returned by County.xlsx` | `from_full_pia/10-30-2022/Absentees Sent and Returned by County.xlsx` |
| 637 [621] | `Press Reports-selected/2022/GG22/10-31-2022/Absentees Sent and Returned by County.xlsx` | `from_full_pia/10-31-2022/Absentees Sent and Returned by County.xlsx` |
| 647 [631] | `Press Reports-selected/2022/GG22/11-1-2022/Absentees Sent and Returned by County.xlsx` | `from_full_pia/11-1-2022/Absentees Sent and Returned by County.xlsx` |
| 657 [641] | `Press Reports-selected/2022/GG22/11-2-2022/Absentees Sent and Returned by County.xlsx` | `from_full_pia/11-2-2022/Absentees Sent and Returned by County.xlsx` |
| 667 [651] | `Press Reports-selected/2022/GG22/11-3-2022/Absentees Sent and Returned by County.xlsx` | `from_full_pia/11-3-2022/Absentees Sent and Returned by County.xlsx` |
| 717 [661] | `Press Reports-selected/2024/PG24/10212024/Absentees Sent and Returned by County.xlsx` | `from_full_pia/10212024/Absentees Sent and Returned by County.xlsx` |
| 727 [671] | `Press Reports-selected/2024/PG24/10222024/Absentees Sent and Returned by County.xlsx` | `from_full_pia/10222024/Absentees Sent and Returned by County.xlsx` |
| 737 [681] | `Press Reports-selected/2024/PG24/10232024/Absentees Sent and Returned by County.xlsx` | `from_full_pia/10232024/Absentees Sent and Returned by County.xlsx` |
| 747 [691] | `Press Reports-selected/2024/PG24/10242024/Absentees Sent and Returned by County.xlsx` | `from_full_pia/10242024/Absentees Sent and Returned by County.xlsx` |
| 757 [701] | `Press Reports-selected/2024/PG24/EV_SDR_Start_10252024/Absentees Sent and Returned by County.xlsx` | `from_full_pia/EV_SDR_Start_10252024/Absentees Sent and Returned by County.xlsx` |
| 767 [711] | `Press Reports-selected/2024/PG24/10262024/Absentees Sent and Returned by County.xlsx` | `from_full_pia/10262024/Absentees Sent and Returned by County.xlsx` |
| 777 [721] | `Press Reports-selected/2024/PG24/10272024/Absentees Sent and Returned by County.xlsx` | `from_full_pia/10272024/Absentees Sent and Returned by County.xlsx` |
| 787 [731] | `Press Reports-selected/2024/PG24/10282024/Absentees Sent and Returned by County.xlsx` | `from_full_pia/10282024/Absentees Sent and Returned by County.xlsx` |
| 797 [741] | `Press Reports-selected/2024/PG24/10292024/Absentees Sent and Returned by County.xlsx` | `from_full_pia/10292024/Absentees Sent and Returned by County.xlsx` |
| 807 [751] | `Press Reports-selected/2024/PG24/10302024/Absentees Sent and Returned by County.xlsx` | `from_full_pia/10302024/Absentees Sent and Returned by County.xlsx` |
| 817 [761] | `Press Reports-selected/2024/PG24/10312024/Absentees Sent and Returned by County.xlsx` | `from_full_pia/10312024/Absentees Sent and Returned by County.xlsx` |
| 827 [771] | `Press Reports-selected/2024/PG24/EV_SDR_End_11012024/Absentees Sent and Returned by County.xlsx` | `from_full_pia/EV_SDR_End_11012024/Absentees Sent and Returned by County.xlsx` |
| 877 [781] | `Press Reports-selected/2026/GG26/10192026/Absentees_Sent_and_Returned_by_County.xlsx` | `from_full_pia/10192026/Absentees_Sent_and_Returned_by_County.xlsx` |
| 887 [791] | `Press Reports-selected/2026/GG26/10202026/Absentees_Sent_and_Returned_by_County.xlsx` | `from_full_pia/10202026/Absentees_Sent_and_Returned_by_County.xlsx` |
| 897 [801] | `Press Reports-selected/2026/GG26/10212026/Absentees_Sent_and_Returned_by_County.xlsx` | `from_full_pia/10212026/Absentees_Sent_and_Returned_by_County.xlsx` |
| 907 [811] | `Press Reports-selected/2026/GG26/10222026/Absentees_Sent_and_Returned_by_County.xlsx` | `from_full_pia/10222026/Absentees_Sent_and_Returned_by_County.xlsx` |
| 917 [821] | `Press Reports-selected/2026/GG26/10232026/Absentees_Sent_and_Returned_by_County.xlsx` | `from_full_pia/10232026/Absentees_Sent_and_Returned_by_County.xlsx` |
| 927 [831] | `Press Reports-selected/2026/GG26/10242026/Absentees_Sent_and_Returned_by_County.xlsx` | `from_full_pia/10242026/Absentees_Sent_and_Returned_by_County.xlsx` |
| 937 [841] | `Press Reports-selected/2026/GG26/10252026/Absentees_Sent_and_Returned_by_County.xlsx` | `from_full_pia/10252026/Absentees_Sent_and_Returned_by_County.xlsx` |
| 947 [851] | `Press Reports-selected/2026/GG26/10262026/Absentees_Sent_and_Returned_by_County.xlsx` | `from_full_pia/10262026/Absentees_Sent_and_Returned_by_County.xlsx` |
| 957 [861] | `Press Reports-selected/2026/GG26/10272026/Absentees_Sent_and_Returned_by_County.xlsx` | `from_full_pia/10272026/Absentees_Sent_and_Returned_by_County.xlsx` |
| 967 [871] | `direct-download/oct_28_2.14pm/Absentees_Sent_and_Returned_by_County(4).xlsx` | `from_full_pia/oct_28_2.14pm/Absentees_Sent_and_Returned_by_County(4).xlsx` |
| 1287 [1112] | `supplemental_reports/absentee_ballots_20221027.xlsx` | `from_full_pia/supplemental_reports/absentee_ballots_20221027.xlsx` |
| 1288 [1113] | `Press Reports-selected/2026/GG26/10222026/Absentees_Sent_and_Returned_by_County.xlsx` | `from_full_pia/10222026/Absentees_Sent_and_Returned_by_County.xlsx` |

## 4. Time domain graphic: the added 2022 and 2024 reports

**Line 676–715** [left: none, added]: New: the extra 2022 or 2024 reports for 4 to 1 days before Election Day: the same code as the blocks above, pointed at the copies in from_full_pia/.

Added:
```r
# 2022: as of Nov. 4, 4 days out
raw <- read_excel("from_full_pia/11-4-2022/Absentees Sent and Returned by County.xlsx", col_names = FALSE)
top_text <- unlist(raw[1:5, ])
mail_2022_11_04 <- raw |>
  slice(6:31) |> remove_empty("cols") |> row_to_names(row_number = 1) |> clean_names() |>
  filter(county_name == "Total") |>
  select(-ends_with("_sent")) |>
  mutate(as_of = mdy(str_extract(str_subset(top_text, "^As of:"), "[A-Z][a-z]+ \\d+, \\d{4}")),
         year = as.numeric(str_extract(str_subset(top_text, "^Election:"), "\\d{4}")))

# 2022: as of Nov. 5, 3 days out
raw <- read_excel("from_full_pia/11-5-2022/Absentees Sent and Returned by County.xlsx", col_names = FALSE)
top_text <- unlist(raw[1:5, ])
mail_2022_11_05 <- raw |>
  slice(6:31) |> remove_empty("cols") |> row_to_names(row_number = 1) |> clean_names() |>
  filter(county_name == "Total") |>
  select(-ends_with("_sent")) |>
  mutate(as_of = mdy(str_extract(str_subset(top_text, "^As of:"), "[A-Z][a-z]+ \\d+, \\d{4}")),
         year = as.numeric(str_extract(str_subset(top_text, "^Election:"), "\\d{4}")))

# 2022: as of Nov. 6, 2 days out
raw <- read_excel("from_full_pia/11-6-2022/Absentees Sent and Returned by County.xlsx", col_names = FALSE)
top_text <- unlist(raw[1:5, ])
mail_2022_11_06 <- raw |>
  slice(6:31) |> remove_empty("cols") |> row_to_names(row_number = 1) |> clean_names() |>
  filter(county_name == "Total") |>
  select(-ends_with("_sent")) |>
  mutate(as_of = mdy(str_extract(str_subset(top_text, "^As of:"), "[A-Z][a-z]+ \\d+, \\d{4}")),
         year = as.numeric(str_extract(str_subset(top_text, "^Election:"), "\\d{4}")))

# 2022: as of Nov. 7, 1 days out
raw <- read_excel("from_full_pia/11-7-2022/Absentees Sent and Returned by County.xlsx", col_names = FALSE)
top_text <- unlist(raw[1:5, ])
mail_2022_11_07 <- raw |>
  slice(6:31) |> remove_empty("cols") |> row_to_names(row_number = 1) |> clean_names() |>
  filter(county_name == "Total") |>
  select(-ends_with("_sent")) |>
  mutate(as_of = mdy(str_extract(str_subset(top_text, "^As of:"), "[A-Z][a-z]+ \\d+, \\d{4}")),
         year = as.numeric(str_extract(str_subset(top_text, "^Election:"), "\\d{4}")))

```

**Line 836–875** [left: none, added]: New: the extra 2022 or 2024 reports for 4 to 1 days before Election Day: the same code as the blocks above, pointed at the copies in from_full_pia/.

Added:
```r
# 2024: as of Nov. 1, 4 days out
raw <- read_excel("from_full_pia/11022024/Absentees Sent and Returned by County.xlsx", col_names = FALSE)
top_text <- unlist(raw[1:5, ])
mail_2024_11_01 <- raw |>
  slice(6:31) |> remove_empty("cols") |> row_to_names(row_number = 1) |> clean_names() |>
  filter(county_name == "Total") |>
  select(-ends_with("_sent")) |>
  mutate(as_of = mdy(str_extract(str_subset(top_text, "^As of:"), "[A-Z][a-z]+ \\d+, \\d{4}")),
         year = as.numeric(str_extract(str_subset(top_text, "^Election:"), "\\d{4}")))

# 2024: as of Nov. 2, 3 days out
raw <- read_excel("from_full_pia/11032024/Absentees Sent and Returned by County.xlsx", col_names = FALSE)
top_text <- unlist(raw[1:5, ])
mail_2024_11_02 <- raw |>
  slice(6:31) |> remove_empty("cols") |> row_to_names(row_number = 1) |> clean_names() |>
  filter(county_name == "Total") |>
  select(-ends_with("_sent")) |>
  mutate(as_of = mdy(str_extract(str_subset(top_text, "^As of:"), "[A-Z][a-z]+ \\d+, \\d{4}")),
         year = as.numeric(str_extract(str_subset(top_text, "^Election:"), "\\d{4}")))

# 2024: as of Nov. 3, 2 days out
raw <- read_excel("from_full_pia/11042024/Absentees Sent and Returned by County.xlsx", col_names = FALSE)
top_text <- unlist(raw[1:5, ])
mail_2024_11_03 <- raw |>
  slice(6:31) |> remove_empty("cols") |> row_to_names(row_number = 1) |> clean_names() |>
  filter(county_name == "Total") |>
  select(-ends_with("_sent")) |>
  mutate(as_of = mdy(str_extract(str_subset(top_text, "^As of:"), "[A-Z][a-z]+ \\d+, \\d{4}")),
         year = as.numeric(str_extract(str_subset(top_text, "^Election:"), "\\d{4}")))

# 2024: as of Nov. 4, 1 days out
raw <- read_excel("from_full_pia/11052024/Absentees Sent and Returned by County.xlsx", col_names = FALSE)
top_text <- unlist(raw[1:5, ])
mail_2024_11_04 <- raw |>
  slice(6:31) |> remove_empty("cols") |> row_to_names(row_number = 1) |> clean_names() |>
  filter(county_name == "Total") |>
  select(-ends_with("_sent")) |>
  mutate(as_of = mdy(str_extract(str_subset(top_text, "^As of:"), "[A-Z][a-z]+ \\d+, \\d{4}")),
         year = as.numeric(str_extract(str_subset(top_text, "^Election:"), "\\d{4}")))

```

## 5. Time domain graphic: 2026's last six days, from Skipjack

**Line 970–1029** [left: none, added]: New: the 2026 reports for Oct. 28 to Nov. 2 (6 to 1 days out). Each block is a copy of the 2026 blocks above, line for line; only the comment, the file (Skipjack's archived copy of the same SBE spreadsheet, in skipjack_download/) and the table's name change.

Added:
```r
  slice(6:31) |> remove_empty("cols") |> row_to_names(row_number = 1) |> clean_names() |>
  filter(county_name == "Total") |>
  select(-ends_with("_sent")) |>
  mutate(as_of = mdy(str_extract(str_subset(top_text, "^As of:"), "[A-Z][a-z]+ \\d+, \\d{4}")),
         year = as.numeric(str_extract(str_subset(top_text, "^Election:"), "\\d{4}")))

# 2026: as of Oct. 28, 6 days out (Skipjack's archived copy of the SBE report)
raw <- read_excel("skipjack_download/sent-returned__county__2026-10-28__b8a3e21aaafe.xlsx", col_names = FALSE)
top_text <- unlist(raw[1:5, ])
mail_2026_10_28 <- raw |>
  slice(6:31) |> remove_empty("cols") |> row_to_names(row_number = 1) |> clean_names() |>
  filter(county_name == "Total") |>
  select(-ends_with("_sent")) |>
  mutate(as_of = mdy(str_extract(str_subset(top_text, "^As of:"), "[A-Z][a-z]+ \\d+, \\d{4}")),
         year = as.numeric(str_extract(str_subset(top_text, "^Election:"), "\\d{4}")))

# 2026: as of Oct. 29, 5 days out (Skipjack's archived copy of the SBE report)
raw <- read_excel("skipjack_download/sent-returned__county__2026-10-29__0171eadb07d0.xlsx", col_names = FALSE)
top_text <- unlist(raw[1:5, ])
mail_2026_10_29 <- raw |>
  slice(6:31) |> remove_empty("cols") |> row_to_names(row_number = 1) |> clean_names() |>
  filter(county_name == "Total") |>
  select(-ends_with("_sent")) |>
  mutate(as_of = mdy(str_extract(str_subset(top_text, "^As of:"), "[A-Z][a-z]+ \\d+, \\d{4}")),
         year = as.numeric(str_extract(str_subset(top_text, "^Election:"), "\\d{4}")))

# 2026: as of Oct. 30, 4 days out (Skipjack's archived copy of the SBE report)
raw <- read_excel("skipjack_download/sent-returned__county__2026-10-30__49c81568d2d1.xlsx", col_names = FALSE)
top_text <- unlist(raw[1:5, ])
mail_2026_10_30 <- raw |>
  slice(6:31) |> remove_empty("cols") |> row_to_names(row_number = 1) |> clean_names() |>
  filter(county_name == "Total") |>
  select(-ends_with("_sent")) |>
  mutate(as_of = mdy(str_extract(str_subset(top_text, "^As of:"), "[A-Z][a-z]+ \\d+, \\d{4}")),
         year = as.numeric(str_extract(str_subset(top_text, "^Election:"), "\\d{4}")))

# 2026: as of Oct. 31, 3 days out (Skipjack's archived copy of the SBE report)
raw <- read_excel("skipjack_download/sent-returned__county__2026-10-31__3fd1c0e5ec54.xlsx", col_names = FALSE)
top_text <- unlist(raw[1:5, ])
mail_2026_10_31 <- raw |>
  slice(6:31) |> remove_empty("cols") |> row_to_names(row_number = 1) |> clean_names() |>
  filter(county_name == "Total") |>
  select(-ends_with("_sent")) |>
  mutate(as_of = mdy(str_extract(str_subset(top_text, "^As of:"), "[A-Z][a-z]+ \\d+, \\d{4}")),
         year = as.numeric(str_extract(str_subset(top_text, "^Election:"), "\\d{4}")))

# 2026: as of Nov. 1, 2 days out (Skipjack's archived copy of the SBE report)
raw <- read_excel("skipjack_download/sent-returned__county__2026-11-01__e83bd308203c.xlsx", col_names = FALSE)
top_text <- unlist(raw[1:5, ])
mail_2026_11_01 <- raw |>
  slice(6:31) |> remove_empty("cols") |> row_to_names(row_number = 1) |> clean_names() |>
  filter(county_name == "Total") |>
  select(-ends_with("_sent")) |>
  mutate(as_of = mdy(str_extract(str_subset(top_text, "^As of:"), "[A-Z][a-z]+ \\d+, \\d{4}")),
         year = as.numeric(str_extract(str_subset(top_text, "^Election:"), "\\d{4}")))

# 2026: as of Nov. 2, 1 day out (Skipjack's archived copy of the SBE report)
raw <- read_excel("skipjack_download/sent-returned__county__2026-11-02__1a7fa11333ab.xlsx", col_names = FALSE)
top_text <- unlist(raw[1:5, ])
mail_2026_11_02 <- raw |>
```

## 6. Time domain graphic: everything else that changed for 16 to 1 days out

**Line 538** [left: 523]: Comment: the time domain graphic now runs 16 to 1 days out.

Was:
```r
# ---- Mail-in: one "Absentees Sent and Returned by County" report per day, 16 to 5 days before Election Day ----
```
Now:
```r
# ---- Mail-in: one "Absentees Sent and Returned by County" report per day, 16 to 1 days before Election Day ----
```

**Line 541** [left: 526]: Comment: 2026's last six days now come from Skipjack's archived copies of the SBE reports.

Was:
```r
# No 2026 reports yet for 6 and 5 days out (Oct. 28 and 29).
```
Now:
```r
# 2026, 6 to 1 days out (Oct. 28 to Nov. 2): the same SBE report, from Skipjack's archive (skipjack_download/, github.com/NewsAppsUMD/skipjack archives/sbe/campaign_stats/GG26), after the 2026 PIA reports below.
```

**Line 544** [left: none, added]: Comment added under your note: the graphic now goes to the night before Election Day, and the early in-person total stays at its final number after early voting ends.

Added:
```r
# Election Day update: now runs on to the night before Election Day (1 day out); after 5 days out the early in-person total stays at its final, all-8-days number.
```

**Line 1038** [left: 882]: Row count: 48 rows now (16 days a year, 16 to 1 days out), was 34.

Was:
```r
# Stack all 34 Total rows into one table
```
Now:
```r
# Stack all 48 Total rows into one table (16 days for each year: 16 to 1 days out)
```

**Line 1052–1055** [left: none, added]: The new days added to the stack of daily Total rows.

Added:
```r
  mail_2022_11_04,
  mail_2022_11_05,
  mail_2022_11_06,
  mail_2022_11_07,
```

**Line 1068–1071** [left: none, added]: The new days added to the stack of daily Total rows.

Added:
```r
  mail_2024_11_01,
  mail_2024_11_02,
  mail_2024_11_03,
  mail_2024_11_04,
```

**Line 1081–1087** [left: 917]: The new days added to the stack of daily Total rows.

Was:
```r
  mail_2026_10_27) |>
```
Now:
```r
  mail_2026_10_27,
  mail_2026_10_28,
  mail_2026_10_29,
  mail_2026_10_30,
  mail_2026_10_31,
  mail_2026_11_01,
  mail_2026_11_02) |>
```

**Line 1094** [left: none, added]: Your Oct. 29 note is kept; the added line says it covered only the original 34 rows.

Added:
```r
# (that check covered the original 34 rows, 16 to 5 days out; the 14 added rows for 4 to 1 days out haven't been hand validated yet)
```

**Line 1169** [left: 998]: Comment: the time domain graphic now runs 16 to 1 days out.

Was:
```r
daily <- mail_daily |>                                                                      # start from mail-in: it has every day, 16 to 5 days out
```
Now:
```r
daily <- mail_daily |>                                                                      # start from mail-in: it has every day, 16 to 1 days out
```

**Line 1171–1174** [left: none, added]: After early voting ends (4 to 1 days out) there's no new early in-person number, so the final total is carried forward instead of turning into 0.

Added:
```r
  group_by(year) |>                                                                         # within each year,
  arrange(desc(days_out), .by_group = TRUE) |>                                              #   from 16 days out down to 1,
  fill(early, .direction = "down") |>                                                       #   4-1 days out: early voting is over, so carry its final total forward
  ungroup() |>
```

**Line 1186** [left: 1011]: Comment: the time domain graphic now runs 16 to 1 days out.

Was:
```r
  pivot_wider(id_cols = days_out,                                   # one row per day (16 to 5 days out)
```
Now:
```r
  pivot_wider(id_cols = days_out,                                   # one row per day (16 to 1 days out)
```

**Line 1206** [left: 1031]: Comment removed: 2026 has every day now.

Was:
```r
         date_2026 = str_c(format(as_of_2026, "%b."), " ", day(as_of_2026), ", ", year(as_of_2026)),    # blank for 6 and 5 days out (no 2026 reports yet)
```
Now:
```r
         date_2026 = str_c(format(as_of_2026, "%b."), " ", day(as_of_2026), ", ", year(as_of_2026)),
```

**Line 1246** [left: 1071]: "Early voting day" stays at 8 for 4 to 1 days out (without this it would count on to 9, 10, 11, 12).

Was:
```r
            `Early voting day` = if_else(days_out <= 12, 13 - days_out, NA),          # 12 days out = day 1 ... 5 days out = day 8
```
Now:
```r
            `Early voting day` = if_else(days_out <= 12, pmin(13 - days_out, 8), NA), # 12 days out = day 1 ... 5 days out = day 8; 4-1 days out stay at 8 (it's over)
```

**Line 1254** [left: 1079]: Comment: the time domain graphic now runs 16 to 1 days out.

Was:
```r
# Stack them (Mail-in, then Early in-person, then Combined, each from 16 down to 5 days out), attach the shared columns,
```
Now:
```r
# Stack them (Mail-in, then Early in-person, then Combined, each from 16 down to 1 days out), attach the shared columns,
```

## 7. The new last chunk: the D3 charts

**Line 1305–1322** [left: none, added]: New last chunk: writes graphic 7's and graphic 9's tables into the two D3 chart files in this folder (the original story did this step outside R).

Added:
```r

```{r}
# ---- Election Day update: put the new numbers into the two D3 charts in this folder ----
# Each D3 page keeps its data inline, between <script type="application/json" id="chart-data"> and </script>.
# This swaps that block for the two Flourish tables above (graphic 7 -> table_1, graphic 9 -> section_5); open the charts afterward to check them.
inject <- \(html_file, table) {
  page <- read_file(html_file)
  start_tag <- "<script type=\"application/json\" id=\"chart-data\">"
  before <- str_split_1(page, fixed(start_tag))                  # [1] everything before the data, [2] the data and everything after
  after <- str_split_1(before[2], fixed("</script>"))            # [1] the old data, [2...] everything after it
  rows <- table |> mutate(across(everything(), \(x) if_else(is.na(x), "", as.character(x))))   # every value as text, blanks for NA
  json <- toJSON(rows, pretty = TRUE) |> str_replace_all(fixed("</"), "<\\/")                 # "<\/" so the HTML in the popups can't end the script early
  write_file(str_c(before[1], start_tag, "\n", json, "\n</script>", str_c(after[-1], collapse = "</script>")), html_file)
}
inject("table_1_stacked_bars_d3.html", voting_methods_flourish)
inject("section_5_districts_stacked_bars_d3.html", in_person_congressional_flourish)
```

```
