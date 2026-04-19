# Predicting User Discomfort in Augmented Reality

This repository contains an **end-to-end machine learning and MLOps project** focused on predicting user discomfort in AR smart glasses using behavioral interaction data.

Completed as part of the **M.S. in Applied Data Science (ADS 508 – Data Science with Cloud Computing)** at the University of San Diego.

---

## Project Overview

REAL Glass is a consumer electronics company building AR smart glasses in a market projected to reach **$120B by 2034**.

A key barrier to adoption is **user discomfort** (e.g., nausea, eye strain, dizziness), with research suggesting:
- ~45% of users experience side effects  
- ~25% still experience symptoms after 1 hour

This project explores whether **machine learning can detect discomfort early**, enabling real-time interventions that improve user experience and extend wear time.

---

## Objective

Build a system that can:

- Predict discomfort risk from behavioral and motion signals  
- Detect early signs of discomfort before users disengage  
- Enable **real-time software interventions** (no hardware changes required)  
- Provide a scalable MLOps framework for deployment  

---

## Approach

- **Dataset:** Meta Nymeria (Project Aria), 1,100+ AR sessions  
- **Data Sources:** metadata, narration logs, derived motion + interaction features  
- **Feature Engineering:**  
  - Motion intensity  
  - Interaction efficiency  
  - Fragmentation (repetitive behavior)  
  - Text-based interaction complexity  
- **Target:** Proxy discomfort label derived from behavioral thresholds (no direct user feedback available)  

---

## Model & Performance

Multiple models were evaluated:

- Random Forest (baseline)  
- XGBoost  
- **LightGBM (selected)**  

**Final Results:**
- ROC-AUC ≈ 0.98  
- Strong separation between discomfort and non-discomfort sessions

Key insight:
> Discomfort is not driven by a single factor — it emerges from **patterns of inefficient, fragmented, and unstable interaction behavior**

---

## Production Design

The system is designed for **real-time AR environments**:

- Session data → transformed into lightweight feature set  
- Features → sent to SageMaker endpoint  
- Model → returns discomfort probability  
- System → triggers interventions (e.g., adjust depth, pacing, content placement)  

Also includes:
- Batch scoring for monitoring and retraining  
- Drift detection and performance tracking  
- Model versioning and rollback capability  

---

## Key Takeaways

- User discomfort is predictable from behavior  
- Behavioral features outperform simple duration metrics 
- Software can mitigate hardware limitations  
- Real-time intervention is feasible with lightweight features  

---

## Limitations

- Target variable is a **proxy**, not true user-reported discomfort  
- Model performance reflects learned behavioral thresholds, not validated outcomes  
- Future validation requires **real user feedback data**

---

## Future Enhancements

- Collect real user comfort feedback (ground truth labels)  
- Introduce **time-series / sequence modeling** (e.g., LSTM)  
- Optimize decision thresholds for real-world tradeoffs  
- Add interpretability (e.g., SHAP)  

---

## Why This Project Matters

This project reframes AR discomfort as a **software + data problem**, not just a hardware limitation.

Instead of reacting after users disengage, it enables:
> **predict → intervene → improve experience in real time**

This approach supports:
- Higher retention  
- Longer wear time  
- Scalable adoption of AR as a computing platform  

---

## Authors

- Bart Sosa-Teeuwen  
- Kamran Shirazi  
- Nikita Rogers  

---

## Notes

- Built using AWS SageMaker (Learner Lab environment)  
- Data sourced from Meta Project Aria (Nymeria dataset)  
- Includes full pipeline: ingestion → modeling → deployment design  
