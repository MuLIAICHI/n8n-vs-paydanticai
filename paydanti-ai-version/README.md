# Pydantic AI RAG Implementation

This directory contains a Python-based implementation of an agentic RAG system using the Pydantic AI framework. The agent crawls Pydantic AI documentation, stores it in a vector database, and uses retrieval-augmented generation to answer user questions.

## Files Overview

- `crawl_pydantic_ai_docs.py`: Web crawler for Pydantic AI documentation
- `pydantic_ai_expert.py`: Agent implementation using Pydantic AI framework
- `streamlit_ui.py`: Streamlit-based user interface
- `requirements.txt`: Python dependencies
- `site_pages.sql`: SQL script for database setup
- `.env.example`: Example environment variables file
- `.env`: Environment variables file (not committed)
- `.gitignore`: Git ignore file

## Prerequisites

- Python 3.11+
- Supabase account
- OpenAI API key
- Streamlit (for web UI)

## Setup Instructions

1. **Environment Setup**

   Create a copy of the `.env.example` file and rename it to `.env`:

   ```bash
   cp .env.example .env
   ```

   Edit the `.env` file with your API keys:

   ```
   OPENAI_API_KEY=your_openai_api_key
   SUPABASE_URL=your_supabase_url
   SUPABASE_SERVICE_KEY=your_supabase_service_key
   LLM_MODEL=gpt-4o-mini
   ```

2. **Install Dependencies**

   ```bash
   pip install -r requirements.txt
   ```

3. **Database Setup**

   Run the SQL script in your Supabase project:
   
   - Go to your Supabase project dashboard
   - Open the SQL Editor
   - Paste the contents of `site_pages.sql`
   - Run the script

## Running the Application

1. **Crawl Documentation**

   ```bash
   python crawl_pydantic_ai_docs.py
   ```

   This will:
   - Fetch URLs from the Pydantic AI documentation
   - Crawl and process the content
   - Store chunks with embeddings in Supabase

2. **Launch the UI**

   ```bash
   streamlit run streamlit_ui.py
   ```

   The interface will be available at http://localhost:8501

## How It Works

1. **Crawling and Processing**:
   - `crawl_pydantic_ai_docs.py` fetches and processes the Pydantic AI documentation
   - Content is split into chunks with intelligent boundary detection
   - OpenAI embeddings are generated for each chunk
   - Chunks and embeddings are stored in Supabase

2. **Agent Implementation**:
   - `pydantic_ai_expert.py` defines a Pydantic AI agent with tools for:
     - Retrieving relevant documentation
     - Listing available pages
     - Fetching complete page content

3. **User Interface**:
   - `streamlit_ui.py` provides a chat interface
   - Users can ask questions about Pydantic AI
   - Responses are streamed in real time

## Additional Resources

- `crawl4AI-examples`: Example scripts for using Crawl4AI
- `crawl4AI-agent-code-workspace`: VS Code workspace configuration

## Customization

You can modify the agent's behavior by:

1. Updating the system prompt in `pydantic_ai_expert.py`
2. Adjusting chunking parameters in `crawl_pydantic_ai_docs.py`
3. Enhancing the UI in `streamlit_ui.py`