---
name: machine-learning-engineering
description: Develop production-ready ML/DL models using PyTorch or Scikit-Learn with mandatory ONNX export, following best practices from Hinton, LeCun, Bengio, Andrew Ng, and Karpathy
user-invocable: true
---

# Machine Learning Engineering Rules

> *"The qualities that in my experience correlate most strongly to success in deep learning are patience and attention to detail."*
> — Andrej Karpathy, Former Director of AI at Tesla, Founding Member of OpenAI

## Purpose

These rules establish the methodology for developing robust, production-ready machine learning and deep learning models. Drawing from the foundational work of the "Godfathers of AI" (Geoffrey Hinton, Yann LeCun, Yoshua Bengio), Andrew Ng's Stanford courses, Andrej Karpathy's practical wisdom, and the best practices from Google, Meta, and Microsoft Research, this guide covers classical ML algorithms, deep learning architectures, and production deployment via ONNX.

**Framework Requirements:** All implementations must use **PyTorch** or **Scikit-Learn**, with mandatory **ONNX export** for production deployment.

---

## The Pioneers: Standing on Giants' Shoulders

### The Turing Award Winners (2018)

```
┌─────────────────────────────────────────────────────────────────┐
│              THE GODFATHERS OF DEEP LEARNING                    │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  GEOFFREY HINTON ───────────────────────────────────────────    │
│  │ "The Father of Deep Learning"                                │
│  │ • Backpropagation algorithm                                  │
│  │ • Boltzmann machines                                         │
│  │ • Nobel Prize in Physics 2024                                │
│  │ • Key insight: Deep networks learn hierarchical features     │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  YANN LECUN ────────────────────────────────────────────────    │
│  │ "Convolutional Neural Networks Pioneer"                      │
│  │ • LeNet architecture (1989)                                  │
│  │ • Chief AI Scientist at Meta                                 │
│  │ • Key insight: Spatial hierarchies in visual data            │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  YOSHUA BENGIO ─────────────────────────────────────────────    │
│  │ "Most-cited computer scientist globally"                     │
│  │ • Sequence-to-sequence learning                              │
│  │ • Attention mechanisms foundations                           │
│  │ • First AI researcher with 1M+ citations                     │
│  │ • Key insight: Representation learning                       │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  Recognition: 2018 ACM Turing Award                             │
│  "For conceptual and engineering breakthroughs that have        │
│   made deep neural networks a critical component of computing"  │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Modern Practitioners

**Andrew Ng (Stanford CS229):** Created the world's most popular machine learning course with 4.8M+ learners. His methodical approach to ML fundamentals is the gold standard.

**Andrej Karpathy:** Architect of Stanford's CS231n, his "Recipe for Training Neural Networks" is essential reading for avoiding common pitfalls.

---

## Classical Machine Learning Algorithms

### The Algorithm Landscape

```
┌─────────────────────────────────────────────────────────────────┐
│              ML ALGORITHM TAXONOMY                              │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  SUPERVISED LEARNING                                            │
│  ├── Classification                                             │
│  │   ├── Logistic Regression (baseline)                         │
│  │   ├── Decision Trees (interpretable)                         │
│  │   ├── Random Forest (robust)                                 │
│  │   ├── XGBoost/LightGBM (competition winner)                  │
│  │   └── Support Vector Machines (margin-based)                 │
│  │                                                              │
│  └── Regression                                                 │
│      ├── Linear Regression (baseline)                           │
│      ├── Ridge/Lasso (regularized)                              │
│      ├── Elastic Net (combined regularization)                  │
│      └── Gradient Boosting Regressors                           │
│                                                                 │
│  UNSUPERVISED LEARNING                                          │
│  ├── Clustering                                                 │
│  │   ├── K-Means (centroid-based)                               │
│  │   ├── DBSCAN (density-based)                                 │
│  │   └── Hierarchical (agglomerative)                           │
│  │                                                              │
│  └── Dimensionality Reduction                                   │
│      ├── PCA (linear)                                           │
│      ├── t-SNE (visualization)                                  │
│      └── UMAP (topology-preserving)                             │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Ensemble Methods: Leo Breiman's Legacy

Leo Breiman's work on ensemble methods revolutionized machine learning:

