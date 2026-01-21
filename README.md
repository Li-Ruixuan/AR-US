# AR-US

Overview
This project implements a markerless augmented reality ultrasound (AR-US) system for 3D visualization of spinal anatomy during minimally invasive spine surgery (MISS). The system eliminates the need for external optical tracking markers by combining:

FoundationPose (FP): Deep learning-based 6-DoF pose estimation of the ultrasound probe from HoloLens camera images

A-Net: Ultrasound image flow-based motion estimation for smooth inter-frame constraints (based on Li et al., IEEE TBME 2024)

UNet: Bone surface segmentation from 2D ultrasound images

Extended Kalman Filter (EKF): Sensor fusion with CTRV motion model for robust pose tracking

The reconstructed 3D bone surface is rendered on a Microsoft HoloLens 2, providing surgeons with intuitive visualization of underlying anatomy without radiation exposure.



┌─────────────────────────────────────────────────────────────┐
│                    Your Integration Code                    │
│                         (src/)                              │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   ┌─────────────┐  ┌─────────────┐  ┌─────────────┐         │
│   │   FP        │  │   A-Net     │  │   UNet      │         │
│   │  Wrapper    │  │  Wrapper    │  │  Wrapper    │         │
│   └──────┬──────┘  └──────┬──────┘  └──────┬──────┘         │
│          │                │                │                │
├──────────┼────────────────┼────────────────┼────────────────┤
│          │                │                │                │
│         ▼                ▼                ▼                │
│   ┌─────────────┐  ┌─────────────┐  ┌─────────────┐         │
│   │ Foundation  │  │  freehand   │  │ Your UNet   │         │
│   │    Pose     │  │  (Li et al.)│  │   code      │         │
│   │ (external/) │  │ (external/) │  │  (src/)     │         │
│   └─────────────┘  └─────────────┘  └─────────────┘         │
│                                                             │
└─────────────────────────────────────────────────────────────┘
