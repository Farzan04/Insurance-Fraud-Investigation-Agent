# Insurance Fraud Investigation Agent

An AI-powered insurance fraud investigation system combining **multi-source machine learning** with a **LangGraph-based investigation agent**.

## Project Overview

The goal of this project is to assist insurance investigators in identifying potentially fraudulent claims by combining information from multiple sources rather than relying only on claim-level information.

The system integrates:

- Insurance claim information
- Policy information
- Payment and premium records
- Agent / ghost-broking records
- Relationship-based features
- Machine learning fraud prediction
- A LangGraph investigation agent for evidence-based analysis

The agent retrieves relevant evidence, obtains an ML-based fraud probability, and produces an investigation report with key evidence, mitigating evidence, recommendation, and final classification.

---

## System Architecture

The investigation workflow follows this general pipeline:

```text
Insurance Data Sources
        |
        v
Data Loading & Preprocessing
        |
        v
Feature Engineering
        |
        +----------------------+
        |                      |
        v                      v
Claim-only Model       Multi-source Model
                               |
                               v
                    Relationship Features
                               |
                               v
                    Fraud Prediction Tool
                               |
                               v
                    LangGraph Investigation Agent
                               |
                               v
                  Evidence-based Investigation
                               |
                               v
                    Final Fraud Assessment
Data Sources

The project uses four primary datasets:

claims.csv — insurance claim information
policies_free_insurance.csv — policy and policy-status information
payments_bad_payments.csv — payment and remittance information
ghost_broking.csv — agent, license, complaint, and premium-related information

The datasets are stored in the data/ directory.

Machine Learning Experiments

Three Random Forest approaches were evaluated:

Model	Accuracy	Fraud Precision	Fraud Recall	Fraud F1	ROC-AUC
Claim-only RF	0.830	0.8000	0.1081	0.1905	0.6783
Multi-source RF	0.805	0.4688	0.4054	0.4348	0.7096
Relationship-enhanced RF	0.790	0.4242	0.3784	0.4000	0.6801

The Multi-source Random Forest was selected for the final fraud prediction tool because it achieved the highest ROC-AUC among the three evaluated models.

Agent Development Sample

A separate 10-claim development sample was also evaluated:

Accuracy: 0.9000
Fraud Precision: 1.0000
Fraud Recall: 0.8000
Fraud F1: 0.8889
Context Tool Usage: 100%
Prediction Tool Usage: 100%

This development sample is separate from the main model comparison and should not be interpreted as the overall model performance.

Investigation Agent

The final LangGraph agent uses seven investigation tools:

claim_tool
policy_tool
payment_tool
agent_tool
evidence_tool
investigation_context_tool
fraud_prediction_tool

The agent combines structured evidence retrieval with the ML fraud prediction to produce an investigation-oriented assessment.

Example Investigation

For example, the system can investigate a claim such as:

CLM000001

The agent retrieves relevant claim, policy, payment, and agent information and then obtains the ML fraud probability.

The final response is structured into:

Key Evidence
Contradictory or Mitigating Evidence
Fraud Prediction
Recommendation
Final Classification

The system explicitly distinguishes the ML prediction from the overall investigation assessment.

Technologies Used
Python
Pandas
NumPy
Scikit-learn
Random Forest
LangChain
LangGraph
Jupyter Notebook
Machine Learning
Agentic AI / Tool Calling
Repository Structure
Insurance-Fraud-Investigation-Agent/
│
├── data/
│   ├── claims.csv
│   ├── ghost_broking.csv
│   ├── payments_bad_payments.csv
│   └── policies_free_insurance.csv
│
├── presentation/
│   └── Insurance_Fraud_Investigation_Agent_Presentation.pptx
│
├── results/
│   ├── f1_score_fraud.jpg
│   └── model_comparision_fraud.jpg
│
└── Insurance_Fraud_Agent.ipynb
How to Run
Clone or download this repository.
Open Insurance_Fraud_Agent.ipynb in Jupyter Notebook or JupyterLab.
Ensure the required Python libraries are installed.
Run the notebook cells in sequence.
Use the final LangGraph workflow to investigate an insurance claim.

The notebook contains the complete workflow from data processing and feature engineering to model evaluation, tool creation, and end-to-end agent investigation.

Project Outputs

The repository contains:

Complete Jupyter Notebook
Source datasets
Model comparison visualization
Fraud F1-score visualization
Project presentation
Limitations

The project is a prototype investigation-support system. The ML model should be treated as a decision-support component rather than a final determination of insurance fraud.

The final investigation should consider both model predictions and supporting evidence retrieved from the available data sources.

Author

Mohammad Farzan Nawaz Faruqui

Insurance Fraud Investigation Agent
IIT Bhilai — Data Science & Analytics
