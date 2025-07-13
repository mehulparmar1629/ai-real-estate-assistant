# [🏡 Smart Property Advisor](https://smart-property-advisor.streamlit.app/)

## Overview
Smart Property Advisor is an AI-powered conversational assistant designed to simplify the property discovery process for buyers and renters. It utilizes natural language understanding and retrieval-augmented generation (RAG) to deliver personalized property recommendations based on user preferences.

For complete project goals and features, see the [Project Specs Document](PRD.MD).

---

## Solution Design & Architecture

### Technical Overview

This project combines LLMs with structured property data, embedding-based search, and a friendly UI to create a seamless real estate advisory experience.

| Component         | Tool/Library                     | Reason for Choice |
|------------------|----------------------------------|-------------------|
| LLM Integration  | OpenAI GPT / LLaMA               | High-quality language understanding and generation |
| Data Handling    | Pandas                           | Robust data wrangling capabilities |
| Embeddings       | FastEmbed                        | Fast, lightweight embeddings for semantic search |
| Vector Store     | ChromaDB / DocArrayInMemorySearch| Quick, in-memory vector retrieval |
| Memory Chain     | ConversationalRetrievalChain     | Retains dialogue history for multi-turn interactions |
| Frontend         | Streamlit                        | Easy to develop and deploy interactive web UIs |

---

### Workflow Summary

1. **Preprocessing**:
   - Load and clean property data (CSV)
   - Convert listings to vector embeddings
   - Store vectors in memory for similarity search

2. **User Interaction**:
   - Users enter free-text queries
   - The LLM extracts preferences and context
   - Matching listings are retrieved and refined
   - Results are presented with explanations

3. **Retrieval-Augmented Generation**:
   - Combines factual property data with natural language generation
   - Produces accurate and helpful answers with grounding

---

## Core Features

- 🗣 **Conversational Search**: Users can describe their ideal property naturally.
- 🧠 **Context Retention**: Understands user needs across multiple turns.
- 🔍 **Rich Filtering**: Matches based on location, price, amenities, etc.
- 🌐 **Multiple Model Support**: Integrates GPT, LLaMA, and others.
- 💻 **Modern Web Interface**: Built with Streamlit for ease of use.

---

## Strengths & Constraints

### ✅ Strengths

- Natural and human-like interaction
- Retains context and preferences
- Scalable to multiple data sources
- Explains recommendations clearly
- Fast to prototype and iterate

### ⚠️ Limitations

- Results depend on data completeness
- Needs sufficient user input to be accurate
- UI freezes during large queries (performance bottleneck)
- No image/visual comparisons yet
- In-memory DB not suited for large datasets

---

## Tech Stack

- **Frontend**: Streamlit
- **Backend**: Python 3.11+
- **AI Layer**: LangChain, GPT, LLaMA
- **Data**: Pandas, FastEmbed
- **Vector DB**: ChromaDB / DocArrayInMemorySearch
- **Environment**: Poetry (Dependency & Environment Manager)

---

## Directory Layout
├── ai/ # LLM agent logic
├── app.py # V1 - Basic agent
├── app_v2.py # V2 - RAG-based assistant
├── assets/ # Images & screenshots
---

## Application Versions

### 🔹 V1: Basic Search Agent
- Uses LangChain’s Pandas DataFrame Agent
- Single-turn Q&A
- Launched via `app.py` or `run_v1.sh`

![V1](assets/screen.png)

---

### 🔷 V2: Conversational RAG Assistant
- Uses ConversationalRetrievalChain
- Supports OpenAI & open-source models
- Enhanced filtering & multi-turn dialogue
- Launched via `app_v2.py` or `run_v2.sh`

![V2](assets/screen2.png)

---

## Future Enhancements

| Priority | Feature                  | Plan                                  | Impact |
|----------|--------------------------|---------------------------------------|--------|
| 🔴 High  | Async backend             | Use background tasks for heavy ops    | Smoother UI |
| 🟡 Med   | Visual property previews  | Add image previews and comparisons    | Improved UX |
| 🟡 Med   | Multiple data inputs      | REST API, JSON, XLSX support          | More data coverage |
| 🟢 Low   | Investment insights       | Price trend analysis w/ time series   | More value for users |
| 🟢 Low   | Mobile-ready UI           | Responsive layout for phones/tablets  | Wider access |

---

## Key Implementation Notes

| Challenge                        | Solution                            | Approach |
|----------------------------------|-------------------------------------|----------|
| Extracting user preferences      | Function calling with LLMs          | NLP + JSON parsing |
| Maintaining context              | LangChain memory system             | Buffer memory |
| Scalable search                  | Embedding-based vector lookup       | FastEmbed + ChromaDB |
| Diverse CSV formats              | Normalized data schema              | Unified loader |
| Performance issues               | Caching + batch processing          | Optimization layer |

---

## Developer Best Practices

- **Modular Design**:
  ```python
  def load_csv_data(path: str) -> pd.DataFrame:
      """Read and normalize data for AI use."""
Extensible AI Layer:

python
Copy
Edit
class SmartAgent:
    """Supports pluggable LLMs for flexibility."""
Secure Config Handling:

python
Copy
Edit
def get_api_key():
    return os.getenv("OPENAI_API_KEY")
Graceful Error Handling:

python
Copy
Edit
try:
    response = agent.respond(query)
except:
    return "Apologies, something went wrong."
Getting Started
Prerequisites
Python 3.11+

Poetry (https://python-poetry.org)

(Optional) OpenAI API Key

Installation
sh
Copy
Edit
# Clone the repo
git clone https://github.com/your-username/smart-property-advisor.git
cd smart-property-advisor

# Set up Poetry environment
poetry install --no-root
source .venv/bin/activate

# Configure API Key
echo "OPENAI_API_KEY=your-key" > .env
Run the App
sh
Copy
Edit
# Launch version 1
streamlit run app.py

# OR version 2
streamlit run app_v2.py
Deployment
Streamlit Cloud
Deploy directly using Streamlit Cloud.

Docker
sh
Copy
Edit
./utils/run_docker.sh
VS Code Dev Container
sh
Copy
Edit
./utils/run_dev_container.sh
Contribution
Open to community contributions. Fork, code, and send PRs! 🙌

License
Licensed under the Apache License 2.0. See LICENSE for full terms.

yaml
Copy
Edit

---

Let me know if you want this tailored with **your GitHub link**, **your project name**, **screenshots replaced**, or want to **add a specific example user query** like:  
> "Show me a 3-bedroom house with a garage in Brooklyn under $3000."

I can also help convert this into a full **GitHub README**, **Notion template**, or **presentation pitch deck** if needed.
