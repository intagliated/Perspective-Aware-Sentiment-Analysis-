# Perspective-Aware Sentiment Analysis via Multi-Agent Debate

##  Problem
Traditional sentiment analysis (e.g., RoBERTa) assigns a single polarity label to text, 
ignoring that sentiment is inherently subjective and dependent on the reader's perspective.

##  Solution
This project implements a **multi-agent debate framework** where specialized LLM agents 
collaborate to produce explainable, perspective-aware sentiment scores.

##  Architecture

The system consists of four specialized agents orchestrated via LangGraph:

| Agent | Role |
|-------|------|
|  **Stakeholder Advocate** | Argues why the text evokes sentiment from a specific persona's viewpoint |
|  **Context Expert** | Provides objective, real-world background to ground the discussion |
|  **Skeptic** | Challenges emotional overreactions and logical leaps |
| **Supervisor/Judge** | Synthesizes the debate into a final score (-1.0 to 1.0) with rationale |

## 🔧 Tech Stack
- **Orchestration:** LangGraph (stateful multi-agent workflows)
- **LLM Backend:** Groq (open-weight models via `openai/gpt-oss-120b`)
- **Data Ingestion:** Google News RSS via `feedparser`
- **Baseline Comparison:** HuggingFace `twitter-roberta-base-sentiment`

##   Example Output

**Headline:** *"Giannis sits out third consecutive game amid load management concerns."*  
**Perspective:** *"I am a devoted Milwaukee Bucks fan who pays for tickets."*

