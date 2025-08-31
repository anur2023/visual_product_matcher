📑 Table of Contents
🌟 Overview

✨ Features

🏗️ Architecture

📁 File Structure

🛠️ Tech Stack

⚙️ How It Works

🚀 Setup & Installation

🔌 API Endpoints

🗄️ Database

🌐 Deployment

📸 Screenshots

👤 Author & License

🌟 Overview
Visual Product Matcher is a web application that helps users discover products visually similar to an image they upload (either from file or URL). By leveraging deep learning (OpenAI CLIP) and Supabase database, the system performs fast and accurate visual similarity search across a catalog of products.

✨ Features
📤 Upload or URL: Search by uploading an image or providing an image URL

🔍 Visual Similarity: Uses CLIP neural network embeddings for accurate matches

📊 Results with Filters: See a list of similar products, filter by similarity score

📱 Responsive Design: Works on both mobile and desktop devices

🎨 Friendly UI: Loading spinners and intuitive feedback for user actions

⚠️ Error Handling: Shows error messages for invalid uploads or connectivity issues

🏗️ Architecture
Frontend: HTML, CSS, JavaScript, Bootstrap (folder: frontend/)

Backend API: FastAPI (folder: backend/)

AI Model: OpenAI CLIP via Hugging Face Transformers (runs in backend)

Database: Supabase Postgres with product metadata + precomputed image embeddings

🔄 Workflow
User uploads image / provides URL

Backend receives the image, computes its embedding (vector) using CLIP

Backend queries Supabase for product embeddings with highest cosine similarity

Returns a ranked JSON list with products and their metadata

Frontend displays the uploaded image, matched products, and allows filtering

📁 File Structure
text
Product_matching/
│
├── backend/
│   ├── .env                  # Environment variables (Supabase keys etc.)
│   ├── main.py               # FastAPI backend entry point
│   ├── requirements.txt      # Python dependencies
│   ├── supabase_client.py    # Supabase DB interface and similarity logic
│   └── __pycache__/          # Cache (ignored)
│
├── frontend/
│   ├── index.html            # Main web page (UI)
│   ├── script.js             # Client-side logic (uploads, filters, AJAX)
│   └── styles.css            # Styling and layout
│
├── .gitignore                # Git ignored files/patterns
│
└── README.md                 # Project documentation (this file)
🛠️ Tech Stack
Frontend: HTML, CSS, JavaScript, Bootstrap

Backend: Python 3, FastAPI

Database: Supabase (managed Postgres with REST and storage)

Machine Learning: PyTorch, Hugging Face Transformers (OpenAI CLIP)

Hosting: Hugging Face Spaces (for live demo)

⚙️ How It Works
Image Input: User uploads an image file or enters an image URL

Backend Processing: FastAPI receives image, converts to PIL format, uses OpenAI CLIP (ViT-B/32) to compute a normalized embedding vector

Similarity Search: Compares uploaded image's embedding to product embeddings (cosine similarity), returns a sorted product list

Display of Results: Frontend shows the uploaded image, similarity-ranked products with metadata

Error Handling: Clear messages shown for easy troubleshooting

🚀 Setup & Installation
Backend
bash
cd backend
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
# Set up your .env with Supabase credentials
uvicorn main:app --host 0.0.0.0 --port 7860 --reload
Frontend
Simply open frontend/index.html in a browser, or access via deployed domain.

🔌 API Endpoints
Endpoint	Method	Description
/api/upload	POST	Upload an image file
/api/url	POST	Submit an image URL
/api/health	GET	Health check
/	GET	Serves frontend (index.html)
🗄️ Database
Supabase table stores:

Product names, categories, image URLs, descriptions

Precomputed embedding vectors for visual similarity

Uses cosine similarity between CLIP (ViT-B/32) vectors

Retrieves top N similar products with fast vector comparison

🌐 Deployment
Deployed at: Hugging Face Spaces

No installation required for demo—just visit the URL!

👤 Author & License
Author: Anuruddh Kumar (GitHub: anur2023)

License: MIT or as specified in repository

Feel free to fork, improve, or deploy for your own use! If you found this useful, please star the project.

If you have any questions, refer to in-code comments or raise an issue in the repo.

Live Project: https://huggingface.co/spaces/anur2025/Product_matching