```
┌─────────────────────────────────────────────────────────────────┐
│              ENSEMBLE METHODS                                   │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  BAGGING (Bootstrap Aggregating) ───────────────────────────    │
│  │ • Train models on random subsets (with replacement)          │
│  │ • Aggregate predictions (voting/averaging)                   │
│  │ • Reduces variance, prevents overfitting                     │
│  │ • Example: Random Forest                                     │
│  │                                                              │
│  │ ┌─────┐ ┌─────┐ ┌─────┐                                      │
│  │ │Tree1│ │Tree2│ │Tree3│ ... (parallel training)              │
│  │ └──┬──┘ └──┬──┘ └──┬──┘                                      │
│  │    └───────┼───────┘                                         │
│  │            ▼                                                 │
│  │      [Aggregation]                                           │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  BOOSTING (Sequential Learning) ────────────────────────────    │
│  │ • Train models sequentially                                  │
│  │ • Each model corrects predecessor's errors                   │
│  │ • Reduces bias, increases accuracy                           │
│  │ • Examples: XGBoost, LightGBM, CatBoost                      │
│  │                                                              │
│  │ ┌─────┐    ┌─────┐    ┌─────┐                                │
│  │ │Tree1│───▶│Tree2│───▶│Tree3│ ... (sequential)               │
│  │ └─────┘    └─────┘    └─────┘                                │
│  │ (errors)   (errors)   (final)                                │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Random Forest (Breiman, 2001)

```
Key Characteristics:
├── Ensemble of decision trees with feature randomness
├── Each tree trained on bootstrap sample
├── Random subset of features at each split
├── Final prediction: majority vote (classification) / average (regression)
│
Hyperparameters (Scikit-Learn):
├── n_estimators: Number of trees (100-1000)
├── max_depth: Maximum tree depth (None for unlimited)
├── min_samples_split: Minimum samples to split node
├── max_features: Features to consider at each split
│   ├── 'sqrt' for classification
│   └── 'log2' or n_features/3 for regression
│
Strengths:
├── Robust to overfitting
├── Handles missing values
├── Feature importance built-in
└── Parallelizable training
```

### XGBoost (Chen & Guestrin, 2016)

```
Key Characteristics:
├── Extreme Gradient Boosting
├── Regularized objective (L1 + L2)
├── Sparse-aware algorithm
├── Parallel tree construction
│
Hyperparameters:
├── n_estimators: Number of boosting rounds (100-1000)
├── learning_rate (eta): Step size shrinkage (0.01-0.3)
├── max_depth: Maximum tree depth (3-10)
├── subsample: Row sampling ratio (0.5-1.0)
├── colsample_bytree: Column sampling ratio (0.5-1.0)
├── reg_alpha (L1): Lasso regularization
└── reg_lambda (L2): Ridge regularization

Competition Dominance:
"XGBoost has been the winningest method in Kaggle competitions
 for structured/tabular data."
```

---

## Deep Learning Architectures

### Neural Network Fundamentals

```
┌─────────────────────────────────────────────────────────────────┐
│              NEURAL NETWORK BUILDING BLOCKS                     │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  LAYERS (PyTorch nn.Module) ────────────────────────────────    │
│  │                                                              │
│  │ Linear/Dense:     nn.Linear(in_features, out_features)       │
│  │ Convolution 1D:   nn.Conv1d(in_ch, out_ch, kernel_size)      │
│  │ Convolution 2D:   nn.Conv2d(in_ch, out_ch, kernel_size)      │
│  │ Recurrent:        nn.RNN, nn.LSTM, nn.GRU                    │
│  │ Transformer:      nn.Transformer, nn.MultiheadAttention      │
│  │ Normalization:    nn.BatchNorm2d, nn.LayerNorm               │
│  │ Regularization:   nn.Dropout(p)                              │
│  │ Pooling:          nn.MaxPool2d, nn.AvgPool2d                 │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  ACTIVATIONS ───────────────────────────────────────────────    │
│  │                                                              │
│  │ ReLU:      f(x) = max(0, x)           [Default choice]       │
│  │ LeakyReLU: f(x) = max(αx, x)          [Prevents dead neurons]│
│  │ GELU:      f(x) = x·Φ(x)              [Transformers default] │
│  │ Sigmoid:   f(x) = 1/(1+e^-x)          [Binary output]        │
│  │ Softmax:   f(x)_i = e^xi / Σe^xj      [Multi-class output]   │
│  │ Tanh:      f(x) = (e^x-e^-x)/(e^x+e^-x) [Range: -1 to 1]     │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  LOSS FUNCTIONS ────────────────────────────────────────────    │
│  │                                                              │
│  │ Classification:                                              │
│  │ ├── nn.CrossEntropyLoss()      [Multi-class]                 │
│  │ ├── nn.BCEWithLogitsLoss()     [Binary]                      │
│  │ └── nn.NLLLoss()               [With log-softmax]            │
│  │                                                              │
│  │ Regression:                                                  │
│  │ ├── nn.MSELoss()               [L2 loss]                     │
│  │ ├── nn.L1Loss()                [L1 loss, robust]             │
│  │ └── nn.SmoothL1Loss()          [Huber loss]                  │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  OPTIMIZERS ────────────────────────────────────────────────    │
│  │                                                              │
│  │ SGD:      Basic gradient descent with momentum               │
│  │ Adam:     Adaptive learning rates [Default choice]           │
│  │ AdamW:    Adam with decoupled weight decay                   │
│  │ RMSprop:  Adaptive learning rate                             │
│  │                                                              │
│  │ Learning Rate Schedulers:                                    │
│  │ ├── StepLR: Decay by gamma every step_size epochs            │
│  │ ├── CosineAnnealingLR: Cosine decay                          │
│  │ ├── ReduceLROnPlateau: Reduce when metric plateaus           │
│  │ └── OneCycleLR: Super-convergence                            │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Convolutional Neural Networks (CNNs)

