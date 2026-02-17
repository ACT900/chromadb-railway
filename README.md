# Deploy and Host ChromaDB with Railway

[![Deploy on Railway](https://railway.com/button.svg)](https://railway.com/deploy/chromadb-1?referralCode=Qf6zrX)

ChromaDB is the open-source vector database built for AI.

Deploy v1.5.0 in under 2 minutes using the official Docker image (3.9M+ pulls).

One service, one volume, no auth proxy.

Runs on private networking so your data stays internal and traffic between services is free.

## About Hosting ChromaDB

ChromaDB is purpose-built for AI applications. Its Rust core delivers up to 4x faster writes and queries, scaling from prototype to billions of embeddings without switching databases. It ships with hybrid search combining vector similarity, full-text, BM25, and SPLADE through Reciprocal Rank Fusion for better retrieval quality out of the box. Multi-modal support means text, image, and audio embeddings live in a single collection. This template deploys the official chromadb/chroma image directly from Docker Hub with no forks, no modifications, and no custom code. Data persists to a Railway Volume at `/data` and survives restarts and redeploys automatically.

## Common Use Cases

- **RAG pipelines** - Store document embeddings and retrieve high-relevance context for LLM prompts
- **Hybrid search** - Combine semantic similarity with keyword matching for better results than either alone
- **LLM memory** - Give AI agents persistent long-term memory across conversations
- **Multimodal search** - Query text, image, and audio embeddings from a single collection
- **Recommendation engines** - Surface similar content at scale using embedding similarity

## Dependencies for ChromaDB Hosting

- Official Docker image: [chromadb/chroma v1.5.0](https://hub.docker.com/r/chromadb/chroma) (3.9M+ pulls)
- Railway Volume at `/data` for persistent storage
- Private networking only, never exposed to the public internet
- No external databases or additional services required

## Quick Start

1. Click the **Deploy on Railway** button above
2. Wait for the build to complete (~2 minutes)
3. Connect from any service in your project via `chromadb.railway.internal:8000`

> This template uses private networking only. No public domain is exposed. Access ChromaDB securely from other Railway services using the internal URL.

## Configuration

| Variable | Default | Description |
|---|---|---|
| `IS_PERSISTENT` | `TRUE` | Persist data to the volume at `/data` |
| `ANONYMIZED_TELEMETRY` | `false` | Disable anonymous usage telemetry |
| `CHROMA_HOST_ADDR` | `::` | Listen on all interfaces (IPv4 + IPv6) |
| `CHROMA_HOST_PORT` | `8000` | HTTP server port |
| `CHROMA_WORKERS` | `1` | Number of Uvicorn workers |
| `CHROMA_TIMEOUT_KEEP_ALIVE` | `30` | Keep-alive timeout in seconds |

## Connect from Your App

```python
import chromadb

client = chromadb.HttpClient(host="chromadb.railway.internal", port=8000)
collection = client.get_or_create_collection("my_embeddings")
```

For full API documentation, see the [ChromaDB docs](https://docs.trychroma.com).

## Resources

- [ChromaDB GitHub](https://github.com/chroma-core/chroma) (22K+ stars)
- [ChromaDB Python Client](https://pypi.org/project/chromadb/)
- [ChromaDB JavaScript Client](https://www.npmjs.com/package/chromadb)

## License

MIT
