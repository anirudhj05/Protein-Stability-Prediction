# Protein Thermostability Prediction

## Project Overview
This project aims to predict the thermostability of proteins based on their amino acid sequences using a sophisticated ML model. Leveraging a bidirectional LSTM network enhanced with a custom attention mechanism, the model captures complex dependencies within protein sequences, providing an accurate estimation of protein behavior under various temperature conditions.

## Key Features
- **Bidirectional LSTM**: Captures patterns from both directions of the sequence data, enhancing the understanding of context in protein sequences.
- **Attention Mechanism**: Focuses on the most relevant parts of the protein sequence for predicting thermostability, improving model accuracy.
- **Model Generalization**: Evaluated using a split dataset to ensure robustness against overfitting and reliability on unseen data.

## Dataset
The dataset comprises mass spectrometry-based assay measurements designed to capture the effects of global and local sequence variations on protein thermostability:
- `train.csv`: Includes three columns — sequence ID, protein sequence, and thermostability measure.
- `test.csv`: Consists of two columns — sequence ID and protein sequence.

### Data Processing
1. **Sequence Encoding**: Amino acids are mapped to integers with a predefined dictionary for model ingestion.
2. **Padding and Truncation**: Sequences are padded or truncated to a consistent length of 1000 for uniform input size.
3. **Data Splitting**: Data is split into 80% for training and 20% for testing to validate model performance on unseen data.

## Model Architecture
1. **Input and Embedding Layer**: Transforms raw sequence data into dense vectors of size 128, facilitating effective learning of amino acid properties.
2. **Bidirectional LSTM Layers**: Includes two layers with 256 and 128 units, respectively, processing embedded sequences in both directions.
3. **Custom Attention Mechanism**: Weighs the importance of different sequence parts, enhancing focus on critical regions affecting thermostability.
4. **Batch Normalization and Dense Layers**: Normalize features and transform learned representations into predictions. Incorporates dropout for regularization.
5. **Output Layer**: Outputs the predicted thermostability measure.

## Requirements
- **TensorFlow 2.x**: For building and training the deep learning model.
- **Pandas**: For data manipulation.
- **NumPy**: For numerical operations.
- **Scikit-Learn**: For data preprocessing and performance metrics.
- **SciPy**: For Spearman correlation computation.

## Hyperparameters
- **Embedding Dimension**: 128
- **LSTM Units**: 256 (first layer), 128 (second layer)
- **Dropout Rate**: 0.5
- **Learning Rate**: Initially 0.001, with exponential decay
- **Epochs**: 100
- **Batch Size**: 16
- These parameters were optimized through extensive testing to balance between computational efficiency and model accuracy.

## Results
The model demonstrates strong predictive performance with a Spearman correlation coefficient of 0.60908 on the test set. This high level of accuracy indicates the model's effectiveness in capturing and understanding the nuanced influences of amino acid sequences on protein stability.