Pioneered by Yann LeCun for image processing:

```
┌─────────────────────────────────────────────────────────────────┐
│              CNN ARCHITECTURE                                   │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  Input Image                                                    │
│       │                                                         │
│       ▼                                                         │
│  ┌─────────────────────────────────────────────────────────┐    │
│  │  CONVOLUTIONAL BLOCK (repeat N times)                   │    │
│  │  ┌─────────┐   ┌──────────┐   ┌──────────┐   ┌───────┐  │    │
│  │  │ Conv2d  │──▶│BatchNorm │──▶│   ReLU   │──▶│MaxPool│  │    │
│  │  └─────────┘   └──────────┘   └──────────┘   └───────┘  │    │
│  └─────────────────────────────────────────────────────────┘    │
│       │                                                         │
│       ▼                                                         │
│  ┌─────────────────────────────────────────────────────────┐    │
│  │  CLASSIFIER HEAD                                        │    │
│  │  ┌─────────┐   ┌─────────┐   ┌─────────┐   ┌─────────┐  │    │
│  │  │ Flatten │──▶│ Linear  │──▶│ Dropout │──▶│ Linear  │  │    │
│  │  └─────────┘   └─────────┘   └─────────┘   └─────────┘  │    │
│  └─────────────────────────────────────────────────────────┘    │
│       │                                                         │
│       ▼                                                         │
│  Output (logits)                                                │
│                                                                 │
│  Key Concepts:                                                  │
│  • Kernel/Filter: Learnable feature detector                    │
│  • Stride: Step size of convolution                             │
│  • Padding: Border handling (same/valid)                        │
│  • Receptive Field: Input region affecting one output           │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Recurrent Neural Networks (RNNs, LSTM, GRU)

For sequential data processing:

```
┌─────────────────────────────────────────────────────────────────┐
│              SEQUENCE MODELS                                    │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  VANILLA RNN ───────────────────────────────────────────────    │
│  │ h_t = tanh(W_hh · h_{t-1} + W_xh · x_t + b)                  │
│  │                                                              │
│  │ Problem: Vanishing gradients for long sequences              │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  LSTM (Hochreiter & Schmidhuber, 1997) ─────────────────────    │
│  │ "Capable of learning long-term dependencies"                 │
│  │                                                              │
│  │ Gates:                                                       │
│  │ ├── Forget gate:  f_t = σ(W_f · [h_{t-1}, x_t] + b_f)        │
│  │ ├── Input gate:   i_t = σ(W_i · [h_{t-1}, x_t] + b_i)        │
│  │ ├── Output gate:  o_t = σ(W_o · [h_{t-1}, x_t] + b_o)        │
│  │ │                                                            │
│  │ Cell state: C_t = f_t ⊙ C_{t-1} + i_t ⊙ tanh(...)           │
│  │ Hidden:     h_t = o_t ⊙ tanh(C_t)                            │
│  │                                                              │
│  │ "Cell state works like a conveyor belt carrying              │
│  │  relevant information through the sequence"                  │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  GRU (Cho et al., 2014) ────────────────────────────────────    │
│  │ Simplified LSTM: combines forget + input gates               │
│  │                                                              │
│  │ Gates:                                                       │
│  │ ├── Reset gate:  r_t = σ(W_r · [h_{t-1}, x_t])               │
│  │ └── Update gate: z_t = σ(W_z · [h_{t-1}, x_t])               │
│  │                                                              │
│  │ "Comparable performance to LSTM with faster computation"     │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  PyTorch Usage:                                                 │
│  │ lstm = nn.LSTM(input_size, hidden_size, num_layers,          │
│  │                batch_first=True, bidirectional=True)         │
│  │ gru = nn.GRU(input_size, hidden_size, num_layers,            │
│  │              batch_first=True)                               │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Transformer Architecture (Vaswani et al., 2017)

