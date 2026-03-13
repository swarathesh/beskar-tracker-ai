# Beskar Tracker AI

A toolkit for scraping, storing, and semantically searching posts from Beskar Capital (@beskarcapital) on Blossom Social.

## What's Included

| File | Purpose |
|------|---------|
| `crawl_beskar_posts.py` | Scrapes all posts from the Blossom Social API and saves to JSON |
| `export_posts_to_excel.py` | Exports scraped posts to Excel |
| `ingest_to_vectordb.py` | Embeds posts into a local ChromaDB vector database |
| `query_vectordb.py` | Semantic search over the vector database |
| `beskar_posts_scraped.json` | 2,073 scraped posts (source of truth) |
| `KTS_Complete_Guide.md` | All 107 Knowledge Transfer Series (KTS) posts compiled into one document |
| `Beskar_Capital_KTS_Complete_Guide.pdf` | PDF version of the KTS guide |
| `chroma_db/` | Local ChromaDB vector store (persisted embeddings) |

## Setup

```bash
python -m venv venv
source venv/bin/activate
pip install requests pandas chromadb openpyxl
```

## Usage

### 1. Scrape posts
```bash
python crawl_beskar_posts.py
```
Fetches all posts from the Blossom Social API and writes them to `beskar_posts_scraped.json`.

### 2. Export to Excel
```bash
python export_posts_to_excel.py
```
Exports all posts to `beskar_posts.xlsx`.

### 3. Ingest into vector database
```bash
python ingest_to_vectordb.py
```
Embeds each post (title + caption) using local sentence-transformers and stores them in ChromaDB at `./chroma_db`.

### 4. Semantic search
```bash
python query_vectordb.py "real estate cycle"
python query_vectordb.py "RSI divergence"
python query_vectordb.py "options LEAPs"
```
Returns the top 5 most semantically similar posts with relevance scores.

## Knowledge Transfer Series (KTS)

The KTS is Beskar Capital's investment education series. `KTS_Complete_Guide.md` contains all 107 KTS episodes compiled from the scraped data, covering topics including:

- RSI & technical indicators
- Money flow and insider tracking
- Options (LEAPs, Calls, Puts)
- Real estate and banking crisis cycles
- Sector rotation
- Compounding and dividend rights
- Bubble mechanics
