# 🎙️ Automatic Speech Recognition using Whisper (Kaggle Project)

## 📌 Overview
This project implements an **Automatic Speech Recognition (ASR)** pipeline using the **Whisper-small model** from OpenAI via Hugging Face Transformers.

The system processes audio files, generates transcriptions, and prepares outputs for evaluation and deployment.

---

## 🚀 Features
- Load dataset from `.jsonl` files  
- Preprocess and validate audio file paths  
- Perform speech-to-text using Whisper-small  
- Batch inference with progress tracking  
- Save model locally for reuse  
- Upload model to Hugging Face Hub  

---

## 🧠 Tech Stack
- Python  
- PyTorch  
- Hugging Face Transformers  
- Librosa  
- Pandas  
- TQDM  

---

## 📂 Project Structure
.
├── train.jsonl  
├── val.jsonl  
├── audio/  
├── notebook.ipynb  
└── README.md  

---

## ⚙️ Installation
pip install transformers datasets torchaudio librosa soundfile jiwer tqdm

---

## 📊 Dataset Format
Each `.jsonl` file contains entries like:

{
  "audio_filepath": "audio/xyz.wav",
  "text": "ground truth transcription"
}

---

## 🔧 Workflow

### 1. Load Dataset
- Read `.jsonl` files into a Pandas DataFrame  
- Clean and validate entries  

### 2. Fix Audio Paths
- Ensure all file paths exist  
- Remove invalid/missing files  

### 3. Load Model
- Load **Whisper-small** using Transformers  
- Move model to GPU (if available)  

### 4. Transcription
- Convert audio to 16kHz  
- Generate text predictions  
- Decode output tokens  

### 5. Batch Processing
- Run inference on validation dataset  
- Store predictions in DataFrame  

---

## 🤖 Model
- Model: `openai/whisper-small`  
- Type: Encoder-Decoder Transformer  
- Use Case: Speech-to-Text  

---

## 💾 Model Saving
model.save_pretrained("whisper_small_saved")  
processor.save_pretrained("whisper_small_saved")  

---

## ☁️ Upload to Hugging Face
from huggingface_hub import HfApi  

api.upload_folder(  
    folder_path="whisper_small_saved",  
    repo_id="your-username/whisper-small",  
    repo_type="model"  
)  

---

## 📈 Output
Predicted transcriptions stored in:  
val_df["raw_hyp"]

---

## ⚠️ Notes
- Ensure all audio files exist before running inference  
- Use GPU (`cuda`) for faster processing  
- Kaggle `/working` directory is used for saving outputs  

---

## 🔮 Future Improvements
- Add WER (Word Error Rate) evaluation  
- Fine-tune model on custom dataset  
- Real-time speech recognition  
- Deploy as API (FastAPI / Flask)  

---

## 🙌 Acknowledgements
- OpenAI for Whisper  
- Hugging Face for Transformers  
