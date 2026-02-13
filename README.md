# 🎬 Movie Recommendation System

> A production-ready, AI-powered movie recommendation system built with Django and advanced machine learning. Scalable from thousands to millions of movies.

[![Python](https://img.shields.io/badge/Python-3.11+-blue.svg)](https://www.python.org/)
[![Django](https://img.shields.io/badge/Django-6.0-green.svg)](https://djangoproject.com/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

![Logo Image](./assets/images-for-readme/Logo.png)

---

## 📑 Table of Contents

- [Overview](#-overview)
- [Screenshots](#-screenshots)
- [Features](#-features)
- [Quick Start](#-quick-start)
- [Project Structure](#-project-structure)
- [Usage](#-usage)
- [Model Training](#-model-training)
- [API Reference](#-api-reference)
- [Configuration](#-configuration)
- [Documentation](#-documentation)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🎯 Overview

The Movie Recommendation System provides intelligent movie suggestions using **content-based filtering** with TF-IDF and SVD dimensionality reduction. It features a modern web interface, RESTful API, and supports datasets from 2K to 1M+ movies.


### Why This Project?

- ✅ **Production Ready** - Security hardened, optimized, well-documented
- ✅ **Scalable Architecture** - Handles millions of movies efficiently
- ✅ **Modern Tech Stack** - Django 5.0, Python 3.10+, advanced ML
- ✅ **Easy to Use** - Simple installation, clear documentation
- ✅ **Flexible** - Train your own models or use demo models

### Key Technologies

- **Backend**: Django 6.0, Python 3.10+
- **ML/Data**: scikit-learn, pandas, numpy, scipy
- **Storage**: Parquet (efficient data format)
- **Deployment**: Render, Heroku, Docker compatible


## ✨ Features

### User Features
- 🔍 **Smart Search** - Real-time autocomplete with fuzzy matching
- 🎬 **AI Recommendations** - Content-based filtering with 15+ suggestions
- ⭐ **Rich Metadata** - Ratings, votes, genres, production companies
- 🔗 **External Links** - Google Search and IMDb integration
- 📱 **Responsive Design** - Works seamlessly on all devices
- ⚡ **Fast Performance** - Sub-50ms recommendation generation

### Technical Features
- 🤖 **Advanced ML** - TF-IDF + SVD dimensionality reduction
- 📊 **Scalable** - Handles 2K to 1M+ movies
- 💾 **Efficient Storage** - Parquet format with compression
- 🔧 **Configurable** - Easy model switching via `MODEL_DIR`
- 📡 **REST API** - JSON endpoints for integration
- 🔒 **Secure** - Production-ready security settings
- 📝 **Logging** - Comprehensive error tracking
- 🚀 **Deployment Ready** - Render, Heroku, Docker configs included

---

## 🚀 Quick Start

### Prerequisites

- Python 3.10 or higher
- pip package manager
- 8GB RAM (recommended for training)
- Git

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/yourusername/movie-recommendation-system.git
cd movie-recommendation-system

# 2. Create virtual environment
python -m venv venv

# 3. Activate virtual environment
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

# 4. Install dependencies
pip install -r requirements.txt

# 5. Run database migrations
python manage.py migrate

# 6. Start the development server
python manage.py runserver
```

### Access the Application

Open your browser and navigate to:
```
http://localhost:8000
```

That's it! The demo model (2K movies) is included and works out of the box. 🎉

---

## 📁 Project Structure

```
movie-recommendation-system/
│
├── 📚 Documentation
│   ├── README.md                  # This file - overview and quick start
│   ├── PROJECT_GUIDE.md           # Complete technical guide
│   └── CHANGELOG.md               # Version history and changes
│
├── ⚙️ Django Application
│   ├── movie_recommendation/      # Django project settings
│   │   ├── settings.py           # Configuration
│   │   ├── urls.py               # URL routing
│   │   └── wsgi.py               # WSGI entry point
│   │
│   ├── recommender/              # Main application
│   │   ├── views.py              # Recommendation logic
│   │   ├── urls.py               # App URLs
│   │   └── templates/            # HTML templates
│   │       └── recommender/
│   │           ├── index.html    # Search page
│   │           ├── result.html   # Results page
│   │           └── error.html    # Error page
│   │
│   ├── manage.py                 # Django management script
│   └── requirements.txt          # Python dependencies
│
├── 🎓 Model Training
│   └── training/
│       ├── train.py              # Training pipeline
│       ├── infer.py              # Inference examples
│       └── guide.md              # Training documentation
│
├── 🎯 Models (Created after training)
│   └── models/
│       ├── movie_metadata.parquet    # Movie information
│       ├── similarity_matrix.npz     # Similarity scores
│       ├── title_to_idx.json         # Title mappings
│       ├── tfidf_vectorizer.pkl      # TF-IDF model
│       └── svd_model.pkl             # SVD reduction model
│
├── 📦 Static Files
│   └── static/
│       ├── logo.png                  # Application logo
│       ├── demo_model.parquet        # Demo similarity model (2K)
│       └── top_2k_movie_data.parquet # Demo movie data (2K)
│
└── 🚀 Deployment
    ├── Procfile                  # Heroku configuration
    ├── render.yaml               # Render configuration
    └── .gitignore                # Git ignore rules
```

---

## 💡 Usage

### Web Interface

1. **Search for a Movie**
   - Go to `http://localhost:8000`
   - Start typing a movie name in the search box
   - Select from autocomplete suggestions or type the full name

2. **View Recommendations**
   - Click "Get Recommendations"
   - Browse 15 similar movie suggestions
   - Each card shows: rating, release date, genres, production company

3. **Explore Movies**
   - Click "Google" to search for the movie
   - Click "IMDb" to view on IMDb (if available)

### API Usage

#### Search Movies (Autocomplete)
```bash
GET /api/search/?q=matrix

Response:
{
  "movies": ["The Matrix", "The Matrix Reloaded", "The Matrix Revolutions"],
  "count": 3
}
```

#### Health Check
```bash
GET /api/health/

Response:
{
  "status": "healthy",
  "movies_loaded": 100000,
  "model_dir": "./models",
  "model_loaded": true
}
```

---

## 🎓 Model Training

### Using Demo Model

The project includes a pre-trained demo model with 2,000 popular movies. No training needed!

```bash
# Demo model is in static/ directory
export MODEL_DIR=./static
python manage.py runserver
```

### Training Your Own Model

Want to train on more movies or your own dataset? See the [**Training Guide**](training/guide.md) for:

- 📖 Complete training documentation
- 🎯 Configuration options (10K to 1M+ movies)
- ⚙️ Performance tuning guidelines
- 📊 Dataset requirements
- 🔧 Advanced features

**Quick Training Example:**

```python
from training.train import MovieRecommenderTrainer

# Initialize trainer
trainer = MovieRecommenderTrainer(
    output_dir='./models',
    use_dimensionality_reduction=True,
    n_components=500
)

# Train on your dataset
df, sim_matrix = trainer.train(
    'path/to/your/dataset.csv',
    quality_threshold='medium',  # low/medium/high
    max_movies=100000            # Limit dataset size
)
```

**For detailed training instructions**, see:
- 📘 [Training Guide](training/guide.md) - Complete training documentation
- 📘 [PROJECT_GUIDE.md](PROJECT_GUIDE.md#-model-training) - Training setup and configurations

---

## 📡 API Reference

### Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/` | GET | Home page with search interface |
| `/` | POST | Submit movie search and get recommendations |
| `/api/search/` | GET | Search movies (autocomplete) |
| `/api/health/` | GET | Health check endpoint |

### Search Movies

**Request:**
```http
GET /api/search/?q=inception
```

**Response:**
```json
{
  "movies": ["Inception", "Inception: The Cobol Job"],
  "count": 2
}
```

### Health Check

**Request:**
```http
GET /api/health/
```

**Response:**
```json
{
  "status": "healthy",
  "movies_loaded": 100000,
  "model_dir": "./models",
  "model_loaded": true
}
```

</div>

