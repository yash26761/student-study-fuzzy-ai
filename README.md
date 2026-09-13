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
