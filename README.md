# Deep Reinforcement Learning for Traffic Signal Control: Real-world data and communication
Welcome to the collaborative repository for George Washington University (GW) and Uzilina. This repository provides:
1) A traffic simulation (SUMO) with traffic flow models calibrated with collected traffic data for vehicles and pedestrian: Traffic simulated on Foggy Bottom Metro intersection in Washington DC
2) A simulated communication between connected vehicles, pedestrians and road-side units: OMNeT++ simulation embedded with SUMO to simulate all types of communication and their impact on trasnportation.
3) A Deep Reinforcement Learning model for Traffic Signal Control that uses communicated vehicle and pedestrian information to provide optimal actions.

Both simulations can run independently or together.
# Installation
1) Download and install SUMO 1.2.0
2) Download and install OMNeT++ 6.0.2. Follow OMNeT++ 6.0.2 Install Guide to build OMNeT++.
3) Download the simulation files archive (https://gwu.box.com/s/ubhn2obphfvjuv12ju5gwgrgv9dud2qc), extract them and move them to this repository 

## Traffic Sim
This repository has all files needed for running the simulation:
1) baseline_simulation.py : the simulation starts and some information will be extracted by running this python file
2) route_creator.py creates the routing files based on extracted data and creates calibrated vehicles and pedestrians
3) Other typical SUMO network files

## DRL_Control 
It contains all necessary elements to control the traffic signals using a Deep Reinforcement Learning model

## Models
Model 17 is the most recent best performant model
## Communication Sim
1) Launch OMNeT++. After the first launch, you will see a pop-up window offering you to install INET and OMNeT++ sample projects. Do not install INET Framework or sample projects.
2) Go to File->Import...->General->Existing Projects into Workspace
3) Select the inet4.4 directory of the simulation files
4) Enable the "Search for nested projects" option in the Import Projects dialog and click Finish to import INET.
5) Import Simu5G project the same way following steps 2-4 and selecting the simu5G folder.
6) Import Veins 5.2 the same way. In the Import Projects dialog, select "veins" and "veins_inet" projects. Do NOT import "veins_catch","veins_inet3" and "veins_testsims" projects.
7) In OMNeT++ go to "Project->Clean...". Make sure the "Clean all projects" option is enabled and click Clean. If the "Start build immediately" option is checked the workspace will be built automatically. If not, select "Project->Build All (Ctrl+B)".
8) Wait until the workspace is built. This may take a long time depending on the number of CPU cores available in your machine. 
9) Navigate to "DRL_Control/utils.py". Adjust all paths to refer to the actual locations of the corresponding files in your filesystem. 

## Combined Simulation and DRL:
1. Make sure the $SUMO_HOME variable is set to your SUMO 1.2.0 root directory.
2. Navigate to the location of the extracted simulation files. Open "DRL_Control/" directory and launch the "testing_main.py" using Python. 
2. Launch OMNeT++.
3. In OMNeT++ workspace, navigate to "simu5g/simulations/NR/cars" and open omnetpp.ini file.
4. Launch the simulation by selecting "Run->Run As->OMNeT++ Simulation" from the OMNeT++ menu. Select the "Hybrid-DSRC-5G" configuration when prompted. The simulation should start. If SUMO is launched in GUI mode, the simulation is initiated by launching the simulation from SUMO, otherwise, it should start automatically.
Some edits for the pedestrian routes will be added.
