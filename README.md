<div align="center">

# 🤖 FAQ Chatbot — AI-Powered Question Answering

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=20&pause=1000&color=6C63FF&center=true&vCenter=true&width=600&lines=FAQ+Chatbot+with+NLP;TF-IDF+%2B+Cosine+Similarity+Matching;25+FAQs+%7C+5+Categories;Built+by+Tauseef+Alam+%40+CodeAlpha" alt="Typing SVG" />

<br/>

![Python](https://img.shields.io/badge/Python-3.12-3776AB?style=for-the-badge&logo=python&logoColor=white)
![NLTK](https://img.shields.io/badge/NLTK-3.8.1-4CAF50?style=for-the-badge)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.3-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)
![Gradio](https://img.shields.io/badge/Gradio-5.x-FF7C00?style=for-the-badge)
![Colab](https://img.shields.io/badge/Google_Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white)
![Status](https://img.shields.io/badge/Task-2%2F4%20Complete-success?style=for-the-badge)

<br/>

| 👨‍💻 Developer | 🏢 Company | 📅 Batch | 🧠 Domain |
|:---:|:---:|:---:|:---:|
| **Tauseef Alam** | **CodeAlpha** | **May 2026** | **NLP · Machine Learning** |

<br/>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](YOUR_LINKEDIN_URL)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-181717?style=for-the-badge&logo=github&logoColor=white)](YOUR_GITHUB_URL)

</div>

---

## 📌 Table of Contents

- [About the Project](#-about-the-project)
- [Live Demo](#-live-demo)
- [Features](#-features)
- [How It Works](#-how-it-works)
- [NLP Pipeline](#-nlp-pipeline-step-by-step)
- [FAQ Knowledge Base](#-faq-knowledge-base)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [How to Run](#-how-to-run)
- [Screenshots](#-screenshots)
- [What I Learned](#-what-i-learned)
- [Connect](#-connect)

---

## 🎯 About the Project

A **Natural Language Processing chatbot** that understands the *meaning* of your question — not just exact keywords — and returns the most relevant answer from a curated FAQ knowledge base.

> Type `"tell me about ML"` and it correctly matches `"What is machine learning?"` — because it compares **semantic meaning**, not word-for-word text.

Built as **Task 2** of the **CodeAlpha AI Internship** (May 2026 Batch) using Python, NLTK, TF-IDF vectorization, and cosine similarity.

> *"The chatbot doesn't search for keywords. It measures the angle between ideas."*

---

## 🎬 Live Demo

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  You   →  "tell me about ML"

  Bot   →  📊 Machine Learning (ML) is a type of AI
           where computers learn from data — WITHOUT
           being explicitly programmed with rules...

           📌 Matched: "What is machine learning?"
           🎯 Confidence: [████████░░] 82%

           📚 You can also ask:
              • What is deep learning?
              • What is TF-IDF?
              • What is a neural network?
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  You   →  "pizza recipe"

  Bot   →  🤔 I don't have information on that yet.

           Try asking about:
           • What is AI?
           • What is machine learning?
           • How to submit CodeAlpha tasks?
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 💬 **Smart Matching** | Matches question meaning using TF-IDF + Cosine Similarity |
| 🔑 **Keyword Boosting** | Exact keyword matches get an extra confidence score boost |
| 📊 **Confidence Score** | Every answer shows a percentage bar (e.g. `[████████░░] 82%`) |
| 🗂️ **Category Filter** | Search only within AI, Python, Computer Vision, CodeAlpha, or Career |
| 📚 **Related Questions** | 3 related questions suggested after every answer |
| 🗃️ **FAQ Browser Tab** | Explore all 25 questions in a filterable table |
| 💾 **Chat Export** | Download full conversation as a `.txt` file |
| ⚡ **10 Quick Buttons** | Pre-loaded suggestion questions on the right panel |
| 🧹 **Clear Chat** | Reset the conversation with one click |
| ⚙️ **How It Works Tab** | Built-in technical explanation of the NLP pipeline |

---

## 🔬 How It Works

The chatbot uses a classic **NLP retrieval pipeline** — no GPT, no paid AI, just math and text processing:

```
┌─────────────────────────────────────────────────────────┐
│                   User types a question                  │
└────────────────────────┬────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────┐
│              STEP 1 — preprocess_text()                 │
│  lowercase → remove punctuation → tokenize              │
│  → remove stopwords → lemmatize → rejoin                │
│                                                         │
│  "What IS Machine Learning?!"  →  "machine learn"      │
└────────────────────────┬────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────┐
│           STEP 2 — TfidfVectorizer.transform()          │
│  Converts cleaned text → numeric vector                 │
│  Rare important words score HIGH                        │
│  Common words ("the", "is") score LOW                   │
│                                                         │
│  "machine learn"  →  [0.0, 0.82, 0.0, 0.45, ...]       │
└────────────────────────┬────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────┐
│             STEP 3 — cosine_similarity()                │
│  Compares user vector vs ALL 25 FAQ vectors             │
│  Measures the angle between them (0 = different,       │
│  1 = identical meaning)                                 │
│                                                         │
│  Scores: [0.82, 0.03, 0.15, 0.01, ...]                 │
└────────────────────────┬────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────┐
│          STEP 4 — Keyword Boost (Advanced)              │
│  If user words match FAQ keywords exactly               │
│  → add +0.08 bonus to that FAQ's score                  │
└────────────────────────┬────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────┐
│               STEP 5 — Return Answer                    │
│  argmax() → FAQ with highest score wins                 │
│  score < 0.10 → "I don't know" (graceful fallback)      │
│  Return: answer + confidence + related questions         │
└─────────────────────────────────────────────────────────┘
```

---

## 🧪 NLP Pipeline — Step by Step

### Text Preprocessing

```python
from nltk.tokenize import word_tokenize
from nltk.corpus import stopwords
from nltk.stem import WordNetLemmatizer

def preprocess_text(text):
    # Step 1: Lowercase everything
    text = text.lower()
    # "What IS Machine Learning?!" → "what is machine learning?!"

    # Step 2: Remove punctuation
    text = re.sub(r'[^\w\s]', '', text)
    # "what is machine learning?!" → "what is machine learning"

    # Step 3: Split into individual words
    tokens = word_tokenize(text)
    # → ["what", "is", "machine", "learning"]

    # Step 4: Remove stopwords (common useless words)
    tokens = [w for w in tokens if w not in stop_words]
    # → ["machine", "learning"]  (removed "what", "is")

    # Step 5: Lemmatize (reduce to base form)
    tokens = [lemmatizer.lemmatize(w) for w in tokens]
    # "running" → "run" | "better" → "good"
    # → ["machine", "learn"]

    return ' '.join(tokens)
    # → "machine learn"
```

### TF-IDF Vectorization

```python
from sklearn.feature_extraction.text import TfidfVectorizer

# TF-IDF = Term Frequency × Inverse Document Frequency
# Words appearing everywhere ("the", "is") → LOW score
# Unique important words ("algorithm", "neural") → HIGH score

vectorizer = TfidfVectorizer(ngram_range=(1, 2), sublinear_tf=True)
tfidf_matrix = vectorizer.fit_transform(processed_faq_questions)
# Shape: (25 FAQs) × (N unique word features)
```

### Cosine Similarity Matching

```python
from sklearn.metrics.pairwise import cosine_similarity

user_vector = vectorizer.transform([preprocess_text(user_question)])
scores = cosine_similarity(user_vector, tfidf_matrix).flatten()
# → [0.82, 0.03, 0.15, ...] — one score per FAQ

best_idx = np.argmax(scores)      # FAQ with highest score
best_score = scores[best_idx]     # confidence value

if best_score < 0.10:
    return "I don't know"         # graceful fallback
else:
    return faq_df.iloc[best_idx]['answer']
```

---

## 📚 FAQ Knowledge Base

The chatbot knows **25 questions** organized across **5 categories**:

### 🤖 AI Fundamentals (6 questions)
- What is Artificial Intelligence?
- What is machine learning?
- What is deep learning?
- What is natural language processing?
- What is a neural network?
- What is the difference between AI, ML, and Deep Learning?

### 🐍 Python & Libraries (6 questions)
- What Python libraries are used in AI?
- What is TF-IDF?
- What is cosine similarity?
- What is Gradio?
- What is NLTK?
- What is scikit-learn?

### 👁️ Computer Vision (4 questions)
- What is computer vision?
- What is YOLO object detection?
- What is OpenCV?
- What is object tracking?

### 🏢 CodeAlpha Internship (5 questions)
- What is CodeAlpha?
- What are the CodeAlpha AI internship tasks?
- How do I submit CodeAlpha tasks?
- What certificate do I get from CodeAlpha?
- What is the GitHub repo name for CodeAlpha?

### 💼 Career & Learning (4 questions)
- How to become an AI engineer?
- What skills are needed for AI jobs?
- What is Google Colab?
- What is GitHub and why is it important?

---

## 🛠️ Tech Stack

<div align="center">

| Library | Version | Role |
|---------|---------|------|
| `Python` | 3.12 | Core language |
| `nltk` | 3.8.1 | Tokenization · stopwords · lemmatization |
| `scikit-learn` | 1.3+ | TF-IDF vectorizer + cosine similarity |
| `pandas` | 2.0+ | FAQ dataset organization |
| `numpy` | 2.0+ | Array operations and scoring |
| `gradio` | 5.x | Web interface (already in Colab) |

</div>

---

## 📁 Project Structure

```
Task2_FAQChatbot/
│
├── Task2_FAQ_Chatbot_FIXED.py    ← Main application (error-free)
└── README.md                     ← This file
```

---

## 🚀 How to Run

### Option A — Google Colab (Recommended)

**Step 1 — Open Colab and install libraries**
```python
!pip install nltk scikit-learn gradio pandas numpy
```

**Step 2 — Run NLTK downloads**
```python
import nltk
for pkg in ['punkt', 'punkt_tab', 'stopwords', 'wordnet', 'omw-1.4']:
    nltk.download(pkg, quiet=True)
```

**Step 3 — Run the app file**
Paste the contents of `Task2_FAQ_Chatbot_FIXED.py` into Colab cells and run top to bottom.

**Step 4 — Click the public URL**
The last cell launches Gradio and prints a `gradio.live` URL. Click it.

---

### Option B — Local Machine

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/codealpha_tasks.git
cd codealpha_tasks/Task2_FAQChatbot

# Install dependencies
pip install nltk scikit-learn gradio pandas numpy

# Run the app
python Task2_FAQ_Chatbot_FIXED.py
```

App opens at: `http://localhost:7860`

---

### Common Errors & Fixes

| Error | Cause | Fix |
|-------|-------|-----|
| `ModuleNotFoundError: nltk` | Not installed | Run `pip install nltk` |
| `LookupError: punkt` | NLTK data missing | Run `nltk.download('punkt_tab')` |
| `ModuleNotFoundError: websockets.legacy` | Wrong gradio/websockets versions | Do NOT reinstall gradio — use Colab's pre-installed version |
| `Chatbot not responding` | Model not trained | Make sure all cells ran top to bottom |

---

## 🧪 Test Cases

After launching, try these questions to verify everything works:

```
✅ "What is AI?"              → returns AI definition
✅ "tell me about ML"         → matches "What is machine learning?" (abbreviation test)
✅ "what is yolo"             → returns YOLO detection answer (keyword boost)
✅ "how do I submit my tasks" → returns CodeAlpha submission guide
✅ "what is the repo name"    → returns codealpha_tasks info
✅ "career in artificial intelligence" → matches career question
✅ "pizza recipe"             → returns "I don't know" (out-of-scope test)
✅ Click suggestion buttons   → loads question into input box
✅ Change category filter     → narrows search to one topic
✅ Click "Export Chat"        → downloads .txt file
```

---

## 📸 Screenshots

> *(Add screenshots of your running Gradio app here)*

**How to add:**
1. Take a screenshot while your app is running
2. Save as `screenshot.png`
3. Upload to this folder on GitHub
4. Replace the line below with: `![App Screenshot](screenshot.png)`

---

## 📖 What I Learned

**Text preprocessing matters more than the model.**
Before I built this, I thought matching questions was about finding similar words. After building it, I realized most of the work happens *before* any matching — cleaning the text, removing noise, reducing words to their base forms. Without preprocessing, "running" and "run" would never match.

**TF-IDF is elegant.**
The idea that a word's importance should be weighted by how *rare* it is across all documents is beautifully simple. Words like "the" appear everywhere so they tell you nothing. Words like "algorithm" are specific — they tell you a lot. One formula captures all of that.

**Cosine similarity measures meaning, not distance.**
Two sentences can have completely different lengths and still mean almost the same thing. Cosine similarity doesn't care about magnitude — it only measures the *angle* between vectors. That's why "What is ML?" and "Explain machine learning to me" can still match.

**Graceful fallbacks are good AI design.**
I taught the chatbot to say "I don't know" when its confidence is below 10%. A model that admits its limits is more trustworthy than one that confidently gives wrong answers. This was a deliberate design choice, not just error handling.

---

## 🔗 Related Tasks

| Task | Project | Link |
|------|---------|------|
| Task 1 | Language Translation Tool | [View →](../Task1_LanguageTranslation/) |
| Task 2 | FAQ Chatbot *(you are here)* | — |
| Task 3 | Music Generation with AI | [View →](../Task3_MusicGeneration/) |
| Task 4 | Object Detection & Tracking | [View →](../Task4_ObjectDetection/) |

---

## 👨‍💻 Connect

<div align="center">

**Tauseef Alam**

*AI Intern @ CodeAlpha | May 2026 Batch*

<br/>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Tauseef_Alam-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](YOUR_LINKEDIN_URL)
[![GitHub](https://img.shields.io/badge/GitHub-Profile-181717?style=for-the-badge&logo=github&logoColor=white)](YOUR_GITHUB_URL)
[![Email](https://img.shields.io/badge/Email-Get_in_touch-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:YOUR_EMAIL)

<br/>

---

<sub>
Built with ❤️ during the <strong>CodeAlpha AI Internship</strong> — May 2026<br/>
Python · NLTK · scikit-learn · TF-IDF · Cosine Similarity · Gradio
</sub>

</div>
