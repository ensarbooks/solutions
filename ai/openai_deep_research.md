# Open Deep Research

Open Deep Research is an experimental, fully OpenAI research assistant developed by LangChain that automates in-depth research and generates comprehensive reports on any topic. This versatile tool represents a significant advancement in AI-powered research capabilities, allowing users to obtain detailed, well-cited analyses with minimal manual effort.

## Key Features and Architecture

Open Deep Research features two distinct implementation approaches, each designed for different use cases and research needs[1]:

### Graph-based Workflow Implementation

The workflow implementation follows a structured plan-and-execute methodology that prioritizes user control and research quality[1]:

- **Planning Phase**: Employs a planner model to analyze topics and generate structured report plans
- **Human-in-the-Loop**: Enables user feedback and approval before proceeding with research
- **Sequential Research**: Creates sections one by one with reflection between search iterations
- **Section-Specific Research**: Dedicates custom search queries to each section
- **Multi-Tool Support**: Works with numerous search providers including Tavily, Perplexity, Exa, ArXiv, PubMed, and more[1]

This implementation is highly configurable, allowing users to customize parameters such as report structure, number of queries per section, search depth, and model selection for both planning and writing phases[1].

### Multi-Agent Implementation

The multi-agent approach uses a supervisor-researcher architecture optimized for efficiency and parallel processing[1]:

- **Supervisor Agent**: Manages the overall research process, plans sections, and assembles final reports
- **Researcher Agents**: Multiple independent agents work simultaneously, each researching specific sections
- **Parallel Processing**: All sections are researched concurrently, significantly reducing generation time
- **Specialized Tool Design**: Each agent has access to tools specific to its role
- **Current Limitations**: Currently only works with Tavily Search, though designed for future expansion[1]

This implementation focuses on speed and parallelization, making it ideal for faster report generation with less direct user involvement[1].

## Technical Implementation and Deployment

Open Deep Research offers multiple deployment options and integration capabilities[1]:

### Installation and Setup

Users can install the package directly via pip:

```
pip install open-deep-research
```

Alternatively, they can clone the repository and configure it locally:

```
git clone https://github.com/langchain-ai/open_deep_research.git
cd open_deep_research
```

The assistant can be launched with the LangGraph server locally, providing both API access and a Studio UI for interaction[1].

### Model Compatibility

The system is designed to work with various language models through the `init_chat_model()` API integration[1]. However, there are important considerations:

- Models must support structured outputs for the workflow implementation
- Tool calling support is essential (tested with Claude 3.7, o3, o3-mini, and GPT-4.1)
- Token-per-minute limits may apply for certain providers like Groq
- Some models (like deepseek-R1) have limitations with function calling capabilities[1]

### Search API Configuration

The system supports extensive configuration for search APIs, with particular options available for Exa, ArXiv, PubMed, and Linkup[1]. For example, with Exa, users can configure:

```python
thread = {
    "configurable": {
        "thread_id": str(uuid.uuid4()),
        "search_api": "exa",
        "search_api_config": {
            "num_results": 5,
            "include_domains": ["nature.com", "sciencedirect.com"]
        }
    }
}
```

## Context in the Deep Research Landscape

Open Deep Research is part of a broader trend in AI research assistance. Since OpenAI introduced their Deep Research capability in early 2025[7], there has been significant interest in developing similar tools:

- **Together AI's Open Deep Research**: Enhances web search with comprehensive, well-cited content on complex topics[2]
- **DeepSearcher**: A local OpenAI implementation using only OpenAI models and tools like Milvus and LangChain[5]
- **Independent implementations**: Several developers have created their own versions, leveraging the recently launched OpenAI Agents SDK[4]

The core innovation across these implementations is their ability to go beyond simple search and produce long-form content with in-depth explanations through multi-hop reasoning[7][2].

## Conclusion

LangChain's Open Deep Research represents a significant advancement in AI-powered research assistance. By providing two distinct implementation approaches and extensive customization options, it offers researchers, content creators, and knowledge workers a powerful tool for automating complex research tasks. Its OpenAI nature and integration with multiple search providers and language models make it highly adaptable to diverse research needs and technical environments[1].

Citations:
[1] https://github.com/langchain-ai/open_deep_research
[2] https://github.com/langchain-ai/open_deep_research
[3] https://www.together.ai/blog/open-deep-research
[4] https://www.youtube.com/watch?v=DU_W9tgFcqo
[5] https://www.reddit.com/r/LLMDevs/comments/1jpfa8f/i_built_open_source_deep_research_heres_how_it/
[6] https://milvus.io/blog/introduce-deepsearcher-a-local-OpenAI-deep-research.md
[7] https://github.com/langchain-ai/open_deep_research
[8] https://openai.com/index/introducing-deep-research/
[9] https://www.reddit.com/r/ChatGPTPro/comments/1in87ic/mastering_aipowered_research_my_guide_to_deep/
[10] https://www.youtube.com/watch?v=2mSNIX-l_Zc
[11] https://xenoss.io/blog/open-ai-deep-research-use-cases-and-best-practices
[12] https://huggingface.co/blog/open-deep-research
[13] https://www.reddit.com/r/AI_Agents/comments/1jk14wz/open_source_deep_research_using_the_openai_agents/
[14] https://www.reddit.com/r/ollama/comments/1iijkmy/stepbystep_guide_to_running_open_deep_research/
[15] https://www.perplexity.ai/hub/blog/introducing-perplexity-deep-research
[16] https://www.youreverydayai.com/openais-deep-research-how-it-works-and-what-to-use-it-for/
[17] https://github.com/togethercomputer/open_deep_research
[18] https://langfuse.com/blog/2025-02-20-the-agent-deep-dive-open-deep-research
[19] https://www.datacamp.com/blog/deep-research-openai
[20] https://gemini.google/overview/deep-research/
[21] https://www.keywordsai.co/blog/how-to-use-openai-deep-research-effectively
[22] https://n8n.io/workflows/2883-open-deep-research-ai-powered-autonomous-research-workflow/
