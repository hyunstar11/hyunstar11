# Andrew Leem

### Featured Projects – [Resume](https://)
- [Sneaker Demand Intelligence Platform](#sneaker-demand-intelligence-platform-feb-2026)
- [H&M Personalized Fashion Recommender](#hm-personalized-fashion-recommendation-system-mar-2025)
- [FUSION RAG: Multi-Agent GenAI System](#fusion-rag-multi-agent-genai-system-mar-2025)
- [H&M Customer Churn Prediction](#hm-customer-churn-prediction-system-may-2025)

---

Welcome to my GitHub!

I'm **Andrew Leem**, a Master's student in Machine Learning & Data Science at Northwestern University with prior experience as a Data Scientist and AI Intern. My work spans **demand forecasting, NLP/social listening, recommender systems, and GenAI pipelines** — with a focus on consumer and retail domains. I'm passionate about building ML systems that connect behavioral signals to business decisions.

---

## About Me

At Breakthru Beverage Group, I developed forecasting models to improve inventory planning, orchestrated Azure-hosted AI agents in C#/.NET Core, and led segmentation of 1,000+ retail accounts to guide sales strategy. Previously at Concentrix Catalyst, I enhanced global data accuracy, automated GDPR-compliant data retention pipelines in BigQuery, and standardized 20,000+ e-commerce tags across 100+ sites. Earlier at GLG, I built automated Python pipelines and Selenium scrapers to enrich company datasets and improve efficiency.

I bring a strong foundation in Python, SQL, PyTorch, and TensorFlow, along with experience in cloud platforms like Azure, AWS, GCP, and Snowflake. My focus is on building interpretable, scalable AI systems that drive measurable business impact.

---

## Skills & Technologies
- **Programming:** Python, R, SQL, C#, Bash
- **ML & AI:** Scikit-learn, PyTorch, TensorFlow, XGBoost, LightGBM, Prophet, ARIMA, FAISS, LoRA
- **NLP:** VADER, HuggingFace Transformers (RoBERTa), TF-IDF, spaCy
- **Data Platforms:** Snowflake, BigQuery, Hadoop
- **DevOps & Infra:** Azure DevOps, Docker, .NET Core, ASP.NET Core
- **Analytics & Visualization:** Plotly, Streamlit, Tableau, Power BI, Google Analytics
- **Collaboration Tools:** GCP, Jira, Confluence, Git

---

## Projects

### Sneaker Demand Intelligence Platform (Feb 2026)

A two-part end-to-end system that combines **quantitative aftermarket signals** with **real-time consumer sentiment** to support footwear demand planning decisions.

| Component | Repo | Description |
|-----------|------|-------------|
| **sneaker-intel** | [hyunstar11/sneaker-intel](https://github.com/hyunstar11/sneaker-intel) | Tabular ML pipeline on 99K+ StockX transactions |
| **reddit-sentiment** | [hyunstar11/reddit-sentiment](https://github.com/hyunstar11/reddit-sentiment) · [Live Demo](https://reddit-sentiment-x87v7p7tqt6fcauzah6jnd.streamlit.app) | NLP sentiment pipeline on 2,400+ Reddit posts across 9 subreddits |

**sneaker-intel** — ML demand forecasting:
- XGBoost / LightGBM / Random Forest ensemble; 35-feature pipeline (brand, colorway, size, release recency, regional demand)
- Outputs: demand tier classification, price premium prediction, sell-through risk score
- 4 analysis notebooks: StockX EDA, market dynamics, model benchmarking, release strategy optimization
- FastAPI inference server + Streamlit dashboard; 28 tests

**reddit-sentiment** — NLP social listening:
- Hybrid scoring: VADER (fast baseline) + `cardiffnlp/twitter-roberta-base-sentiment-latest` on brand-context windows; blended 0.6 / 0.4
- Detects brand mentions, 40+ retail channels, 7 purchase intent types, and 31 shoe models
- 3 analysis notebooks covering data collection, sentiment analysis, and brand insights
- CLI pipeline (`collect → analyze → report`); HTML report with Plotly charts; 101 tests

**Combined insight example:**
> sneaker-intel places Nike in the *High* demand tier at 1.3–1.8× retail. reddit-sentiment shows Nike at +0.21 avg sentiment with 188 active purchase-seekers and eBay/GOAT as the dominant secondary channels. → Demand exceeds supply; prioritize Nike Direct allocation and hold restock for 60+ days.

---

### H&M Personalized Fashion Recommendation System (Mar 2025)
- Built end-to-end recommender using collaborative filtering (FAISS), content-based similarity, and hybrid logic with association rules
- Achieved **MAP@12 = 0.0470** across 1.3M customers and 31M transactions
- Constructed 4,000+ RFM features, applied Incremental PCA + MiniBatchKMeans, and uncovered high-value customer clusters

---

### FUSION RAG: Multi-Agent GenAI System (Mar 2025)
- Built multi-agent Retrieval-Augmented Generation system with GPT-3.5, Pinecone, and ChromaDB
- Designed LoRA-tuned agents with specialized tasks (retrieval, summarization, synthesis) orchestrated via prompt chaining
- Improved modularity and context relevance in climate change Q&A pipelines

---

### H&M Customer Churn Prediction System (May 2025)
- Built an end-to-end churn prediction pipeline with automated data processing, feature engineering, and reproducible experiment management
- Developed a Random Forest model to identify high-risk customers, enabling targeted retention strategies with interpretable churn scores
- Deployed an interactive Streamlit dashboard on AWS to visualize churn risk, feature importance, and model performance in real time

---

## Get in Touch
- [LinkedIn](https://www.linkedin.com/in/andrewleem)
- Email: [andrew.leem@gmail.com](mailto:andrew.leem@gmail.com)
