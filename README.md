# SignalHealth: Deterministic Clinical Triage Prompt Architecture

An enterprise-grade, multi-state system prompt designed to safely orchestrate conversational LLMs within digital health and medical triage environments. This architecture enforces strict safety guardrails, eliminates probabilistic diagnostic liability, and dynamically manages risk transitions.

## 🧠 Core System Architecture

### 1. Strict State-Based Control Engine
To prevent the common LLM failure mode of hallucinating or mixing conflicting behaviors, this system restricts the model to a binary choice at every turn:
* **STATE 1 - Information Gathering:** Deployed when clinical data is incomplete. The model is restricted to asking exactly *one focused question* at a time, barred from summarizing patterns prematurely, and blocked from mentioning clinical urgency until thresholds are met.
* **STATE 2 - Clinical Escalation:** Triggered instantly by predefined red flags or functional impairment. It enforces an **Escalation Lock (Hard Stop)**, closing the symptom diagnostic thread, limiting review advice to a single brief sentence, and shifting entirely to logistical support or GP summary generation.

### 2. Diagnostic Language Lock (Liability Mitigation)
The architecture programmatically insulates the application from diagnostic liability by stripping out predictive phrasing. The model is strictly prohibited from using probabilistic language (*"this fits with"*, *"most likely means"*) or discussing underlying pathology (*"infection"*, *"fluid overload"*). Instead, its output space is restricted exclusively to describing:
* Symptom severity & functional impact
* Objective risk level
* Clear, non-alarmist navigation to formal clinical assessment

### 3. Dynamic Risk Recalculation & De-Escalation Lock
Risk is evaluated dynamically turn-by-turn rather than persisting statically. If a user introduces reassurance, clinical resolution, or humor, the system triggers a **De-Escalation Lock** to immediately exit emergency framing and return smoothly to baseline longitudinal monitoring.

### 4. Structured Medication Safety Engine
Features an integrated screening framework that monitors for critical high-risk compound combinations (e.g., Opioids + Benzodiazepines, Sedatives + Alcohol). When triggered, it forces immediate safety disclosures, driving warnings, and structured medication reviews.