"Attention Is All You Need" - The architecture behind GPT, BERT, and modern AI:

```
┌─────────────────────────────────────────────────────────────────┐
│              TRANSFORMER ARCHITECTURE                           │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  SELF-ATTENTION MECHANISM ──────────────────────────────────    │
│  │                                                              │
│  │ Attention(Q, K, V) = softmax(QK^T / √d_k) · V                │
│  │                                                              │
│  │ Where:                                                       │
│  │ ├── Q (Query):  What am I looking for?                       │
│  │ ├── K (Key):    What do I contain?                           │
│  │ └── V (Value):  What do I output?                            │
│  │                                                              │
│  │ Multi-Head Attention:                                        │
│  │ "Allows model to attend to information from different        │
│  │  representation subspaces at different positions"            │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  ENCODER BLOCK ─────────────────────────────────────────────    │
│  │                                                              │
│  │  Input ──┬──▶ Multi-Head ──▶ Add & ──▶ Feed ──▶ Add & ──▶    │
│  │          │    Attention      Norm     Forward    Norm        │
│  │          │         ▲                     ▲                   │
│  │          └─────────┴─────────────────────┘ (residuals)       │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  DECODER BLOCK ─────────────────────────────────────────────    │
│  │                                                              │
│  │  Same as encoder, plus:                                      │
│  │  ├── Masked self-attention (causal: can't see future)        │
│  │  └── Cross-attention to encoder output                       │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  POSITIONAL ENCODING ───────────────────────────────────────    │
│  │                                                              │
│  │ PE(pos, 2i) = sin(pos / 10000^(2i/d_model))                  │
│  │ PE(pos, 2i+1) = cos(pos / 10000^(2i/d_model))                │
│  │                                                              │
│  │ "Since transformers have no recurrence, positional           │
│  │  information must be injected explicitly"                    │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  PyTorch:                                                       │
│  │ transformer = nn.Transformer(                                │
│  │     d_model=512,      # Embedding dimension                  │
│  │     nhead=8,          # Number of attention heads            │
│  │     num_encoder_layers=6,                                    │
│  │     num_decoder_layers=6,                                    │
│  │     dim_feedforward=2048,                                    │
│  │     dropout=0.1                                              │
│  │ )                                                            │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Karpathy's Recipe for Training Neural Networks

Andrej Karpathy's methodical approach to avoid common pitfalls:

```
┌─────────────────────────────────────────────────────────────────┐
│              THE RECIPE (Karpathy, 2019)                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  STEP 1: BECOME ONE WITH THE DATA ──────────────────────────    │
│  │ • Visualize the data extensively                             │
│  │ • Understand the distributions                               │
│  │ • Look for patterns, imbalances, outliers                    │
│  │ • "Spend quality time with your data"                        │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  STEP 2: SET UP END-TO-END TRAINING + EVALUATION ───────────    │
│  │ • Establish baselines (random, simple models)                │
│  │ • Set up proper train/val/test splits                        │
│  │ • Implement metrics that matter                              │
│  │ • Create visualization of predictions                        │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  STEP 3: OVERFIT ───────────────────────────────────────────    │
│  │ • Start with a small subset                                  │
│  │ • "If you can't overfit a single batch, something is wrong"  │
│  │ • Verify loss decreases to near-zero                         │
│  │ • This validates your training loop                          │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  STEP 4: REGULARIZE ────────────────────────────────────────    │
│  │ • Add data augmentation                                      │
│  │ • Add dropout                                                │
│  │ • Add weight decay                                           │
│  │ • Reduce model size if needed                                │
│  │ • Goal: close gap between train and val performance          │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  STEP 5: TUNE ──────────────────────────────────────────────    │
│  │ • Random search > grid search                                │
│  │ • Learning rate is the most important hyperparameter         │
│  │ • Use learning rate finder                                   │
│  │ • Tune batch size (larger = more stable gradients)           │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  STEP 6: SQUEEZE OUT THE JUICE ─────────────────────────────    │
│  │ • Ensemble multiple models                                   │
│  │ • Use learning rate schedules                                │
│  │ • Try different architectures                                │
│  │ • Knowledge distillation                                     │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  DEBUGGING CHECKLIST:                                           │
│  [ ] Loss on init matches expected (e.g., -ln(1/C) for C classes)│
│  [ ] Overfit on one batch successfully                          │
│  [ ] Gradients are flowing (not vanishing/exploding)            │
│  [ ] Learning rate is in reasonable range                       │
│  [ ] Batch normalization statistics are updating                │
│  [ ] No data leakage between train/val/test                     │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Hyperparameter Tuning & Validation

