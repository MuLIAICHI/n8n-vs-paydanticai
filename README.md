# Agentic RAG System: Two Approaches

This repository demonstrates two different approaches to building an agentic Retrieval-Augmented Generation (RAG) system focused on Pydantic AI documentation:

1. **Pydantic AI Implementation**: A Python-based implementation using Pydantic AI framework
2. **n8n Implementation**: A workflow-based implementation using n8n and Crawl4AI

Both implementations achieve the same goal: creating an AI assistant that can answer questions about Pydantic AI by retrieving information from its documentation.

## Project Structure

- `/paydanti-ai-version`: Python-based implementation using Pydantic AI framework
- `/n8n-version`: Workflow-based implementation using n8n

## Comparison

These implementations represent two fundamentally different approaches to building AI systems:

| Feature | Pydantic AI Approach | n8n Approach |
|---------|---------------------|--------------|
| Development paradigm | Code-first | Visual workflow |
| Language | Python | JSON workflow definition |
| Learning curve | Python knowledge required | Visual interface, less coding |
| Customization | Highly customizable | Limited to available nodes |
| Deployment | Standard Python deployment | n8n server required |
| Web crawling | Using Crawl4AI library | Using Crawl4AI service |
| Database | Supabase vector database | Supabase vector database |

## Getting Started

### Pydantic AI Version

See detailed instructions in the [pydantic-ai-version README](paydanti-ai-version/README.md).

### n8n Version

See detailed instructions in the [n8n-version README](n8n-version/README.md).

## Further Reading

For a more detailed comparison between these two approaches, check out my Medium article [read me](https://medium.com/@mustaphaliaichi/building-agentic-rag-systems-n8n-vs-pydantic-ai-b9088b496c84).

## License

This project is licensed under the MIT License - see the LICENSE file for details.