# AI-Based Study Time Recommendation System Using Fuzzy Logic

**B.Sc. Information Technology – Third Year Internal Assessment Project**

## Project Overview

This project recommends how much time a student should study per day based on their current study situation.

The student can describe their situation in normal English, for example:

> My exam is in 5 days. I studied 2 hours today and my preparation is poor.

The system uses an LLM through LangChain to understand the input and extract the required information. These values are then processed by a Mamdani Fuzzy Inference System to calculate the recommended study time.

A second LangChain/LLM step explains the recommendation and provides simple study tips.

## Objective

- Understand a student's study situation from natural language.
- Extract useful study information using an LLM.
- Use fuzzy logic to calculate study requirements.
- Give a daily study-time recommendation.
- Explain the result and provide study tips.

## IKS Connection

This project is developed under the **Indian Knowledge Systems (IKS)** initiative for Third Year B.Sc. IT.

### 1. Selected IKS Theme
**Indian Holistic and Learner-Centred Educational Perspective.**

### 2. Relevant Indian Educational Perspective
In traditional Indian educational philosophy, learning is not viewed as a rigid, one-size-fits-all production line. It emphasizes:
- **Learner-Centred Readiness (*Adhikara*):** Recognizes that every student starts from a unique state of readiness, prior study, and individual capacity.
- **Self-Directed Study (*Svadhyaya*):** Stresses meaningful self-study, self-reflection, and realistic self-assessment rather than blind, stressful cramming.
- **Balanced Effort (*Yukta Abhyasa*):** Promotes moderation and balance to avoid academic burnout and maintain mental well-being.

### 3. Connection to Personalized Student Learning
In modern exam preparation, students often face stressful, arbitrary advice (e.g., "study 10 hours daily regardless of anything"). This project implements the Indian holistic learning philosophy by assessing each student as an individual:
- How many days remain before the exam?
- How many hours have already been studied today?
- How confident does the student feel about their preparation?

The recommendation is customized to support balanced, sustainable daily progress rather than imposing harsh, identical quotas.

### 4. Application of Modern AI
Modern AI (**LangChain + Groq LLM**) acts as the natural-language interface. It allows students to describe their study situation in conversational English. The LLM extracts the relevant parameters into structured, validated Pydantic data and provides encouraging, actionable study tips.

### 5. Role of Fuzzy Logic
Human feelings about study readiness (e.g., "fair preparation", "exam is close") are continuous and gradual, not binary true/false. A **Mamdani Fuzzy Inference System** (with 18 rules and centroid defuzzification) calculates realistic study hours smoothly, avoiding the unnatural jumps of rigid `if/else` logic.

### 6. What the IKS Component Does NOT Claim
To maintain scientific and academic integrity:
- We do **NOT** claim that ancient Indian texts invented fuzzy logic (fuzzy sets were mathematically introduced by Lotfi Zadeh in 1965).
- We do **NOT** claim that ancient texts specify the 0–8 hour study formula or defuzzification math.
- We do **NOT** claim that the 18 fuzzy rules were taken from Vedas or ancient scriptures.
- The distinction is clear: **IKS provides the educational perspective and rationale**, while **modern AI and fuzzy logic provide the computational implementation**.

