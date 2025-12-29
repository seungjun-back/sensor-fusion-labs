# INS/GNSS Error-State EKF Simulation
## Overview
A complete simulation of an INS/GNSS navigation system using an error-state Extended Kalman Filter (ES-EKF).  
This project demonstrates:
- IMU noise modeling  
- Strapdown INS mechanization  
- Error-state filter design  
- GNSS fusion  
- Performance evaluation and visualization  

## System Architecture
<img width="469" height="911" alt="Portfolio_Nav_Arch" src="https://github.com/user-attachments/assets/1da9b950-88e9-47aa-a313-e2a5d979922b" />

- **IMU Simulator**
  - Generates accel/gyro with bias, random walk, bias instability, scale factor error
- **GNSS Measurement Model**
  - Position/velocity updates at low rate (e.g., 1 Hz)
  - Optional outlier injection
- **Error-State INS**
  - 15-state or 18-state formulation
  - Quaternion attitude propagation  
- **Kalman Filter**
  - Error propagation  
  - GNSS update  
  - State correction

## Features
- IMU truth trajectory generation  
- INS propagation  
- ES-EKF implementation  
- RMSE evaluation (Position / Velocity)  
- Bias estimation convergence  
- Graph and trajectory visualization  

## Results
- Position RMSE  
- Velocity RMSE  
- Bias estimation curves  
- Trajectory comparison

## folder structure

ins-gnss-ekf-sim/
    src/
        imu_sim.py
        ins.py
        ekf.py
        gnss.py
    results/
    plots/
    README.md


## Key Equations
(Include your discretized F, G, Q, update equations)

## How to Run
```bash
python main.py

