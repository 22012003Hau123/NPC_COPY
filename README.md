# 📄 NPC Copy Doc Workflow (n8n)

## 🎯 Overview
This repository contains an **n8n workflow** (`NPC_copy_doc.json`) that automates the creation of **Google Docs** from data stored in **Google Sheets**.  
It selects the right Google Docs template based on the number of grammar items, fills in placeholders with data, and updates the source Google Sheet with a link to the generated document.

---

## ⚙️ Features
- ⏱ **Automated schedule**: Runs every 45 seconds via a schedule trigger.
- 📑 **Google Sheets integration**: Reads rows with `Status = Todo`.
- 🔀 **Dynamic template selection**: Chooses between 4 Google Docs templates (0G–3G) depending on grammar count.
- ✍️ **Auto-fill placeholders**: Replaces `{{keys}}` in the document with real data from the sheet.
- 🔗 **Sheet update**: Marks row as `Done` and inserts link to the generated Google Doc.

---

## 🛠️ How It Works
1. **Trigger**: Workflow runs every 45 seconds.
2. **Fetch Data**: Pulls the first row in Google Sheets where `Status = Todo`.
3. **Grammar Count**: A code node counts how many grammar fields are filled.
4. **Switch Node**: Based on grammar count → chooses one of 4 templates:
   - **0G** → no grammar
   - **1G** → 1 grammar
   - **2G** → 2 grammars
   - **3G** → 3 grammars
5. **Copy Template**: Copies the correct Google Docs template from Google Drive.
6. **Format Data**: Processes text, splits lines, counts words, and prepares key-value pairs.
7. **Replace in Doc**: Calls Google Docs API to replace placeholders with actual values.
8. **Update Google Sheets**: Sets row `Status = Done` and adds the generated Google Doc link.

---

## 📂 File Structure
