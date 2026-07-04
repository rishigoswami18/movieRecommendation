# Movie Recommendation

A movie recommendation app with a `FastAPI` backend and a `Streamlit` frontend.

## Features

- Search movies by title
- View trending and popular home feeds
- Open movie details with poster, backdrop, overview, and genres
- Get TF-IDF based similar movies
- Get genre-based recommendations
- Uses TMDB for movie metadata and images

## Tech Stack

- `FastAPI`
- `Streamlit`
- `scikit-learn`
- `pandas`
- `numpy`
- `httpx`

## Project Files

- `main.py` ? FastAPI backend
- `app.py` ? Streamlit frontend
- `requirements.txt` ? Python dependencies
- `df.pkl`, `indices.pkl`, `tfidf.pkl`, `tfidf_matrix.pkl` ? recommendation assets

## Setup

### 1. Create and activate a virtual environment

```powershell
python -m venv .venv
.\.venv\Scripts\activate
```

### 2. Install dependencies

```powershell
pip install -r requirements.txt
```

### 3. Configure environment variables

Create a `.env` file:

```env
TMDB_API_KEY=your_tmdb_api_key
API_BASE=http://127.0.0.1:8000
```

## Run Locally

### Start the FastAPI backend

```powershell
uvicorn main:app --reload
```

### Start the Streamlit frontend

Open another terminal and run:

```powershell
streamlit run app.py
```

Then open `http://localhost:8501`.

## API Endpoints

- `GET /health`
- `GET /home?category=trending&limit=24`
- `GET /tmdb/search?query=batman`
- `GET /movie/id/{tmdb_id}`
- `GET /recommend/genre?tmdb_id=603&limit=18`
- `GET /recommend/tfidf?title=Inception&top_n=10`
- `GET /movie/search?query=Inception&tfidf_top_n=12&genre_limit=12`

## Notes

- `.env` is not committed.
- The frontend defaults to the local backend using `API_BASE`.
- TMDB responses are reused and cached to improve speed.
