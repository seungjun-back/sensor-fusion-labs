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

## Key Technical Highlights
- Robustness: Integrated Chi-square tests within the innovation check phase for effective measurement outlier rejection.
- Reliability: Implemented Time Alignment Buffers to handle and synchronize asynchronous sensor data streams from IMU and GNSS.
- Adaptability: Optimized filter performance using Context-aware Adaptive R-scaling based on real-time GNSS signal quality.

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

```text
ins-gnss-ekf-sim/
├── src/
│   ├── imu_sim.py
│   ├── ins.py
│   ├── ekf.py
│   └── gnss.py
├── results/
├── plots/
└── README.md
```

## Key Equations
(Include your discretized F, G, Q, update equations)

### 1. Error-State Kinematics (Continuous-time)
The linearized error-state dynamics are governed by:
$$\delta \dot{\mathbf{x}}(t) = \mathbf{F}(t) \delta \mathbf{x}(t) + \mathbf{G}(t) \mathbf{w}(t)$$
where the 15-state error vector is defined as:
$$\delta \mathbf{x} = [\delta \mathbf{p}^T, \delta \mathbf{v}^T, \delta \boldsymbol{\theta}^T, \delta \mathbf{a}_b^T, \delta \mathbf{g}_b^T]^T$$

### 2. Covariance Propagation (Discrete-time)
The uncertainty is propagated through the system dynamics:

$$\mathbf{P}_{k|k-1} = \boldsymbol{\Phi}_{k-1} \mathbf{P}_{k-1|k-1} \boldsymbol{\Phi}_{k-1}^T + \mathbf{Q}_d$$

where $\boldsymbol{\Phi}$ is the state transition matrix derived from the IMU mechanization.

### 3. Measurement Update (GNSS Fusion)
When a GNSS measurement $\mathbf{y}_k$ is available, the Kalman gain $\mathbf{K}_k$ and error-state $\delta \hat{\mathbf{x}}_k$ are computed:

$$\mathbf{K}_k = \mathbf{P}_{k|k-1} \mathbf{H}_k^T (\mathbf{H}_k \mathbf{P}_{k|k-1} \mathbf{H}_k^T + \mathbf{R}_k)^{-1}$$

$$\delta \hat{\mathbf{x}}_k = \mathbf{K}_k (\mathbf{y}_k - \mathbf{H}_k \hat{\delta \mathbf{x}}_{k|k-1})$$

### 4. State Injection & Reset
The estimated errors are injected back into the nominal state:

$$\mathbf{x}_{true} = \mathbf{x}_{nominal} \oplus \delta \hat{\mathbf{x}}$$

After injection, the error state is reset: $\delta \hat{\mathbf{x}} \leftarrow 0$.

## How to Run
```bash
python main.py

