# DocQNBot


## Project Overview

DocQNBOT is an AI-powered Question-Answering system that enables users to ask questions based on the content of Google Documents. It automates document processing, extracts content, converts it into vector embeddings, and utilizes an LLM model to generate responses.

### Features

📂 Google Drive Integration – Monitors changes in a specific Google Doc.

📜 Text Extraction – Reads document content whenever updated.

🔢 Vector Embeddings – Converts text into embeddings for semantic search.

🗄️ Supabase Storage – Stores document embeddings in a PostgreSQL database.

🤖 LLM-Powered Q&A – Retrieves relevant content and generates answers using an AI model.

### Tech Stack

n8n – Workflow automation for handling data processing.

Google Drive API – Accesses and monitors Google Docs.

Supabase – Stores document embeddings and query results.

PostgreSQL with Vector Extension – Enables similarity search.

OpenAI API (or equivalent LLM) – Generates answers based on retrieved content.

### System Architecture

1️⃣ Google Drive Trigger – Detects document updates using n8n.
2️⃣ Text Extraction – Extracts text from Google Docs.
3️⃣ Vector Embedding Generation – Converts text into numerical representations.
4️⃣ Supabase Storage – Saves document embeddings in a PostgreSQL database.
5️⃣ User Query Processing – Searches for relevant document content.
6️⃣ LLM Answer Generation – Uses an AI model to generate human-like answers.

### Installation & Setup

1. Install n8n

npm install -g n8n

Or run n8n using Docker:

docker run -it --rm -p 5678:5678 n8nio/n8n

2. Connect Google Drive API

Enable Google Drive API in Google Cloud Console.

Create OAuth 2.0 credentials and add them to n8n.

Allow necessary permissions for document access.

3. Set Up Supabase Database

Create a new Supabase project.

Enable the vector and uuid-ossp extensions:

create extension if not exists "uuid-ossp";
create extension if not exists vector;

Create the document_embeddings table:

create table document_embeddings(
  id uuid default uuid_generate_v4() primary key,
  doc_name text,
  content text,
  embedding vector(1536)
);

4. Configure n8n Workflow

Set up a Google Drive Trigger node to detect document changes.

Use an HTTP Request node to extract document content.

Process the text into embeddings and store them in Supabase.

Configure an API endpoint in n8n to handle user queries.

Retrieve relevant document embeddings and generate answers using an LLM model.

### Usage

1️⃣ Upload a Google Document and let n8n process it.
2️⃣ Ask a question via the n8n interface.
3️⃣ The system retrieves relevant document data and generates an AI-powered answer.

### Future Enhancements

✅ Improve retrieval performance with advanced search techniques.

✅ Add a frontend for user interaction.

✅ Support multiple document types beyond Google Docs.

Contributors

[Somya Jain] – Developer & Architect

License

This project is open-source and licensed under the MIT License.

