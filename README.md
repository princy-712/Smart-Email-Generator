# Smart Email Generator

A cold email generator that scrapes job postings from career pages and creates personalized outreach emails using AI.

## Features

- **Web Scraping**: Extracts job postings from career pages
- **AI-Powered Generation**: Uses Groq's LLaMA model to generate personalized emails
- **Portfolio Integration**: Matches job requirements with relevant portfolio projects
- **Vector Database**: Uses ChromaDB for efficient skill-based portfolio matching

## Setup

1. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

2. **Environment Variables**:
   Create a `.env` file in the root directory:
   ```
   GROQ_API_KEY=your_groq_api_key_here
   ```

3. **Portfolio Data**:
   The portfolio data is stored in `app/resource/my_portfolio.csv`. 
   Update this file with your actual projects and links.

## Usage

Run the Streamlit app:
```bash
streamlit run app/main.py
```

## Project Structure

```
├── app/
│   ├── chains.py          # LLM chains for job extraction and email generation
│   ├── main.py            # Streamlit web interface
│   ├── portfolio.py       # Portfolio management with ChromaDB
│   ├── utils.py           # Text cleaning utilities
│   └── resource/
│       └── my_portfolio.csv # Portfolio data
├── vectorstore/           # ChromaDB vector storage
├── requirements.txt       # Python dependencies
└── .env                  # Environment variables
```

## How It Works

1. **Input**: User provides a URL to a career page
2. **Scraping**: WebBaseLoader extracts job postings
3. **Processing**: LLM extracts structured job data (role, skills, experience)
4. **Matching**: Portfolio is queried for relevant projects based on skills
5. **Generation**: Personalized email is generated using job description and portfolio links

## Dependencies

- `streamlit` - Web interface
- `langchain` - LLM framework
- `langchain-groq` - Groq API integration
- `chromadb` - Vector database
- `pandas` - Data manipulation
- `python-dotenv` - Environment variable management