### Cross-Validation (Andrew Ng's Approach)

```
┌─────────────────────────────────────────────────────────────────┐
│              VALIDATION STRATEGIES                              │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  TRAIN/VAL/TEST SPLIT ──────────────────────────────────────    │
│  │                                                              │
│  │ ┌──────────────────────────────────────────────────────┐     │
│  │ │     TRAINING (60-80%)     │ VAL (10-20%) │TEST (10-20%)│   │
│  │ └──────────────────────────────────────────────────────┘     │
│  │                                                              │
│  │ • Training: Fit model parameters                             │
│  │ • Validation: Tune hyperparameters                           │
│  │ • Test: Final unbiased evaluation (touch ONCE)               │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  K-FOLD CROSS-VALIDATION ───────────────────────────────────    │
│  │                                                              │
│  │ Fold 1: [VAL][ TRAIN ][ TRAIN ][ TRAIN ][ TRAIN ]            │
│  │ Fold 2: [ TRAIN ][VAL][ TRAIN ][ TRAIN ][ TRAIN ]            │
│  │ Fold 3: [ TRAIN ][ TRAIN ][VAL][ TRAIN ][ TRAIN ]            │
│  │ Fold 4: [ TRAIN ][ TRAIN ][ TRAIN ][VAL][ TRAIN ]            │
│  │ Fold 5: [ TRAIN ][ TRAIN ][ TRAIN ][ TRAIN ][VAL]            │
│  │                                                              │
│  │ Final score = mean(fold_scores)                              │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  NESTED CROSS-VALIDATION ───────────────────────────────────    │
│  │ "The gold standard for model evaluation"                     │
│  │                                                              │
│  │ Outer loop: Evaluate generalization                          │
│  │   └── Inner loop: Tune hyperparameters                       │
│  │                                                              │
│  │ Prevents optimistic bias from hyperparameter tuning          │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  CRITICAL WARNING (Scikit-learn docs):                          │
│  "Testing model performance on the test set instead of          │
│   cross-validation is considered cheating because you 'leak'    │
│   knowledge of the test set to the model."                      │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Scikit-Learn Hyperparameter Search

```python
# Recommended approach: RandomizedSearchCV first, then GridSearchCV

# Step 1: Broad random search
from sklearn.model_selection import RandomizedSearchCV
from scipy.stats import uniform, randint

param_distributions = {
    'n_estimators': randint(100, 1000),
    'max_depth': randint(3, 15),
    'learning_rate': uniform(0.01, 0.29),
    'subsample': uniform(0.5, 0.5),
}

random_search = RandomizedSearchCV(
    estimator=model,
    param_distributions=param_distributions,
    n_iter=100,
    cv=5,
    scoring='accuracy',
    random_state=42,
    n_jobs=-1
)

# Step 2: Narrow grid search around best parameters
from sklearn.model_selection import GridSearchCV

