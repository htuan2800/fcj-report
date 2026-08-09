---
title: "Week 1 Log"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---
### Week 1 Objectives:

* Get to know fellow First Cloud AI Journey (FCAJ) members and understand the internship workflow.
* Study foundational AWS Cloud concepts, global infrastructure, and management tools.
* Practice account security (MFA) and IAM permission management.
* Participate in group discussions, finalize the "Smart Docs AI" project topic, and accept responsibility for the **AI & RAG** ​​component (document vectorization, prompt engineering, semantic search).

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Resources |
| --- | --- | --- | --- | --- |
| Mon | - Meet FCAJ members, review internship rules, and understand reporting procedures and weekly Worklog deadlines <br> - Watch "First Cloud Journey Kick-off 2024"; view tutorials on AWS architecture diagramming with Draw.io and complete the workshop; install Hugo and familiarize myself with directory structure and Markdown syntax | 22/06/2026 | 22/06/2026 | [Kick-off](https://www.youtube.com/watch?v=AQlsd0nWdZk&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=1) <br> [Draw.io Tutorial](https://www.youtube.com/watch?v=l8isyDe-GwY&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=2) |
| Tue | - Learn about cloud computing, AWS differentiators, global infrastructure (Region/AZ/Edge Location), and management tools (Console/CLI/SDK) <br> - Overview of AWS service categories: Compute/Storage/Networking/Database — pay special attention to AI/ML services (Amazon Bedrock, SageMaker) as this will be the focus of my work on the project <br> - Hands-on: set up AWS Free Tier, enable MFA for the root account, and configure an AWS Budget alert at $5/month to avoid costs from forgetting to shut down resources | 23/06/2026 | 23/06/2026 | [Cloud Concepts](https://www.youtube.com/watch?v=HxYZAK1coOI&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=4) <br> [AWS Free Tier](https://000001.awsstudygroup.com/vi/) |
| 4 | - Learn IAM (Group/User/Policy/Role) and the principle of least privilege — attach policies to Groups/Roles instead of directly to Users <br> - Hands-on: create a dedicated IAM User/Role for testing Amazon Bedrock API calls; attach a policy restricting permissions to `InvokeModel` only, rather than granting full Bedrock access | 24/06/2026 | 24/06/2026 | [AWS IAM](https://000002.awsstudygroup.com/vi/) |
| 5 | - Team discussion: finalize the "Smart Docs AI" topic (RAG chatbot for document processing) and the technology stack (ReactJS, Python, AWS Serverless) <br> - Role assignment: I am responsible for the **AI & RAG** ​​component, specifically two stages: (1) generating vector embeddings for documents, and (2) semantic search + prompt engineering for the LLM during the Q&A phase | 25/06/2026 | 25/06/2026 | |
| 6 | - Read the official Amazon Bedrock documentation overview: list of available models (Titan Embed, Titan/Nova, Claude, etc.) and the distinction between models used for generating embeddings and those used for generating responses (LLMs) <br> - Sync notes to the team's GitHub | 26/06/2026 | 26/06/2026 | [Amazon Bedrock User Guide](https://docs.aws.amazon.com/bedrock/latest/userguide/what-is-bedrock.html) |
| 7 | - Explore the concept of RAG (Retrieval-Augmented Generation): the general pipeline involving document embedding → storing in a vector store → similarity querying → injecting context into the LLM prompt <br> - Take notes comparing available vector stores on AWS (RDS + pgvector vs. OpenSearch Serverless) to prepare for the project proposal | 27/06/2026 | 27/06/2026 | [What is RAG? – AWS](https://aws.amazon.com/what-is/retrieval-augmented-generation/) |


### Week 1 Achievements:

*   Got acquainted with FCAJ team members and understood the internship workflow.
*   Gained foundational knowledge of AWS Cloud: global infrastructure, key service categories, and specifically AI/ML services.
*   Created an AWS Free Tier account, enabled MFA, and set up AWS Budgets for cost control.
*   Understood and practiced IAM permission management based on the principle of least privilege, applying it to Bedrock API access permissions.
*   Finalized the "Smart Docs AI" project topic and assumed the role responsible for the AI ​​& RAG component (vector generation, semantic search, prompt design).
*   Grasped RAG concepts and the Amazon Bedrock overview, building a knowledge base for the upcoming implementation weeks.