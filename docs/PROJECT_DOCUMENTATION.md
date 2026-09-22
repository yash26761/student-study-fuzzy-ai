# PAGE 1: COVER PAGE

### Individual IKS Academic Project Report
**Academic Term:** Third Year B.Sc. Information Technology (Semester VI)  
**Subject:** Indian Knowledge Systems (IKS) & Applied Artificial Intelligence  
**Curricular Initiative:** Individual IKS Project (Indian Knowledge Systems)  
**Academic Year:** 2025–2026  


### Individual IKS Academic Project Report
**Academic Term:** Third Year B.Sc. Information Technology (Semester VI)  
**Subject:** Indian Knowledge Systems (IKS) & Applied Artificial Intelligence  

| Project Attribute | Project Record Details |
| :--- | :--- |
| **Project Title** | **AI-Based Student Study Time Recommendation System Using Fuzzy Logic** |
| **Student Name** | Yash Sanjay Haldankar |
| **Roll Number** | TYIT-IKS-2026-042 |
| **Class & Stream** | T.Y. B.Sc. IT (Third Year Bachelor of Science in Information Technology) |
| **Curricular Component** | Individual IKS Project (Indian Knowledge Systems) |
| **Institutional College** | Department of Information Technology |
| **Academic Year** | 2025 – 2026 |
| **Project Guide / Evaluator** | Faculty of Information Technology |
| **Official Repository** | [https://github.com/yash26761/student-study-fuzzy-ai](https://github.com/yash26761/student-study-fuzzy-ai) |
| **Live Deployed App** | [https://student-study-fuzzy-ai.streamlit.app/](https://student-study-fuzzy-ai.streamlit.app/) |

---

<!-- PAGE BREAK: PAGE 2 -->

# PAGE 2: ABSTRACT, INTRODUCTION & PROBLEM STATEMENT

## 1. Abstract
The **AI-Based Student Study Time Recommendation System Using Fuzzy Logic** is a hybrid intelligent advisory system that personalizes daily study time schedules for students preparing for examinations. Conventional examination advice typically relies on arbitrary, rigid quotas (e.g., "study 10 hours daily regardless of context"), inducing intense academic burnout and anxiety. This project bridges the **Indian Knowledge Systems (IKS)** learner-centred educational philosophy (*Adhikara-Bheda*, *Svadhyaya*, and *Yukta Abhyasa*) with modern computational reasoning. The system allows students to describe their current exam readiness in unstructured, conversational English. A Large Language Model (LangChain + Groq API) extracts quantitative parameters with Pydantic validation into days remaining, hours studied today, and subjective preparation level. A pure-Python Mamdani Fuzzy Inference System evaluates an 18-rule base across triangular/trapezoidal membership curves and performs centroid defuzzification to determine balanced daily study hours and an urgency score. Finally, an AI academic coach generates supportive explanations and categorized study tips. Deployed publicly on Streamlit Community Cloud, the system delivers verifiable, transparent, and empathetic academic guidance.

## 2. Introduction
In undergraduate education, efficient time allocation is pivotal to academic achievement and psychological well-being. However, students evaluate their readiness using vague, subjective impressions:
* *"My exam is in about two weeks..."*
* *"I managed only three hours today..."*
* *"My preparation feels around fifty-five percent..."*

Standard computational systems rely on Boolean `if/else` logic with sharp boundaries that produce unnatural, abrupt jumps (e.g., an abrupt shift in recommendations between 2.9 days and 3.0 days). Conversely, pure Generative AI models often produce inconsistent numerical calculations or hallucinate schedule feasibility. This project implements a hybrid AI pipeline: modern LLMs handle natural language comprehension, while deterministic fuzzy logic governs the quantitative decision boundary.

## 3. Problem Statement
To design, implement, test, and deploy an individual academic decision-support web application that:
1. Accepts ambiguous, natural-language descriptions of examination circumstances from students.
2. Extracts and validates numerical bounds for days remaining ($0–30$), hours studied ($0–12$), and preparation percentage ($0–100\%$).
3. Formulates a complete, mathematically sound Mamdani Fuzzy Inference System that calculates realistic recommended daily study hours ($0–8\text{ hrs/day}$) and an urgency need score ($0–100$).
4. Anchors the educational rationale within the Indian Knowledge Systems (IKS) holistic pedagogical framework, honoring learner baseline and balanced effort.
5. Provides verifiable deployment on Streamlit Community Cloud with end-to-end unit testing.

---

<!-- PAGE BREAK: PAGE 3 -->

# PAGE 3: OBJECTIVES, SCOPE & TECHNOLOGIES USED

## 1. Main Objectives
* **Natural-Language Understanding:** Eliminate rigid form inputs by enabling students to express their exam situation in everyday conversational sentences.
* **Rigorous Mathematical Inference:** Formulate a 5-stage Mamdani Fuzzy Inference System from first principles using NumPy, avoiding opaque black-box fuzzy libraries.
* **Complete Rule-Base Coverage:** Engineer a multi-variable 18-rule base ensuring zero orphan states across the continuous 3D domain.
* **Authentic IKS Educational Framing:** Embed traditional Indian pedagogical tenets (*Adhikara*, *Svadhyaya*, *Yukta Abhyasa*) into personalized learning recommendations.
* **Automated Defensive Validation:** Enforce schema validation via Pydantic and unit-test all boundaries via Pytest.
* **Cloud Accessibility:** Deliver a secure, zero-secret web dashboard on Streamlit Community Cloud.

## 2. Project Scope
* **Target Audience:** College and university students facing upcoming mid-term or end-semester examinations.
* **Functional Boundaries:** Focuses on daily revision time allocation ($0–8\text{ hrs/day}$) and situational urgency; does not generate syllabus timetables or act as an institution-wide learning management system (LMS).
* **Privacy Scope:** Zero persistence of student personal identifiable information (PII); API credentials managed strictly through ephemeral browser sessions or server-side cloud secrets.

## 3. Technologies Used
Only technologies actually implemented in the repository are listed below:

| Technology Layer | Tool / Library | Role & Implementation Details |
| :--- | :--- | :--- |
| **Core Language** | Python 3.11+ / 3.14 | Underlying language for mathematical computation and backend scripting. |
| **Fuzzy Math Engine** | NumPy (`numpy`) | Custom, first-principles implementation of triangular/trapezoidal membership curves, min/max operators, and centroid integration. |
| **LLM Orchestration** | LangChain Core (`langchain`, `langchain-core`) | Prompt templating, structured message handling, and LLM output parsing. |
| **LLM Providers** | LangChain-Groq (`langchain-groq`), LangChain-OpenAI (`langchain-openai`) | Cloud LLM inference. Default: Groq (`qwen/qwen3.8-27b`); optional user fallback: OpenAI (`gpt-4o-mini`). |
| **Schema Validation** | Pydantic V2 (`pydantic`) | Strict type enforcement, numerical bounds validation, and structured entity extraction. |
| **Web Dashboard** | Streamlit (`streamlit`) | Responsive interactive user interface, reactive state management, and custom CSS styling. |
| **Visualizations** | Matplotlib (`matplotlib`) | Real-time generation of input membership functions and defuzzified centroid area graphs. |
| **Configuration** | Python-Dotenv (`python-dotenv`) | Secure environment variable parsing for local and cloud secret discovery. |
| **Automated Testing** | Pytest (`pytest`) | 29-test automated unit suite covering rule firing, centroid math, and exception handling. |
| **Cloud Hosting** | Streamlit Community Cloud | Public container deployment connected directly to GitHub `main` branch. |

---

<!-- PAGE BREAK: PAGE 4 -->

# PAGE 4: INDIAN KNOWLEDGE SYSTEMS (IKS) CONNECTION

## 1. Selected IKS Educational Theme
**Indian Holistic and Learner-Centred Educational Perspective.**

In traditional Indian pedagogical philosophy, learning is conceived not as an industrial, one-size-fits-all assembly line, but as an individualized, balanced, and student-centered journey. This perspective is central to the National Education Policy 2020 (NEP 2020, Ministry of Education, Govt. of India) and the mandate of the Ministry’s IKS Division.

```text
       Traditional Indian Pedagogy (IKS)
   ┌────────────────────────────────────────┐
   │ • Adhikara-Bheda (Learner Readiness)   │
   │ • Svadhyaya (Self-Directed Study)      │
   │ • Yukta Abhyasa (Balanced Effort)      │
   └───────────────────┬────────────────────┘
                       │ Educational Motivation
                       ▼
       Modern Academic Advisory Problem
   ┌────────────────────────────────────────┐
   │ Imprecise, Stressful Student Situations│
   │ "Exam in 5 days, studied 2 hrs, poor"  │
   └───────────────────┬────────────────────┘
                       │ Computational Solution
                       ▼
       Modern AI & Fuzzy Mathematical System
   ┌────────────────────────────────────────┐
   │ • LangChain + Groq LLM (NLU Interface) │
   │ • Lotfi Zadeh (1965) Mamdani Fuzzy Sys │
   │ • Centroid Math: Balanced Study Hours  │
   └────────────────────────────────────────┘
```

## 2. Foundational IKS Pedagogical Concepts
1. **Learner-Centred Readiness (*Adhikara-Bheda*):**
   * Recognizes that every student begins from a distinct state of prior preparation, comprehension, and psychological readiness.
   * Rather than prescribing an identical 10-hour study quota to every candidate, guidance must calibrate to where the learner currently stands.
2. **Self-Directed Study and Self-Reflection (*Svadhyaya*):**
   * *Svadhyaya* represents dedicated, self-paced learning combined with honest self-assessment.
   * It values regular, introspective revision over frenzied, last-minute cramming, encouraging learners to reflect realistically on their preparation.
3. **Balanced Effort (*Yukta Abhyasa*):**
   * Classical Indian philosophy stresses harmony and moderation across human activity.
   * Excessive study marathons that cause exhaustion, mental agitation, and health breakdown are counterproductive. Effective study (*abhyasa*) must remain sustainable, calm, and proportionate to the timeline.

## 3. Academic Integrity & Non-Claims
To uphold scientific and academic integrity:
* **No Algorithmic Invention Claim:** We explicitly do **not** claim that ancient Indian scriptures invented fuzzy logic, fuzzy sets, or computer algorithms. Fuzzy set theory was mathematically formulated by Lotfi A. Zadeh in 1965.
* **No Formulaic Claim:** We do **not** claim that ancient texts contain the 0–8 hour study scale, centroid formulas, or Python source code.
* **Defensible Relationship:** IKS provides the **educational philosophy and humanistic rationale**; modern AI and fuzzy mathematics provide the **computational calculation and interface**.

---

<!-- PAGE BREAK: PAGE 5 -->

# PAGE 5: SYSTEM ARCHITECTURE & METHODOLOGY

## 1. System Architecture Pipeline
The end-to-end system integrates natural language extraction, mathematical fuzzy inference, AI explanation, and interactive visualization:

```text
┌────────────────────────────────────────────────────────────────────────┐
│ 1. Student Natural-Language Input                                      │
│    "I have 14 days until my exam, I can study 3 hours daily,           │
│     and my preparation is around 55 percent."                          │
└──────────────────────────────────┬─────────────────────────────────────┘
                                   │
                                   ▼
┌────────────────────────────────────────────────────────────────────────┐
│ 2. LangChain + Groq LLM Extraction (`extractor.py`)                    │
│    • System prompt directs structured parameter extraction             │
│    • Classifies relevance (`is_study_related = True`)                  │
└──────────────────────────────────┬─────────────────────────────────────┘
                                   │
                                   ▼
┌────────────────────────────────────────────────────────────────────────┐
│ 3. Pydantic Schema Validation (`models.py`)                            │
│    • days_until_exam: 14 [0–30]                                        │
│    • study_hours: 3.0 [0–12]                                           │
│    • preparation_level: 55.0% [0–100]                                  │
└──────────────────────────────────┬─────────────────────────────────────┘
                                   │
                                   ▼
┌────────────────────────────────────────────────────────────────────────┐
│ 4. Mamdani Fuzzy Inference Engine (`fuzzy_system.py`)                  │
│    Step 1: Fuzzification (Triangular & Trapezoidal curves)             │
│            days: Medium(0.43), Far(0.25) | hours: Medium(0.40)         │
│            prep: Average(0.75)                                         │
│    Step 2: Rule Evaluation across 18 rules (MIN / fuzzy AND)           │
│            (e.g., R6: Med days AND Med hours AND Avg prep -> Med time) │
│    Step 3: Implication (Clipping output curves at firing strength)     │
│    Step 4: Aggregation across rules (MAX / fuzzy OR)                   │
│    Step 5: Centroid Defuzzification (Center of Gravity formula)        │
└──────────────────────────────────┬─────────────────────────────────────┘
                                   │
                                   ▼
┌────────────────────────────────────────────────────────────────────────┐
│ 5. Fuzzy Output Results                                                │
│    • Recommended Study Time: 3.14 hrs / day                            │
│    • Study Need Score: 50.0 / 100 (Moderate Need — Steady Pace)        │
└──────────────────────────────────┬─────────────────────────────────────┘
                                   │
                                   ▼
┌────────────────────────────────────────────────────────────────────────┐
│ 6. AI Explanation & Study Recommendations (`explainer.py`)             │
│    • Supportive coaching explanation tailored to computed urgency      │
│    • 5 Actionable tips (Targeted Review, Active Recall, etc.)          │
└──────────────────────────────────┬─────────────────────────────────────┘
                                   │
                                   ▼
┌────────────────────────────────────────────────────────────────────────┐
│ 7. Streamlit Web Dashboard (`app.py` + `visualization.py`)             │
│    • Metric cards, Matplotlib charts, color-coded urgency status pills │
└────────────────────────────────────────────────────────────────────────┘
```

## 2. Mathematical Methodology
1. **Fuzzification:** Maps crisp values to degrees of membership $\mu_A(x) \in [0, 1]$ using:
   $$\text{trimf}(x; a, b, c) = \max\left(\min\left(\frac{x-a}{b-a}, \frac{c-x}{c-b}\right), 0\right)$$
   $$\text{trapmf}(x; a, b, c, d) = \max\left(\min\left(\frac{x-a}{b-a}, 1, \frac{d-x}{d-c}\right), 0\right)$$
2. **Rule Evaluation (Mamdani AND):** Firing strength $\alpha_k$ for rule $k$:
   $$\alpha_k = \min\left(\mu_{A_k}(days), \mu_{B_k}(hours), \mu_{C_k}(prep)\right)$$
3. **Aggregation:** Combines implied output curves using the MAX operator:
   $$\mu_{agg}(y) = \max_k \left( \min(\alpha_k, \mu_{out_k}(y)) \right)$$
4. **Centroid Defuzzification:** Computes the crisp output value $z^*$:
   $$z^* = \frac{\sum_{i} y_i \cdot \mu_{agg}(y_i)}{\sum_{i} \mu_{agg}(y_i)}$$

---

<!-- PAGE BREAK: PAGE 6 -->

# PAGE 6: MODULE IMPLEMENTATION

The codebase is organized into seven modular Python components:

```text
student-study-fuzzy-ai/
├── app.py              # Streamlit web UI & reactive presentation
├── extractor.py        # First LangChain chain: Natural Language -> Pydantic Data
├── explainer.py        # Second LangChain chain: Fuzzy Result -> Advice & Tips
├── fuzzy_system.py     # Pure-Python Mamdani Fuzzy Inference Engine (NumPy)
├── llm_config.py       # 3-tier secret management & multi-provider factory
├── models.py           # Pydantic schemas for data integrity
└── visualization.py    # Matplotlib membership and defuzzification plots
```

### 1. `fuzzy_system.py` (Fuzzy Logic Engine)
Implements fuzzification, 18-rule evaluation, implication, aggregation, and centroid defuzzification entirely in plain Python and NumPy without external fuzzy packages:
```python
# Centroid defuzzification implementation in fuzzy_system.py
def _centroid(universe: np.ndarray, membership: np.ndarray, default: float) -> float:
    total_membership = np.sum(membership)
    if total_membership <= 1e-9:
        return default
    return float(np.sum(universe * membership) / total_membership)
```

### 2. `extractor.py` (NLU Parameter Extraction)
Invokes the Groq LLM through LangChain with strict Pydantic output constraints (`ExtractedStudentData`). Validates input length, filters casual chit-chat ("hello"), detects off-topic queries, and maps qualitative language ("poor preparation" $\rightarrow 20\%$) into valid bounded ranges.

### 3. `explainer.py` (AI Academic Coach)
Takes the defuzzified numbers and fuzzy need category, prompting the LLM to formulate an encouraging 2–4 sentence summary and exactly 5 actionable study recommendations (e.g., Active Recall, Spaced Repetition).

### 4. `models.py` (Schema & Bounds Validation)
Defines strict Pydantic schemas: `ExtractedStudentData` (relevance check, raw parameters), `StudentStudyData` (clipped integer/float bounds), and `ExplanationResult` (structured text and tip lists).

### 5. `llm_config.py` (Security & Multi-Provider Architecture)
Implements a 3-tier fallback strategy for credentials:
1. `st.session_state` (Browser-local session override)
2. `st.secrets` (Streamlit Community Cloud Secrets)
3. `os.getenv` (Local development `.env`)
Supports both Groq (`qwen/qwen3.8-27b`) and OpenAI (`gpt-4o-mini`).

### 6. `app.py` & `visualization.py` (User Interface & Graphics)
Streamlit-based dashboard featuring a collapsible **🏛️ IKS Educational Perspective** expander, metric cards, a rule-firing data table, color-coded urgency status pills (Low: Green, Medium: Amber, High: Red), and Matplotlib plots.

---

<!-- PAGE BREAK: PAGE 7 -->

# PAGE 7: SCREENSHOTS & EXPERIMENTAL RESULTS

The application was tested against live benchmarks on Streamlit Community Cloud:

## 1. Verified Benchmark Test Cases

| Parameter | Normal Scenario (Steady Pace) | Urgent Scenario (Exam in 2 Days) |
| :--- | :--- | :--- |
| **Input Sentence** | *"I have 14 days until my exam, I can study 3 hours daily, and my preparation is around 55 percent."* | *"My exam is in 2 days, I can study 1 hour per day, and my preparation is about 15 percent."* |
| **Extracted Days** | **14 days** | **2 days** |
| **Extracted Hours** | **3.0 hrs** | **1.0 hrs** |
| **Extracted Preparation** | **55%** | **15%** |
| **Fuzzy Recommended Time**| **3.14 hrs / day** | **6.85 hrs / day** |
| **Study Need Score** | **50.0 / 100** | **83.1 / 100** |
| **Urgency Classification** | **Moderate Need — Steady Pace** (Amber) | **High Need — Urgent Action** (Red) |
| **AI Explanation Status** | Generated (Consistency & targeted review) | Generated (High-weight syllabus triage) |

## 2. Key Screen Captures

### Figure 1: Natural-Language Input & IKS Perspective
The primary interface displays the input container alongside the expanded **🏛️ IKS Educational Perspective** detailing learner baseline (*Adhikara*) and balanced effort (*Yukta Abhyasa*).
```text
[ Screenshot Reference: docs/screenshots/01_main_ui.png & 06_iks_perspective.png ]
```

### Figure 2: Extracted Numerical Parameters
Displays extracted quantitative metrics (`14 days`, `3.0 hrs`, `55%`) cleanly parsed from conversational student text.
```text
[ Screenshot Reference: docs/screenshots/03_extracted_values.png ]
```

### Figure 3: Fuzzy Logic Analysis & Defuzzification Curves
Visualizes input fuzzification across triangular/trapezoidal membership functions and output centroid defuzzification areas.
```text
[ Screenshot Reference: docs/screenshots/07_visualization.png ]
```

### Figure 4: Final Recommendation & AI Coaching Tips
Displays the defuzzified recommendation (3.14 hrs/day), status pill, and structured study tips.
```text
[ Screenshot Reference: docs/screenshots/04_fuzzy_result.png & 05_ai_explanation.png ]
```

---

<!-- PAGE BREAK: PAGE 8 -->

# PAGE 8: TESTING, VERIFICATION & LIMITATIONS

## 1. Verification Test Suite Summary
The system underwent rigorous automated and manual verification:

| Test Category | Target Component | Verification Scope | Status |
| :--- | :--- | :--- | :--- |
| **Unit Testing** | `tests/test_fuzzy.py` | 29 automated Pytest test cases covering math, boundaries, and rules. | **PASS (29/29)** |
| **Input Clipping** | `extractor.py` | Validated clamping: days $[0, 30]$, hours $[0, 12]$, prep $[0, 100]\%$. | **PASS** |
| **Zero-Division Guard**| `fuzzy_system.py` | Tested centroid calculation under zero membership; safe default returned. | **PASS** |
| **Rule Completeness** | 18 Mamdani Rules | 1,320 continuous state combinations evaluated; **0 orphan states** found. | **PASS** |
| **Input Rejection** | Fast-path filters | Empty strings, whitespace, greetings ("hello"), and recipes correctly rejected. | **PASS** |
| **Security Audit** | Git history & UI | Zero hardcoded keys in 4 commits; credentials masked in sidebar. | **PASS** |
| **Cloud Deployment** | Streamlit Cloud | Live container health status confirmed (`/healthz` HTTP 200 OK). | **PASS** |

## 2. Project Limitations
* **External API Dependency:** Natural language extraction and explanation require network connectivity to cloud LLM inference endpoints (Groq / OpenAI).
* **Rule Base Granularity:** The 18 Mamdani rules cover 3 linguistic sets per variable; highly subtle nuances (e.g., student illness, practical lab exams) are not explicitly distinguished.
* **Stateless Architecture:** The application does not store historical progress across days in a database; each recommendation evaluates the immediate session.

## 3. Future Scope
* **Multi-Subject Scheduling:** Extending the fuzzy engine to balance multiple competing course syllabi simultaneously.
* **Longitudinal Progress Tracking:** Incorporating local encrypted storage to track daily revision consistency over a semester.
* **Adaptive Membership Functions:** Applying neuro-fuzzy techniques (ANFIS) to tune membership boundaries based on student exam outcomes.
* **Multilingual Interface:** Leveraging LLM capabilities to support Indian regional languages for broader academic accessibility.

---

<!-- PAGE BREAK: PAGE 9 -->

# PAGE 9: CONCLUSION & REFERENCES

## 1. Conclusion
The **AI-Based Student Study Time Recommendation System Using Fuzzy Logic** demonstrates how modern artificial intelligence and classical fuzzy mathematics can synergize to solve an everyday student dilemma. By combining LangChain’s natural language comprehension with a transparent, first-principles Mamdani Fuzzy Inference System, the project eliminates both the rigid, abrupt cut-offs of Boolean algorithms and the numerical unpredictability of unconstrained generative models. 

Furthermore, grounding the educational rationale in the **Indian Knowledge Systems (IKS)** concepts of *Adhikara-Bheda* (individual learner readiness), *Svadhyaya* (self-directed study), and *Yukta Abhyasa* (balanced effort) aligns the engineering effort with the holistic vision of NEP 2020. The application successfully fulfills all curricular guidelines for the Third Year B.Sc. IT project, delivering a functional, tested, and publicly accessible academic advisory platform.

## 2. Academic & Technical References

1. **National Education Policy 2020 (NEP 2020)**, Ministry of Education, Government of India. Emphasizes learner-centric education, student mental wellness, and the integration of Indian Knowledge Systems (pp. 4–18).  
   *URL:* `https://www.education.gov.in/sites/upload_files/mhrd/files/NEP_Final_English_0.pdf`
2. **Indian Knowledge Systems (IKS) Division**, Ministry of Education, Govt. of India (Hosted at AICTE, New Delhi). Established to foster interdisciplinary research connecting indigenous pedagogical insights with modern computing.  
   *URL:* `https://iksindia.org/`
3. **University Grants Commission (UGC)**, *Guidelines for Training and Orientation of Faculty on Indian Knowledge Systems (IKS)*, New Delhi, 2023. Highlights individualized guidance (*adhikara*) and balanced daily routine (*dinacharya*).  
   *URL:* `https://www.ugc.gov.in/`
4. **Zadeh, Lotfi A.**, "Fuzzy Sets", *Information and Control*, Vol. 8, Issue 3, 1965, pp. 338–353. The foundational paper formulating mathematical fuzzy set theory.  
   *DOI:* `10.1016/S0019-9958(65)90241-X`
5. **Mamdani, Ebrahim H. and Assilian, Sedrak**, "An Experiment in Linguistic Synthesis with a Fuzzy Logic Controller", *International Journal of Man-Machine Studies*, Vol. 7, Issue 1, 1975, pp. 1–13.  
   *DOI:* `10.1016/S0020-7373(75)80002-2`
6. **LangChain Documentation**, *Building Applications with LLMs and Structured Outputs*, 2024.  
   *URL:* `https://python.langchain.com/`
7. **Streamlit Documentation**, *Deploying Web Applications on Streamlit Community Cloud*, 2024.  
   *URL:* `https://docs.streamlit.io/`

---

<!-- PAGE BREAK: PAGE 10 -->

# PAGE 10: PROJECT ACCESS LINKS & FINAL EXHIBITS

## 1. Official Project Access Links
All source code, automated test suites, documentation, and live deployments are accessible via the official links:

* **GitHub Source Code Repository:**  
  [https://github.com/yash26761/student-study-fuzzy-ai](https://github.com/yash26761/student-study-fuzzy-ai)
* **Streamlit Community Cloud Live Application:**  
  [https://student-study-fuzzy-ai.streamlit.app/](https://student-study-fuzzy-ai.streamlit.app/)

## 2. Final System Architecture Summary Table

| Module | Primary Source File | Mathematical / Computational Role |
| :--- | :--- | :--- |
| **Web Dashboard** | `app.py` | Renders the responsive UI, handles session secrets, and embeds the IKS educational expander. |
| **NLU Extractor** | `extractor.py` | Single-turn LangChain extraction with Pydantic structured output (`qwen/qwen3.8-27b`). |
| **Fuzzy Engine** | `fuzzy_system.py` | 5-stage Mamdani inference engine (Triangular/Trapezoidal fuzzification, 18 rules, Centroid defuzzification). |
| **AI Coach Explainer**| `explainer.py` | Translates numerical study hours and urgency into supportive advice and 5 actionable tips. |
| **Data Models** | `models.py` | Pydantic V2 schemas enforcing boundaries on days, hours, and preparation percentages. |
| **Graphics Engine** | `visualization.py` | Real-time Matplotlib generation of membership functions and defuzzified output curves. |
| **Security Manager** | `llm_config.py` | 3-tier credentials resolver protecting API keys from exposure. |

## 3. Project Submission Checklist & Compliance

| Requirement | Prescribed Criterion | Project Compliance Status |
| :--- | :--- | :--- |
| **Page Budget** | Maximum 10 pages | **COMPLIANT (Exactly 10 concise structured pages)** |
| **IKS Integration** | Authentic academic connection | **COMPLIANT (*Adhikara*, *Svadhyaya*, *Yukta Abhyasa* / NEP 2020)** |
| **Fuzzy Math** | Mamdani inference system | **COMPLIANT (18 rules, Centroid defuzzification from scratch)** |
| **AI Understanding**| Natural language interface | **COMPLIANT (LangChain + Groq structured extraction)** |
| **Verification** | Automated testing suite | **COMPLIANT (29/29 Pytest tests passed, zero orphan states)** |
| **Deployment** | Public cloud URL | **COMPLIANT (Live on Streamlit Community Cloud)** |
| **Security** | Zero exposed secrets | **COMPLIANT (All keys managed via Streamlit Secrets)** |

---
*End of Project Documentation — AI-Based Student Study Time Recommendation System Using Fuzzy Logic*
