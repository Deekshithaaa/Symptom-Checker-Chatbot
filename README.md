[Symptom_Checker_Chatbot_README.md](https://github.com/user-attachments/files/21997057/Symptom_Checker_Chatbot_README.md)
# Symptom Checker Chatbot

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:4facfe,100:00f2fe&height=200&section=header&text=Symptom%20Checker%20Chatbot&fontSize=42&fontColor=fff&animation=fadeIn&fontAlign=50&desc=Python%20%7C%20Flask%20%7C%20PyTorch%20RNN%20%7C%20NLTK&descSize=16&descAlign=50&descAlignY=75" />

[![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](#)
[![Flask](https://img.shields.io/badge/Flask-000?style=for-the-badge&logo=flask&logoColor=white)](#)
[![PyTorch](https://img.shields.io/badge/PyTorch-ee4c2c?style=for-the-badge&logo=pytorch&logoColor=white)](#)
[![NLTK](https://img.shields.io/badge/NLTK-NLP-154F8B?style=for-the-badge)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)](LICENSE)

</div>

---

## 📌 Overview
An interactive **health symptom assistant** that understands free‑text inputs and suggests relevant intents (e.g., fever, cough) and nearby medical center information.  
It uses a **PyTorch RNN** for intent classification, **NLTK** utilities for tokenization/stemming, and a **Flask** UI for conversational interaction.

> **Disclaimer:** This tool is for **educational/demonstration purposes** only and **not** a substitute for professional medical advice.

---

## 🧠 How It Works
1. **Preprocess**: Text is tokenized and stemmed via `nltk_utils.py`.
2. **Vectorize**: Inputs are converted to numerical tensors compatible with the model.
3. **Infer**: A trained **RNN** (weights in `data_rnn.pth`) predicts an **intent** from `intents.json`.
4. **Respond**: The Flask app renders a chat UI and replies; when relevant, it surfaces entries from `medical_centers.json`.

---

## 🗂 Project Structure
```
.
├── app.py                # Flask entrypoint (serves chat UI & routes)
├── chat.py               # Chat wrapper that loads model & runs inference
├── train.py              # Training loop to build/update the RNN model
├── model.py              # RNN model architecture
├── model_chat.py         # Model utilities used during inference
├── nltk_utils.py         # Tokenization/stemming helpers (NLTK)
├── intents.json          # Labeled intents, patterns, & responses
├── medical_centers.json  # Sample data for nearby facilities
├── data_rnn.pth          # Pretrained model weights (binary)
├── templates/            # HTML templates (Flask)
├── static/               # CSS/JS assets
├── requirements.txt
└── LICENSE
```

---

## 🚀 Quickstart

### 1) Clone & Create a Virtual Env
```bash
git clone https://github.com/Deekshithaaa/Symptom-Checker-Chatbot.git
cd Symptom-Checker-Chatbot

python -m venv venv
# Windows: venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate
```

### 2) Install Dependencies
```bash
pip install -r requirements.txt
```
> If NLTK raises missing resource errors, run:
> ```python
> python -c "import nltk; nltk.download('punkt'); nltk.download('stopwords')"
> ```
> (Only if your environment needs these.)

### 3) Run the App
```bash
python app.py
```
Open **http://127.0.0.1:5000/** in your browser.

---

## 🧪 Retraining the Model
Customize intents or extend the domain:
1. Edit **`intents.json`** to add new patterns/responses.
2. Train:
   ```bash
   python train.py
   ```
3. The script emits a new `.pth` file. Update the model path in **`chat.py`** (the `FILE` constant) to your new weights.

---

## 🔌 Configuration
- **Model path**: set in `chat.py` (points to the `.pth` file to load).
- **Medical centers**: update `medical_centers.json` with your region’s data.
- **Port/host**: adjust in `app.py` if needed (Flask dev server).

---

## 📡 Endpoints
- **GET /** → Chat UI (Flask template).  
*(All messaging typically flows through the web form; no public REST contract is guaranteed.)*

---

## 🧱 Limitations
- A compact RNN intent classifier – not a diagnostic model.
- Predictions depend on coverage/design of `intents.json`.
- No PHI storage; example data only. Add your own privacy controls for production.

---

## 🤝 Contributing
PRs and issues are welcome! Consider:
- Expanding intents and utterances
- Improving the model (e.g., GRU/LSTM, attention, transformers)
- Adding unit tests for preprocessing & model I/O
- Packaging a minimal REST API for headless use

---

## 👩‍💻 Maintainer
**Deekshitha Obulreddygari — Full Stack Developer**  
📧  [obulreddygarideekshitha@gmail.com](mailto:obulreddygarideekshitha@gmail.com)  
🔗  [linkedin.com/in/deekshitha-obulreddygari](https://linkedin.com/in/deekshitha-obulreddygari)  
📍  Phoenix, AZ

---

## 📄 License
This project is licensed under the **MIT License**. See `LICENSE` for details.
