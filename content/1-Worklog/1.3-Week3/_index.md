---
title: "Week 3 Log"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---
### Week 3 Objectives:

*   Code the `create-vector` Lambda function: receive OCR-processed text and call Amazon Bedrock to generate vector embeddings.
*   Collaborate with the team to finalize the AWS Overall Architecture diagram for use in the Proposal and section 5.1.3.
*   Review progress and perform cross-testing on related components (e.g., the frontend authentication flow) implemented by teammates.

### Tasks to be executed this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon-Tue | - Code `create-vector` Lambda: receive text string (Textract output), split into chunks based on fixed character size with overlap <br> - Write function to call Amazon Bedrock's `InvokeModel` API (Titan Embed) for each chunk; process response to obtain 1,024-dimensional vectors <br> - Manual testing with a sample PDF document; verify that the number of generated chunks and vectors matches expectations | 06/07/2026 | 07/07/2026 | [Amazon Bedrock – Titan Embeddings](https://docs.aws.amazon.com/bedrock/latest/userguide/titan-embedding-models.html) |
| Wed | - Collaborated with the team to finalize the High-Level AWS Architecture diagram (item 5.1.3), focusing on accurately mapping the flows for the two Lambda functions under my responsibility (`create-vector` and the semantic search Lambda scheduled for next week) within the "Interface & Orchestration" block <br> - Cross-referenced the diagram with the AWS Well-Architected Framework; confirmed that separating the Bedrock-calling Lambda (non-VPC) from the RDS-insertion Lambda (VPC-enabled) is cost-effective | 08/07/2026 | 08/07/2026 | [AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html) |
| 5 | - Developed the `vector-insert` Lambda (deployed within a VPC) to receive vectors from `create-vector` via `lambda_client.invoke()` and write them to the `document_chunks` table in RDS PostgreSQL (`pgvector`) <br> - Performed insertion tests using simulated vectors; verified that data was stored in the correct `vector(1024)` format | 09/07/2026 | 09/07/2026 | |
| 6 | - Reviewed and tested the frontend authentication flow (Login/Register/Protected Route) implemented by a teammate to ensure the returned JWT follows the correct format, facilitating future request authentication by the AI-side Lambda <br> - Logged issues regarding cross-tab session conflicts for the team to address next week (while outside the scope of the AI ​​Lambda, these issues indirectly impact end-to-end testing) | 10/07/2026 | 10/07/2026 | |
| 7 | - Attended the "Cloud Architect x Meet Up" community event | 11/07/2026 | 11/07/2026 | |


### Week 3 Achievements:

* Completed the `create-vector` Lambda: successfully split text into chunks and invoked Amazon Bedrock to generate vector embeddings. * Completed the `vector-insert` Lambda function (running within a VPC) to write vectors to RDS PostgreSQL (`pgvector`) using a synchronous invocation mechanism between the two Lambda functions.
* Finalized the high-level AWS architecture diagram (used in the proposal and section 5.1.3), ensuring accurate representation of the Lambda component under my responsibility.
* Reviewed the frontend authentication flow and confirmed the appropriate JWT format for integration with the AI/RAG Lambda functions.
* Attended the "Cloud Architect x Meet Up" event (July 11, 2026).