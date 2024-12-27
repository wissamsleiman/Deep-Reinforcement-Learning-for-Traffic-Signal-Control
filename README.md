# Collaborative Repository for GWU and Uzilina
Welcome to the collaborative repository for George Washington University (GWU) and Uzilina. This repository serves as a central hub for joint projects, research, and development efforts between our institutions.  Here, you will find shared resources, code, documentation, and updates on ongoing projects. 

The SUMO version used is 1.2.0. 

## Network
This folder has all files needed for running the simulation:
1) baseline_simulation.py : the simulation starts and some information will be extracted by running this python file
2) route_creator.py creates the routing files based on extracted data and will incorporate the calibration parameters distribution soon
3) Other typical SUMO network files

## DRL_Control 
It contains all necessary elements to control the traffic signals using a Deep Reinforcement Learning model

## Models
Model 17 is the most recent best performant model
## Installation
1. Download the archive with simulation files, move it to your desirable location and extract it. 
2. Download and install SUMO 1.2.0
3. Download and install OMNeT++ 6.0.2. Follow OMNeT++ 6.0.2 Install Guide to build OMNeT++.
4. Launch OMNeT++. After the first launch, you will see a pop-up window offering you to install INET and OMNeT++ sample projects. Do not install INET Framework or sample projects.
5. Go to File->Import...->General->Existing Projects into Workspace
6. Select the inet4.4 directory of the simulation files
7. Enable the "Search for nested projects" option in the Import Projects dialog and click Finish to import INET.
8. Import Simu5G project the same way following steps 5-7 and selecting the simu5G folder.
9. Import Veins 5.2 the same way. In the Import Projects dialog, select "veins" and "veins_inet" projects. Do NOT import "veins_catch","veins_inet3" and "veins_testsims" projects.
10. In OMNeT++ go to "Project->Clean...". Make sure the "Clean all projects" option is enabled and click Clean. If the "Start build immediately" option is checked the workspace will be built automatically. If not, select "Project->Build All (Ctrl+B)".
11. Wait until the workspace is built. This may take a long time depending on the number of CPU cores available in your machine. 
12. Navigate to the location of the extracted simulation files. In the file "TRB-SUMO-Model/DRL_Control/utils.py" adjust all paths to refer to the actual locations of the corresponding files in your filesystem. 

## Simulation:
1. Make sure the $SUMO_HOME variable is set to your SUMO 1.2.0 root directory.
2. Navigate to the location of the extracted simulation files. Open "TRB-SUMO-Model/DRL_Control/" directory and launch the "testing_main.py" using Python. 
2. Launch OMNeT++.
3. In OMNeT++ workspace, navigate to "simu5g/simulations/NR/cars" and open omnetpp.ini file.
4. Launch the simulation by selecting "Run->Run As->OMNeT++ Simulation" from the OMNeT++ menu. Select the "Hybrid-DSRC-5G" configuration when prompted. The simulation should start. If SUMO is launched in GUI mode, the simulation is initiated by launching the simulation from SUMO, otherwise, it should start automatically.
Some edits for the pedestrian routes will be added.
