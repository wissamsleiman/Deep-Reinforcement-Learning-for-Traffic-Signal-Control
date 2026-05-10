<h1 align="center">Deep Reinforcement Learning for Traffic Signal Control: Real-world data and communication</h1>

<p align="center">
  <a href="https://journals.sagepub.com/doi/10.1177/03611981251384965"><img alt="TRR paper" src="https://img.shields.io/static/v1?label=TRR&amp;message=Paper&amp;color=purple&amp;style=flat-square"></a>&nbsp;&nbsp;&nbsp;&nbsp;
  <a href="LICENSE"><img alt="License" src="https://img.shields.io/static/v1?label=License&amp;message=MIT&amp;color=rose&amp;style=flat-square"></a>
</p>

---

This repository supports the work in [*Transportation Research Record*](https://journals.sagepub.com/doi/10.1177/03611981251384965) on **impact of pedestrian and vehicle connectivity on intersection performance** using a **high-fidelity co-simulation**: microscopic traffic in **SUMO** is coupled with communication stack simulation in **OMNeT++** (Veins, INET, Simu5G). Real-world trajectories from the **TGSIM** dataset calibrate vehicle routes and behavior (intelligent driver model) and pedestrian behavior (social force model). A **Deep Q-Network** traffic signal controller uses a state representation aligned with discrete-time estimation so you can study **partial connectivity**—how penetration rates for connected vehicles and pedestrians affect learning and performance relative to classical control.

It is a collaboration between **George Washington University (GW)** and **Uzilina**. The traffic simulator, communication simulator, and DRL training/testing pipeline can be used **standalone** or **together** for end-to-end experiments.

### What’s in the repository

- **Traffic simulation (SUMO)** — Network and scenarios for the Foggy Bottom Metro intersection in Washington, DC, with flows derived from collected data for vehicles and pedestrians.
- **Communication simulation (OMNeT++)** — Co-simulation with SUMO via Veins; models V2I and related links so you can explore how connectivity assumptions change outcomes.
- **Deep reinforcement learning (DRL)** — Code to train and test a traffic signal controller that can use information from connected vehicles and pedestrians when available.

## Installation

1. Install **SUMO 1.2.0**.
2. Install **OMNeT++ 6.0.2** and follow the official OMNeT++ 6.0.2 install guide to build it.
3. Download the [simulation files archive](https://gwu.box.com/s/ubhn2obphfvjuv12ju5gwgrgv9dud2qc), extract it, and merge or place the contents alongside this repository as needed for your paths.

## Traffic simulation

Typical entry points and assets:

1. **`Network/baseline_simulation.py`** — Start the simulation and extract information for calibration.
2. **`Network/route_creator.py`** — Build route files from extracted data and create calibrated vehicles and pedestrians.
3. Standard SUMO network and configuration files under **`Network/`** (e.g. `foggybottommetro.sumocfg`).

## DRL control

The **`DRL_Control/`** directory contains training and testing scripts, the DQN model, memory, utilities, and settings for traffic signal control with the co-simulation when you run the full stack.

## Models

Trained checkpoints live under **`models/`**. Model **17** is currently the best-performing checkpoint referenced in this project.

## Communication simulation

1. Launch OMNeT++. On first launch, skip installing the INET Framework and sample projects when prompted.
2. **File → Import… → General → Existing Projects into Workspace**
3. Import **inet4.4** from the extracted simulation files; enable **Search for nested projects**, then Finish.
4. Import **Simu5G** the same way (select the `simu5g` folder).
5. Import **Veins 5.2**: select **`veins`** and **`veins_inet`** only. Do **not** import `veins_catch`, `veins_inet3`, or `veins_testsims`.
6. **Project → Clean…** with **Clean all projects**; build the workspace (**Project → Build All** / Ctrl+B if it does not build automatically).
7. Edit **`DRL_Control/utils.py`** and set all file paths to match your machine.

## Combined simulation and DRL

1. Set **`SUMO_HOME`** to your SUMO 1.2.0 root directory.
2. From your extracted simulation files location, open **`DRL_Control/`** and run **`testing_main.py`** with Python.
3. Launch OMNeT++.
4. Open **`simu5g/simulations/NR/cars/omnetpp.ini`** in the workspace.
5. **Run → Run As → OMNeT++ Simulation** and choose the **Hybrid-DSRC-5G** configuration. If SUMO uses the GUI, start the run from SUMO as needed; otherwise the coupled run should start automatically.

Additional pedestrian-route updates may be documented in the repo over time.

## Citation

If you use this repository or the associated methods in your research, please cite our paper:

```bibtex
@article{sleiman2025impact,
  title={Impact of Pedestrian and Vehicle Connectivity on Intersection Performance: A High-Fidelity Simulation with Deep Reinforcement Learning Control},
  author={Sleiman, Wissam and Beigi, Pedram and Petrov, Tibor and Buzna, Lubos and Pocta, Peter and Hamdar, Samer},
  journal={Transportation Research Record},
  pages={03611981251384965},
  year={2025},
  publisher={SAGE Publications Sage CA: Los Angeles, CA}
}
```

## License

This project is licensed under the MIT License; see [LICENSE](LICENSE).
