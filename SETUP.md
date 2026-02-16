# Setup Guide

## Quick Start

### Option 1: Google Colab (Recommended for Dashboard)

1. **Upload notebooks to Google Colab**:
   - `StudentATT_ML.ipynb` - Run first to train model
   - `AUN_DSS_DASHBOARD.ipynb` - Run to launch dashboard

2. **Required files for dashboard**:
   - `AUN_SRO.owl` (ontology file - required)
   - `best_rf_model.pkl` (generated from ML notebook)

### Option 2: Local Environment

1. **Clone the repository**:
```bash
git clone https://github.com/[your-username]/aun-student-retention.git
cd aun-student-retention
```

2. **Install dependencies**:
```bash
pip install -r requirements.txt
```

3. **Run ML Training**:
```bash
jupyter notebook StudentATT_ML.ipynb
```
- Execute all cells to generate synthetic data and train model
- Outputs: `new_synthetic_aun_students.csv` and `best_rf_model.pkl`

4. **Run Dashboard**:
```bash
jupyter notebook AUN_DSS_DASHBOARD.ipynb
```
- Upload `AUN_SRO.owl` and `best_rf_model.pkl` when prompted
- Follow the Flask server URL to access the dashboard

## File Structure After Setup

```
aun-student-retention/
├── README.md
├── SETUP.md
├── requirements.txt
├── .gitignore
├── StudentATT_ML.ipynb          # ML training & data generation
├── AUN_DSS_DASHBOARD.ipynb      # Flask dashboard
├── new_synthetic_aun_students.csv   # Generated data (after ML run)
├── best_rf_model.pkl            # Trained model (after ML run)
└── AUN_SRO.owl                  # Ontology file 
```

## Troubleshooting

### Issue: Ontology file not loading
- Ensure `AUN_SRO.owl` is in the same directory
- Check file permissions

### Issue: Model prediction errors
- Verify `best_rf_model.pkl` was generated from `StudentATT_ML.ipynb`
- Check that all required features are present in input data

### Issue: Flask dashboard not accessible
- In Colab, use the ngrok URL provided
- Locally, access via `http://localhost:5000`

## System Requirements

- Python 3.8+
- 4GB RAM minimum
- Internet connection (for Colab)

## Support

For issues or questions, please open an issue on GitHub or contact the researcher.
