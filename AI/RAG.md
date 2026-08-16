LLM - Twinkle twinkle little -----
- Predict next word

LLM vs 
## AI agent
- can actually do the job
- LLM + Tools + API
- API - Programmatical way of calling a s/w
- Agentic system - reasoning loop
- 


Problems
- fine tuning does not work for frequently changing data (external data) Ex. polices
- Retrieval Augmented Generation


RAG 
- Connect llm with external knowledge
- embedding is way of converting word to vector (stack of numbers )
- king and prince => their embedding will be more similar

![](attachments/Pasted%20image%2020260811200624.png)

Chunking - breaking a big document into smaller vectors
- Embed individual chunks
- Chunking techniques - Recursive character text splitter
- chunkviz.up.railway.app
- Chunk size depends on documents

Vector embedding
Semantic search
- User query into embeddings, match with chunk => similarity search => select top k chunks => all the context of relevant chunk only loaded in the memory
- Context window is amount of text, LLM eat at a time

FOCUS ON CONCEPT, CODE IS HOW YOU IMPLEMENT

Basic RAG => improve it (scalability) => case studies => 

![](attachments/Pasted%20image%2020260811202821.png)

API Key? OpenAI, Groq, 

Langchain, langgraph, => frameworks, or wrappers around 
- We don't have to write boilerplate python code

Vector database

RAG Pipeline - series of steps
Knowledge Base 

pydantic in python
Reranking: fixed precision not just coverage


Basic RAG - fragments, coverage, re ranking

Basic 
Adaptive 
Corrective 
Agentic RAG

![](attachments/Pasted%20image%2020260811213502.png)
