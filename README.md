 <div align="center">

<img src="https://images.unsplash.com/photo-1504711434969-e33886168f5c?auto=format&fit=crop&w=1600&q=85" alt="News publication and journalism" width="100%" />

# ◉ AI NEWS INTELLIGENCE

### AI News Summarizer with SerpAPI & n8n

  **Less scrolling. More understanding. One intelligent news digest.**
  
  An automated news-processing workflow that combines RSS feeds and web search results, uses Google Gemini to generate concise summaries, and   delivers the output through Gmail.

<p>
<img src="https://img.shields.io/badge/n8n-Workflow%20Automation-EA4B71?style=flat-square&logo=n8n&logoColor=white" alt="n8n" />
<img src="https://img.shields.io/badge/SerpAPI-Web%20Search-222222?style=flat-square" alt="SerpAPI" />
<img src="https://img.shields.io/badge/Google%20Gemini-Generative%20AI-4285F4?style=flat-square&logo=google&logoColor=white" alt="Google Gemini" />
<img src="https://img.shields.io/badge/Gmail-Email%20Delivery-EA4335?style=flat-square&logo=gmail&logoColor=white" alt="Gmail" />
<img src="https://img.shields.io/badge/License-MIT-2EA44F?style=flat-square" alt="MIT License" />
</p>

</div>

---

## ◈ 01 — The Concept

  News moves quickly. Valuable information is spread across websites, feeds, and search results, making it difficult to keep up with            everything that matters.

  **AI News Summarizer** explores a smarter approach: automatically collect information from multiple configured sources, combine the           results, and use generative AI to create a digest that is easier to read.

  Instead of manually opening multiple sources and summarizing articles one by one, this workflow connects the collection, processing, and      delivery stages in a single automated pipeline.
  
  > **The mission:** Transform scattered news information into a concise, AI-assisted briefing.

## ◈ 02 — The Intelligence Pipeline

<div align="center">

<img src="https://images.unsplash.com/photo-1451187580459-43490279c0fa?auto=format&fit=crop&w=1200&q=85" alt="Global information networks and digital connectivity" width="100%" />

</div>

### What the workflow does

  - **Scheduled collection:** Starts automatically according to the configured schedule.
  - **Multi-source ingestion:** Collects information from two configured RSS feeds.
  - **Search integration:** Uses an HTTP Request node to retrieve results from SerpAPI.
  - **Data consolidation:** Combines incoming data through a Merge node.
  - **Content aggregation:** Organizes collected items using an Aggregate node.
  - **AI summarization:** Uses Google Gemini through a Basic LLM Chain.
  - **Email delivery:** Sends the generated news digest through Gmail.

## ◈ 03 — Workflow Architecture

  The following diagram reflects the node connections visible in the n8n workflow screenshot.

  ```mermaid
  flowchart TD
      A["⏰ Schedule Trigger"]
  
      B["📰 RSS NormalTech"]
      C["📰 RSS AIBusiness"]
      D["🔎 HTTP Request · SerpAPI"]
  
      E["🔀 Merge · Append"]
      F["📦 Aggregate"]
      G["🧠 Basic LLM Chain"]
      H["✨ Google Gemini Chat Model"]
      I["📧 Gmail · Send a Message"]

      A --> B
      A --> C
      A --> D
  
      B --> E
      C --> E
      D --> E
  
      E --> F
      F --> G
      H -. AI model .-> G
      G --> I
  
      style A fill:#172554,color:#FFFFFF,stroke:#60A5FA
      style B fill:#164E63,color:#FFFFFF,stroke:#67E8F9
      style C fill:#164E63,color:#FFFFFF,stroke:#67E8F9
      style D fill:#312E81,color:#FFFFFF,stroke:#A5B4FC
      style E fill:#334155,color:#FFFFFF,stroke:#94A3B8
      style F fill:#334155,color:#FFFFFF,stroke:#94A3B8
      style G fill:#4C1D95,color:#FFFFFF,stroke:#C4B5FD
      style H fill:#1D4ED8,color:#FFFFFF,stroke:#93C5FD
      style I fill:#991B1B,color:#FFFFFF,stroke:#FCA5A5
  ```

### The process, step by step

**01. Trigger the workflow**

   The Schedule Trigger initiates execution based on the interval configured in n8n.

**02. Collect from RSS feeds**

   The RSS nodes retrieve news items from the configured NormalTech and AIBusiness feeds.

**03. Search the web with SerpAPI**

   The HTTP Request node calls the configured SerpAPI endpoint to retrieve search results. The query and returned information depend on your     node settings.

**04. Merge the incoming information**

   The Merge node combines items from the three incoming branches using its configured append operation.

**05. Aggregate the content**

   The Aggregate node organizes the merged items for the next processing stage.

**06. Generate an AI summary**

   The Basic LLM Chain uses the connected Google Gemini Chat Model to process the collected content according to the configured prompt.

**07. Deliver the digest**

   The Gmail node sends the generated message to the configured recipient.

   *The quality and format of the digest depend on the configured RSS sources, SerpAPI query, aggregation settings, AI prompt, and Gmail         message template.*

## ◈ 04 — Workflow Preview

 <img src="https://res.cloudinary.com/dntdfccdk/image/upload/v1792166776/Screenshot_2026-10-16_213410_be9kvk.png" alt="AI news summarizer  serpAPI n8n " width="100%" />

