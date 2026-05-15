# 📊 Project A3: AI-Powered Customer Feedback Dashboard & Chatbot

![Python](https://img.shields.io/badge/Python-3.11-blue.svg)
![HuggingFace](https://img.shields.io/badge/HuggingFace-Transformers-yellow.svg)
![Gradio](https://img.shields.io/badge/Gradio-UI-orange.svg)
![Gemini](https://img.shields.io/badge/Google%20Gemini-LLM-blueviolet.svg)

## 📌 Overview
[cite_start]Businesses today receive thousands of customer reviews, and manually analyzing this volume is time-consuming and inefficient[cite: 202, 203]. [cite_start]Furthermore, many existing tools ignore Arabic-language reviews, creating a blind spot in customer intelligence[cite: 206]. 

**Project A3** is an end-to-end AI-powered system designed to solve this. [cite_start]It processes large volumes of unstructured, multilingual customer feedback (Arabic and English) [cite: 213, 223][cite_start], extracts key themes, and provides a conversational chatbot interface so business users can query their data naturally[cite: 216].

---

## 🚀 Key Features

* **Multilingual Sentiment Analysis:** Utilizes dual, language-specific transformer models to classify text into Positive, Negative, or Neutral:
  * [cite_start]**English:** `distilbert-base-uncased-finetuned-sst-2-english` [cite: 247]
  * [cite_start]**Arabic:** `CAMeL-Lab/bert-base-arabic-camelbert-mix-sentiment` [cite: 248]
* [cite_start]**Smart Keyword Extraction:** Uses `KeyBERT` to extract semantically meaningful keywords and themes from mixed-language reviews[cite: 252].
* **Generative AI Chatbot:** Features a "Gemini Insight Generator" powered by Google's Gemini 3 Flash model via LangChain. [cite_start]The chatbot routes natural language queries to provide data-grounded business insights[cite: 262].
* [cite_start]**Interactive Dashboard:** A Gradio-based web interface that visualizes real-time sentiment distribution alongside the chat interface[cite: 261].

---

## 🧠 System Architecture

The NLP pipeline is structured sequentially for maximum efficiency, with GPU acceleration enabled:

1. **Data Acquisition:** Automatically downloads the Yelp dataset (English) and the Arabic Sentiment Twitter Corpus via the Kaggle API.
2. [cite_start]**Preprocessing:** Cleans text by removing special characters and standardizing formats while preserving Arabic diacritics where necessary[cite: 241].
3. **Inference (Transformers):** Feeds cleaned text into the respective HuggingFace pipelines for sentiment scoring.
4. **Keyword Extraction:** Passes short contexts to KeyBERT (`paraphrase-multilingual-MiniLM-L12-v2`) to find top n-grams.
5. **Dashboard & LLM:** Aggregates the processed data into a statistical summary injected into Gemini's system prompt, allowing the chatbot to answer specific questions about the dataset.

---

## ⚙️ Installation & Setup

### Prerequisites
Ensure you have Python installed and a valid **Google Gemini API Key** and **Kaggle API Token** (`kaggle.json`).

### 1. Install Dependencies
Run the following pip command to install all required libraries:

```bash
pip install kaggle pandas numpy nltk langdetect textblob transformers torch keybert langchain langchain-google-genai gradio matplotlib seaborn wordcloud camel-tools
