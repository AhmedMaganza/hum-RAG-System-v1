# AI-Powered Knowledge Management RAG Agent 
> [!NOTE]
> I am currently rebuilding and synthesizing my professional data pipelines and enterprise models into this public portfolio. To respect strict institutional data governance and non-disclosure agreements, all proprietary datasets are being meticulously anonymized or replaced with high-fidelity synthetic data before deployment. Stay tuned for regular updates!
> 
### *Version 1.0* (Simple RAG Agent Prototype)

<img width="975" height="533" alt="image" src="1.png" />
<img width="975" height="333" alt="image" src="2.png" />

Simple RAG Agent Prototype. It reads docx files form google drive folder and convert them to google docs to be chunked and loaded to the vector database. Then the user interacts with the agent via chat interface to retrieve information.

## Use Case
A Program Officer in a local NGO is trying to prepare a report on the humanitarian projects and interventions implemented in a district with a predefined duration. This report will be provided to the management as evidence to support resource prioritization. The PO is using the RAG agent to extract and prepare the report.

## System Components
### 01. Data Workflow
-	Reads Created/Updated docx files from google drive.
-	When updating the file, remove the old copy.
-	Convert Docx files to Google documents before downloading/extracting text. This magnificently reduces the files size and results in boosting performance as it prevents browser freeze or loading massive-sized files to the system.
-	Chunk the data and load it to the vector database.
### 0.2 Agent
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

## *version 2.0* (State-Driven Approach)
<img width="975" height="507" alt="image" src="3.png" />
<br>
A transition from the old trigger-based setup to a robust, bulk-processing RAG agent.

### New Features:
-	Change the flow from "Event-Driven" (one file at a time) to "State-Driven" (scanning and checking google drive folder).
-	Based on a schedule trigger, It searches for files added/updated to the google drive folder (determine via metadata).
-	Notify the user/team of files added/updated via Slack.


## *version 2.0.1*
<img width="975" height="473" alt="image" src="4.png" />
<img width="975" height="232" alt="image" src="5.png" />

### New Features:
-	An error-handler for corrupted/empty files.
-	An error-handler for empty google drive folder.
-	Manage rate limits (Wait Node)
-	meta-data tagging (to decide whether to add data to the vector database)
-	Added a RESET Workflow (remove tags from “appProperties”, “properties”)