## ◈ 05 — Technology Stack

  | Technology | Purpose |
  |---|---|
  | **n8n** | Visual workflow orchestration |
  | **RSS feeds** | News collection from configured sources |
  | **SerpAPI** | Search-engine result retrieval through an API |
  | **HTTP Request** | Connects n8n to the SerpAPI endpoint |
  | **Merge** | Combines incoming items |
  | **Aggregate** | Organizes collected content |
  | **Google Gemini** | AI-powered news summarization |
  | **Basic LLM Chain** | Coordinates the summarization process |
  | **Gmail** | Automated email delivery |
  | **Mermaid** | Workflow visualization in the README |

## ◈ 06 — Setup & Configuration

### Requirements

  Before running this workflow, prepare:
  
  - An n8n account or self-hosted n8n instance.
  - Working RSS feed URLs.
  - A SerpAPI account and API key.
  - Google Gemini access and the required credentials.
  - A Gmail account with the necessary authorization.
  - The exported n8n workflow JSON file.

### Installation

**Step 1 — Import the workflow**

   Export the workflow from n8n as a JSON file. Import that file into your own n8n workspace.

**Step 2 — Configure the RSS feeds**

   Open both RSS nodes and verify their feed URLs and any other required settings.

**Step 3 — Configure SerpAPI**

   Set the HTTP Request URL, query parameters, and authentication according to the SerpAPI endpoint you intend to use. Store your API key        securely rather than hardcoding it in a public workflow.

**Step 4 — Connect Google Gemini**

   Configure the required credentials and confirm that the Basic LLM Chain uses the intended model.

**Step 5 — Review Merge and Aggregate**

   Confirm that all three branches supply the expected data and that the aggregated output contains the fields needed by your AI prompt.

**Step 6 — Configure the AI prompt**

   Specify the desired summary style, length, important fields, and instructions for handling missing or uncertain information.

**Step 7 — Configure Gmail**

   Authorize Gmail and set the recipient, subject, and message body.

**Step 8 — Test before activation**

   Run the workflow manually. Inspect the data at each stage, check the generated summary, and verify that the email arrives correctly.

**Step 9 — Enable scheduled execution**

   After successful testing, activate or publish the workflow according to your n8n version and configuration.

## ◈ 07 — Output & Expected Result

  The intended output is an email digest containing AI-generated summaries of collected news information.
  
  Depending on your prompt and data mapping, a useful digest could contain:
  
  - News headline
  - Short summary
  - Source name
  - Original article URL, when available
  - Key takeaways
  - Publication date, when available
  
  These are suggested output fields; the actual email content depends on your implementation.

## ◈ 08 — Potential Enhancements

  The workflow can be expanded into a more capable news intelligence system:
  
  - [ ] Categorize articles into AI, technology, business, science, and other topics.
  - [ ] Filter search results by specific keywords.
  - [ ] Detect duplicate stories across RSS feeds and search results.
  - [ ] Preserve source links for fact-checking and further reading.
  - [ ] Add article relevance scoring.
  - [ ] Generate daily or weekly digest emails.
  - [ ] Support different summary lengths and formats.
  - [ ] Add error handling and failure notifications.
  - [ ] Store processed stories in Google Sheets or a database.
  - [ ] Track previously processed URLs to avoid repeating stories.

## ◈ 09 — Security & Responsible AI

  - Never commit API keys, OAuth tokens, passwords, or private credentials.
  - Use n8n's credential manager for supported authentication methods.
  - Inspect exported workflow JSON files before publishing them.
  - Avoid including personal information in screenshots or sample data.
  - Respect the terms of use and rate limits of RSS sources and SerpAPI.
  - Check summaries against original sources before relying on important claims.
  - Remember that AI summaries may omit context or contain errors.

## ◈ 10 — Project Learnings

  This project explores practical skills in:
  
  - Building multi-branch workflows with n8n.
  - Integrating external search APIs through HTTP requests.
  - Combining data from different sources.
  - Aggregating content for downstream processing.
  - Using generative AI for summarization.
  - Automating email delivery.
  - Debugging workflow executions and managing credentials.

## ◈ 11 — Repository Structure

  A suggested structure for publishing the project:
  
  ```text
  ai-news-summarizer-serpapi-n8n/
  ├── README.md
  ├── LICENSE
  ├── workflow/
     └── ai-news-summarizer.json
  ```

  Add only the files you actually include. Before committing the JSON export, remove sensitive information and verify that the workflow can     be imported safely.

## ◈ 12 — About the Creator

**Kalikowsik**

  Aspiring Full Stack Developer | AI & Automation Enthusiast
  
  Exploring practical applications of generative AI, APIs, and workflow automation by building projects that connect intelligent systems with everyday tasks.
  
  - GitHub: https://github.com/kanithikalikowsik
  - LinkedIn: www.linkedin.com/in/kanithi-kali-kowsik

## ◈ License

  This project is distributed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

---

<div align="center">

### THE FUTURE IS LESS ABOUT MORE INFORMATION.
### IT'S ABOUT BETTER UNDERSTANDING.

**Collected with APIs · Summarized with AI · Delivered through automation**

If you find this project useful, consider giving the repository a ⭐.

</div>
