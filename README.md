# 🦷 AI Voice Receptionist for Dental Clinic

**An autonomous voice AI agent designed to handle patient calls, qualify needs, book appointments, and instantly log call summaries to a private Discord server.**

Built with: **Retell AI, n8n, MongoDB, and Discord.**

---

## 📸 Project Overview

This project demonstrates a complete voice automation loop. A user triggers a call via a web link, the AI conducts a natural conversation to gather information, and the data is instantly processed and logged for clinic staff.

### 1. The "Brain" (n8n Automation)
This is the backend listener workflow. It waits for Retell AI to finish a call, receives the transcript analysis via webhook, filters the event, and formats the data for delivery.

![Discord Summary Screenshot](The_n8n_Workflow.png)

### 2. The Result (Discord Log)
Immediately after the patient hangs up, the clinic staff receives a structured summary of the conversation in their private Discord channel.

![n8n Workflow Screenshot](discord_workflow.png)

---

## 🚀 Key Features

* **🗣️ Natural Voice Interaction:** Powered by **Retell AI** (utilizing LLMs like GPT-4o) for low-latency, human-like conversation.
* **⚙️ Automated Orchestration:** Utilizes **n8n** workflows to handle both initiating calls and processing post-call events.
* **📁 Persistent Storage:** Patient lead data is securely saved to **MongoDB Atlas** at the start of the interaction.
* **📝 Real-time Alerts:** Call summaries, actions taken, and sentiment analysis are instantly pushed to **Discord** via webhooks.

## 🛠️ Tech Stack

* [Retell AI](https://www.retellai.com/) - Voice Agent Platform & Telephony
* [n8n](https://n8n.io/) - Workflow Automation & API Integration
* [MongoDB Atlas](https://www.mongodb.com/atlas) - NoSQL Database
* [Discord Webhooks](https://discord.com/) - Instant Notifications

## ⚙️ How it Works (Workflow Summary)

1.  **Trigger:** A webhook receives a request containing a patient's phone number.
2.  **Database Log:** The lead info is saved to MongoDB.
3.  **Call Initiation:** n8n via API tells Retell AI to call the phone number.
4.  **AI Conversation:** The Retell agent (Sarah) converses with the patient to determine their needs (Checkup vs. Emergency) and preferred time.
5.  **Event Processing:** Once the call ends, Retell sends a webhook payload containing the call analysis back to n8n.
6.  **Notification:** n8n formats this analysis and posts it to the designated Discord channel.
