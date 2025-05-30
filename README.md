# 🧠 Image Captioning with Fine-Tuned BLIP

This project focuses on fine-tuning the [BLIP](https://github.com/salesforce/BLIP) image captioning model using a custom dataset and evaluating its performance using semantic similarity metrics.

---

## 📦 1. Tech Stack

**Programming & Libraries**
- Python 3.10  
- Sentence-transformers: 2.2.2  
- Transformers: 4.30.2  
- Huggingface-hub: 0.14.1  
- Tokenizers: 0.13.3  
- NumPy: 1.24.4  
- Pandas: 1.5.3  
- SciPy: 1.10.1  
- Matplotlib: 3.7.1  
- TQDM: 4.65.0  

**Deep Learning Frameworks**
- TensorFlow: 2.11.0  
- Torch: 2.0.1+cu118  
- Torchvision: 0.15.2+cu118  
- Torchaudio: 2.0.2+cu118  
> Installed via: [PyTorch Official](https://download.pytorch.org/whl/torch_stable.html)

**Models**
- **Training**: `Salesforce/blip-image-captioning-base`  
- **Evaluation**: `thenlper/gte-small`  

**Platform**
- Local (RTX 4060 GPU)

---

## ✨ 2. Summary

A custom fine-tuned version of BLIP was trained to generate image captions using beam search. Evaluation was performed using the Fréchet GTE Distance (FGD), which compares sentence embeddings from the GTE-small model. The lower the FGD, the better the semantic match.

---

## 🔍 3. Approach

### 🧠 Model & Training
- Fine-tuned `Salesforce/blip-image-captioning-base` on image-caption pairs.
- Image preprocessing: resize, normalize; Caption preprocessing: tokenization.
- Hardware: RTX 4060 GPU
- Training time: ~45 minutes

### 💬 Inference & Generation
- Beam search decoding used for more fluent and accurate caption generation.

### 📐 Evaluation
- Used `thenlper/gte-small` to generate embeddings.
- Calculated Fréchet GTE Distance (FGD) between generated and reference captions.
- **Final FGD Score: `0.45`** (lower = better)

### ⏱️ Timing
- Training: ~45 min  
- Testing: ~30 min  
- Inference: ~10 min  

---

## 🖼️ 4. Sample Outputs

### ✅ Strong Predictions
**Image:** ![image](https://github.com/user-attachments/assets/e32664f6-17af-4d0a-9a89-4199567ca767) 
**Prediction:** *A blue speedboat glides over water, showcasing its distinctive design and distinctive branding.*  
**Comment:** Excellent recognition of object, color, and setting.

**Image:** ![image](https://github.com/user-attachments/assets/689625f0-b1c0-4740-bd6f-07d1c4cc0c37)

**Prediction:** *A military aircraft is parked on a runway, featuring a camouflage design and a distinctive tail design.*  
**Comment:** Accurate identification of aircraft and details.

---

### 👍 Acceptable Predictions
**Image:** ![image](https://github.com/user-attachments/assets/8f63fa36-67e6-45ca-ac68-51f383504097)
**Prediction:** *A bottle of rose wine from the domaine de beaune...*  
**Comment:** Generally accurate and contextually reasonable.

**Image:** ![image](https://github.com/user-attachments/assets/0c456692-d03c-449d-b521-86e4a302c8c7)
**Prediction:** *A pink and white bus is parked, with passengers visible...*  
**Comment:** Correctly identifies object and context.

**Image:** ![image](https://github.com/user-attachments/assets/eebe7a27-0b84-4833-9284-80e526311e45)

**Prediction:** *An open book displays a page titled "canyon the1," featuring a sunset background...*  
**Comment:** Impressive inference of "sunset" context.

---

### ❌ Poor / Failure Cases
**Image:** ![image](https://github.com/user-attachments/assets/04f1fabf-8b55-4fb2-a88f-c5c2ae08a69c)

**Prediction:** *A vintage box with a label reading "lovecheck"...*  
**Comment:** Misinterpreted symbolism and context.

**Image:** ![image](https://github.com/user-attachments/assets/570cb68b-8d8e-4935-89f1-101a59500977)

**Prediction:** *A table displays a sign for "shelgvive - a. e."...*  
**Comment:** Detected general layout but failed on text and meaning.

---

## 📊 5. Performance Discussion

- Final FGD Score: **0.45**
- Despite only one epoch of training, the model showed promising results.
- Improvements could include:
  - More epochs or larger datasets
  - Data augmentation: rotation, mirroring, cropping, color adjustments

### 🔁 Future Work

- Use more advanced models like:
  - **BLIP-2**: Enhanced vision-language alignment with LLMs (e.g., OPT, Flan-T5)
  - **GIT (Generative Image-to-Text)**: Decoder-only transformer architecture by Microsoft
- More robust and diverse training data
- Experiment with larger beam sizes and diverse decoding strategies

---

## 📬 Feedback

For suggestions, improvements, or questions, feel free to open an issue or contact me.
