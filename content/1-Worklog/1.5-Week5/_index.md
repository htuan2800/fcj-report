---
title: "Week 5 Log"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---
### Week 5 Objectives:

*   Refine response quality: chunk size, similarity threshold, and context injection method into the Prompt.
*   Set up dedicated CloudWatch Alarms for AI/RAG-related Lambda functions (`create-vector`, `vector-search`, `ChatbotRAG`).
*   Optimize Amazon Bedrock invocation costs (limit `top-k`, avoid unnecessary redundant calls).

### Tasks to be implemented this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon | - Fine-tune chunk size (experiment with 1,500 / 2,500 / 3,500 characters with varying overlaps) and re-evaluate response quality using the same test question set <br> - Configure dedicated CloudWatch Alarms for `create-vector`, `vector-search`, and `ChatbotRAG` Lambda functions: monitor error counts, processing time (specifically Bedrock call latency), and throttling events | 20/07/2026 | 20/07/2026 | [Using Amazon CloudWatch alarms](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html) |
| Tue | - Optimize similarity threshold (cosine distance) and the number of chunks (`top_k`) injected into the Prompt: reduce redundant chunks to lower LLM input tokens, thereby cutting costs and minimizing contextual noise <br> - Re-measure Bedrock invocation costs before and after `top_k` optimization using the same test question set | 21/07/2026 | 21/07/2026 | [Amazon Bedrock Pricing](https://aws.amazon.com/bedrock/pricing/) |
| 4 | - Evaluate switching the Bedrock model used for response generation (try `amazon.nova-lite-v1:0`); compare quality and latency against the previous model using the same set of sample questions <br> - Update the prompt to align with the new model's input/output format | 22/07/2026 | 22/07/2026 | |
| 5-6 | - Review and refine the prompt: add instructions to cite source document names in responses; handle cases where no relevant chunk is found (respond with "no information in documents" instead of attempting an answer) <br> - Retest 10 edge-case questions (ambiguous questions, out-of-scope questions, questions requiring synthesis from multiple documents) | 23/07/2026 | 24/07/2026 | |
| 7 | - Team meeting: review progress; peer-review and provide feedback on the report I authored <br> - Participate in the "FCAJ x Agentic AI Build Week powered by GenAI Fund" hackathon | 25/07/2026 | July 25, 2026 | |


### Week 5 Achievements:

* Fine-tuned chunk size/overlap parameters and similarity thresholds, resulting in a marked improvement in response quality.
* Implemented dedicated CloudWatch Alarms for AI/RAG Lambda functions to proactively detect errors or abnormal latency during Bedrock API calls.
* Optimized Amazon Bedrock costs by reducing the number of chunks (`top_k`) included in the prompt while maintaining response quality.
* Evaluated a new Bedrock model and updated prompts for compatibility.
* Refined prompts to handle edge cases (e.g., information not found, ambiguous questions) and ensure proper source citations.
* Participated in the "FCAJ x Agentic AI Build Week powered by GenAI Fund" hackathon (July 25, 2026).