# Machine Learning Based Detection of Encrypted Malware Traffic

## Project Overview

This project investigates machine learning-based detection of encrypted malware traffic using flow-level metadata instead of packet payloads. Since encryption protocols such as TLS and HTTPS hide packet contents, traditional payload-based intrusion detection methods become less effective. This project uses statistical network flow features from the CIC-IDS-2017 dataset to classify traffic as benign or malicious.

The project compares two models:

1. Random Forest Classifier  
2. Multi-Layer Perceptron Neural Network  

The study also applies feature selection and hyperparameter tuning to evaluate how model performance changes under optimized conditions.

---

## Dataset

**Dataset Used:**  
CIC-IDS-2017 Find the dataset at "https://www.unb.ca/cic/datasets/ids-2017.html"

**Source:**  
Canadian Institute for Cybersecurity

The dataset contains labeled benign and malicious network traffic with multiple attack categories, including:

- DDoS
- DoS
- PortScan
- Botnet
- FTP-Patator
- SSH-Patator
- Web Attacks
- Infiltration

Each flow contains network metadata features such as:

- Flow duration
- Packet length statistics
- Flow bytes per second
- Flow packets per second
- TCP flag counts
- Inter-arrival time statistics
- Header length features
- Subflow statistics

---

## Project Goals

- Detect malicious encrypted traffic without decrypting payloads.
- Compare Random Forest and Neural Network performance.
- Analyze performance across different attack types.
- Apply feature selection using Random Forest feature importance.
- Perform hyperparameter tuning.
- Evaluate models using accuracy, precision, recall, and F1-score.

---

## Project Structure

```txt
.
├── data/
│   └── raw/
│       └── 7 CIC-IDS-2017 dataset CSV files
├── Final.py
├── Random Forest.py
├── Neural Network.py
├── README.md
└── requirements.txt
```

---

## Methodology

1. Load CIC-IDS-2017 dataset files.
2. Clean column names and remove formatting inconsistencies.
3. Convert labels into binary classes:
   - Benign = 0
   - Attack = 1
4. Replace infinite values with NaN.
5. Apply median imputation for missing values.
6. Clip extreme numerical values.
7. Scale features for Neural Network training.
8. Split data into training and testing sets using a 70/30 ratio.
9. Train Random Forest classifier.
10. Train Multi-Layer Perceptron Neural Network.
11. Evaluate both models using:
    - Accuracy
    - Precision
    - Recall
    - F1-score
12. Apply feature selection using Random Forest importance.
13. Perform hyperparameter tuning.
14. Compare final model performance.

---

## Models Used

### Random Forest Classifier

- Baseline classical machine learning model
- Handles tabular data well
- Provides feature importance
- Robust to overfitting
- Efficient for intrusion detection

### Neural Network

- Multi-Layer Perceptron classifier
- Learns nonlinear feature relationships
- Requires feature scaling
- Useful for comparison against classical ML methods

---

## Evaluation Metrics

### Accuracy
Measures total correct predictions.

### Precision
Measures how many predicted attacks were actually attacks.

### Recall
Measures how many real attacks were correctly detected.

### F1-score
Balances precision and recall.

---

## Key Findings

- Both Random Forest and Neural Network achieved strong detection performance.
- Random Forest generally performed better on structured tabular flow data.
- DDoS and PortScan attacks were easier to detect due to clear traffic patterns.
- Infiltration and Web Attacks were harder to detect due to similarity with benign traffic.
- Feature selection improved Random Forest performance but reduced Neural Network performance.
- Random Forest was more computationally efficient and suitable for practical IDS deployment.

---

## How to Run

### 1. Clone the repository

```bash
git clone <repository-url>
```

### 2. Navigate to the project folder

```bash
cd encrypted-malware-traffic-detection
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Place dataset files

Add all 7 CIC-IDS-2017 CSV files inside:

```txt
data/raw/
```

### 5. Run the Python files

```bash
python "Random Forest.py"
python "Neural Network.py"
python "Final.py"
```

---

## Expected Outputs

The project generates:

- Model performance metrics
- Classification reports
- Feature importance rankings
- Model comparison tables
- Accuracy, precision, recall, and F1-score results
- Optional confusion matrices and plots

---

## Limitations

- CIC-IDS-2017 is a benchmark dataset and may not fully represent real-world encrypted traffic.
- Some attack classes are highly imbalanced.
- The current work focuses on binary classification.
- Real-time deployment was not implemented.
- Advanced deep learning models such as CNN, RNN, or LSTM were not included.

---

## Future Work

- Test on real-world encrypted TLS traffic.
- Extend the project to multi-class attack classification.
- Add advanced deep learning models such as CNN, RNN, LSTM, or Transformer models.
- Apply imbalance-handling methods such as SMOTE.
- Implement real-time intrusion detection.
- Add explainable AI methods for model interpretation.

---

## Author

**Juhi Sawant**
