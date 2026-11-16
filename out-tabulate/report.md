# Tech Debt Report: tabulate

## Metric definitions
- **Complexity**: Radon cyclomatic complexity per function (A=1-5, B=6-10, C=11-20, D=21-30, E=31-40, F=41+).
- **Function Length**: Physical lines of code from function definition to endline.
- **Size (SLOC)**: Source lines of code (excluding blanks and comments) per file.
- **Maintainability Index (MI)**: 0-100 composite score based on Halstead volume, CC, and SLOC (A: 20-100, B: 10-19, C: 0-9).
- **Import Coupling**: Count of distinct external/internal modules imported (higher = more coupled).
- **Duplication**: Repeated blocks of normalized consecutive lines across the codebase.
- **Hotspot score**: max-complexity rank + size rank per file (lower score = higher investigation priority).
- **Excluded paths**: test, tests, testing, docs, .github, .venv, venv, examples, locale.

## Complexity distribution
| Rank | Functions |
| --- | --- |
| A | 56 |
| B | 9 |
| C | 6 |
| D | 1 |
| E | 2 |
| F | 2 |

### Top 10 functions by complexity
| Function | File:Line | CC | Rank | Length (LOC) |
| --- | --- | --- | --- | --- |
| `_normalize_tabular_data` | __init__.py:1428 | 76 | F | 186 |
| `tabulate` | __init__.py:1696 | 62 | F | 766 |
| `_CustomTextWrap._wrap_chunks` | __init__.py:2792 | 31 | E | 103 |
| `_main` | cli.py:31 | 31 | E | 147 |
| `_format_table` | __init__.py:2612 | 26 | D | 76 |
| `_format` | __init__.py:1302 | 20 | C | 57 |
| `_type` | __init__.py:961 | 18 | C | 48 |
| `_align_column` | __init__.py:1207 | 18 | C | 46 |
| `_align_column_choose_padfn` | __init__.py:1150 | 15 | C | 24 |
| `_wrap_text_to_colwidths` | __init__.py:1616 | 12 | C | 53 |

### Five longest functions
| Function | File:Line | Length (LOC) | CC | Rank |
| --- | --- | --- | --- | --- |
| `tabulate` | __init__.py:1696 | 766 | 62 | F |
| `_CustomTextWrap` | __init__.py:2690 | 205 | 11 | C |
| `_normalize_tabular_data` | __init__.py:1428 | 186 | 76 | F |
| `_main` | cli.py:31 | 147 | 31 | E |
| `_CustomTextWrap._wrap_chunks` | __init__.py:2792 | 103 | 31 | E |

## Hotspots (complex and large files)
| File | Max CC | SLOC | MI | Imports | Score |
| --- | --- | --- | --- | --- | --- |
| __init__.py | 76 | 1639 | 0.0 (C) | 15 | 2 |
| cli.py | 31 | 157 | 57.81 (A) | 9 | 4 |
| __main__.py | 0 | 2 | 100.0 (A) | 1 | 6 |

## Smells: self-admitted debt (2 found in 1 files)

### __init__.py (2 notes)
- Line 748 `[TODO]`: `# TODO: Add multiline support for the remaining table formats:`
- Line 1224 `[TODO]`: `# TODO: refactor column alignment in single-line and multiline modes`

## Code Duplication (45 duplicate patterns detected)

#### Duplicate #1 (8 occurrences)
- __init__.py:388-391
- __init__.py:398-401
- __init__.py:418-421
- __init__.py:438-441
- __init__.py:468-471
- __init__.py:478-481
- __init__.py:498-501
- __init__.py:518-521

#### Duplicate #2 (8 occurrences)
- __init__.py:389-392
- __init__.py:399-402
- __init__.py:419-422
- __init__.py:439-442
- __init__.py:469-472
- __init__.py:479-482
- __init__.py:499-502
- __init__.py:519-522

#### Duplicate #3 (7 occurrences)
- __init__.py:379-382
- __init__.py:449-452
- __init__.py:459-462
- __init__.py:539-542
- __init__.py:549-552
- __init__.py:569-572
- __init__.py:579-582

#### Duplicate #4 (6 occurrences)
- __init__.py:378-381
- __init__.py:448-451
- __init__.py:458-461
- __init__.py:538-541
- __init__.py:568-571
- __init__.py:578-581

#### Duplicate #5 (5 occurrences)
- __init__.py:364-367
- __init__.py:544-547
- __init__.py:609-612
- __init__.py:679-682
- __init__.py:689-692

## What to investigate first
1. **Primary Hotspot**: Which file and function represent the highest immediate risk?
2. **Maintainability & Coupling**: Are the complex files also tightly coupled or poorly rated in MI?
3. **Smells & Duplication**: Do known debt comments align with the highest-risk hotspots?
