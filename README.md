# StepWise
*Process Mining and Intelligence Project, Academic Year 2025/2026*

🏆 **Best Idea Award** · 🚧 **Work in progress**

Step monitoring with smart shoes and AI agents for people with Parkinson's disease.

**Team Members:**
* Ilenia D'Antoni
* Erica Ginevri
* Chiara Nasoni
* Vittoria Vellutini

## 📄 Presentation

The slides are available here: [`StepWisePresentation.pdf`](StepWisePresentation.pdf).

## The problem

How does a person with Parkinson's walk in daily life, when nobody is watching?

Parkinson's is a neurodegenerative disease: steps get shorter and slower, and sometimes the feet freeze to the ground for a few seconds. On average, 60% of people with Parkinson's fall at least once and 39% fall repeatedly (Allen et al., 2013, review of 22 studies).

During a therapy cycle the patient sees the physiotherapist every three weeks, then every two or three months. In between, nobody sees how they walk, and a decline is often noticed too late.

## Our idea

We analyse data from **smart shoes**, with pressure and motion sensors in the sole and Bluetooth, together with two other sources:

| Source | What it tells us |
|---|---|
| Shoe sensors | **How** the patient walks: step length and duration, variability, freezing |
| Calendar | **What** they were doing: daily activities and completed exercises |
| Phone location | **Where** they were walking: at home, uphill, on slippery ground |

Every week a classifier labels the week as **normal** or **anomalous** given the context: short steps uphill can just be caution, while short steps at home on a flat floor are a real decline.

## Why agents

Without agents, sensors and a classifier alone add work: the physiotherapist would have to run **5 manual checks per patient, every week** (gait trend, context, classifier output, similar past cases, medical record).

With agents, they read **one weekly report** and decide.

| Agent | Role | Patterns |
|---|---|---|
| **Step Agent** | Checks the data are reliable (if not, asks for a 2-minute walking test), runs the classifier, tracks the trend against the exercise goals | Tool use, memory management, goal setting & monitoring, exception handling, human-in-the-loop |
| **Clinical Agent** | Flags recent changes that may explain the gait, such as new drugs or dose timing. It never diagnoses | Tool use, reasoning |
| **Anomaly Agent** | Only for anomalous weeks: checks whether the anomaly is credible using the context and the Clinical Agent's notes | Tool use, reasoning, human-in-the-loop |
| **Coach Agent** | The only agent that talks to the patient: asks fixed weekly questions (falls, near-falls, pain), sends reminders and alerts the physiotherapist if something serious comes up | Prompt chaining, guardrails, human-in-the-loop |

If the physiotherapist has doubts, the case goes to the physiatrist, who decides by looking at similar past cases (case-based reasoning). Each decision becomes a new reference case.

**Agents prepare, people decide.**
