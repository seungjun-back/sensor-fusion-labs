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

## Results
(*Add your Allan plots here*)
- Allan deviation curve with slopes  
- Extracted noise coefficients  
- Integrated angle drift comparison (before/after)

## How to Run
```bash
python compute_allan.py
