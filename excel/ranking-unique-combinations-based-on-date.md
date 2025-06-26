---
created: 2025-06-25
tags:
  - TIL
categories:
  - "[[Excel]]"
---

Say you have a table like below and you want to create a new "Order" column that ranks the unique combinations of "Planet" and "Faction", by date in descending order (newest to oldest). 

| Planet      | Faction    | Date       |
| ----------- | ---------- | ---------- |
| Cyberstan   | Automotons | 2025-02-01 |
| Mog         | Automotons | 2024-05-01 |
| Cyberstan   | Automotons | 2024-08-01 |
| Mog         | Automotons | 2024-11-01 |
| Super Earth | Illuminate | 2023-01-01 |
| Super Earth | Illuminate | 2023-04-01 |
| Alairt III  | Illuminate | 2023-07-01 |
| Super Earth | Illuminate | 2023-10-01 |
| Terrek      | Terminids  | 2025-03-01 |
| Terrek      | Terminids  | 2025-09-01 |
| Slif        | Terminids  | 2025-12-01 |

Assuming the data starts in cell `A1`, the following formula will work:

```excel
=COUNTIFS($A$2:$A$12, A2, $B$2:$B$12, B2, $C$2:$C$12, ">"&C2) + 1
```

- `COUNTIFS` allows you to count cells that meet multiple criteria across different ranges. 
- The first and second conditions check the "Planet" and "Faction" columns for values matching the current row's "Planet" and "Faction" (respectively).
- The third condition counts how many entries in the "Date" column, for the matching "Planet" and "Faction", are greater than (i.e., newer) the date in the current row. 
- The `+ 1` is added because the rest of the formula **only counts entries that are newer**, meaning the newest one would equate to `0`, next-to-newest would be `1`, etc. So the `+ 1` fixes this. 
