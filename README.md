# Netflix Content Analysis

Exploratory data analysis of the Netflix catalog using Python (pandas and matplotlib). The project cleans the raw data and answers five questions: what is the content mix, which countries produce the most titles, how have releases changed over time, which genres dominate, and who is the content aimed at.

## Key findings

- **Movies dominate the catalog:** 6,126 Movies (about 70%) vs 2,664 TV Shows (about 30%).
- **The US and India lead production:** together they account for about 50% of titles with a known primary country (3,240 and 1,057 titles), followed by the UK (638) and Pakistan (421).
- **Releases peaked in 2018** with 1,146 titles, then declined. 2021 is likely incomplete because the data ends in 2021.
- **Top genres:** International Movies (2,752), Dramas (2,426) and Comedies (1,674).
- **The catalog skews mature:** TV-MA is the most common rating (3,205 titles, about 36%), followed by TV-14 (2,157).

| Movies vs TV Shows | Top 10 countries |
|---|---|
| ![Content distribution](images/content_distribution.png) | ![Top countries](images/top_countries.png) |

| Releases by year | Top 10 genres |
|---|---|
| ![Releases by year](images/releases_by_year.png) | ![Top genres](images/top_genres.png) |

![Ratings by type](images/ratings_by_type.png)

## Dataset

`data/Netflix.csv` has 8,790 titles and 10 columns.

| Column | Description |
|---|---|
| `show_id` | Unique title ID |
| `type` | Movie or TV Show |
| `title` | Title name |
| `director` | Director (`Not Given` when missing) |
| `country` | Production country or countries (`Not Given` when missing) |
| `date_added` | Date the title was added to Netflix |
| `release_year` | Original release year |
| `rating` | Maturity rating (TV-MA, PG-13, etc.) |
| `duration` | Minutes for movies, seasons for TV shows |
| `listed_in` | Genres / categories |

## Methodology

1. Checked for missing values and duplicate rows (no duplicates found).
2. Converted the `Not Given` placeholder in `country` to `Unknown` so it is not counted as a country.
3. Created `primary country`, `primary rating` and `primary type` columns (first value in each field).
4. Counted titles by type, country, release year, rating and genre (genres are split into one row each).
5. Visualized results and exported the analysis tables.

**Note:** country rankings use each title's *primary* (first listed) country, so co-productions are counted once.

## Project structure

```
netflix-content-analysis/
├── Netflix_Data_Analysis.ipynb   # full analysis
├── data/
│   ├── Netflix.csv               # raw data
│   ├── Netflix_Cleaned.csv       # cleaned data (generated)
│   ├── netflix_by_country.csv    # generated
│   └── netflix_by_genre.csv      # generated
├── images/                       # charts used in this README
├── requirements.txt
├── LICENSE
└── README.md
```

## How to run

```bash
git clone https://github.com/<your-username>/netflix-content-analysis.git
cd netflix-content-analysis
pip install -r requirements.txt
jupyter notebook Netflix_Data_Analysis.ipynb
```

Run all cells from the top. The notebook uses relative paths, so run it from the project root.

## Tools

Python, pandas, matplotlib, Jupyter Notebook

## License

MIT. See [LICENSE](LICENSE).
