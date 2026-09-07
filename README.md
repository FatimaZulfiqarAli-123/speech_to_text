# 🎙️ Text-to-Speech and Speech-to-Text Pipeline Using NLP and Whisper

> An end-to-end speech processing pipeline that combines **Text-to-Speech (TTS)**, **Speech-to-Text (STT)**, audio analysis, visualization, and transcription evaluation using modern NLP and deep learning technologies.

---

## 📌 Project Overview

This project implements an end-to-end **Speech Processing and NLP pipeline** that converts text into speech and subsequently transcribes the generated audio back into text.

The system uses **Google Text-to-Speech (gTTS)** for speech synthesis and **OpenAI Whisper** for automatic speech recognition. In addition to transcription, the pipeline performs audio preprocessing, waveform and spectrogram visualization, timestamp-based speech segmentation, and quantitative evaluation using **Word Error Rate (WER)** and **Character Error Rate (CER)**.

The project demonstrates how multiple speech and NLP technologies can be integrated into a single pipeline for analyzing the relationship between **text, speech, audio features, and automatic transcription**.

---

## 🎯 Objectives

* Convert text into natural speech using TTS.
* Process and analyze generated audio.
* Visualize audio waveforms and spectrograms.
* Convert speech back into text using Whisper.
* Extract timestamps from recognized speech segments.
* Evaluate transcription quality using WER and CER.
* Build a reproducible end-to-end speech processing workflow.

---

## 🚀 Key Features

* 🔊 **Text-to-Speech** using `gTTS`
* 🎧 **Audio Playback** using `sounddevice`
* 🎵 **Audio Format Conversion** using `pydub`
* 🧹 **Optional Noise Reduction** using `noisereduce`
* 🧠 **Automatic Speech Recognition** using OpenAI Whisper
* 📊 **Waveform Visualization** using `librosa`
* 🎼 **Mel Spectrogram Analysis**
* ⏱️ **Timestamped Speech Segmentation**
* 📉 **Word Error Rate (WER)**
* 🔤 **Character Error Rate (CER)**
* 📈 **Audio Energy Analysis**
* 🐍 Fully implemented in Python

---

## 🧠 System Architecture

```text
                 ┌──────────────────┐
                 │    Text Input    │
                 └────────┬─────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │       gTTS       │
                 │ Text → Speech    │
                 └────────┬─────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │   MP3 Audio      │
                 └────────┬─────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │ Audio Processing │
                 │ MP3 → WAV        │
                 └────────┬─────────┘
                          │
             ┌────────────┼────────────┐
             ▼            ▼            ▼
       ┌──────────┐ ┌───────────┐ ┌────────────┐
       │ Waveform │ │   Mel     │ │   Noise    │
       │ Analysis │ │Spectrogram│ │  Reduction │
       └────┬─────┘ └─────┬─────┘ └──────┬─────┘
            │             │              │
            └─────────────┼──────────────┘
                          ▼
                 ┌──────────────────┐
                 │     Whisper      │
                 │ Speech → Text    │
                 └────────┬─────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │   Transcription  │
                 └────────┬─────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │ Evaluation       │
                 │ WER + CER        │
                 └──────────────────┘
```

---

## 🔄 Project Workflow

### 1. Text Input

A predefined text script is provided as the input to the pipeline.

```text
Text Script
     ↓
Text-to-Speech
```

---

### 2. Text-to-Speech

The input text is converted into an audio file using **Google Text-to-Speech (gTTS)**.

```text
Text → gTTS → MP3
```

---

### 3. Audio Processing

The generated MP3 file is converted into WAV format using `pydub`.

The audio can then be loaded for further processing and analysis.

Processing may include:

* Audio format conversion
* Noise reduction
* Sampling and signal analysis
* Audio normalization

---

### 4. Audio Visualization

The audio signal is analyzed using `librosa`.

The system generates visual representations such as:

* Waveform
* Mel spectrogram
* Energy distribution

These visualizations help analyze the characteristics of the generated speech signal.

---

### 5. Speech-to-Text

The processed audio is passed to **OpenAI Whisper**.

Whisper performs automatic speech recognition and produces:

* Transcribed text
* Speech segments
* Start timestamps
* End timestamps

```text
Audio → Whisper → Transcription + Timestamps
```

---

### 6. Transcription Evaluation

The generated transcription is compared with the original reference text.

Two evaluation metrics are calculated:

```text
Reference Text
      │
      ├──────────────┐
      ▼              ▼
 Generated Text   Generated Text
      │              │
      ▼              ▼
     WER            CER
```

---

## 📊 Evaluation Metrics

### Word Error Rate (WER)

**WER** measures transcription errors at the word level.

