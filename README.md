🎬 AI Movie Recommender (Text + Voice Search)

An interactive, semantic movie recommendation system powered by OpenAI embeddings, Whisper speech-to-text, and Streamlit.
Users can type or speak their movie mood, and the system returns personalized, vibe-based movie suggestions enriched with an LLM-generated explanation.

This project replicates a real-world Retrieval-Augmented Generation (RAG) stack, combining vector search + LLM reasoning in an intuitive UI.

🚀 Features
🔍 Semantic Search (Embeddings)

Generates vector embeddings for every movie using text-embedding-3-large.

Finds matches using cosine similarity instead of keyword search.

Captures themes, emotions, moods, genres, and plot energy.

Enables deep semantic queries like:

“slow-burn psychological sci-fi thriller with loneliness and mystery vibes”

🎙 Whisper Voice Input

Upload MP3, WAV, M4A, or OGG audio snippets.

Whisper (whisper-1) converts spoken descriptions into high-quality text.

Transcript automatically populates the search field.

Creates a natural voice-driven movie discovery experience.

🧠 LLM Reasoning Layer

Uses GPT to generate a why these movies? summary.

Adds interpretability — like a concierge telling you why each film fits.

Supports per-movie reasoning extension (optional).

🎛 Interactive Streamlit UI

Clean, modern interface with responsive layout.

Quick example prompts for instant testing.

Beautiful movie cards with similarity scores.

Full end-to-end pipeline:

input → embeddings → similarity search → GPT explanation → recommendations

🧩 Tech Stack
Core

Python

Streamlit

OpenAI API (Embeddings, Whisper, GPT)

Data

MovieLens ml-latest-small dataset

Pandas, NumPy, scikit-learn

Other

python-dotenv for environment management

Modular architecture in src/

FAISS/Pinecone-ready design for future vector DB upgrade

Whisper-ready backend for speech-based RAG flows

📂 Project Structure
movie-recs/
│
├── app.py                   # Streamlit UI (text + voice)
├── .env                     # OpenAI API key (ignored by Git)
├── requirements.txt
│
├── artifacts/               # Embedding index files (auto-created)
│   ├── movie_vectors.npy
│   ├── movie_ids.json
│   └── movie_texts.json
│
├── data/
│   └── ml-latest-small/     # MovieLens dataset
│       ├── movies.csv
│       ├── ratings.csv
│       ├── tags.csv
│       └── links.csv
│
└── src/
    ├── data_loader.py       # Loads dataset
    ├── embed_index.py       # Builds embeddings + JSON metadata
    ├── recommender.py       # Cosine similarity + KNN search
    └── llm.py               # Whisper STT + GPT explanations

🔧 Setup & Installation
1️⃣ Clone the repository
git clone https://github.com/enkrumah/movie-recs.git
cd movie-recs

2️⃣ Create and activate the environment
python -m venv .venv
.\.venv\Scripts\activate    # Windows
# source .venv/bin/activate # Mac/Linux

3️⃣ Install dependencies
pip install -r requirements.txt

🔑 Add Your OpenAI API Key

Create a .env file in the project root:

OPENAI_API_KEY=your_key_here


Ensure that .env is not committed — it's already listed in .gitignore.

📥 Prepare the Dataset

Download MovieLens "ml-latest-small":

🔗 https://grouplens.org/datasets/movielens/

Place it here:

data/ml-latest-small/


It must contain these four files:

movies.csv

ratings.csv

tags.csv

links.csv

🧱 Build the Embedding Index (Required Before Running)

Run:

python -m src.embed_index


This creates the vector index files:

artifacts/movie_vectors.npy
artifacts/movie_ids.json
artifacts/movie_texts.json


These are loaded by the recommender.

▶️ Run the Streamlit App
streamlit run app.py


Open your browser:

http://localhost:8501

🎤 Using the Voice Search Feature

Click Upload Audio.

Select .mp3, .wav, .ogg, or .m4a.

Click Transcribe Voice to Text.

The text box auto-fills — edit if you want.

Hit Recommend Movies.

Whisper → embedding search → GPT reasoning → movie cards.

🎥 Example Query (Text or Voice)

“Romantic drama about memory loss and emotional healing.”

Possible results:

Eternal Sunshine of the Spotless Mind

The Vow

Remember Me

Example GPT explanation:

“These films explore memory, emotional trauma, and romantic reconnection — themes strongly aligned with your input.”

🛠 Future Enhancements

✔ Deploy to Streamlit Cloud or Hugging Face Spaces

✔ Add FAISS or Pinecone for scalable vector search

✔ Add personalized user profiles + watch history

✔ Add analytics dashboards for query insights

✔ Add direct microphone recording (no file upload)

✔ Add poster retrieval for movie cards

✔ Add clustering visualizations using UMAP

👤 Author

Ebenezer Nkrumah Amankwah
MBA Candidate @ Emory Goizueta
Product & AI Systems Builder

GitHub: https://github.com/enkrumah