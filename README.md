# Perspective Aware Sentiment Analysis

## Project Overview
Traditional sentiment analysis models often assign a fixed label (Positive, Negative, Neutral) to text based on general patterns.However, sentiment is often **subjective** and dependent on the reader's point of view.

This project compares **Traditional Models** (RoBERTa) against **Large Language Models** (GPT-4o) to demonstrate **Perspective-Aware Sentiment Analysis**. While traditional models focus on the text's structural polarity, LLMs can adopt specific **personas** (e.g., "I am a sports fan" or "I support a specific political party") to provide context-aware sentiment scoring.

## Data Used
Real-time news data was fetched using the **Google News RSS feed** via the `feedparser` library. The system extracts headlines, links, and publication dates for analysis.

**Source:** Google News RSS (Search Query: "election", "sports", etc.) 
**Libraries:** `feedparser`, `transformers`, `openai`

| Title | Source | Date |
| :--- | :--- | :--- |
| Kerala Local Body Elections Scheduled... | Newsonair | 2025-11-13 |
| Bihar Election 2025 LIVE Updates... | The Economic Times | 2025-11-13 |
| Milwaukee Bucks star Giannis sustained... | N/A (Text Input) | N/A |

Understanding sentiment requires context. For example, a sports injury report is factually "Neutral" to a machine but deeply "Negative" to a fan of that team By leveraging LLMs, this project highlights the shift from **static classification** to **dynamic, personalized content analysis**, which is crucial for next-generation recommendation systems and media monitoring .

We compared a standard Hugging Face pipeline (`twitter-roberta-base-sentiment`) against OpenAI's `gpt-4o-mini` with custom system prompts.

**Test Case:** *Headline about Giannis Antetokounmpo sustaining a groin strain.**.

| Model | Perspective | Detected Sentiment | Confidence/Score |
| :--- | :--- | :--- | :--- |
| **RoBERTa (Traditional)** | General/None | **Neutral** | 0.593 |
| **GPT-4o (LLM)** | "I am a fan of Giannis" | **Negative** | 0.12 |

As shown above, the Traditional model viewed the injury report as a neutral fact, whereas the Perspective-Aware model correctly identified it as negative for a fan.

**Political Context Test:**
When analyzing election news with the prompt *"I don't support BJP"*, the model successfully identified news about an opposition victory as **Positive** and ruling party confidence as **Negative**, demonstrating high adaptability.

## Links
* **Code/Notebook:** [Perspective_Aware_Sentiment_Analysis.ipynb](Perspective_Aware_Sentiment_Analysis.ipynb)
* **Presentation:** [Applied_Data_Analytics_Project_Slides](Applied_Data_Analytics_Project_Slides)
