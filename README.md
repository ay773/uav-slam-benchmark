# UAV SLAM Benchmark

This repository supports the dissertation:  
"Autonomous Navigation of Unmanned Aerial Vehicles in GPS-Denied Environments"  
by Ali Yildirim (2024), University of York

---

📌 Overview

This project benchmarks two SLAM systems for UAVs in GNSS-denied indoor conditions:

- RTAB-Map (RGB-D)
- OpenVSLAM (Monocular)

Evaluation includes:
- Accuracy (APE, RPE via EVO)
- Runtime profiling (FPS, RAM)
- Failure modes under low-parallax, texture-poor motion

---

📁 Repository Structure (Simplified)
uav-slam-benchmark/
├── datasets/
│ ├── airsim/
│ │ ├── images_flight_20250415_005828_zigzag/
│ │ ├── images_flight_20250415_013806/
│ │ ├── images_flight_20250415_024723/
│ │ ├── images_flight_20250415_024806/
│ │ └── images_flight_20250415_032156/
│ └── tum/
├── results/
│ ├── openvslam/
│ │ ├── desk/
│ │ └── xyz/
│ └── rtabmap/
├── scripts/
├── settings/
│ └── Env/


!Getting Started!

This repo assumes ROS Noetic, Python 3.8, and Docker.

```bash
# Clone repo
git clone https://github.com/ali/uav-slam-benchmark.git
cd uav-slam-benchmark

# Install dependencies
pip install evo matplotlib pandas

# Example: Run SLAM
python scripts/zigzag_path.py
./scripts/run_image_slam.sh



Key Evaluation Results
Pipeline	APE RMSE (m)	RPE RMSE (m)	FPS	Peak RAM (GB)
RTAB-Map xyz	0.013	0.020	25	2.3
OpenVSLAM xyz	3.60	0.079	29	1.1

RTAB-Map achieved < 5 cm drift with active loop closure. Monocular OpenVSLAM failed under pure translation or texture loss.

Datasets
Includes:

Example TUM RGB-D sequences (freiburg1_xyz, freiburg1_desk)

5 AirSim flight recordings (zigzag, circular, etc.)

For full datasets, see official TUM or AirSim download links in the dissertation appendix.



Reproducibility
All configs (settings.json, launch scripts), logs, plots, and dataset subsets are included.
This repo is a self-contained benchmark to reproduce all major results.


Citation / Contact
Ali Yildirim
Supervisor: Dr. John Oyekan
University of York (2024)
GitHub: https://github.com/ali/uav-slam-benchmark