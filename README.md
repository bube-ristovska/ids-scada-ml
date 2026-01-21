# SCADA Security: Detecting Attacks with Machine Learning

## Overview
This project for the subject "Network science" analyzes and compares traditional machine learning algorithms for detecting attacks in SCADA (Supervisory Control and Data Acquisition) systems. 
Additionally, analyzes Label Propagation and GNN for detecting the attacks.

### Algorithms Used
- **Decision Tree**  
- **Random Forest**  
- **Logistic Regression**  
- **Naïve Bayes**  
- **K-Nearest Neighbors (KNN)**  
- **Label Propagation (Semi-Supervised Graph-Based)**  
- **Graph Neural Network (GNN, Advanced Graph-Based Model)**  

### Dataset
- Based on the SCADA water tank system testbed from Teixeira et al.  
- Includes normal traffic and several reconnaissance attacks: Port Scan, Address Scan, Device Identification, and Exploit.  
- Total observations: 7,049,989 with ~6% attack traffic (class imbalance).  

## Label Propagation
Label Propagation is a **semi-supervised graph-based algorithm**. It uses a medium set of labeled data and spreads the labels through a graph built from the network traffic. In this project:  
- Only 20% of training data was labeled.  
- The algorithm propagates attack labels to unlabeled nodes based on network connections.  
- Results: **ACC 99.95%, FAR 0.03%, UND 0.31%**, showing high effectiveness even with limited labeled data.  

## Graph Neural Network (GNN)
GNNs learn **representations of SCADA devices and their interactions** to detect complex attack patterns:  
- Nodes represent network flows; edges represent similarity or interactions.  
- The model includes GAT (Graph Attention) layers that weight neighbor contributions differently.  
- Class weighting is applied to handle imbalanced data.  
- Results show **ACC 94.80%, Recall 16.62%, Precision 69.20%, FAR 0.45%, UND 83.38%**, demonstrating potential but requiring careful threshold tuning for deployment.  

## Key Results
| Model             | ACC (%) | FAR (%) | UND (%) |
|------------------|---------|---------|---------|
| Decision Tree     | 100     | 0       | 0       |
| Random Forest     | 100     | 0       | 0       |
| KNN               | 99.98   | 0.01    | 0.09    |
| Logistic Regression | 99.87 | 0.11    | 0.47    |
| Naïve Bayes       | 99.50   | 0.50    | 0.47    |
| Label Propagation | 99.95   | 0.03    | 0.31    |
| Advanced GNN      | 94.80   | 0.45    | 83.38   |

**Conclusion:**  
Decision Tree and Random Forest achieve near-perfect performance. Label Propagation is highly effective with limited labeled data. GNNs capture complex network interactions, but need careful tuning to balance detection and false alarms.  
