## Design and Implementation of a Multidocument Retrieval Agent Using LlamaIndex
## AIM:
To design and implement a multidocument retrieval agent using LlamaIndex (formerly known as GPT Index), which extracts and synthesizes information from multiple research articles and to evaluate its performance by testing it with diverse queries, analyzing its ability to deliver concise, relevant, and accurate responses.

## PROBLEM STATEMENT:
The objective is to create an agent that can handle multiple research articles or documents and retrieve relevant information based on user queries. By leveraging LlamaIndex, we aim to build an efficient retrieval system that can access multiple documents, extract the necessary data, and synthesize it into meaningful responses, improving the speed and accuracy of information retrieval.

## DESIGN STEPS:
### STEP 1: Set Up the Environment
 - Install the necessary Python packages: LlamaIndex (GPT Index), openai, and any other dependencies (e.g., requests, pdfplumber for PDF parsing).
 - Obtain the OpenAI API key (or other model keys for retrieval).
```bash
pip install llama_index openai
```
### STEP 2: Data Ingestion and Indexing
 - Collect the research articles or documents in a structured format (PDF, Word, or plain text).
 - Use LlamaIndex to create an index for the documents, which will allow for efficient retrieval of information.
 - If the documents are in PDF format, use a PDF parsing library (e.g., pdfplumber or PyMuPDF) to extract text.
### STEP 3: Build the Retrieval Agent
 - Implement the agent that will:
 - Load and index the documents using LlamaIndex.
 - Accept a user query.
 - Retrieve the most relevant sections from the documents based on the query.
 - Synthesize the responses and generate a concise answer.
### STEP 4: Testing and Evaluation
 - Create various queries that test the agent's ability to extract and synthesize information from multiple documents.
 - Measure the performance by evaluating the relevance, accuracy, and conciseness of the retrieved answers.

## PROGRAM:
```python
import openai
from llama_index import GPTSimpleVectorIndex, SimpleDirectoryReader
from llama_index import ServiceContext

# Step 1: Set OpenAI API Key (for LlamaIndex to use)
openai.api_key = 'your-openai-api-key'  # Replace with your actual OpenAI API key

# Step 2: Load and index multiple documents
def build_document_index(doc_directory: str):
    # Load documents from the directory (can be PDFs, text files, etc.)
    documents = SimpleDirectoryReader(doc_directory).load_data()
    
    # Create an index using LlamaIndex
    service_context = ServiceContext.from_defaults()
    index = GPTSimpleVectorIndex.from_documents(documents, service_context=service_context)
    
    return index

# Step 3: Query the index and synthesize the result
def query_index(index, user_query: str) -> str:
    response = index.query(user_query)
    return response.response

# Example Usage:
doc_directory = 'path_to_your_documents'
index = build_document_index(doc_directory)

# Query the index with a sample question
user_query = "What are the main findings of the research on AI in healthcare?"
response = query_index(index, user_query)

# Output the result
print("Query Response: ", response)
```

## OUTPUT:


## RESULT:
Prompt Handling: The program constructs a query dynamically and feeds it into the LlamaIndex.
Document Indexing: LlamaIndex efficiently indexed multiple documents (research articles) to retrieve the relevant context.
Query Response: The system retrieved concise, relevant, and accurate responses by synthesizing the content from the indexed documents.
