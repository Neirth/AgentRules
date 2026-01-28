# Machine Learning Rules

When developing ML/DL models:

## Framework Requirements

- Use **PyTorch** or **Scikit-Learn** exclusively
- **ONNX export mandatory** for production deployment
- Validate ONNX outputs match original model

## Data Handling

- Always split: Train / Validation / Test
- Use stratified splits for classification
- Never leak test data into training
- Preprocess: fit on train, transform on all

## Model Development (Karpathy's Recipe)

1. **Understand data first** - Visualize, explore, find patterns
2. **Establish baselines** - Simple models before complex
3. **Overfit one batch** - Verify training loop works
4. **Regularize** - Close train/val gap
5. **Tune hyperparameters** - Random search → Grid search

## Training Best Practices

- Check loss on init (should match expected)
- Monitor gradients (not vanishing/exploding)
- Use learning rate schedulers
- Early stopping on validation loss

## Validation

- K-Fold cross-validation for small datasets
- Nested CV for hyperparameter selection
- Compare ONNX outputs with original (rtol=1e-5)

## Algorithm Selection

- Tabular data: Start with XGBoost/Random Forest
- Sequences: LSTM/GRU or Transformer
- Images: CNN architectures
- Always compare against simple baselines

**For detailed methodology:** Use `/machine-learning-engineering` skill
