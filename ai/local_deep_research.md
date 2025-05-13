# Local Deep Researcher: A Fully Local Web Research Assistant

Local Deep Researcher is a sophisticated tool that functions as a fully local web research and report writing assistant. It leverages locally hosted Large Language Models (LLMs) through platforms like Ollama or LMStudio to provide comprehensive research capabilities without dependence on external AI services[1].

## Overview and Functionality

Local Deep Researcher operates as an autonomous research agent that takes a user-provided topic and transforms it into a multi-stage research process. Given a topic, the system generates appropriate web search queries, gathers relevant search results, summarizes the findings, and then critically reflects on this summary to identify knowledge gaps. Upon discovering these gaps, it generates new, more targeted search queries to address the missing information. This iterative process continues for a user-defined number of cycles, ultimately producing a final markdown summary with proper citations to all sources used in generating the content[1].

The system is designed with inspiration from IterDRAG methodology, which decomposes queries into sub-queries, retrieves relevant documents for each one, answers these sub-queries sequentially, and builds comprehensive answers by retrieving additional documents for subsequent sub-queries[1]. This approach ensures thorough research coverage while maintaining a structured investigation process.

### Video Resources

The repository provides multiple video tutorials to help users understand and implement the system. These include an overview of Local Deep Researcher with R1 (featuring instructions on loading and testing DeepSeek R1 distilled models) and a comprehensive guide on building Local Deep Researcher from scratch[1]. These resources offer both practical demonstrations of the tool in action and deeper insights into its construction.

## Setup and Configuration

### Local Model Selection

The system offers flexibility in choosing the local LLM provider, with support for both Ollama and LMStudio integrations[1].

For Ollama implementation:

1. Users can pull specific models (e.g., `deepseek-r1:8b`) using the Ollama platform
2. Configuration settings can be adjusted in the `.env` file, including the Ollama service endpoint (default: `http://localhost:11434`) and the model selection[1]

For LMStudio implementation:

1. Users need to download and install LMStudio
2. Load their preferred model (such as `qwen_qwq-32b`)
3. Start the server with OpenAI-compatible API
4. Configure the `.env` file with appropriate settings including the model name and base URL[1]

### Search Tool Configuration

The system defaults to DuckDuckGo for web searches, which requires no API key, making initial setup straightforward. However, users have the flexibility to implement alternative search tools including SearXNG, Tavily, or Perplexity by adding the appropriate API keys to the environment file[1]. Additional configuration options include setting the maximum number of research loop steps (default: 3) and determining whether to fetch full page content with DuckDuckGo searches (default: false)[1].

## Running with LangGraph Studio

LangGraph Studio provides a visual interface for working with Local Deep Researcher. Setup instructions vary by operating system:

For Mac users:

1. Create a virtual environment (recommended): `python -m venv .venv` followed by `source .venv/bin/activate`
2. Install the uv package manager: `curl -LsSf https://astral.sh/uv/install.sh | sh`
3. Launch LangGraph server: `uvx --refresh --from "langgraph-cli[inmem]" --with-editable . --python 3.11 langgraph dev`[1]

For Windows users:

1. Install Python 3.11 (ensuring it's added to PATH)
2. Create and activate a virtual environment: `python -m venv .venv` followed by `.venv\Scripts\Activate.ps1`
3. Install dependencies: `pip install -e .` and `pip install -U "langgraph-cli[inmem]"`
4. Start LangGraph server: `langgraph dev`[1]

Once launched, the LangGraph Studio Web UI becomes available via a provided URL. The configuration tab allows direct adjustment of various assistant settings, with priorities following a clear hierarchy: environment variables (highest), LangGraph UI configuration, and default values in the Configuration class (lowest)[1].

### Compatibility Considerations

When selecting local LLMs, users should be aware that certain steps in the process require structured JSON output. Some models may struggle with this requirement, though the assistant includes fallback mechanisms to handle such difficulties. For example, DeepSeek R1 (7B) and DeepSeek R1 (1.5B) models have known difficulties with producing the required JSON output[1].

For browser compatibility, Firefox is recommended for optimal experience with the LangGraph Studio UI. Safari users might encounter security warnings due to mixed content issues (HTTPS/HTTP). Users experiencing problems should consider using Firefox, disabling ad-blocking extensions, or checking browser console error messages[1].

## Outputs and Visualization

The system generates a markdown file containing a comprehensive research summary with citations to all sources utilized. All sources gathered during the research process are saved to the graph state, which users can visualize directly in LangGraph Studio[1]. This feature enhances transparency and allows users to better understand the research process and source quality.

## Deployment Options

Users have various deployment options available for Local Deep Researcher. For detailed guidance on these options, Module 6 of LangChain Academy provides a comprehensive walkthrough specifically focused on deployment options with LangGraph[1].

### Docker Container Implementation

For users preferring containerized deployment, the repository includes a Dockerfile that runs LangGraph Studio with Local Deep Researcher as a service. This implementation requires Ollama to be run separately, with appropriate configuration of the `OLLAMA_BASE_URL` environment variable. Users can optionally specify the Ollama model through the `LOCAL_LLM` environment variable[1].

To implement the Docker container:

1. Clone the repository and build an image: `docker build -t local-deep-researcher .`
2. Run the container with appropriate environment variables for search API, API keys, LLM provider, Ollama base URL, and LLM model[1]

When accessing the containerized version, users should note that while they'll see a log message with a URL, the browser won't launch automatically from the container. Instead, they should manually visit the correct baseUrl: `https://smith.langchain.com/studio/thread?baseUrl=http://127.0.0.1:2024`[1].

## Additional Implementations

For users preferring TypeScript, a TypeScript port of the project is available at https://github.com/PacoVK/ollama-deep-researcher-ts. This implementation includes most features of the original project but notably does not support Perplexity search functionality[1].

## Conclusion

Local Deep Researcher represents a significant advancement in locally-hosted AI research capabilities. By combining the power of local LLMs with web search functionality, it offers users a privacy-conscious and customizable research assistant that can iteratively improve its findings through multiple research cycles. The project's flexible configuration options, compatibility with multiple LLM hosting solutions, and comprehensive documentation make it accessible to both technical and non-technical users interested in enhanced research capabilities without relying on cloud-based AI services.

Citations:
[1] https://github.com/langchain-ai/local-deep-researcher
[2] https://github.com/langchain-ai/local-deep-researcher
