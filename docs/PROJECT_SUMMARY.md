# 🎓 PROJECT SUMMARY & VIVA REFERENCE
# AI-Based Study Time Recommendation System Using Fuzzy Logic

**Academic Level:** Third Year B.Sc. Information Technology (B.Sc. IT)  
**Project Category:** Individual IKS Project (Indian Knowledge Systems)  
**Author:** Yash Sanjay Haldankar (`yash26761`)  
**GitHub Repository:** [https://github.com/yash26761/student-study-fuzzy-ai](https://github.com/yash26761/student-study-fuzzy-ai)  
**Date:** September 2026  

---

## 1. Executive Summary: What You Built

You have created an **intelligent academic advisory web application** that solves a classic real-world decision-making problem:  
**"How many hours should a student study today given vague, stressful exam conditions?"**

### The Core Problem:
Students evaluate their exam readiness in imprecise, qualitative terms:
- *"My exam is in a few days..."*
- *"I studied a little bit today..."*
- *"My preparation is pretty poor..."*

Traditional Boolean programming (rigid `if/else` statements) fails because hard thresholds create sudden, unrealistic jumps (e.g., 2.9 days vs. 3.0 days getting drastically different advice). Pure LLMs often hallucinate or output inconsistent numerical advice.

### The Solution:
A **hybrid AI architecture** combining:
1. **Large Language Model (LangChain + Groq API)** to read natural conversational English and translate it into structured quantitative parameters.
2. **A Pure Python Mamdani Fuzzy Inference System (NumPy)** built from scratch to calculate realistic, mathematically sound daily study hours and urgency scores.
3. **An AI Academic Coach** that turns the numbers into friendly, supportive explanations and 5 actionable study tips.
4. **An Interactive Streamlit Dashboard** with real-time Matplotlib visualizations.

---

## 2. System Architecture & The 4 Modules

```text
[1. Student Input]
"My exam is in 5 days, I studied 2 hours today, preparation is poor."
               │
               ▼
[2. Module 1: Natural Language Extractor (extractor.py)]
- Uses LangChain + Groq Chat Model (`qwen/qwen3.8-27b`)
- Single structured call with Pydantic schema (`ExtractedStudentData`)
- Extracts: days=5, hours=2.0, prep=20%
- Filters out empty messages, casual greetings ("hello"), and off-topic questions
               │
               ▼
[3. Module 2: Mamdani Fuzzy Inference Engine (fuzzy_system.py)]
- Step 1: Fuzzification using Triangular and Trapezoidal curves
- Step 2: 18 Fuzzy Rules evaluated using MIN operator (fuzzy AND)
- Step 3: Implication by clipping output curves at rule firing strength
- Step 4: Aggregation across all firing rules using MAX operator
- Step 5: Centroid Defuzzification (Center of Gravity)
- Output: Recommended Study Time: ~5.15 hrs/day | Urgency Need: High (79.4/100)
               │
               ▼
[4. Module 3: AI Academic Coach & Explainer (explainer.py)]
- Formulates an encouraging explanation of the fuzzy recommendation
- Generates 5 categorized study strategies (Active Recall, Time Management, etc.)
               │
               ▼
[5. Module 4: Web Interface & Visualizations (app.py + visualization.py)]
- Streamlit web application
- Dynamic Matplotlib plots for membership functions and defuzzification curves
- Color-coded urgency status pills (Green / Amber / Red)
```

---

## 3. Mathematical Fuzzy Logic System Design

Implemented from first principles using NumPy (zero third-party fuzzy libraries like `scikit-fuzzy`):

### Variables & Universes of Discourse:
| Variable Name | Type | Range | Fuzzy Linguistic Sets |
|---|---|---|---|
| **Days Until Exam** | Input | 0 – 30 days | Near, Medium, Far |
| **Study Hours Today** | Input | 0 – 12 hours | Low, Medium, High |
| **Preparation Level** | Input | 0 – 100 % | Poor, Average, Good |
| **Recommended Study Time** | Output | 0 – 8 hrs/day | Low, Medium, High |
| **Study Need Score** | Output | 0 – 100 score | Low (<35), Medium (35–65), High (>65) |

### Membership Functions:
- **Triangular Function (`trimf`)**: Used for intermediate concepts like `Medium` days, `Medium` hours, and `Average` preparation.
- **Trapezoidal Function (`trapmf`)**: Used for boundary concepts like `Near` (with flat top) and `Far` (with shoulder).

### Centroid Defuzzification Formula:
$$z^* = \frac{\sum_{i} x_i \cdot \mu(x_i)}{\sum_{i} \mu(x_i)}$$
Calculates the exact center of gravity of the combined fuzzy area, ensuring continuous, smooth recommendations without abrupt jumps.

### Rule Base Completeness:
- Exactly **18 rules** covering all multi-variable scenarios.
- Tested across **2,288 state combinations** in the continuous 3D domain: **0 orphan states** (at least one rule fires with positive strength for every possible input).

---

## 4. Key Engineering & Software Quality Highlights

1. **First-Principles Implementation**:
   - Written directly in NumPy. Examiners will see that you understand the mathematical mechanics of fuzzification, implication, and defuzzification rather than relying on a black-box package.
2. **Pydantic Data Contracts**:
   - Strict validation with `ge` (greater-than-or-equal) and `le` (less-than-or-equal) bounds constraints.
3. **Production Rate-Limit & Token Budgeting**:
   - Extractor capped at `max_tokens=250`.
   - Explainer capped at `max_tokens=600`.
   - Prevents free-tier Groq 429 rate limits (1,000 OTPM ceiling).
4. **Security & Privacy**:
   - `.env` is git-ignored and excluded from version control.
   - User prompt input is sanitized via `html.escape()` against XSS injection.
   - Streamlit Cloud Secrets (`st.secrets["GROQ_API_KEY"]`) supported seamlessly.
5. **Comprehensive Automated Testing**:
   - 29 unit tests in `tests/test_fuzzy.py`.
   - Tests run in ~1.0 second completely offline using mocked LLM responses with zero API token consumption.

---

## 5. Top 10 Viva / Presentation Questions & Exact Answers

#### Q1: What is the main objective of your project?
> *"It is an intelligent study recommendation system that translates a student's natural-language description of their exam situation into a mathematically calculated daily study recommendation using Fuzzy Logic, and explains the advice using an AI coach."*

#### Q2: Why did you use Fuzzy Logic instead of regular IF-ELSE conditions?
> *"Real-world academic preparation is continuous and imprecise. Regular IF-ELSE requires hard thresholds (e.g., `< 3 days = Near`). A student with 2.9 days and 3.1 days would get drastically different recommendations. Fuzzy logic allows degrees of truth and partial memberships, producing smooth, realistic transitions."*

#### Q3: Where is AI / LangChain used in your project?
> *"AI is used in two places: First, in `extractor.py` to read natural language and extract quantitative parameters into a Pydantic schema in a single structured call. Second, in `explainer.py` to translate the numeric fuzzy output into personalized, human-friendly coaching tips."*

#### Q4: Why didn't you let the LLM do the whole calculation?
> *"LLMs excel at natural language understanding, but they are non-deterministic and hallucinate when performing mathematical calculations. Fuzzy logic is deterministic, transparent, and mathematically grounded. We use the LLM as the linguistic interface and Fuzzy Logic as the core reasoning engine."*

#### Q5: What is Mamdani Inference?
> *"Mamdani inference is the most popular fuzzy methodology. It follows five steps: Fuzzification of crisp inputs, Rule evaluation using the MIN operator (fuzzy AND), Implication by clipping output curves, Aggregation of all firing rules using MAX, and Defuzzification using the Centroid method."*

#### Q6: What is Centroid Defuzzification?
> *"Centroid (Center of Gravity) defuzzification calculates the balance point of the aggregated output fuzzy area using the formula $z^* = \frac{\sum x \cdot \mu(x)}{\sum \mu(x)}$. It evaluates the entire shape rather than just the peak, preventing abrupt output jumps."*

#### Q7: Why didn't you use `scikit-fuzzy`?
> *"Implementing the Mamdani system from first principles in NumPy gave me total control over membership slopes, clipping, and defuzzification. It keeps the project lightweight, fully interpretable, and allowed me to verify zero orphan states."*

#### Q8: How many rules are in your rule base, and are there any orphan states?
> *"There are 18 rules (13 for recommended study hours, 5 for study need urgency). We mathematically tested 2,288 state combinations across the 3D domain, and verified that 0 orphan states exist — at least one rule fires for every possible input."*

#### Q9: How do you handle edge cases and malicious inputs?
> *"We validate input lengths (rejecting <4 chars), check fast-path greetings, and use structured LLM output with an `is_study_related` flag to politely reject off-topic questions. We also sanitize user text with `html.escape()` to prevent XSS attacks."*

#### Q10: How do you handle Groq API rate limits?
> *"Groq free-tier has an Output Tokens Per Minute (OTPM) limit of 1,000. We enforce strict token budgeting by setting `max_tokens=250` for extraction and `max_tokens=600` for explanation, along with an automatic 2-attempt retry policy."*

#### Q11: What is the Indian Knowledge Systems (IKS) connection?
> *"The IKS connection is the Indian holistic and learner-centred educational perspective supported by NEP 2020. Rather than imposing rigid, stressful quotas, it respects the student's individual readiness (*adhikara*), encourages self-directed reflection (*svadhyaya*), and promotes balanced effort (*yukta abhyasa*). Modern AI and Fuzzy Logic provide the computational implementation of this learner-centered philosophy."*

---

## 6. How to Run Locally & Run Tests

```bash
# 1. Activate virtual environment
venv\Scripts\activate

# 2. Run automated unit test suite (29 tests)
python -m pytest tests/test_fuzzy.py -v

# 3. Launch Streamlit Web UI
streamlit run app.py
```
Open **`http://localhost:8501`** in your browser.

---

## 7. How to Deploy on Streamlit Community Cloud (Free)

1. Sign in to **[share.streamlit.io](https://share.streamlit.io/)** with GitHub account `yash26761`.
2. Click **Create app**:
   - Repository: `yash26761/student-study-fuzzy-ai`
   - Branch: `main`
   - Main file path: `app.py`
3. Expand **Advanced settings...** $\rightarrow$ **Secrets**, and enter:
   ```toml
   GROQ_API_KEY = "your_actual_groq_api_key_here"
   ```
4. Click **Deploy!**
