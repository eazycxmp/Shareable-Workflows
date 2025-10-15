# 🎧 AI Call Summary Workflow (CSM Summary to Slack)

This repository contains a sanitized version of an **n8n workflow** that automatically summarizes customer call transcripts into structured **Gainsight-style CSM notes**, then posts them directly to Slack.

---

## 🚀 Overview

This workflow takes a transcript (manually or from Google Drive), runs it through **OpenAI**, and outputs a concise, structured summary with:

- Call Purpose  
- Customer Concerns  
- Next Steps / Tasks  
- Owner / Action Items  

The summary is then automatically formatted and posted to a specified Slack channel.

---

## 🧠 Workflow Logic

**Nodes Breakdown**
1. **Trigger: Manual Run** – Starts the workflow manually.  
2. **Input Transcript (Manual)** – Option to paste transcript text directly.  
3. **Check Transcript Source** – Conditional check to decide whether to use manual input or Google Docs source.  
4. **Get Transcript from Google Docs** – Fetches a transcript file from Google Drive (if not entered manually).  
5. **Convert File to Text** – Converts `.docx` or `.txt` file content into text format.  
6. **Combine Transcript Paths** – Merges input paths so all transcripts flow into one unified text stream.  
7. **Generate Gainsight Summary (OpenAI Node)** –  
   Prompts the model with:

Summarize the following customer call transcript into clear, structured CSM notes for Gainsight.

Include:

Call Purpose

Customer Concerns

Next Steps / Tasks

Owner / Action Items

Keep it concise and professional.

Transcript:
{{$json["transcript"]}}

8. **Send Summary to Slack** – Posts the AI-generated summary to Slack with the message:

Call Summary
{{$json["message"]["content"] || $json["data"][0]["message"]["content"] || $json["choices"][0]["message"]["content"]}}


---

## ⚙️ Setup Instructions

### 1. Import Workflow
- Open n8n → **Workflows → Import → From File**
- Select `workflow-sanitized.json`

### 2. Create Credentials
Replace any placeholder credentials with your own:
- **Slack API Token** → for posting messages
- **Google Drive / Google Docs credentials** → for file fetching
- **OpenAI API Key** → for summarization

**Important:** none of these are included in the repo.  
Define them inside n8n under **Credentials** and assign them manually to each relevant node.

### 3. Environment Variables (optional)
You can reference credentials via `.env`:


### 4. Test the Flow
Run manually in n8n.  
Paste a transcript or select a Google Drive file → the workflow summarizes and sends it to Slack.

---

## 🧩 Files Included

README.md
workflow-sanitized.json
SHARE_INSTRUCTIONS.txt
.env.example


---

## 🔒 Security Notes
- All credentials are **removed** from this workflow export.  
- Do not upload `.env` or credentials to GitHub.  
- Check your `.gitignore` to make sure `.env` is excluded.

---

## 🧠 Why It’s Useful
For Customer Success Managers, this automation eliminates the manual work of:
- Writing post-call summaries
- Formatting for Gainsight or Slack
- Remembering follow-ups  

Use it as a template for similar automations like:
- AI ticket summaries  
- Sales call recaps  
- Product feedback digest  

---

## 📘 Learn More
- [n8n Documentation](https://docs.n8n.io)
- [OpenAI API Reference](https://platform.openai.com/docs)
- [Slack API](https://api.slack.com)



