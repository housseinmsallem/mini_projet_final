# Information Retrieval System - Project Setup

## Overview

This project implements an information retrieval system with document indexing, vector-based ranking, relevance feedback (Rocchio), and ablation studies on preprocessing techniques.

## Project Initialization

### Prerequisites

- Python 3.8 or higher
- pip (Python package manager)

### Setup Steps

1. **Clone the repository** (if not already done):

   ```bash
   git clone <repository-url>
   cd mini_projet_final
   ```

2. **Create a virtual environment** (recommended):

   ```bash
   python -m venv venv
   # On Windows:
   venv\Scripts\activate
   # On macOS/Linux:
   source venv/bin/activate
   ```

3. **Install dependencies**:

   ```bash
   pip install -r requirements.txt
   ```

   Key dependencies include:

   - numpy
   - scikit-learn
   - pandas
   - nltk (for stopword removal and stemming)

4. **Download NLTK data** (required for text preprocessing):
   ```bash
   python -c "import nltk; nltk.download('stopwords'); nltk.download('punkt')"
   ```

## Data Folder Structure

### Required Data

This project requires datasets to be placed in the `data/` folder. The following files are expected:

```
data/
├── News_Category_Dataset_v3.json
└── wikinews_en.csv
```

### Important Notes

⚠️ **The `data/` folder is NOT included in the repository** for the following reasons:

- Large file sizes (datasets can be hundreds of MB)
- License/copyright considerations
- Repository size optimization

### Obtaining the Data

You must download and add the datasets to the `data/` folder before running the project:

1. **News_Category_Dataset_v3.json**:

   - Download from Kaggle or your data source
   - Place in `data/News_Category_Dataset_v3.json`

2. **wikinews_en.csv**:
   - Download from your data source
   - Place in `data/wikinews_en.csv`

### Folder Structure After Setup

After downloading the data, your project structure should look like:

```
mini_projet_final/
├── README.md
├── CODEBASE_OVERVIEW.md
├── requirements.txt
├── data/                    ← Create and add data files here
│   ├── News_Category_Dataset_v3.json
│   └── wikinews_en.csv
├── outputs/                 ← Auto-generated (indexes, matrices, results)
│   ├── inverted_index.json
│   ├── X.npz
│   ├── ablation/
│   ├── plots/
│   └── results/
└── src/                     ← Python source code
    ├── build_index.py
    ├── vectorize.py
    ├── rank_and_eval.py
    ├── evaluate.py
    ├── ablation_pipelines.py
    ├── run_ablation.py
    ├── plot_results.py
    ├── mock_judgments.py
    └── utils.py
```

## Running the Project

### Step-by-step Pipeline

1. **Build the inverted index**:

   ```bash
   python -m src.build_index
   ```

2. **Vectorize documents (TF-IDF)**:

   ```bash
   python -m src.vectorize
   ```

3. **Run ranking and evaluation**:

   ```bash
   python -m src.rank_and_eval
   ```

4. **Run ablation studies** (optional):

   ```bash
   python -m src.run_ablation
   ```

5. **Generate visualizations** (optional):
   ```bash
   python -m src.plot_results
   ```

## Output Files

Results and generated files are saved to the `outputs/` folder:

- `inverted_index.json` - Inverted index for boolean retrieval
- `X.npz` - TF-IDF document-term matrix
- `results.csv` - Baseline ranking results
- `results_rocchio.csv` - Rocchio relevance feedback results
- `ablation_metrics.csv` - Ablation study performance metrics
- `plots/` - Generated visualization plots

## Troubleshooting

### Data not found error

- Ensure the `data/` folder exists in the project root
- Verify that both required CSV/JSON files are present and correctly named
- Check file paths in `src/utils.py` match your data filenames

### NLTK data missing

- Run: `python -c "import nltk; nltk.download('stopwords'); nltk.download('punkt')"`

### Import errors

- Ensure all dependencies are installed: `pip install -r requirements.txt`
- Verify you're using the correct Python interpreter from your virtual environment

## Documentation

For detailed information about each component, see [CODEBASE_OVERVIEW.md](CODEBASE_OVERVIEW.md).
