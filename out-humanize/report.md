# Tech Debt Report: humanize

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
| A | 25 |
| B | 9 |
| C | 2 |
| D | 1 |
| E | 1 |
| F | 0 |

### Top 10 functions by complexity
| Function | File:Line | CC | Rank | Length (LOC) |
| --- | --- | --- | --- | --- |
| `naturaldelta` | time.py:94 | 35 | E | 164 |
| `precisedelta` | time.py:476 | 26 | D | 205 |
| `metric` | number.py:539 | 12 | C | 76 |
| `naturalsize` | filesize.py:39 | 12 | C | 73 |
| `intcomma` | number.py:144 | 10 | B | 61 |
| `clamp` | number.py:461 | 9 | B | 76 |
| `naturalday` | time.py:325 | 8 | B | 36 |
| `intword` | number.py:224 | 7 | B | 76 |
| `_date_and_delta` | time.py:67 | 6 | B | 25 |
| `naturaltime` | time.py:260 | 6 | B | 49 |

### Five longest functions
| Function | File:Line | Length (LOC) | CC | Rank |
| --- | --- | --- | --- | --- |
| `precisedelta` | time.py:476 | 205 | 26 | D |
| `naturaldelta` | time.py:94 | 164 | 35 | E |
| `intword` | number.py:224 | 76 | 7 | B |
| `clamp` | number.py:461 | 76 | 9 | B |
| `metric` | number.py:539 | 76 | 12 | C |

## Hotspots (complex and large files)
| File | Max CC | SLOC | MI | Imports | Score |
| --- | --- | --- | --- | --- | --- |
| time.py | 35 | 353 | 37.39 (A) | 9 | 2 |
| number.py | 12 | 254 | 44.87 (A) | 7 | 4 |
| filesize.py | 12 | 57 | 77.9 (A) | 3 | 6 |
| i18n.py | 6 | 76 | 69.22 (A) | 6 | 6 |
| lists.py | 5 | 16 | 86.58 (A) | 3 | 10 |
| __init__.py | 0 | 52 | 100.0 (A) | 3 | 10 |

## Smells: self-admitted debt (0 found in 0 files)
No self-admitted technical debt comments found.

## Code Duplication (15 duplicate patterns detected)

#### Duplicate #1 (3 occurrences)
- number.py:130-134
- number.py:258-262
- number.py:329-333

#### Duplicate #2 (3 occurrences)
- number.py:131-135
- number.py:259-263
- number.py:330-334

#### Duplicate #3 (3 occurrences)
- number.py:133-136
- number.py:261-264
- number.py:332-335

#### Duplicate #4 (3 occurrences)
- number.py:134-137
- number.py:262-265
- number.py:333-336

#### Duplicate #5 (3 occurrences)
- number.py:135-138
- number.py:263-266
- number.py:334-337

## What to investigate first
1. **Primary Hotspot**: Which file and function represent the highest immediate risk?
2. **Maintainability & Coupling**: Are the complex files also tightly coupled or poorly rated in MI?
3. **Smells & Duplication**: Do known debt comments align with the highest-risk hotspots?
