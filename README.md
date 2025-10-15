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

