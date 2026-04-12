# AI-Powered RAG System v1.0
***Simple RAG Agent Prototype

<img width="975" height="533" alt="image" src="https://github.com/user-attachments/assets/9a3815a7-50ee-496b-bc37-8f8e8a28ad4c" />
<img width="975" height="333" alt="image" src="https://github.com/user-attachments/assets/b51b60b5-e273-4b1c-b3ac-dd098419bfb2" />

Simple RAG Agent Prototype. It reads docx files form google drive folder and convert them to google docs to be chunked and loaded to the vector database. Then the user interacts with the agent via chat interface to retrieve information.

## Use Case:
A Program Officer in a local NGO is trying to prepare a report on the humanitarian projects and interventions implemented in a district with a predefined duration. This report will be provided to the management as evidence to support resource prioritization. The PO is using the RAG agent to extract and prepare the report.

## System Flow
### Data Workflow:
-	Reads Created/Updated docx files from google drive.
-	When updating the file, remove the old copy.
-	Convert Docx files to Google documents before downloading/extracting text. This magnificently reduces the files size and results in boosting performance as it prevents browser freeze or loading massive-sized files to the system.
-	Chunk the data and load it to the vector database.
### Agent:
-	The user request information via the chat interface.
-	The agent then connects to the vector database and retrieves the information.
-	The chat has a memory (PostgresSQL) in supabase.
Testing and Evaluation:
 Will do later

## Set backs:
-	Reads only one file at a time, usually the last created/updated file in the google drive folder.
-	The agent fabricates information if it can find none.
-	When updating the files, old files are removed from google drive. However, data stored in the vector database isn’t removed and may cause confusion/weaken data quality.
-	No error-handling whatsoever (Empty google drive folder, corrupted files …)
-	No guardrails and security.
-	No data governance