It considers:

* Substitutions
* Insertions
* Deletions

A lower WER indicates better transcription performance.

```text
WER = (Substitutions + Insertions + Deletions) / Number of Reference Words
```

---

### Character Error Rate (CER)

**CER** evaluates transcription accuracy at the character level.

It is particularly useful when analyzing fine-grained differences between the reference and predicted text.

A lower CER indicates better character-level transcription accuracy.

---

## 🎧 Audio Analysis

The project performs multiple forms of audio analysis.

### Waveform Analysis

The waveform represents the amplitude of the audio signal over time.

```text
Amplitude
   │
   │      /\      /\
   │  /\ /  \    /  \
   │ /  V    \__/    \__
   └──────────────────────── Time
```

Waveforms provide an overview of speech activity and signal variation.

### Mel Spectrogram

The Mel spectrogram represents the distribution of audio frequencies over time using a perceptually motivated Mel scale.

It can help identify:

* Frequency patterns
* Speech activity
* Energy distribution
* Acoustic characteristics

---

## ⏱️ Whisper Timestamp Segmentation

Whisper provides timestamp information for recognized speech segments.

Example:

```text
[00:00.00 - 00:03.20] → First speech segment
[00:03.20 - 00:06.45] → Second speech segment
[00:06.45 - 00:09.80] → Third speech segment
```

This allows the system to associate recognized text with specific portions of the audio.

---

## 🛠️ Technology Stack

| Technology     | Purpose                        |
| -------------- | ------------------------------ |
| Python         | Core programming language      |
| PyTorch        | Deep learning framework        |
| OpenAI Whisper | Speech-to-text                 |
| gTTS           | Text-to-speech                 |
| Librosa        | Audio analysis                 |
| Pydub          | Audio conversion               |
| Sounddevice    | Audio playback                 |
| Soundfile      | Audio file handling            |
| Noisereduce    | Noise reduction                |
| Matplotlib     | Visualization                  |
| NumPy          | Numerical processing           |
| JiWER          | WER/CER evaluation             |
| Imageio-ffmpeg | Audio/video processing support |

---

## 📂 Project Structure

```text
Text-to-Speech-and-Speech-to-Text/
│
├── LLM.JPG
├── requirements.txt
├── README.md
│
└── [Python source files]
```

> Add your actual Python filenames above if they are available in the repository. Keeping the structure synchronized with the repository makes the README easier to navigate.
---

## ⚙️ Installation

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd <your-repository-folder>
```

### 2. Create a Virtual Environment

#### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

#### macOS / Linux

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## ▶️ Running the Project

Run the main Python script associated with the pipeline:

```bash
python <your_main_file>.py
```

The pipeline will then perform the following operations:

```text
Text Input
   ↓
gTTS
   ↓
Audio Generation
   ↓
Audio Processing
   ↓
Audio Visualization
   ↓
Whisper Transcription
   ↓
WER / CER Evaluation
```

---

## 🔬 Research Perspective

This project demonstrates an important connection between **Natural Language Processing, Speech Processing, and Deep Learning**.

The pipeline can be used to study:

* Automatic Speech Recognition
* Text-to-Speech systems
* Speech signal processing
* Audio feature extraction
* Transformer-based speech recognition
* Transcription quality
* Robustness of speech recognition systems
* Quantitative evaluation of NLP outputs

The combination of **Whisper + WER/CER** makes the project particularly useful as a foundation for experimentation and speech-processing research.

---

## 🌍 Potential Applications

This type of pipeline can be extended to applications such as:

* 🗣️ Voice assistants
* 🎓 Educational speech applications
* 📝 Automatic transcription systems
* 🎙️ Meeting and lecture transcription
* ♿ Accessibility technologies
* 📞 Voice-based customer service
* 🌐 Multilingual speech processing
* 🔎 Speech analytics
* 📚 Language-learning systems


---

## 📈 Possible Evaluation Extensions

For a more comprehensive research evaluation, the system could compare:

| Experiment               | Evaluation                |
| ------------------------ | ------------------------- |
| Clean audio              | WER + CER                 |
| Noisy audio              | WER + CER                 |
| Noise reduction          | WER improvement           |
| Different Whisper models | WER/CER comparison        |
| Different languages      | Language-wise performance |
| Different speech rates   | Transcription robustness  |

This would make the project suitable for a more systematic experimental study.

---

## 📄 License

This project is intended for **educational and research purposes**.

Add your preferred license file, such as `MIT License`, if the repository is intended for open-source distribution.

---

## 👩‍💻 Author

**Fatima Zulfiqar Ali**

Machine Learning • Artificial Intelligence • Natural Language Processing • Speech Processing

---

