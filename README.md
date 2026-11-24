# BharatGPT  
**Chatbot-offline version – with audio, PDF, text & image input support!**  

##  What is BharatGPT?  
BharatGPT is an offline AI chatbot that works just like ChatGPT but runs **completely on your device**. No internet, no tracking – just fast, private AI magic.

##  Features  
-  **Chat offline** using local LLMs  
-  **Talk with voice** – mic input supported  
-  **Ask questions from PDFs**  
-  **Text-based Q&A**  
-  **Image understanding** (basic vision model support)  
-  100% Private – all data stays on your system  
-  Super fast responses (no server delay)

##  Tech Stack  
- Python  
- LLMs (LLaMA/Mistral or any GGUF format)  
- Whisper (for speech-to-text)  
- PyMuPDF / pdfplumber (for PDF reading)  
- OpenCV / transformers (for image input)  
- Streamlit (UI)

##  How to Use  
```bash
python -m venv .venv
# Windows PowerShell:
.\.venv\Scripts\Activate.ps1
# Windows Command Prompt:
# .venv\Scripts\activate.bat
python -m pip install -r requirements.txt
python -m streamlit run app.py
```

The project disables Streamlit's file watcher to avoid a PyTorch `torch.classes`
inspection error on Windows. Restart the app manually after changing code.

The model files are not included in the project. Put existing model files in this layout:

```text
models/
  llava/
    ggml-model-q4_k.gguf
    mmproj-model-f16.gguf
  bge-large-en-v1.5/
    model.safetensors
    config.json
    modules.json
    1_Pooling/config.json
    ...tokenizer files
  whisper-small/
    model.safetensors
    config.json
    preprocessor_config.json
    ...tokenizer files
```

The LLaVA GGUF is used for text and image questions; image understanding also requires
the matching `mmproj-model-f16.gguf` projector. The project pins `llama-cpp-python`
to version 0.2.90 for compatibility with this canonical LLaVA 1.5 pair. The text GGUF
and mmproj must belong to the same vision model. The BGE and Whisper folders should
contain their complete local model files. Model loading is local-only; the app does not
download models at runtime. Whisper-small was found in the Windows Hugging Face cache
for this setup and copied into `models/whisper-small`.

Chroma telemetry is disabled. Local chat avatars are built into the app and do not load
images from external websites.

##  Requirements  
```bash
python -m pip install -r requirements.txt
```

## Why BharatGPT?  
Because not everyone wants to send their data to the cloud. BharatGPT gives you full control over your AI chatbot – in your language, on your terms.

