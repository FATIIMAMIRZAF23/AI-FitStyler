Markdown# 🛍️ AI-FitStyler: Your Personal Multi-Agent Fashion Advisor

## 📄 Project Overview
AI-FitStyler is an innovative, web-based fashion recommendation system designed to provide **hyper-personalized outfit suggestions**. It leverages a **multi-agent architecture** to combine **Computer Vision (CV)** analysis of the user's physique (body type and skin tone) with a highly efficient **Retrieval-Augmented Generation (RAG)** engine for finding optimal, trend-aware, and budget-friendly outfits from a product catalog.

The system addresses critical gaps in traditional online shopping by offering **speed, personalization, and actionable style advice**.

---

## 🚀 Key Features

* **Precision Body Analysis:** Uses **MediaPipe Pose** to detect body landmarks and determine the user's body type (slim, curvy, athletic) based on hip-to-shoulder ratios.
* **Skin Tone & Color Palette Detection:** Uses **MediaPipe Face Mesh** and **LAB Color Space** analysis to identify skin tone (fair, wheatish, dark) and suggest a complementary color palette.
* **Rapid RAG Engine:** Utilizes a **FAISS Vector Store** paired with **HuggingFace Embeddings** for fast and semantically relevant outfit retrieval from your local dataset catalog.
* **Trend Critique:** Provides a dynamic **Trend Score (7/10 to 10/10)** accompanied by automated fashion commentary for every retrieved suggestion.
* **Interactive UI:** Built using **Streamlit** for a responsive, fast, and web-friendly layout interface.

---

## ⚙️ System Architecture

AI-FitStyler runs on a modular **Multi-Agent Architecture**, orchestrated with custom Python routing modules.

```text
[User Input Image/Filters] 
           │
           ▼
┌──────────────────────────────────────┐
│       Analysis Agents (CV)           │ ──► body_analyzer.py & skin_color_analyzer.py
└──────────────────────────────────────┘
           │
           ▼
┌──────────────────────────────────────┐
│    Data & Retrieval Layer (RAG)      │ ──► rag_system.py (FAISS Vector Store Index)
└──────────────────────────────────────┘
           │
           ▼
┌──────────────────────────────────────┐
│      Generation Agents (RAG)         │ ──► outfit_generator.py & trend_critic.py
└──────────────────────────────────────┘
           │
           ▼
 [Streamlit Application Interface]     ──► app.py Framework UI Rendering
🛠️ Installation and Setup
Prerequisites
Python 3.8 or higher
pip 
(Python Package Installer)
1. Install Required Libraries
 Install all required libraries mapped inside the project workspace directory:
    Bash
    pip install -r requirements.txt
2. Build the RAG Index (Mandatory)
 The system must parse your internal catalog data and generate the local vector embeddings store before running queries:
  Bash
  python core/rag_system.py
 Expected Terminal Output:
  Plaintext
  RAG built and saved! Ready for queries.
3. Launch the Application
 Run the Streamlit web deployment application layout locally:
  Bash
  streamlit run app.py
 The application interface will automatically launch inside your default browser at: http://localhost:8501
👨‍💻 Usage Instruction Flow
 Set Preferences: 
  Utilize the interactive sidebar options to specify target Gender, Occasion styling type, and Budget caps.
Upload Photo:
  Provide a clear, portrait full-body image for accurate dimension extraction calculations.
Analyze Metrics:
  View real-time extracted outputs displaying calculated Body Type, Skin Tone matrix values, and Suggested Color Palettes.
Get Suggestions: 
  Trigger the system generation to retrieve ranked outfit listings alongside individual trend critiques.