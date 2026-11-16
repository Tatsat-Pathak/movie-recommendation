# Movie Recommendation

Content-based movie recommender: type a movie you like, get similar movies back.

Built during the Machine Learning Internship at **Acmegrade (Feb–Apr 2024)**.

## Dataset

**TMDB 5000 Movie Dataset** (`movies.csv`, 4,803 movies)

- Columns used: `genres`, `keywords`, `tagline`, `cast`, `director`
- `movies.csv` is **not committed to git** (23 MB) — download it from Kaggle ([TMDB 5000 Movie Dataset](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)) and place it next to the notebook. It is included in the folder here only so the notebook runs as-is.

## How it works

1. Combine the five text fields of each movie into one string (missing values filled with `''`)
2. `TfidfVectorizer` → TF-IDF matrix of shape **(4803 × 17318)**
3. `cosine_similarity` → **4803 × 4803** similarity matrix
4. Type a movie name; `difflib.get_close_matches` finds the closest title (so typos still work)
5. The 30 most similar movies are printed, most similar first

## Example

Input: `Iron Man` → Iron Man 2, Iron Man 3, Avengers: Age of Ultron, The Avengers, Captain America: Civil War, Captain America: The Winter Soldier, Ant-Man, X-Men, …

There is no accuracy number for this project, and there shouldn't be — a content-based recommender has no ground-truth labels to score against. Quality is judged by whether the suggestions make sense, and for franchise movies they do.

## Run it

```bash
pip install -r requirements.txt
jupyter notebook "Movie Recommendation.ipynb"
```

## Files

- `Movie Recommendation.ipynb` — the recommender (markdown section headers added in cleanup; one-line fix above, code otherwise unchanged)
- `movies.csv` — TMDB 5000 Movie Dataset (git-ignored, see above)
- `requirements.txt` — dependencies
