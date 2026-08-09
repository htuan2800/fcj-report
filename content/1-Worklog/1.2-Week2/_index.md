---
title: "Week 2 Log"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---
### Week 2 Objectives:

*   Deep dive into Amazon Bedrock: available embedding models, token limits, and per-request costs.
*   Research Amazon RDS PostgreSQL + the `pgvector` extension for use as a vector store in the RAG pipeline.
*   Explore Amazon Cognito (in parallel with the team) to understand the authentication flow required for integration with the AI-focused Lambda functions.
*   Draft conceptual flow diagrams for "Phase 2 - Document Processing" and "Phase 3 - Q&A."

### Tasks to be implemented this week:
| Days | Task | Start Date | Completion Date | Resources |
| --- | --- | --- | --- | --- |
| Mon-Tue | - Detailed research on the **Titan Embed Text** model on Amazon Bedrock: output vector dimensions, 8,192-token limit per call, and token-based cost calculation <br> - Write a test Python script calling the Bedrock `InvokeModel` API to convert a sample text into a vector and verify the response format | 29/06/2026 | 30/06/2026 | [Amazon Bedrock – Titan Embeddings](https://docs.aws.amazon.com/bedrock/latest/userguide/titan-embedding-models.html) |
| Wed | - Research Amazon RDS & the `pgvector` extension: syntax for creating `vector` type columns, index types supporting similarity search (IVFFlat, HNSW), and distance metrics (cosine, L2, inner product) <br> - Preliminary comparison of `pgvector` on RDS vs. OpenSearch Serverless (vector engine) — selected `pgvector` due to lower cost and the team's familiarity with SQL | 01/07/2026 | 01/07/2026 | [pgvector GitHub](https://github.com/pgvector/pgvector) <br> [Amazon RDS Guide](https://000005.awsstudygroup.com/vi/) |
| 5 | - Experiment with creating a test table with a `vector(1024)` column on a local RDS PostgreSQL instance (Docker), insert sample vectors, and run the query `ORDER BY embedding <=> query_vector LIMIT 5` to understand the cosine search mechanism <br> - Note parameters requiring future tuning: text chunk size, vector dimensions, and similarity threshold | 02/07/2026 | 02/07/2026 | |
| 6 | - Study Amazon Cognito (in parallel with the teammate handling authentication) to understand how the AI-side Lambda function will receive and validate user JWT tokens before processing requests <br> - Read the AWS KMS overview and note its potential for encrypting sensitive vector data/metadata later | 03/07/2026 | 03/07/2026 | [Amazon Cognito](https://000081.awsstudygroup.com/vi/) |
| 7 | - Draft conceptual diagrams for the two assigned phases: **Phase 2 (Document Processing)** — Lambda receives OCR'd text, calls Bedrock to generate vectors, and stores them in RDS; **Phase 3 (Q&A)** — Lambda receives a question, generates a query vector, performs a semantic search in RDS, and constructs a prompt with context to send to the LLM <br> - Finalize and update the Worklog for Weeks 1 and 2 | 04/07/2026 | 04/07/2026 | Personal GitHub Repository |


### Week 2 Achievements:

* Gained a detailed understanding of how to call Amazon Bedrock to generate vector embeddings (Titan Embed model, token limits, costs). * Gained a foundational understanding of `pgvector` on Amazon RDS PostgreSQL, including vector data types, indexing, and similarity metrics.
* Successfully tested cosine similarity queries on a sample vector table running locally.
* Understood the Cognito authentication flow sufficiently to integrate JWTs into the AI-side Lambda function.
* Drafted conceptual diagrams for Phase 2 (Document Processing) and Phase 3 (Q&A)—establishing the foundation for coding in the coming weeks.