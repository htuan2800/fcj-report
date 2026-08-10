---
title: "Week 4 Log"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---
### Week 4 Objectives:

*   Code the semantic search Lambda function (`vector-search`): match the query vector against document vectors stored in RDS.
*   Design a standard prompt to constrain the LLM to answer based solely on provided documents, preventing information fabrication.
*   Configure VPC settings for the Q&A Lambda function to enable RDS (`pgvector`) queries — addressing the **VPC REQUIRED** note from the task assignment table.
*   Collaborate on fixing multi-tenancy issues affecting user-specific vector data.

### Tasks to be implemented this week:
| Days | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon-Tue | - Code `vector-search` Lambda: receive user query, call Amazon Bedrock (Titan Embed) to generate the query vector <br> - Implement logic to calculate similarity (cosine similarity) between the query vector and document vectors stored in RDS using the query `ORDER BY embedding <=> query_vector LIMIT k`; extract the top-k most relevant chunks to serve as context | 13/07/2026 | 14/07/2026 | [pgvector – Querying](https://github.com/pgvector/pgvector#querying) |
| Wed | - Issue detection: `vector-search` Lambda unable to connect to RDS because RDS resides in a private subnet without an outbound route <br> - Research and configure Lambda to join the VPC (attach Subnet + Security Group corresponding to RDS) per the **VPC REQUIRED** note in the assignment table; verify successful connection <br> - Cost analysis: confirm that a NAT Gateway is not required for this specific Lambda, as it only needs to access RDS internally within the VPC and does not require internet access | 15/07/2026 | 15/07/2026 | [Configuring a Lambda function to access resources in a VPC](https://docs.aws.amazon.com/lambda/latest/dg/configuration-vpc.html) |
| 5 | - Design a standard prompt for the LLM in Amazon Bedrock: structure includes system instructions (respond only based on provided context; state that information is unavailable if not found), a section for inserting context chunks, and the user question <br> - Test with "trick" questions (out-of-scope queries) to verify if the prompt successfully compels the LLM to refuse fabricating information | 16/07/2026 | 16/07/2026 | [Prompt engineering guidelines – Amazon Bedrock](https://docs.aws.amazon.com/bedrock/latest/userguide/prompt-engineering-guidelines.html) |
| 6 | - Collaborate to fix a multi-tenancy data leakage issue within my assigned scope: add filter conditions—`WHERE user_id = :user_id` (and `document_id IN (...)` when specific documents are selected)—to the `vector-search` query to prevent returning context belonging to other users <br> - Conduct real-world testing with two accounts to confirm that each user receives context only from their own documents | 17/07/2026 | 17/07/2026 | |
| 7 | - Integrate `ChatbotRAG` (orchestration Lambda) with `vector-search` and Bedrock (LLM); perform the first end-to-end Q&A flow test using real data <br> - Log inaccurate responses to refine the prompt and chunk size in the following week | 18/07/2026 | 18/07/2026 | | ### Week 4 Achievements:

*   Completed the `vector-search` Lambda function: implemented question vectorization and semantic search (cosine similarity) within RDS PostgreSQL.
*   Successfully configured the VPC for the Q&A Lambda function to enable RDS (`pgvector`) queries; confirmed no additional NAT Gateway costs were incurred.
*   Designed and tested a standardized prompt to ensure the LLM's responses remain grounded in the source documents and minimize the fabrication of information outside the context.
*   Collaborated to resolve a multi-user data leakage issue in the vector query process, ensuring proper data isolation between users.
*   Successfully executed the end-to-end RAG Q&A workflow for the first time (ChatbotRAG → vector-search → Bedrock LLM).