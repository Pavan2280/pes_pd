# Physical Design Flow 
This repository provides a comprehensive guide to navigate the entire physical design flow, starting from scratch.

# Physical Design Flow Assignments - Guided by Kunal Ghosh

# Table of contents
<details>
<summary>Day 1 - Introduction to QFN-48 Package, chip, pads, core, die and IPs</summary>
<br>
  
#### QFN-48 Package
The QFN-48 (Quad Flat No-Lead 48) package is a widely used integrated circuit (IC) package in the electronics industry. It belongs to the family of leadless surface-mount 
packages designed to maximize space efficiency on printed circuit boards (PCBs) while providing excellent thermal performance and electrical connectivity.
The QFN-48 package typically consists of 48 pins arranged in a square or rectangular grid. The pins are numbered and positioned along the package's perimeter.

![QFN-Package](https://github.com/Pavan2280/pes_pd/assets/131603225/f0d98e95-8f05-4d8a-af1b-51b63c15bb1a)

#### Chip
The chip is centrally positioned within the package, as illustrated in the image below, depicting the method of connection between the chip and the package.By connecting the chip in this manner, we can efficiently transfer signals from the external world into the interior of the chip.

![image](https://github.com/Pavan2280/pes_pd/assets/131603225/a4bf87fa-257d-46e1-93e8-1bd83656d67c)

# Components of Chip
- **Pads** : Pads serve as conduits for transmitting signals both into and out of a chip, facilitating bidirectional communication between the chip's internal and external components.
- **Core** : The core essentially serves as the central region where various digital logic components, including AND gates, OR gates, multiplexers (mux), and other types of logic elements, are located.
- **Die** : It essentially defines the dimensions or physical size of the chip.
- **IP's** : Intellectual Property known as IP refers to pre-designed and pre-verified functional blocks or modules that can be integrated into a semiconductor chip's design. These blocks typically encompass a wide range of functions, such as processors, memory, communication interfaces, and specialized functions.

![image](https://github.com/Pavan2280/pes_pd/assets/131603225/00e971c8-4bf4-4b93-8335-5fb20850fbf6)
![image](https://github.com/Pavan2280/pes_pd/assets/131603225/1fb78871-f8d4-4e87-9d14-1f15caf832ed)

# What are PDK's
PDK stands for "Process Design Kit." It is a set of tools, libraries, and documentation used in the semiconductor industry for designing and verifying the manufacturing process of integrated circuits (ICs) or microchips. PDKs are essential for semiconductor companies, foundries, and design houses to create and optimize semiconductor devices.

# RTL  to GDS Flow

![image](https://github.com/Pavan2280/pes_pd/assets/131603225/79f2b9dc-ad16-447e-924d-12d5503589c6)

RTL to GDS (Register Transfer Level to Graphic Design System) flow is a series of steps and processes used in the semiconductor industry to transform a high-level hardware description of an integrated circuit (IC) or microchip into a physical layout that can be fabricated in a semiconductor foundry.Here's a overview of the RTL to GDS flow:

- **Synthesis** : Involves transforming the RTL code into a gate-level representation, optimizing the design to enhance area, power, and timing characteristics, ultimately generating a gate-level netlist.
- **Floor Planning** : In the process of floor planning and power planning, we establish a comprehensive floorplan that meticulously dictates the arrangement of diverse blocks and macros across the chip while taking into account the essential aspects of power distribution and signal routing requirements.
- **Power Planning** :  It involves the careful management and distribution of power throughout the chip to ensure that it operates reliably, efficiently, and within specified power constraints.
- **Placement** : It involves determining the precise location of each standard cell or logic element within the chip's floorplan.
- **Clock Tree Synthesis** : Its primary purpose is to create an optimized clock distribution network that ensures reliable and efficient clock signal distribution throughout the chip.
- **Routing** : Perform global and detailed routing to create the physical connections between standard cells, optimize routing for signal integrity and manufacturability.
- **Sign-off** : Sign-off represents the final checks and confirmations that the design meets all the specified requirements and is ready for fabrication. 

# Openlane ASIC Flow
![image](https://github.com/Pavan2280/pes_pd/assets/131603225/24e63c09-da0d-4da6-943c-f54d6abbda85)

# Labs
# Task 1: Invoking OpenLane
Step 1: Navigate to the OpenLane Working Directory
Open your terminal and navigate to the OpenLane working directory on your Desktop.
```
cd Desktop/work/tools/openlane_working_dir/
```
Step 2: Check Directory Contents
List the contents of the directory to ensure you are in the correct location.
```
ls -ltr
```
Step 3: Enter the OpenLane Docker Environment
To work with OpenLane, you will need to enter the Docker environment. Use the following command:
```
cd openlane
docker
```
After running this command, you will see a new prompt, which should look something like `bash-4.2$`. This indicates that you are now inside the Docker environment.
Step 4: Invoke OpenLane
To invoke OpenLane, run the following commands
```
ls
./flow.tcl -interactive
```
After executing these commands, you will see a new prompt, which should now be `%`. This means you have successfully invoked OpenLane.
Step 5: Load OpenLane Package
If you want to use a specific version of the OpenLane package, you can load it using the following command.
```
package require openlane 0.9
```
![image](https://github.com/Pavan2280/pes_pd/assets/131603225/98126aa2-a5f8-4b07-9f33-7069917e778c)
![image](https://github.com/Pavan2280/pes_pd/assets/131603225/d0d7f989-75d0-4524-acb3-de1547bb0f12)
If you can achieve these results, then you have now successfully invoked OpenLane and are prepared to use it for your projects.
</details>
