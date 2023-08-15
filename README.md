Tools being compared:
- Paper QA https://github.com/whitead/paper-qa
- mayooear https://github.com/mayooear/gpt4-pdf-chatbot-langchain
- LlamaIndex https://github.com/jerryjliu/llama_index
- Dagster https://github.com/petehunt/langchain-github-bot
- Onboard https://www.getonboard.dev/chat/zulip/zulip

My personal rank:
1. Onboard
2. Mendable
3. Mayo
4. Paper QA
5. Dagster
6. Unoptimized LlamaIndex

|               | Paper QA            | mayooear | LlamaIndex default| Dagster            |
| ------------- | ------------------- | -------- | ----------------- | ------------------- |
|embedding model| ?                   | ?        | ?                 | ?                   |
|vector DB      | FAISS               | Pinecone | SimpleVectorStore | FAISS               |
| similarity    | FAISS (L2 distance) | cosine   | cosine            | FAISS (L2 distance) |
|response mode  | tree_summarize      | ?        | compact           | langchain stuff     |

All of them use GPT-3.5.

## Prompts

Paper QA
```python
PAPERQA_PROMPT = (
    "Write an answer "
    "for the question below based on the provided context. "
    "If the context provides insufficient information, "
    'reply "I cannot answer". '
    "For each part of your answer, indicate which sources most support it "
    "via valid citation markers at the end of sentences, like (Example2012). "
    "Answer in an unbiased, comprehensive, and scholarly tone. "
    "If the question is subjective, provide an opinionated answer in the concluding 1-2 sentences. \n\n"
    "{context_str}\n"
    "Question: {query_str}\n"
    "Answer: "
)
```

mayooear
```javascript
const QA_PROMPT = `You are a helpful AI assistant. Use the following pieces of context to answer the question at the end.
If you don't know the answer, just say you don't know. DO NOT try to make up an answer.
If the question is not related to the context, politely respond that you are tuned to only answer questions that are related to the context.

{context}

Question: {question}
Helpful answer in markdown:`;
```

LlamaIndex
```python
DEFAULT_TEXT_QA_PROMPT_TMPL = (
    "Context information is below.\n"
    "---------------------\n"
    "{context_str}\n"
    "---------------------\n"
    "Given the context information and not prior knowledge, "
    "answer the question: {query_str}\n"
)
```

Dagster
```python
```

## Questions

Questions 6-8 are rephrases to figure out if the bot would have answered differently based on the phrasing.

Questions asked:
1. How do I configure LDAP authentication in Zulip?
2. How do I import Slack workspace export into a Zulip organization?
3. How do I upgrade my Zulip instance to the latest Git version?
4. How do I create a self-signed SSL certificate for my Zulip server?
5. How do I delete a Zulip organization?
6. Can you explain the rough working of Zulip?
7. Can you describe Zulip architecture, as in, its inner working?
8. Can you describe an overview of Zulip architecture?
9. How do I get an account's username via the Zulip Python API?
10. How I set up a bot for Zulip?
11. What framework does Zulip use for its frontend?
