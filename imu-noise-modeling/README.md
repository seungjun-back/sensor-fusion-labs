# IMU Noise Characterization Using Allan Variance

## Overview
This project analyzes IMU noise characteristics using Allan Variance.  
It shows:
- How IMU noise sources appear in real/logged data  
- How to extract ARW, RRW, Bias Instability, Quantization Noise  
- How noise parameters affect INS performance  
- How compensation improves stability of integrated signals

## Pipeline
1. Load IMU angular rate & accelerometer data  
2. Compute Allan Variance  
3. Identify noise parameters  
4. Build a probabilistic IMU noise model  
5. Apply noise compensation  
6. Compare before/after performance  

## Noise Terms
- **Angle Random Walk (ARW)**  
- **Rate Random Walk (RRW)**  
- **Bias Instability**  
- **Quantization Noise**

- ## folder structure
```text
├── data/               # imu data (CSV/Numpy)
├── src/
│   ├── data_loader.py  # [Step 1] loading data
│   ├── allan_calc.py   # [Step 2] Allan Variance 
│   ├── param_id.py     # [Step 3] extract the parameters (Log-fitting)
│   ├── noise_model.py  # [Step 4] Random Walk modelling
│   └── compensator.py  # [Step 5] Bias removal
├── notebook/
│   └── final_report.ipynb 
└── README.md           
```

## Results
(*Add your Allan plots here*)
- Allan deviation curve with slopes  
- Extracted noise coefficients  
- Integrated angle drift comparison (before/after)

## How to Run
```bash
python compute_allan.py
