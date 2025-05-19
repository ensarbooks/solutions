# Ensar Web Crawl & Search

## System Overview

Ensar Web Crawl & Search Worker is an intelligent web crawling and semantic search platform designed to discover, process, and index web content. The system transforms unstructured web content into semantically searchable documents, allowing users to find information based on meaning rather than just keywords.

## Core Architecture

### 1. Web Crawling Engine

- **Distributed Crawling**: Asynchronous web crawler with BFS traversal strategy
- **Content Extraction**: Intelligent filtering to remove navigation elements and non-essential content
- **Controlled Exploration**: Configurable depth and page limits to manage crawl scope

### 2. Document Processing Pipeline

- **Text Chunking**: Splits documents into semantic units for processing
- **Vector Embedding**: Generates numerical representations using OpenAI's models
- **Metadata Enrichment**: Associates URLs, domains, and custom tags with content
- **Concurrent Processing**: Manages parallel operations with controlled batch sizes

### 3. Vector Storage System

- **DuckDB + VSS**: Core storage with Vector Similarity Search capabilities
- **HNSW Indexing**: Efficient nearest-neighbor search for vector embeddings
- **Payload Association**: Stores document metadata alongside vectors
- **Transaction Safety**: Ensures data integrity through proper transaction management

### 4. Job Management

- **Redis Queue**: Orchestrates distributed task processing
- **Worker Processes**: Executes jobs asynchronously
- **Progress Tracking**: Real-time monitoring of job status
- **Error Recovery**: Robust exception handling and retry mechanisms

### 5. REST API Layer

- **Search API**: Semantic search with filtering options
- **Document Management**: Content retrieval and organization
- **Tag System**: Flexible categorization and discovery
- **Pagination Support**: Efficient handling of large result sets

## Data Flow

1. **Job Creation**

   - Client submits URL to crawl with optional parameters
   - System creates job record and enqueues task in Redis

2. **Crawling & Extraction**

   - Worker retrieves job from queue
   - Discovers and retrieves web pages
   - Extracts and cleans text content
   - Updates job progress in real-time

3. **Processing & Indexing**

   - Text is split into semantic chunks
   - Chunks are converted to vector embeddings
   - Vectors and metadata are stored in DuckDB
   - Job status is updated throughout the process

4. **Search & Retrieval**
   - Query text is converted to embedding vector
   - System finds semantically similar content
   - Results are ranked by similarity score
   - Content is retrieved with associated metadata

## Technical Implementation

### Storage Layer

- **Jobs Table**: Tracks crawl operations and their status
- **Pages Table**: Stores raw document content and metadata
- **Document Embeddings Table**: Contains text chunks with vector representations

### Processing Components

- **TextChunker**: LangChain-based document segmentation
- **VectorIndexer**: Vector storage and similarity search
- **Embedder**: OpenAI API integration for embedding generation

### Infrastructure

- **Redis**: Message broker for distributed task processing
- **DuckDB**: Vector-enabled database for storage
- **FastAPI**: REST API framework for endpoints
- **Pydantic**: Type-safety and validation for API models

## Key Features

- **Semantic Search**: Find content based on meaning, not just keywords
- **Flexible Organization**: Tag-based content categorization
- **Real-time Monitoring**: Comprehensive job tracking
- **Efficient Retrieval**: High-performance vector similarity search
- **Scalable Architecture**: Distributed processing with controlled concurrency

This architecture enables a powerful document discovery and search system that transforms unstructured web content into an intelligently searchable knowledge base.
