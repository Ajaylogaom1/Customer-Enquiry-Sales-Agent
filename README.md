# Customer-Enquiry-Sales-Agent

A **client-ready demo AI workflow** that automates e-commerce customer support using **n8n**, **Telegram**, and an **AI chat model**.

## 🚀 What This Workflow Does

- Receives customer messages from **Telegram**
- Uses **AI** to understand customer intent
- Converts AI output into **structured JSON**
- Routes conversations using **Switch & IF logic**
- Generates **automatic customer replies**
- Logs chats into a **CRM (Airtable)**
- Escalates complex cases to a **human/admin**

This workflow simulates a **real e-commerce support system** without hiring support staff.

---

## 🧠 Supported Intents

The AI detects and classifies customer messages into intents such as:

- `order_status`
- `product_question`
- `refund_request`
- `talk_to_human`

Each intent follows a different automated path.

---

## 🧱 Workflow Overview

Telegram Trigger  
→ AI Intent Detection  
→ Confidence Validation  
→ Intent Routing (Switch)  
→ AI Reply Generation  
→ Auto Reply to Customer  
→ CRM Logging  
→ Admin Escalation (if required)

---

## 🔗 Node-by-Node Explanation

### 1️⃣ Telegram Trigger
Listens for incoming customer messages from Telegram.

---

### 2️⃣ Edit Fields
Prepares and cleans incoming message data before sending it to the AI.

---

### 3️⃣ AI Agent (Chat Model + Output Parser)
- Analyzes the customer message
- Detects intent
- Returns **structured JSON**

**Example Output:**
```json
{
  "intent": "order_status",
  "confidence": 1
}
# 4️⃣ IF Node – Confidence Check

Prevents incorrect AI replies.

If confidence < 0.5 → escalate to admin

Else → continue automation

This makes the system reliable and safe for businesses.

# 5️⃣ Switch Node – Intent Routing

Routes conversations based on detected intent.

Each output path handles a different customer request.

# 6️⃣ Message a Model – Reply Generator

Generates a friendly, short, and professional reply.

Reply rules:

Max 2 sentences

E-commerce support tone

Clear and polite language

# 7️⃣ Auto Reply (Telegram)

Sends the AI-generated reply back to the customer instantly.

# 8️⃣ Create Record (CRM / Airtable)

Logs all conversations for tracking and reporting.

Stored data includes:

Customer message

Detected intent

Confidence score

AI reply

Escalation status

Timestamp

# 9️⃣ IF Node – Escalation Logic

Checks if a human agent is required.

Triggers when:

Intent = talk_to_human

Or confidence is low

🔟 Admin Notification (Telegram)

Sends an alert to the admin/support team with customer details.
