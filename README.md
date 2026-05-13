# 🏷️ Data Labeling for AI Systems — Forage Simulation

> A hands-on professional simulation covering the end-to-end workflow of labeling customer support messages for machine learning pipelines.

---

## 📌 Overview

This project documents my completion of a **Data Labeling Simulation** built on real-world AI training workflows. The simulation was structured around labeling short customer-support messages using a three-label schema — **Intent**, **Sentiment**, and **PII Flag** — and then reviewing labels produced by others using a structured quality-assurance framework.

Data labeling is the invisible backbone of every AI system. Without accurately labeled data, machine learning models cannot learn patterns, classify inputs, or make reliable predictions. This simulation offered practical exposure to the precision, consistency, and ethical responsibility that professional data labelers are expected to uphold.

---

## 🧠 What I Learned

### 1. The Three-Label Schema

Every customer message was evaluated across three independent dimensions:

| Label | Options | Purpose |
|-------|---------|---------|
| **Intent** | Billing, Technical, Account, Other | Tells the model *what* the user wants |
| **Sentiment** | Positive, Neutral, Negative | Tells the model *how* the user feels |
| **PII Flag** | Yes / No | Signals whether personal data is present and must be handled securely |

**Intent Categories:**
- `Billing` — Charges, refunds, invoices, payment methods, subscriptions
- `Technical` — App errors, bugs, connectivity, login issues (non-billing)
- `Account` — Profile/contact updates, access requests, account status
- `Other` — Anything outside the above (shipping, small talk, general questions)

**Sentiment Categories:**
- `Positive` — Gratitude, praise, satisfaction
- `Neutral` — Matter-of-fact, informational, unclear emotion
- `Negative` — Frustration, complaints, urgency, threats to cancel

---

### 2. PII Identification & Data Privacy

Using the **PII Quick Card**, I learned to identify and flag Personally Identifiable Information without ever copying or storing it. PII types covered include:

- **Contact:** Full name, email address, phone number, physical address
- **Identifiers:** Customer IDs paired with names/emails, government IDs
- **Financial:** Credit/debit card numbers (any part), bank account or routing numbers
- **Auth:** Usernames paired with passwords, reset links, tokens
- **Device/Network:** IP addresses, device IDs, MAC addresses (when tied to a person)
- **Special/Sensitive PII (Escalate):** SSNs, passport numbers, full 16-digit card numbers, IBANs, health info, date of birth combined with name/address

> ⚠️ **Key rule:** When in doubt, flag PII = Yes. Never copy or retype sensitive data into rationale notes. Generalize: *"email present," "last 4 digits," "account number present."*

---

### 3. Edge Case Reasoning

Not every message fits neatly into a category. I developed structured reasoning for ambiguous cases:

- **Multiple topics** → Choose the dominant request (first explicit ask or majority of text)
- **Equal weight** → Prefer `Account` over `Other`; prefer `Technical` over `Billing` when a technical issue *causes* a billing outcome
- **Mixed tone** → Any strong frustration/complaint → `Negative`; mild annoyance without explicit complaint → `Neutral`
- **Polite phrasing** → Tone depends on *emotion*, not politeness. "Could you please help?" can still be `Neutral`
- **Emojis / ALL CAPS** → Use as supporting clues; primary decision from text content

**Edge Case Note Format:**
```
I chose [Intent] because [primary request evidence]. I picked [Sentiment] because [tone evidence].
```

---

### 4. Label Review — Keep / Fix / Flag Framework

In Task 2, I shifted from labeler to **reviewer**, applying a QA framework to evaluate five sets of labels produced by others:

| Decision | When to Use |
|----------|-------------|
| ✅ **Keep** | Labels follow guidelines and are consistent — no changes needed |
| 🔧 **Fix** | One or more labels are incorrect or inconsistent — explain what should change |
| 🚩 **Flag** | Message is ambiguous or the guideline doesn't fully cover it — note the difficulty |

This mirrors professional **data quality assurance** workflows used in real ML pipelines.

---

### 5. Submission Format

Labels were submitted in CSV format with the following schema:

```csv
id, intent, sentiment, pii_flag, rationale
```