param_grid = {
    'n_estimators': [best - 50, best, best + 50],
    'max_depth': [best - 1, best, best + 1],
    # ... narrow ranges around RandomizedSearchCV results
}
```

---

## ONNX: Production Deployment

### Why ONNX?

```
┌─────────────────────────────────────────────────────────────────┐
│              ONNX ECOSYSTEM                                     │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  "ONNX is an open standard format for machine learning models   │
│   that enables interoperability—train in one framework and      │
│   run on any platform or hardware."                             │
│                                                                 │
│  TRAINING FRAMEWORKS          DEPLOYMENT TARGETS                │
│  ┌─────────────────┐          ┌─────────────────┐               │
│  │ PyTorch         │          │ ONNX Runtime    │               │
│  │ Scikit-Learn    │────────▶ │ TensorRT        │               │
│  │ TensorFlow      │   ONNX   │ OpenVINO        │               │
│  │ XGBoost         │          │ CoreML          │               │
│  └─────────────────┘          │ Web Browsers    │               │
│                               │ Edge Devices    │               │
│                               └─────────────────┘               │
│                                                                 │
│  BENEFITS:                                                      │
│  • Framework independence                                       │
│  • Optimized inference (often 2-5x faster)                      │
│  • Smaller deployment footprint                                 │
│  • Hardware acceleration (CPU, GPU, NPU)                        │
│  • Cross-platform compatibility                                 │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### PyTorch to ONNX Export

```python
import torch
import torch.onnx

# Define your model
model = MyModel()
model.eval()

# Create dummy input matching your model's expected input
dummy_input = torch.randn(1, 3, 224, 224)  # Example: batch, channels, H, W

# Export to ONNX
torch.onnx.export(
    model,
    dummy_input,
    "model.onnx",
    export_params=True,          # Store trained weights
    opset_version=17,            # ONNX version (use recent)
    do_constant_folding=True,    # Optimize constants
    input_names=['input'],       # Input tensor names
    output_names=['output'],     # Output tensor names
    dynamic_axes={               # Variable batch size
        'input': {0: 'batch_size'},
        'output': {0: 'batch_size'}
    }
)

# Verify the exported model
import onnx
onnx_model = onnx.load("model.onnx")
onnx.checker.check_model(onnx_model)
```

### Scikit-Learn to ONNX Export

```python
from skl2onnx import convert_sklearn
from skl2onnx.common.data_types import FloatTensorType

# Define input type
initial_type = [('float_input', FloatTensorType([None, n_features]))]

# Convert model
onnx_model = convert_sklearn(
    sklearn_model,
    initial_types=initial_type,
    target_opset=17
)

# Save
with open("model.onnx", "wb") as f:
    f.write(onnx_model.SerializeToString())
```

### ONNX Runtime Inference

```python
import onnxruntime as ort
import numpy as np

# Load model
session = ort.InferenceSession("model.onnx")

# Get input/output names
input_name = session.get_inputs()[0].name
output_name = session.get_outputs()[0].name

# Run inference
result = session.run(
    [output_name],
    {input_name: input_data.astype(np.float32)}
)[0]

# ONNX Runtime is typically 2-5x faster than native inference
```

### ONNX Export Checklist

```
┌─────────────────────────────────────────────────────────────────┐
│              ONNX EXPORT CHECKLIST                              │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  BEFORE EXPORT:                                                 │
│  [ ] Model is in eval() mode                                    │
│  [ ] All custom operations are ONNX-compatible                  │
│  [ ] Input shapes are known or dynamic axes defined             │
│  [ ] No Python control flow in forward pass                     │
│                                                                 │
│  AFTER EXPORT:                                                  │
│  [ ] Run onnx.checker.check_model()                             │
│  [ ] Compare outputs: original vs ONNX (rtol=1e-5, atol=1e-5)   │
│  [ ] Test with ONNX Runtime                                     │
│  [ ] Verify on target deployment platform                       │
│                                                                 │
│  VALIDATION (Critical):                                         │
│  "Always compare the approximate equality of the predictions    │
│   on a validation set prior to deploying the exported model."   │
│                              — Microsoft ONNX Documentation     │
│                                                                 │
│  LIMITATIONS:                                                   │
│  • Sparse data not fully supported                              │
│  • Some sklearn models (NMF, LDA) not convertible               │
│  • Custom layers may need manual ONNX operators                 │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Complete ML Pipeline Template

```python
"""
Production ML Pipeline Template
Framework: PyTorch + Scikit-Learn → ONNX
"""

# ============================================================
# 1. DATA PREPARATION
# ============================================================
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
import torch
from torch.utils.data import DataLoader, TensorDataset

