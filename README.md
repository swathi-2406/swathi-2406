<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=26&duration=3000&pause=1000&color=7B6BBF&center=true&vline=true&repeat=true&width=650&lines=Hi%2C+I'm+Swathi+%F0%9F%91%8B;AI+Engineer+%7C+RAG+%7C+Multi-Agent+LLMs;Production-minded+AI+systems+that+hold+up" alt="Typing SVG" />

<br/>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/swathigudivada)
[![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:sgudiva3@asu.edu)
[![Portfolio](https://img.shields.io/badge/Portfolio-4C3D8F?style=for-the-badge&logo=vercel&logoColor=white)](https://swathi-2406.github.io)

</div>

---

## About me

I'm an AI engineer who spends a lot of time figuring out why models confidently say the wrong thing, and building systems to catch it before anyone else does.

My focus is reliability-focused AI engineering: RAG pipelines, multi-agent orchestration, hallucination detection, and multimodal systems. I care about the gap between "works in a notebook" and "works when it matters."

Currently at **RVCoLab, Arizona State University**, building multimodal emotion recognition systems and agentic voice pipelines.

M.S. Computer Science, ASU (GPA 3.89, graduating Dec 2025). Co-author of a granted patent for ML-based dermatology diagnosis (IND 102069).

---

## What I work with

**Gen AI and Agentic Systems**

![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![LlamaIndex](https://img.shields.io/badge/LlamaIndex-7B6BBF?style=flat-square&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat-square&logo=openai&logoColor=white)
![HuggingFace](https://img.shields.io/badge/HuggingFace-FFD21E?style=flat-square&logo=huggingface&logoColor=black)
![Stable Diffusion](https://img.shields.io/badge/Stable_Diffusion-FF6B35?style=flat-square&logoColor=white)

**ML and Computer Vision**

![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat-square&logo=tensorflow&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=flat-square&logo=opencv&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)

**Backend and Infrastructure**

![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonwebservices&logoColor=white)
![MLflow](https://img.shields.io/badge/MLflow-0194E2?style=flat-square&logo=mlflow&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)

---

## Flagship project

### [RAG Hallucination Firewall](https://github.com/swathi-2406/RAG-Hallucination-Firewall)

Most RAG systems have no idea when they're hallucinating. This one does.

A three-stage hallucination detection pipeline that validates LLM outputs against retrieved context before they reach users. The design challenge: each signal catches different failure modes. Entropy alone misses confident hallucinations. NLI alone is too slow for every query. The pipeline runs fast checks first and reserves the expensive check for flagged outputs.

**Architecture**

```
User Query
    |
    v
Retriever (FAISS)  <-- 198 research papers indexed
    |
    v
LLM Generation
    |
    v
Stage 1: Entropy check       <-- Is the model uncertain?
    |
    v
Stage 2: KL Divergence       <-- Is the output distributionally unusual?
    |
    v
Stage 3: NLI Verification    <-- Does the answer contradict the source docs?
    |
    v
Validated Response / Hallucination Flag
```

**Results**
- Retrieval latency: under 162ms across 198 documents
- Adversarial query coverage: reliable flagging across prompt injection and out-of-corpus queries
- Evaluation dashboard: tracks retrieval quality and model faithfulness per query

**Deployment:** Dockerized FastAPI endpoint with async inference support. Evaluation metrics logged per request.

`LangChain` `FAISS` `NLI` `FastAPI` `Docker` `Python`

---

## Other projects

### [NudgeOps](https://github.com/swathi-2406/NudgeOps)

Full-stack MLOps platform for personalized habit optimization using a contextual multi-armed bandit. The system learns which motivational strategy works for each user and adapts in real time without retraining.

**How it works**

```
User action logged
    |
    v
Feature store update (14 behavioral features, 30-day window)
    |
    v
Thompson Sampling: sample from Beta(alpha, beta) per arm
    |
    v
Highest sample wins -> intervention delivered
    |
    v
Feedback collected -> alpha/beta updated
    |
    v
A/B test evaluation (t-test + Cohen's d) -> policy versioning
```

**What's production-grade about it:** fairness constraints on intervention intensity, cold-start exploration strategy, shadow-mode policy testing before promotion, rate-limited deployment, scheduled retraining via Celery.

`Thompson Sampling` `FastAPI` `PostgreSQL` `Redis` `Celery` `React` `Netlify`

---

### [SpeechOps](https://github.com/swathi-2406/SpeechOps)

Systematic benchmark of five deep learning architectures for speech recognition on 100K+ audio samples. Best model: 92.1% accuracy at 12ms inference latency. Built MFCC preprocessing and augmentation pipelines specifically to generalize across noisy real-world environments, not just clean test sets.

`PyTorch` `MFCC` `Deep Learning` `MLflow`

---

### Dermatology Diagnosis (Patent IND 102069, granted Sept 2022)

MobileNetV2 trained on 12K dermoscopy images across 8 disease classes. 95% diagnostic accuracy. Used MC Dropout for uncertainty estimation so the model knows when to say "I'm not confident" rather than always returning a hard classification. Improved generalizability by 18% through targeted augmentation for skin tone and lighting variation.

`MobileNetV2` `MC Dropout` `Computer Vision` `TensorFlow`

---

## Currently researching

Multimodal fusion strategies for real-time avatar emotion adaptation using EEG, GSR, and facial embeddings. The hard part is fusing signals with different sampling rates and noise profiles without introducing latency that breaks the interaction loop.

Also: agentic ASR-to-LLM-to-TTS pipelines where the agent decides mid-conversation whether to retrieve, generate, or ask for clarification.

---

<div align="center">
<img src="https://github-readme-stats.vercel.app/api?username=swathi-2406&show_icons=true&theme=tokyonight&hide_border=true&title_color=7B6BBF&icon_color=7B6BBF" height="160"/>
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=swathi-2406&layout=compact&theme=tokyonight&hide_border=true&title_color=7B6BBF" height="160"/>
</div>

<div align="center">

[![LinkedIn](https://img.shields.io/badge/Let's_connect-Swathi_Gudivada-0A66C2?style=flat-square&logo=linkedin)](https://linkedin.com/in/swathigudivada)
&nbsp;
[![Email](https://img.shields.io/badge/Get_in_touch-sgudiva3@asu.edu-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:sgudiva3@asu.edu)

</div>
