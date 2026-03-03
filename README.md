# Everything Wrong with GCP GenAI and VertexAI

_nuances, missing features, strange API, things to watchout, and wishlist_

## Batch API

- Batch API in go client does not match official API and is not working. not resolved for 6+ months, as of 2026-03-03 still not resolved. Google maintainers ignore bug reports. the only viable path for BatchAPI is to define your own type and schema. [bug-1](https://github.com/googleapis/go-genai/issues/666) [bug-2](https://github.com/googleapis/go-genai/issues/579) [bug-3](https://github.com/googleapis/go-genai/issues/513) [bug-4](https://github.com/googleapis/go-genai/issues/506) [bug-5](https://github.com/googleapis/go-genai/issues/505)
- confusing and low quality errors in schema validation [bug](https://github.com/googleapis/go-genai/issues/512)

## Embeddings

- As of 2026-03-03, it is not possible to compute embeddings in Batch API
- `gemini-embedding-001` does not support generic Batch API inference requests
- Vertex AI does not support `batches.createEmbeddings`
- `CreateEmbeddings` supports only local-file or inlined requests, no Cloud Storage Support
- `CreateEmbeddings` may or may not provide output destination file upon job creation. It is also not possible to specify it ahead of time. This means it is not possible to set up Cloud Storage object notifications through Pub/Sub.
