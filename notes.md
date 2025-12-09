## 📚 Background Readings

**Read first!!**

### Speech / Audio Models
- Tacotron  
- DCTTS  
- AudioLM  
- AudioPaLM  
- Speech LM  
- Speech-T5  
- Wesper  

### Foundation Models
- GPT papers  
- LLaMA papers  

### ASR / Representation Learning
- Whisper  
- Wav2Vec 2.0   
- WavLM  
- Wav2Vec-BERT  

### Voice Conversion
- AutoVC   
- NoiseVC  

---

## 🧠 Small Summary

| Paper | Methodology | Training Objective | Architecture | Data Type | Advantages | Limitations & Future Work | Notes |
|------|------------|-------------------|-------------|-----------|------------|---------------------------|-------|
| **Wav2Vec 2.0** | Learning from unlabeled speech audio with fine-tuning on transcribed speech | Codebook diversity loss + contrastive loss | Conv feature encoder + quantization module + Transformer | Unlabeled audio (pretraining), labeled data (fine-tuning) | Works well in low-resource settings | Compared to LSTMs; future: seq2seq with word-piece vocab | - Uses convolutional layers as relative positional embeddings<br>- Fine-tuning via linear projection + CTC loss<br>- VQ not differentiable → Gumbel-Softmax approximation |
| **Whisper** | Multitask learning (ASR, language ID, translation, VAD, timestamps) | Seq2seq multitask objective | Encoder–Decoder | Weakly labeled audio | No dataset-specific fine-tuning needed | Biased towards English | - No text normalization<br>- No explicit regularization or augmentation due to dataset diversity |
| **AutoVC** | Autoencoder with carefully designed bottleneck for content–style disentanglement | Reconstruction loss | Speaker encoder + content encoder + decoder | Non-parallel, unlabeled speech | - No parallel data needed<br>- No transcriptions<br>- Zero-shot voice conversion | Pitch transfer imperfect | - Speaker encoder trained with GE2E loss<br>- Bottleneck forces style-independent content code |
| **NoiseVC** | Instance normalization + vector quantization + contrastive learning | Reconstruction + adversarial loss + VQ loss | Similar to AutoVC with dual mel-spectrogram inputs | Non-parallel, unlabeled speech | - Better style transfer via instance norm<br>- Improved content disentanglement | — | - Two mel-spectrograms (clean + Gaussian-noise augmented)<br>- Noise changes pitch while preserving content |

---

## 🔊 Audio & Speech Models (Unsorted / To Review)

- AudioLM  
- AudioPaLM  
- WaveNet (slow inference, autoregressive audio synthesis)  
- Tacotron  
- DCTTS  
- Speech LM  
- Speech-T5  
- Wesper  

---

## 🤖 Large Language Models

- GPT  
- GPT-2  
- GPT-3  
- GPT-4  
- LLaMA  
- LLaMA-2  
- LLaMA-3  

---

## ⭐ Important Topics

### Neural Audio Codecs

Neural audio codecs split audio into **discrete tokens**, making it easier to:
- compress audio
- model continuations
- reconstruct audio from a compressed representation  

This is more efficient than predicting raw audio samples directly (e.g. WaveNet).  
However, such models may also learn **non-linguistic artifacts** like breathing or mouth movements.

📖 **Nice blog post:**  
https://kyutai.org/next/codec-explainer

**Examples:**
- SoundStream  
- Opus  
- EVS  

---

### Residual Vector Quantization (RVQ)

📖 **Nice blog post:**  
https://drscotthawley.github.io/blog/posts/2023-06-12-RVQ.html

🔗 **Repository:**  
https://github.com/lucidrains/vector-quantize-pytorch