- `intent` ∈ {Billing, Technical, Account, Other}
- `sentiment` ∈ {Positive, Neutral, Negative}
- `pii_flag` ∈ {Yes, No}
- `rationale` — only for designated edge-case items; 1–2 sentences max

---

## 🔗 Applications in Data Science & Business Analysis

### In Data Science

| Area | How Data Labeling Applies |
|------|--------------------------|
| **NLP / Text Classification** | Labeled intent and sentiment data trains models for customer support automation, chatbots, and email routing |
| **Sentiment Analysis Models** | Consistent sentiment labels are the ground truth for training BERT, RoBERTa, and similar transformers |
| **PII Detection Systems** | Flagging PII in training data feeds Named Entity Recognition (NER) models used in data masking pipelines |
| **Model Evaluation** | Labeled datasets serve as test sets for benchmarking classification accuracy, precision, and recall |
| **Active Learning** | Reviewers (Task 2) mirror real-world human-in-the-loop systems where model uncertainty triggers human review |
| **Data Quality Management** | The Keep/Fix/Flag framework maps directly to data validation pipelines in MLOps |

### In Business Analysis

| Area | How Data Labeling Applies |
|------|--------------------------|
| **Customer Experience Analytics** | Sentiment labels enable trend analysis across support tickets to surface systemic issues |
| **Process Automation** | Intent classification drives intelligent ticket routing, reducing resolution time |
| **Compliance & Risk** | PII awareness is foundational to GDPR, CCPA, and DPDP (India) compliance workflows |
| **Product Feedback Analysis** | Labeled support messages help product teams prioritize bugs vs. feature requests |
| **KPI Dashboards** | Aggregated intent/sentiment labels power executive-level dashboards on support health |
| **Vendor & Tool Evaluation** | Understanding labeling schema helps BAs evaluate AI tools, ensuring the underlying data quality meets business requirements |

---

## 🛠️ Skills Developed

```
✔ Analytical Thinking       — Applying rule-based frameworks to ambiguous, real-world text
✔ Attention to Detail       — Catching PII, mixed tones, and multi-intent messages accurately
✔ Data Privacy Awareness    — Understanding PII taxonomy, escalation protocols, and safe handling
✔ Documentation             — Writing concise, non-sensitive rationales for edge case decisions
✔ Feedback Delivery         — Constructive QA reviews with actionable, guideline-referenced fixes
✔ Consistency Management    — Treating similar items uniformly to reduce model training noise
```

---

## 📂 Project Structure

```
📁 data-labeling-simulation/
├── 📄 README.md                        # This file
├── 📋 task_1.txt                       # Task 1 instructions — Batch Labeling & PII Awareness
├── 📋 task_2.txt                       # Task 2 instructions — Label Review Framework
├── 📄 One_Page_Guidelines_Task_1.pdf   # Label definitions, edge-case rules, examples
└── 📄 PII_Quick_Card_Task_1.pdf        # PII identification checklist and escalation guide
```

---

## 📖 Key Takeaways

> **Consistency is more valuable than perfection.** Inconsistent labels introduce noise that degrades model performance far more than a few well-reasoned borderline calls. The goal is to be predictable, not just correct.

> **Privacy is not optional.** PII handling isn't a checkbox — it is a professional and legal responsibility. When in doubt, flag and escalate.

> **Edge cases are opportunities.** Every ambiguous message is a chance to improve the guidelines. Good labelers document confusion so the system gets smarter over time.

---

## 🏅 Simulation Details

| Field | Detail |
|-------|--------|
| **Platform** | Forage |
| **Simulation Type** | Data Labeling for AI/ML Systems |
| **Tasks Completed** | Task 1: Batch Labeling & PII Awareness · Task 2: Label Review (Keep/Fix/Flag) |
| **Skills Demonstrated** | Analytical Thinking, Data Privacy, Documentation, Feedback Delivery, Attention to Detail |

---

## 📬 Connect

If you're working on AI training data, NLP pipelines, or data quality — feel free to connect!

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com)

---

*"Good data is not just clean data. It's consistently labeled, privacy-respecting, and grounded in clear reasoning."*
