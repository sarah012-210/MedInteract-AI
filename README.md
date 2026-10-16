# MedInteract AI 

MedInteract AI is an advanced, safety-audited medical interaction and prescription interpretation system. It bridges real-world medication data, fine-tuned handwriting optical character recognition (**TrOCR**), and Retrieval-Augmented Generation (**RAG**) grounded in official FDA drug labels to help identify potential drug-drug interactions safely and accurately.

---

##  Key Features

* **Real Drug Interaction Data:** Powered by **DDInter** (Xiong et al., Nucleic Acids Res. 2022; CC BY-NC-SA 4.0), classifying interaction pairs and severity levels (*Major, Moderate, Minor, Unknown*).
* **Fine-Tuned Handwriting OCR:** Integrates a fine-tuned Microsoft `TrOCR` model (`sarah012/trocr-rx-medinteract`) trained on multi-source handwritten prescription datasets to read physician handwriting accurately.
* **Smart Name Normalization:** Translates brand names and International Nonproprietary Names (INN) to generic substances using openFDA metadata, RxNorm APIs, and custom local alias mapping.
* **Evidence-Grounded RAG:** Uses sentence embeddings and vector search (Sentence-Transformers + FAISS / TF-IDF) over official openFDA drug labels. The system strictly refuses to hallucinate and references exact text passages.
* **Interactive Streamlit Web App:** Features an easy-to-use web interface supporting photo/PDF prescription uploads and direct text queries with built-in safety validation gates.

---

##  Project Structure

* `medinteract.py`: Core logic module containing data loaders, interaction database wrappers, text normalizers, fine-tuned TrOCR routines, RAG components, and the orchestration agent.
* `app.py`: Streamlit application interface for checking prescriptions and asking medication-related questions.
* `models/trocr_rx`: Local directory for the fine-tuned TrOCR vision-encoder-decoder model.
* `data/`: Folder containing DDInter database CSVs, lexicon JSON files, safety gate configurations, and local brand-to-generic alias maps.

---

##  Installation & Setup

1. **Clone the repository or open in Google Colab:**
   Ensure you have a GPU runtime enabled (e.g., NVIDIA T4) for optimal OCR performance.

2. **Install Dependencies:**
   ```bash
   pip install rapidfuzz scikit-learn sentence-transformers faiss-cpu easyocr transformers pymupdf anthropic streamlit pyngrok requests pillow pandas kaggle huggingface_hub
