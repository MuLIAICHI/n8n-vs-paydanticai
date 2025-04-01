# n8n RAG Implementation

This directory contains a workflow-based implementation of an agentic RAG system using n8n. The workflow crawls Pydantic AI documentation, stores it in a vector database, and uses retrieval-augmented generation to answer user questions.

## Files Overview

- `Crawl4AI_Agent.json`: n8n workflow definition for the RAG agent and crawler
- `README.md`: This documentation file

## Prerequisites

- [n8n](https://n8n.io/) (self-hosted or cloud)
- Supabase account
- OpenAI API key
- Access to a Crawl4AI service

## Setup Instructions

### 1. Import the Workflow

1. Open your n8n instance
2. Go to "Workflows" and click "Import from file"
3. Select the `Crawl4AI_Agent.json` file
4. Save the imported workflow

### 2. Configure Credentials

In n8n, set up the following credentials:

1. **OpenAI API**:
   - Go to "Settings" > "Credentials"
   - Add new "OpenAI API" credentials with your API key

2. **Supabase API**:
   - Add new "Supabase API" credentials
   - Enter your Supabase URL and service key

3. **HTTP Header Authentication** (for Crawl4AI if needed):
   - Add new "HTTP Header Auth" credentials
   - Enter your authentication details for the Crawl4AI service

### 3. Set Up Supabase

1. Create a new project in Supabase
2. Enable the pgvector extension
3. Create necessary tables for document storage (refer to the SQL script in the pydantic-ai-version directory)

### 4. Configure Workflow Nodes

Update the following nodes in the workflow:

1. In the `HTTP Request` nodes:
   - Update the Crawl4AI API URL to your deployed instance

2. In the Supabase Vector Store nodes:
   - Verify the table names match your Supabase setup

## Running the Workflow

The workflow has two main parts:

1. **Document Crawling and Indexing**:
   - Start this process by clicking "Test workflow" on the crawling workflow
   - This will fetch the Pydantic AI documentation sitemap
   - Process each URL through Crawl4AI
   - Store the content in Supabase with vector embeddings

2. **Chat Interface**:
   - Activate the workflow by toggling it to "Active"
   - This will create a webhook endpoint for the chat interface
   - You can interact with the agent through n8n's chat interface

## How It Works

1. **Web Crawling Process**:
   - Fetches the sitemap.xml from the Pydantic AI documentation
   - Extracts URLs and processes them through Crawl4AI
   - Chunks content and generates embeddings
   - Stores vectorized content in Supabase

2. **Agent Process**:
   - Receives questions through the chat interface
   - Uses vector search to find relevant documentation
   - Generates answers using OpenAI models
   - Returns responses to the user

## Customization

You can modify the workflow by:

1. Adjusting the chunk size in the Character Text Splitter node
2. Updating the system prompt in the AI Agent node
3. Adding additional tools to the agent
4. Extending the workflow with additional data sources

## Troubleshooting

- If crawling fails, check the Crawl4AI service connection
- If vector operations fail, verify pgvector is properly set up in Supabase
- If the agent provides incorrect answers, you may need to adjust the system prompt or chunking strategy