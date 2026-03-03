# Everything Wrong with GCP GenAI and VertexAI

_nuances, missing features, strange API, things to watchout, and wishlist_

## Model Deprecations

- GCP unilaterally deprecates models (with 2 weeks notice) to more expensive models, with worse performance. GCP representatives just shrug their shoulders. relying on GCP is a risk to your business.

## Batch API

- Batch API in go client does not match official API and is not working. not resolved for 6+ months, as of 2026-03-03 still not resolved. Google maintainers ignore bug reports[^1][^2][^3][^4][^5]. the only viable path for BatchAPI is to define your own type and schema.
- confusing and low quality errors in schema validation[^6]. maintainers are not addressing the root of problem.
- Batch API iterates over full BigQuery table on every inference request
- Batch API silently discards request fields that it does not recognize (e.g. arrays, maps). only scalar types are allowed

## Embeddings

- As of 2026-03-03, it is not possible to compute embeddings in Batch API
- `gemini-embedding-001` does not support generic Batch API inference requests
- Vertex AI does not support `batches.createEmbeddings`
- `CreateEmbeddings` supports only local-file or inlined requests, no Cloud Storage Support
- `CreateEmbeddings` may or may not provide output destination file upon job creation. It is also not possible to specify it ahead of time. This means it is not possible to set up Cloud Storage object notifications through Pub/Sub.

[^1]: https://github.com/googleapis/go-genai/issues/666
[^2]: https://github.com/googleapis/go-genai/issues/579
[^3]: https://github.com/googleapis/go-genai/issues/513
[^4]: https://github.com/googleapis/go-genai/issues/506
[^5]: https://github.com/googleapis/go-genai/issues/505
[^6]: https://github.com/googleapis/go-genai/issues/512
