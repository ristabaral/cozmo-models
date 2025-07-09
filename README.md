# cozmo-models

This notebook demonstrates two language models designed to enhance robot-human interactions through emotion recognition and behavior generation. All models are trained using behavior-emotion data collected from the **Cozmo robot**. In addition to baseline models, the notebook introduces feedback-based enhancements that significantly improve the generative model’s emotional alignment and behavioral novelty—enabling more emotionally expressive and diverse robot behaviors.

## 📌 Overview

### 1. Emotion Model of Robot Observation (EMRO-cozmo)

This model classifies robot behaviors into one of six emotion categories based on observed behavioral patterns.
- **Base Architecture**: Fine-tuned RoBERTa  
- **Inputs**: A textual description of Cozmo robot behaviors
- **Output**: One of six grouped emotion labels

#### Emotion Classes:
| Class | Emotion Category                       |
|-------|----------------------------------------|
| 0     | Anger / Frustration                    |
| 1     | Confusion / Sorrow / Boredom           |
| 2     | Disgust / Surprise / Alarm / Fear      |
| 3     | Interest / Desire                      |
| 4     | Joy / Hope                             |
| 5     | Understanding / Gratitude / Relief     |


---
### 2. 🤖 Generate Robot Emotional Display (GRED-Cozmo)

This generative model produces robot behaviors conditioned on a given emotion label, ensuring behaviors are emotionally aligned and contextually appropriate.
- **Base Architecture**: Fine-tuned GPT-2 Medium  
- **Inputs**: Emotion Label  
- **Output**:  A textual description of Cozmo robot behaviors


---

### 3. Enhanced GRED Models with Feedback Integration
- **GRED with EMRO Feedback**:  
  EMRO loss is computed by comparing the emotion predicted from generated behaviors against input emotion labels. This loss is then backpropagated into the GRED model to enhance emotional accuracy.

- **GRED with Novelty Feedback**:  
  Incorporates novelty feedback by computing novelty loss based on cosine similarity between generated behaviors across the same emotion. This encourages diversity in the generated behaviors.

- **Combined GRED (EMRO + Novelty Feedback)**:  
  This final enhanced model integrates both EMRO and novelty losses, optimizing simultaneously for emotional accuracy and behavioral novelty. It shows substantial improvements in both aspects compared to the baseline GRED model.

---
## 📘 What's Included in the Notebook?

- ✅ **Data Preprocessing**  
  Cleaning, formatting, and tokenizing the emotion-behavior dataset collected from the Cozmo robot.

- ✅ **Model Training**
  - **EMRO**: A RoBERTa-based emotion classifier fine-tuned to predict one of six grouped emotions from behavior text.
  - **GRED**: A GPT-2-medium-based causal language model trained to generate robot behavior sequences conditioned on emotion labels.
  - **Feedback Models**: Enhanced GRED models with EMRO and/or novelty loss for improving emotional alignment and uniqueness.
    
- ✅ **Model Evaluation**
  - **EMRO**: Evaluated using accuracy and confusion matrix on test data.
  - **GRED**: Assessed based on the **novelty** of generated behaviors and their **emotional accuracy** (via EMRO predictions).
  - **emotional accuracy** (e.g., via EMRO predictions).

---
These models are specifically developed for the **Cozmo robot**, using its observed behaviors as training data for both emotion recognition and behavior generation tasks.

---

## 🔗 Hugging Face Model Cards

You can explore and use the finalized models here:

- **EMRO-Cozmo (Emotion Classification)**
  [bsu-slim/emro-cozmo on Hugging Face](https://huggingface.co/bsu-slim/emro-cozmo)  

- **GRED-Misty (Behavior Generation)**  
  [bsu-slim/gred-cozmo on Hugging Face](https://huggingface.co/bsu-slim/gred-cozmo)

Each model card includes sample usage code and downloadable model files.
