Fortunately there are many providers for LLM's and some of them can even be ran locally

There are two models used in the app:
1. Embeddings
2. Text generation

By default we use OpenAI's models but if you want to change it or even run it locally, its very simple!

### Go to .env file or set environment variables:

`LLM_NAME=<your Text generation>`

`API_KEY=<api_key for Text generation>`

`EMBEDDINGS_NAME=<llm for embeddings>`

`EMBEDDINGS_KEY=<api_key for embeddings>`

`VITE_API_STREAMING=<true or false (true if using openai, false for all others)>`

You dont need to provide keys if you are happy with users providing theirs, so make sure you set LLM_NAME and EMBEDDINGS_NAME

Options:  
LLM_NAME (openai, manifest, cohere, Arc53/docsgpt-14b, Arc53/docsgpt-7b-falcon)  
EMBEDDINGS_NAME (openai_text-embedding-ada-002, huggingface_sentence-transformers/all-mpnet-base-v2, huggingface_hkunlp/instructor-large, cohere_medium)

Thats it!

### Hosting everything locally and privately (for using our optimised open-source models)
If you are working with important data and dont want anything to leave your premises.

Make sure you set SELF_HOSTED_MODEL as true in you .env variable and for your LLM_NAME you can use anything thats on Huggingface 
