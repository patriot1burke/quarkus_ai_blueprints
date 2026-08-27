
# Retrieval and RAG

Enterprise knowledge bases that you can query with AI.

LLMs have a limitation on what they are trained on.  You can still use an LLM to query and analyze your company's
data, web sites, and documentation through a concept called [RAG]() (Retrieval Augmented Generation).
With RAG, you chunk and index your documentation and information within a Vector DB. At runtime, a user's query is turned into
a vector and a similarity search is done within the Vector DB to pull all relevant text and information.  These
chunks are sent to the LLM along with the user's query and the LLM generates a response from it.  Granted, there
is more going on here, but that's the gist of it.

## Quarkus Easy RAG

If you just have a handful of documents that you want to chat about with your LLM, Quarkus Easy RAG, 
allows you define a directory with your documents, and it will automatically be wired with in.  No extra code.

## Advanced RAG Pipelines

RAG is generally more complex.  You may have multiple sources of information you are federating together.  There are various
techniques to improve the quality of the results (i.e. Hybrid Search, Prompt Engineering, etc.).  Bringing all these techniques
together is called a [RAG Pipeline](https://docs.langchain4j.dev/tutorials/rag#advanced-rag).  Quarkus AI has [abstractions
and APIs](https://docs.quarkiverse.io/quarkus-langchain4j/dev/rag.html) to help build each stage of this pipeline.

![RAG Pipeline](https://quarkus.io/assets/images/ai/contextualrag-query.webp)

