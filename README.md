# Everything Wrong with GCP GenAI and VertexAI

_nuances, missing features, strange API, things to watchout, and wishlist_

## Batch API

- Batch API in go client does not match official API and is not working. not resolved for 6+ months, as of 2026-03-03 still not resolved. Google maintainers ignore bug reports. [bug-1](https://github.com/googleapis/go-genai/issues/666) [bug-2](https://github.com/googleapis/go-genai/issues/579) [bug-3](https://github.com/googleapis/go-genai/issues/513) [bug-4](https://github.com/googleapis/go-genai/issues/506) [bug-5](https://github.com/googleapis/go-genai/issues/505)
- confusing and low quality errors in schema validation [bug](https://github.com/googleapis/go-genai/issues/512)

## Embeddings

- `gemini-embedding-001` does not support generic Batch API inference requests
- Vertex AI does not support `batches.createEmbeddings`
- `CreateEmbeddings` supports only local-file or inlined requests, no Cloud Storage Support