### 7. Official Source References
- **National Education Policy 2020 (NEP 2020):** Ministry of Education, Govt. of India. Emphasizes holistic, learner-centric education and integration of IKS. [NEP 2020 PDF](https://www.education.gov.in/sites/upload_files/mhrd/files/NEP_Final_English_0.pdf)
- **IKS Division, Ministry of Education, Govt. of India:** Established at AICTE to promote interdisciplinary research bridging traditional knowledge with modern computing. [IKS Division Website](https://iksindia.org/)
- For detailed academic documentation, see [`docs/iks_connection.md`](docs/iks_connection.md) and verified source records in [`docs/iks_sources.md`](docs/iks_sources.md).

## How It Works

```text
Student's Natural-Language Input
              ↓
       LangChain + LLM
              ↓
     Structured Information
              ↓
       Pydantic Validation
              ↓
     Mamdani Fuzzy System
              ↓
 Fuzzification → Rules → Aggregation
              ↓
      Centroid Defuzzification
              ↓
   Recommended Study Time
              ↓
       LangChain + LLM
              ↓
 Explanation + Study Tips
              ↓
        Streamlit UI
```

## Fuzzy Logic

The project uses a **Mamdani Fuzzy Inference System**.

### Inputs

| Input | Range | Fuzzy Sets |
|---|---|---|
| Days Until Exam | 0–30 days | Near, Medium, Far |
| Study Hours Today | 0–12 hours | Low, Medium, High |
| Preparation Level | 0–100% | Poor, Average, Good |

### Output

| Output | Range | Fuzzy Sets |
|---|---|---|
| Recommended Study Time | 0–8 hours/day | Low, Medium, High |

The fuzzy system uses:

- Triangular and trapezoidal membership functions
- 18 fuzzy rules
- Minimum operation for fuzzy AND
- Maximum aggregation
- Centroid defuzzification

## AI / LangChain

LangChain and the LLM are used in two places:

**1. Information Extraction**

The LLM understands the student's natural-language input and extracts:

- Days until exam
- Study hours today
- Preparation level

The extracted information is returned as structured Pydantic data.

**2. Explanation**

After the fuzzy system calculates the recommendation, the result is sent to the LLM again.

The LLM explains the recommendation and gives simple study tips.

## Technologies Used

- Python
- LangChain
- Groq LLM
- Pydantic
- NumPy
- Streamlit
- Matplotlib
- Pytest

## Project Structure

```text
student-study-fuzzy-ai/
│
├── app.py
├── extractor.py
├── explainer.py
├── fuzzy_system.py
├── llm_config.py
├── models.py
├── visualization.py
├── requirements.txt
├── README.md
├── .env.example
├── .gitignore
│
├── docs/
│   ├── iks_connection.md
│   ├── iks_sources.md
│   ├── PROJECT_SUMMARY.md
│   └── viva_notes.md
│
└── tests/
    └── test_fuzzy.py
```

## How to Run

Clone the repository:

```bash
git clone https://github.com/yash26761/student-study-fuzzy-ai.git
cd student-study-fuzzy-ai
```

Create and activate a virtual environment.

**Windows:**

```bash
python -m venv venv
venv\Scripts\activate
```

Install the required packages:

```bash
pip install -r requirements.txt
```

Configure your Groq API key in a local `.env` file using `.env.example` as a guide.

Then start the application:

```bash
streamlit run app.py
```

The application will open at:

```text
http://localhost:8501
```

## Deploy to Streamlit Community Cloud (Free)

1. Sign in to [share.streamlit.io](https://share.streamlit.io/) using your GitHub account (`yash26761`).
2. Click **Create app** (or **New app**), and select:
   - **Repository:** `yash26761/student-study-fuzzy-ai`
   - **Branch:** `main`
   - **Main file path:** `app.py`
3. Expand **Advanced settings...** $\rightarrow$ **Secrets**, and enter your Groq API key:
   ```toml
   GROQ_API_KEY = "your_groq_api_key_here"
   ```
4. Click **Deploy!**

## Example

**Student Input:**

> My exam is in 5 days. I studied 2 hours today and my preparation is poor.

**AI Extracts:**

```text
Days until exam: 5
Study hours: 2
Preparation level: 20%
```

**Fuzzy Result:**

```text
Recommended Study Time: 5.15 hours/day
Study Need: High
```

The second AI step then explains the result and provides study tips.

## Conclusion

This project combines **LangChain and an LLM** for natural-language understanding with a **Mamdani Fuzzy Inference System** for decision making.

The combination allows the system to understand a student's study situation, handle gradual conditions using fuzzy logic, calculate a study-time recommendation, and explain the result in simple language.
