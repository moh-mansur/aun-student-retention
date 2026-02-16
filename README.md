# AUN Student Retention Ontology (AUN-SRO) - Decision Support System

An ontology-driven decision support framework integrating semantic web technologies with machine learning for proactive, explainable student attrition prediction at the American University of Nigeria (AUN).

##  Overview

This repository contains the implementation of a system that addresses student retention challenges in Sub-Saharan African universities. The system combines:

- **Ontology-based reasoning** for transparent, policy-grounded risk assessment
- **Machine Learning** for detecting subtle multivariate risk patterns
- **Interactive Dashboard** for advisor-facing decision support

##  Key Features

- **Explainable AI**: Policy-grounded explanations through SWRL rules
- **Proactive Intervention**: Early identification of at-risk students
- **Multi-domain Integration**: Academic, financial, engagement, and residential factors
- **Stakeholder-validated**: Rules refined through consultation with Finance and Academic Advising departments

## Repository Contents

### 1. `StudentATT_ML.ipynb`
**Machine Learning & Synthetic Data Generation**

This notebook contains:
- **Synthetic Data Generation**: Creates realistic student data with 1000 records
  - Features: GPA, outstanding balance, logins, classes missed, incident count, advising sessions
  - Handles missing data (20% NaN in logins and sessions)
  - Generates balanced at-risk labels with correlations
  
- **ML Model Training**: Random Forest classifier
  - Feature engineering and preprocessing
  - Model training with hyperparameter tuning
  - Performance evaluation and metrics
  - Model export for dashboard integration

**Key Output**: `best_rf_model.pkl` - Trained Random Forest model

### 2. `AUN_DSS_DASHBOARD.ipynb`
**Flask-based Interactive Dashboard**

This notebook implements:
- **Ontology Integration**: Loads and queries AUN-SRO ontology (requires `AUN_SRO.owl`)
- **ML Integration**: Uses trained Random Forest model for predictions
- **Interactive Interface**: 
  - Student search functionality
  - Risk classification display (High/Medium/Low)
  - Policy-based intervention recommendations
  - Dark mode support
  
**Technologies Used**:
- Flask web framework
- Owlready2 for ontology reasoning
- Joblib for ML model loading
- Responsive HTML/CSS interface

##  Getting Started

### Prerequisites

```bash
pip install owlready2 flask joblib scikit-learn pandas numpy
```

### Running the ML Training

1. Open `StudentATT_ML.ipynb` in Jupyter or Google Colab
2. Run all cells to:
   - Generate synthetic student data
   - Train the Random Forest model
   - Save the trained model (`best_rf_model.pkl`)

### Running the Dashboard

1. **Required Files**:
   - `AUN_SRO.owl` (ontology file)
   - `best_rf_model.pkl` (from ML training notebook)

2. Open `AUN_DSS_DASHBOARD.ipynb` in Google Colab
3. Upload required files when prompted
4. The Flask server will start and display a URL
5. Access the dashboard through the provided URL

##  System Architecture

```
┌─────────────────┐
│   User Input    │
│  (Student ID)   │
└────────┬────────┘
         │
    ┌────▼────┐
    │ Flask   │
    │Dashboard│
    └────┬────┘
         │
    ┌────┴────────────────┐
    │                     │
┌───▼────┐         ┌─────▼──────┐
│ AUN-SRO│         │  Random    │
│Ontology│         │  Forest    │
│        │         │  Model     │
│ SWRL   │         │            │
│ Rules  │         │            │
└───┬────┘         └─────┬──────┘
    │                    │
    └────────┬───────────┘
             │
        ┌────▼────┐
        │  Risk   │
        │Classifi-│
        │ cation  │
        │   +     │
        │Recommend│
        │-ations  │
        └─────────┘
```

##  Ontology Structure

The AUN-SRO formalizes seven knowledge domains:

1. **Academic Domain**: GPA, enrollment status, academic standing
2. **Financial Domain**: Outstanding balances, payment plans, financial aid
3. **Engagement Domain**: LMS logins, 
4. **Residential Domain**: Housing incidents, conduct records
5. **Advisory Domain**: Advising sessions, intervention tracking
6. **Risk Assessment Domain**: Risk levels, early warning indicators
7. **Intervention Domain**: Recommended actions, support resources

**Technical Specifications**:
- 45 Classes
- 28 Object Properties
- 36 Data Properties
- 10 SWRL Rules (policy-encoded)

### Sample SWRL Rules

**Financial Risk Assessment**:
```
Student(?s) ∧ hasOutstandingBalance(?s, ?b) ∧ swrlb:greaterThan(?b, 1500) 
→ hasFinancialRisk(?s, High)
```

**Academic Risk Protocol**:
```
Student(?s) ∧ hasGPA(?s, ?g) ∧ swrlb:lessThan(?g, 2.0) 
→ requiresParentNotification(?s, true) ∧ requiresMandatoryAdvising(?s, true)
```

##  Research Contribution

This work contributes:

1. **First ontology-based retention framework** for African liberal arts universities
2. **Hybrid symbolic-statistical AI** demonstrating explainable educational prediction
3. **Stakeholder-driven ontology engineering** methodology for educational contexts
4. **Modular architecture** enabling institutional adaptation

## 📖 Citation

If you use this work in your research, please cite:

```bibtex
@thesis{aun_sro_2026,
  author = {[Muhammad Idris Mansur ]},
  title = {Ontology-Driven Decision Support for Student Retention: 
           A Case Study at the American University of Nigeria},
  school = {American University of Nigeria},
  year = {2026},
  type = {[Thesis Type]}
}
```

##  Data Privacy

All synthetic data used in this repository is artificially generated and does not contain real student information. The system is designed with privacy-preserving principles for deployment in production environments.

##  Acknowledgments

- Finance Department, AUN (Policy consultation - February 2026)
- Academic Advising Department, AUN (Policy validation)
- Research supervisors and advisors

##  License

[Academic Use Only]

##  Contact

[Muhammad Mansur]  
[muhdmansur1.mm@gmail.com]  
American University of Nigeria

---


