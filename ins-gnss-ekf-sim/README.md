# INS-GNSS-Error-State-EKF-Simulation

## Overview
A complete simulation of an INS/GNSS navigation system using an error-state Extended Kalman Filter (ES-EKF).
This project demonstrates:
- IMU noise modeling
- Strapdown INS mechanization
- Error-state filter design
- GNSS fusion
- Performance evaluation and visualization


System Architecture

  IMU Simulator
  
    - Accel/Gyro generation
    - Bias, random walk, bias instability
    - Scale factor error modeling

  GNSS Measurement Model
  
    - Low-rate position/velocity (1 Hz)
    - Optional outlier injection

  Error-State INS
  
    - 15-state / 18-state formulation
    - Quaternion propagation

  Kalman Filter (ESKF)
  
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
