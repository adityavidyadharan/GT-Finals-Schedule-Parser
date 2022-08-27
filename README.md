# GT-Finals-Schedule-Parser
Module to parse the PDF provided by Georgia Tech with the semester's finals schedule.<br>
Provides output as both Pandas `DataFrame` and `CSV`

# Purpose
To parse the [PDFs](https://registrar.gatech.edu/files/202208%20Final%20Exam%20Matrix.pdf) found on the GT Registrar's [website](https://registrar.gatech.edu/files/202208%20Final%20Exam%20Matrix.pdf)

# Usage

```
parser = Parser()
parser.parseFile("202208")
parser.parseCommon()
parser.export(title="Finals Schedule")
schedule = parser.schedule
common = parser.common
```

### parseFile
`parseFile` takes a term number as input and looks it up in `matrix.json` to find the PDF address. It returns a Pandas DataFrame where the index is a MultiIndex consisting of the *Meeting Days* and *Timeslot*

**Example:**
|                          index| finalDate    | finalTime          |
|:------------------------------|:-------------|:-------------------|
| ('TR', '8:00 am - 9:15 am')   | Dec 15, 2022 | 8:00 am - 10:50 am |
| ('T', '8:00 am - 10:45 am')   | Dec 15, 2022 | 8:00 am - 10:50 am |
| ('TWRF', '8:25 am - 9:15 am') | Dec 15, 2022 | 8:00 am - 10:50 am |
| ('TRF', '8:25 am - 9:15 am')  | Dec 15, 2022 | 8:00 am - 10:50 am |
| ('TR', '8:25 am - 9:15 am')   | Dec 15, 2022 | 8:00 am - 10:50 am |

### parseCommon

`parseCommon` will generate a DataFrame with information about courses with the same timeslot for all sections


**Example:**

<br>

| Course    | Date         | Time              |
|:----------|:-------------|:------------------|
| ECE 3710  | Dec 08, 2022 | 6:00 PM - 8:50 PM |
| MATH 1551 | Dec 08, 2022 | 6:00 PM - 8:50 PM |
| MATH 1552 | Dec 08, 2022 | 6:00 PM - 8:50 PM |
| PHYS 2211 | Dec 09, 2022 | 6:00 PM - 8:50 PM |
| PHYS 2212 | Dec 12, 2022 | 6:00 PM - 8:50 PM |
| MATH 1553 | Dec 13, 2022 | 6:00 PM - 8:50 PM |
| MATH 1554 | Dec 13, 2022 | 6:00 PM - 8:50 PM |

### export

`export` will output the main schedule to a csv with name `title`
