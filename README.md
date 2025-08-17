# True Label Prediction from Noisy Data (IE506 – Programming Challenge)

##  Overview
This project was developed as part of the **IE506 Programming Challenge (2025)**.  
The task was to predict the **true class label (0–9)** for each test sample.  
The dataset included **150 features per sample** and two candidate labels (`label1`, `label2`), of which only **one is correct**.  
This setup introduced **label noise**, making the challenge harder.  
The evaluation metric was **Macro F1 Score**, ensuring balanced performance across all classes.

---

##  Approach

1. **Using Both Labels**  
   - Each sample was duplicated with both `label1` and `label2`.  
   - Increased dataset size and reduced the negative effect of noisy labels.  

2. **Model: Multi-Layer Perceptron (MLP)**  
   - 3 hidden layers (512, 512, 256 neurons).  
   - **ReLU** activation + **Dropout (0.25)**.  
   - Final layer with 10 outputs (classes 0–9).  

3. **Training Setup**  
   - Loss: CrossEntropyLoss with **class weights** (handling class imbalance).  
   - **Label smoothing (0.1)** → reduced overconfidence on noisy labels.  
   - **Weight decay (L2)** → avoided overfitting.  
   - **Cosine Annealing LR Scheduler** → adaptive learning rate scheduling.  
   - Validation split: 80% train / 20% validation.  
   - Saved the **best model checkpoint** based on validation Macro F1.  

---

##  Key Results
- Achieved **Macro F1 Score: 0.822** on the hidden test set.  
- Secured **12th rank** out of all participants in the IE506 Programming Challenge.  
 
---

##  Why This Worked
- **Both-label strategy** improved robustness against noisy data.  
- **MLP with dropout + label smoothing** handled overfitting and label uncertainty.  
- **Cosine annealing + weight decay** improved generalization.  
- Balanced approach → strong competition performance.  



