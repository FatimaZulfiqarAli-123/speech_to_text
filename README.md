# 🎙️ Text-to-Speech and Speech-to-Text Pipeline Using NLP and Whisper

## 📌 Project Overview
This project is an end-to-end Speech Processing system that combines **Text-to-Speech (TTS)** and **Speech-to-Text (STT)** using modern NLP and deep learning tools.

It generates speech audio from text using Google Text-to-Speech (gTTS), processes and analyzes the audio, and then transcribes it back into text using OpenAI Whisper. The system also evaluates transcription performance using Word Error Rate (WER) and Character Error Rate (CER).

---

## 🚀 Features

- 🔊 **Text-to-Speech (TTS)** using `gTTS`
- 🎧 **Audio playback** using `sounddevice`
- 🎵 Audio format conversion using `pydub`
- 🧹 Optional noise reduction using `noisereduce`
- 🧠 **Speech-to-Text (STT)** using OpenAI Whisper
- 📊 Audio visualization:
  - Waveform plots (`librosa`)
  - Mel spectrogram analysis
- 📉 Model evaluation using:
  - Word Error Rate (WER)
  - Character Error Rate (CER)
- ⏱️ Timestamped speech segmentation from Whisper

---

## 🧠 Tech Stack

- Python 3.x
- PyTorch
- OpenAI Whisper
- Librosa
- gTTS (Google Text-to-Speech)
- pydub
- sounddevice
- soundfile
- noisereduce
- matplotlib
- numpy
- jiwer
- imageio-ffmpeg

---

## 📂 Project Workflow

1. **Text Input**
   - Define NLP text script

2. **Text-to-Speech**
   - Convert text → MP3 using `gTTS`

3. **Audio Processing**
   - Convert MP3 → WAV using `pydub`
   - Load and visualize audio using `librosa`

4. **Speech Playback**
   - Play audio using `sounddevice`

5. **Speech-to-Text**
   - Load Whisper model
   - Transcribe audio into text
   - Extract timestamps per segment

6. **Evaluation**
   - Compare generated text with reference text
   - Compute WER and CER using `jiwer`

7. **Visualization**
   - Waveform plot
   - Mel spectrogram
   - Energy distribution over time

---

## 📊 Evaluation Metrics

- **WER (Word Error Rate)** → measures word-level differences  
- **CER (Character Error Rate)** → measures character-level accuracy  

Lower values indicate better performance.

---

## ⚙️ Installation

```bash
pip install -r requirements.txt