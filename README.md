# WORKING WITH LLMs
---
## TOPICS:
1. Dialogue Summarization with **In-Context Learning**
2. FINE TUNING LLM for Dialogue Summarization
     1. Taking FLAN-T5 as base model .
     1. **Fully Fine Tuning** LLM and evaluating it.
     2. Using **Parameter Efficient Fine Tuning (PEFT)** and evaluating it.
     3. Comparing the results of **Original Model(FAN-T5)** , **Fully Fine Tuned Model**, and **PEFT Model**.


---
## DETAILS:
### 1. Dialogue-Summarization with *In-Context Learning*
- Utilized In-Context Learning to guide the model by embedding examples in the prompt.
  - Zero-shot inference: Summarization without examples; results lacked context and relevance.
  - One-shot learning: Added a single example, leading to clearer and more structured outputs.
  - Few-shot learning: Included multiple examples, yielding the best performance and accuracy.
  - Improved summarization without the need for explicit fine-tuning.


### 2. Fine-Tuning LLM for **Dialogue-Summarization**
- Took **FLAN-T5** as the base model and fully fine-tuned it over a **Dialogue-Summary** dataset from Hugging Face, which contained only 150 dialogue-summary pairs.
  - The number of parameters to be trained: **247,577,856**.
  - This fine-tuning requires significant computational resources, memory storage, and **multiple GPUs** due to the large number of parameters.
  
- Secondly, I used **PEFT (LoRA)** to fine-tune, which only involved **3,538,944** parameters to train—just **1.41%** of the parameters required for the full fine-tuning.
  - This approach is much more **efficient** and **computationally inexpensive**.
  - Can be executed on a **single GPU**, making it a more scalable solution.
- **Evaluating Original Model (FLAN-T5), Fully Fine-Tuned Model, and PEFT Model Quantitatively using ROUGE Scores**
  - The evaluation was performed using **ROUGE** scores to measure the performance of the models on the dialogue summarization task.
  - <img src="https://github.com/user-attachments/assets/a4d287ac-c41a-4a3c-a575-02f465c6b5bc" width="500" height="300" />

  - The results show that, by applying **LoRA** (a PEFT technique), our model performed better than the original **FLAN-T5** model, although it still lagged behind the fully fine-tuned model in certain areas. However, the performance gap is considered acceptable, given that the computational cost and resource requirements of LoRA are significantly lower than that of fully fine-tuning the model.