# Split data (stratified for classification)
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, stratify=y, random_state=42
)
X_train, X_val, y_train, y_val = train_test_split(
    X_train, y_train, test_size=0.2, stratify=y_train, random_state=42
)

# Preprocessing pipeline
preprocessor = StandardScaler()
X_train_scaled = preprocessor.fit_transform(X_train)
X_val_scaled = preprocessor.transform(X_val)
X_test_scaled = preprocessor.transform(X_test)

# ============================================================
# 2. MODEL DEFINITION (PyTorch)
# ============================================================
class Model(torch.nn.Module):
    def __init__(self, input_dim, hidden_dim, output_dim):
        super().__init__()
        self.layers = torch.nn.Sequential(
            torch.nn.Linear(input_dim, hidden_dim),
            torch.nn.ReLU(),
            torch.nn.Dropout(0.3),
            torch.nn.Linear(hidden_dim, hidden_dim),
            torch.nn.ReLU(),
            torch.nn.Dropout(0.3),
            torch.nn.Linear(hidden_dim, output_dim)
        )

    def forward(self, x):
        return self.layers(x)

# ============================================================
# 3. TRAINING LOOP (Karpathy's Recipe)
# ============================================================
def train_model(model, train_loader, val_loader, epochs=100):
    optimizer = torch.optim.AdamW(model.parameters(), lr=1e-3)
    scheduler = torch.optim.lr_scheduler.ReduceLROnPlateau(
        optimizer, patience=5, factor=0.5
    )
    criterion = torch.nn.CrossEntropyLoss()

    best_val_loss = float('inf')

    for epoch in range(epochs):
        # Training
        model.train()
        train_loss = 0
        for X_batch, y_batch in train_loader:
            optimizer.zero_grad()
            outputs = model(X_batch)
            loss = criterion(outputs, y_batch)
            loss.backward()
            optimizer.step()
            train_loss += loss.item()

        # Validation
        model.eval()
        val_loss = 0
        with torch.no_grad():
            for X_batch, y_batch in val_loader:
                outputs = model(X_batch)
                val_loss += criterion(outputs, y_batch).item()

        scheduler.step(val_loss)

        # Early stopping
        if val_loss < best_val_loss:
            best_val_loss = val_loss
            torch.save(model.state_dict(), 'best_model.pt')

# ============================================================
# 4. EXPORT TO ONNX
# ============================================================
def export_to_onnx(model, input_dim, filename="model.onnx"):
    model.eval()
    dummy_input = torch.randn(1, input_dim)

    torch.onnx.export(
        model,
        dummy_input,
        filename,
        export_params=True,
        opset_version=17,
        input_names=['input'],
        output_names=['output'],
        dynamic_axes={
            'input': {0: 'batch_size'},
            'output': {0: 'batch_size'}
        }
    )

    # Verify
    import onnx
    onnx_model = onnx.load(filename)
    onnx.checker.check_model(onnx_model)
    print(f"Model exported to {filename}")

# ============================================================
# 5. INFERENCE WITH ONNX RUNTIME
# ============================================================
def onnx_inference(onnx_path, input_data):
    import onnxruntime as ort
    session = ort.InferenceSession(onnx_path)
    input_name = session.get_inputs()[0].name
    result = session.run(None, {input_name: input_data})[0]
    return result
```

---

## Checklist

### Before Training
- [ ] Data explored and understood
- [ ] Train/val/test splits created (no leakage)
- [ ] Baseline established
- [ ] Metrics defined
- [ ] Preprocessing pipeline ready

### During Training
- [ ] Loss on init is correct
- [ ] Can overfit one batch
- [ ] Gradients are healthy
- [ ] Learning rate appropriate
- [ ] Validation monitored

### Before Deployment
- [ ] Model exported to ONNX
- [ ] ONNX model validated
- [ ] Outputs match original model
- [ ] Preprocessing included/documented
- [ ] Performance benchmarked

---

## Remember

> *"A 'fast and furious' approach to training neural networks does not work and only leads to suffering."*
> — Andrej Karpathy

> *"The use of a validation set or cross-validation is vital when tuning parameters to avoid overfitting."*
> — Scikit-Learn Documentation

> *"Deep learning is not magic; it's engineering. Patience and attention to detail are your most powerful tools."*

**The Golden Rules:**
1. Understand your data before modeling
2. Start simple, add complexity incrementally
3. Validate rigorously, test once
4. Export to ONNX for production
5. Always verify exported model outputs
