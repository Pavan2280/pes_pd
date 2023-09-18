![image](https://github.com/Pavan2280/pes_pd/assets/131603225/968d792a-c9a8-4684-92ad-6dd97a57d5d8)

# Physical Design Flow 
This repository provides a comprehensive guide to navigate the entire physical design flow, starting from scratch.

# Physical Design Flow Assignments - Guided by Kunal Ghosh

# Table of contents
<details>
<summary>Openlane Installation using VDI</summary>
<br>

## Installation Instructions

Please follow these steps to install Openlane on your system, whether you are using Windows or Ubuntu.

1. **Download the Installation PDF**: Start by downloading the Openlane Installation PDF file for detailed instructions.
- [Openlane Installation PDF](https://drive.google.com/drive/folders/1waH794KlrYMaHzZbf1Fr_BIxfMUk4DBk)

2. **Choose Your Operating System**:

   - **For Windows**: Follow the instructions outlined in the PDF under the "Windows Installation" section.
   
   - **For Ubuntu**: Refer to the "Ubuntu Installation" section in the PDF for step-by-step guidance.

3. **Dependencies**: Ensure you have all the necessary dependencies mentioned in the PDF installed on your system.

4. **Verify Installation**: Confirm that Openlane is correctly installed by running a test command or checking the version.(Check Day 1 content in order to verify installation.)

Please note that if you are logged out, the password is "vsdiat."

</details>

<a name="top"></a>
  
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

# Openlane ASIC Design Flow

![image](https://github.com/Pavan2280/pes_pd/assets/131603225/24e63c09-da0d-4da6-943c-f54d6abbda85)

#### Design Stages

1) **Synthesis**
   1. **yosys** - Yosys performs RTL synthesis, converting high-level RTL descriptions into gate-level netlists.
   2. **abc** - ABC is used for further optimization and technology mapping to enhance the gate-level design.
   3. **OpenSTA** - OpenSTA conducts static timing analysis to verify if the synthesized design meets timing constraints in the OpenLane flow.

2) **Floorplan & PND**
   1. **init_fp (Initial Floorplan)** - Floorplanning involves determining the initial placement and arrangement of various functional blocks or cells within the chip's       
   layout area.
   2. **ioplacer** - ioplacer is a tool used in the physical design process to place Input/Output (I/O) pads or pins on the chip's boundary.
   3. **pdn** - The PDN is responsible for distributing power (supply voltage) and ground (reference voltage) throughout the chip, ensuring that all components receive the       necessary power supply and maintain stable electrical operation.
   4. **tapcell** - A "tapcell" is a special type of cell used in digital integrated circuit design, particularly in standard cell libraries.It is typically used to create 
   tap connections for the bulk terminals in digital CMOS (Complementary Metal-Oxide-Semiconductor) designs.

3) **Placement**
   1. **Replace** - RePlace is a tool used in the OpenLane flow for cell placement optimization.It focuses on optimizing the placement of standard cells within the chip's   
   layout to achieve better area utilization, timing, and power efficiency.
   2. **Resizer** - Resizer is a tool employed during the physical design process to perform cell resizing and optimization.
   3. **OpenDP (Open Detailed Placement)** - OpenDP, or Open Detailed Placement, is a detailed placement tool used in OpenLane.It is responsible for the fine-grained 
   placement of cells, ensuring that they are precisely positioned within rows and tracks while adhering to design constraints and achieving optimal utilization of the chip's 
   layout area.
   4. **OpenPhysyn (Open Physical Synthesis)** - OpenPhysyn is a tool within OpenLane that performs physical synthesis tasks.It optimizes the logical and physical aspects of 
   the design simultaneously, improving the placement, power, area, and timing by considering both logic and physical information during the optimization process.

4) **CTS**
   1. **TritonCTS** - TritonCTS generates a clock distribution network.

5) **Routing**
   1. **FastRoute** - FastRoute is a global routing tool used in the physical design stage of ASIC chip design.
   2. **TritonRoute** - TritonRoute is a detailed or global routing tool used in the later stages of ASIC chip design, following placement and initial global routing.
   
6) **GDSII Generation**
   1. **Magic** - Magic is primarily a layout tool used for creating and editing IC layouts, and it is often used for digital CMOS design.
   2. **KLayout** - KLayout is primarily used for viewing, editing, and analyzing IC layouts but is not a layout creation tool like Magic.
   
8) **Checks**
   1. **CVC** - CVC is a tool primarily used for verification and debugging of digital designs.
   2. **Netgen** - Netgen is an open-source digital netlist comparison and LVS (Layout vs. Schematic) tool.
 
# Labs

#### Task 1 - Invoking OpenLane

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
After executing these commands, you will see a new prompt, which should now be `%`.

Step 5: Load OpenLane Package
If you want to use a specific version of the OpenLane package, you can load it using the following command.
```
package require openlane 0.9
```
![image](https://github.com/Pavan2280/pes_pd/assets/131603225/98126aa2-a5f8-4b07-9f33-7069917e778c)
![image](https://github.com/Pavan2280/pes_pd/assets/131603225/d0d7f989-75d0-4524-acb3-de1547bb0f12)
If you can achieve these results, then you have now successfully invoked OpenLane and are prepared to use it for your projects.

#### Task 2 - Designs presnt in openalne and Heirarchy in a Design

Step 1: Navigate to the OpenLane Working Directory 
Enter these commands
```
cd designs/
ls
cd picorv32a
ls
ls -ltr
```
![image](https://github.com/Pavan2280/pes_pd/assets/131603225/67e3d11e-7406-4636-a6a4-adf12b01be9a)
To view `config.tcl` file enter this command
```
vim config.tcl
```
![image](https://github.com/Pavan2280/pes_pd/assets/131603225/058d34cc-6546-466f-909c-60601e0ae338)

Step 2: Prepare the workflow design using OpenLane with the following command.
```
prep -design picorv32a
```
![image](https://github.com/Pavan2280/pes_pd/assets/131603225/e73c709e-3f63-4c73-8118-a76bc4b12d9e)

Step 3: Please utilize the following command in OpenLane for synthesis.
```
run_synthesis
```
![image](https://github.com/Pavan2280/pes_pd/assets/131603225/25f59d56-2ffe-4c38-94e7-404a8b9a6092)
Now our aim is to find Ratio (Number of D-flip flops to Number of cells)
#### Number of D-flip flops to Number of cells ratio = 1613/14876 (0.108 or 10.8%)
![image](https://github.com/Pavan2280/pes_pd/assets/131603225/60b0b776-f6de-47b9-98f8-b749bb3cba04)

[Back to Top](#top)

</details>

<details>
<summary>Day 2 - Good Floorplan vs Bad Floorplan and Introduction to library cells</summary>
<br>

# Labs

#### Task 1 - Floorplan

Step 1: Before running floorplan, lets look into the switches available for the floorplan stage.
![image](https://github.com/Pavan2280/pes_pd/assets/131603225/02148532-a29d-40bd-8754-0ffa2bdbab3d)

Step 2: Make changes in `config.tcl` file for floorplan purpose.
![image](https://github.com/Pavan2280/pes_pd/assets/131603225/f29ca8fd-54c1-43d7-8f31-1751417fa23a)

Step 3: To create a floorplan using OpenLane, please execute the following command.
```
run_floorplan
```
![image](https://github.com/Pavan2280/pes_pd/assets/131603225/fbee5100-d335-40ea-a290-9ff9bde13d14)

The point (0, 0) within the DIE AREA signifies the top-left corner's coordinates, while (660.685, 671.405) designates the bottom-right corner of the die in micrometers.

Step 4: To visualize the floorplan layout, employ the following command.
```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```
![image](https://github.com/Pavan2280/pes_pd/assets/131603225/59dbab09-a76f-40c0-90bc-dac2c02e456c)

#### Task 2 - Library Binding and Placement

1) Bind the netlist with physical cells - Binding the netlist with physical cells involves mapping logical components onto specific physical cells in a technology library for chip design.
2) Optimize Placement - Optimizing placement involves strategically arranging physical cells on a chip's layout to minimize area, meet timing constraints, and enhance overall performance.

Step 1: To visualize the placement, employ the following command.
```
run_placement
```
![image](https://github.com/Pavan2280/pes_pd/assets/131603225/fa165aad-5c32-4cdc-9dc9-53a7e2c2de93)

# Cell Design Flow

Cell Design is the process of creating electronic components, known as cells, for use in integrated circuits. It involves three main stages:

1) **Inputs**: In this phase, designers gather essential information and resources needed for the cell design. This includes Process Design Kits (PDKs), which contain manufacturing details, Design Rule Check (DRC) and Layout vs. Schematic (LVS) rules for ensuring correctness, SPICE models for simulating component behavior, and library specifications. These inputs provide the foundation for the design process.

2) **Design**: During this stage, designers use the gathered inputs to create the electronic cell. This process typically includes Circuit Design, where the logical and electrical schematic is defined, Layout Design, where the physical arrangement of components is determined while adhering to manufacturing rules, and Characterization, where the cell's performance is analyzed using tools like GUNA. Characterization can involve Timing characterization (evaluating signal timing), Power characterization (assessing power consumption), and Noise characterization (examining electrical noise).

3) **Outputs**: The design process yields various outputs that are essential for subsequent phases of chip development. These outputs include the Circuit Description Language (CDL), which describes the cell's behavior, the Graphic Data System II (GDSII) layout data used in manufacturing, the Library Exchange Format (LEF) for tool compatibility, an extracted Spice netlist (which considers parasitic elements for accurate simulation), timing data, noise data, power libraries, and a functional description to understand the cell's purpose.

# Standard Cell Characterization Flow

## Introduction

Standard Cell Libraries are a fundamental component in digital integrated circuit design, providing a collection of pre-designed cells with various functionalities. To effectively use these libraries, they must be characterized to generate Liberty files, which are essential for synthesis tools to determine the optimal arrangement of circuit components.The open-source software GUNA is used for characterization

## Characterization Flow

The characterization process involves the following steps:

1. **Link Model File of CMOS**: This step involves linking a model file that defines the properties and behavior of the CMOS (Complementary Metal-Oxide-Semiconductor) technology process being used.
2. **Specify Process Corner(s)**: Process corners represent different manufacturing variations that impact the performance of the integrated circuits. You must specify one or more process corners for the cell to be characterized. This information helps in understanding how the cell behaves under different conditions.
3. **Specify Cell Delay and Slew Thresholds Percentages**: Define the desired delay and slew thresholds as percentages. These thresholds are crucial for optimizing circuit performance and determining acceptable signal characteristics.
4. **Specify Timing and Power Tables**: Create tables that specify timing and power data for the cell under various conditions. These tables are essential for accurate modeling of cell behavior.
5. **Read the Parasitic Extracted Netlist**: Import the parasitic extracted netlist, which includes information about the interconnections and parasitic elements in the design. This step ensures a more realistic representation of the cell's behavior.
6. **Apply Input or Stimulus**: Provide input signals or stimuli to the cell. This can include various test vectors or patterns that are used to evaluate the cell's response under different conditions.
7. **Provide Necessary Simulation Commands**: Define the simulation commands required to run the characterization process. These commands may include simulation settings, simulation types (e.g., transient, static timing analysis), and other parameters to control the simulation environment.

# Timing threshold definitions

1) **slew_low_rise_thr**: This threshold is set at 20% above the lowest power supply voltage when the signal is transitioning from low to high (rising).
2) **slew_high_rise_thr**: This threshold is set at 20% below the highest power supply voltage when the signal is transitioning from low to high (rising).
3) **slew_low_fall_thr**: This threshold is set at 20% above the lowest power supply voltage when the signal is transitioning from high to low (falling).
4) **slew_high_fall_thr**: This threshold is set at 20% below the highest power supply voltage when the signal is transitioning from high to low (falling).
5) **in_rise_thr**: This threshold is placed at the point where the input signal is halfway through its transition from low to high during a rising edge.
6) **in_fall_thr**: This threshold is placed at the point where the input signal is halfway through its transition from high to low during a falling edge.
7) **out_rise_thr**: This threshold is positioned at the point where the output signal is halfway through its transition from low to high during a rising edge.
8) **out_fall_thr**: This threshold is positioned at the point where the output signal is halfway through its transition from high to low during a falling edge.
9) **Propagation Delay**: This is the time it takes for a signal to propagate from an input threshold (in_thr) to an output threshold (out_thr). It represents the time it takes for a change at the input to affect the output.
Propagation Delay = time(out_thr) - time(in_thr)
11) **Transition Time**: This is the time it takes for a signal to transition from a low to high state (rising edge) or from a high to low state (falling edge) within a specific voltage range. In this case, you are calculating the transition time from the high threshold (slew_high_rise_thr) to the low threshold (slew_low_rise_thr) during a rising edge.
Transition Time = time(slew_low_rise_thr) - time(slew_high_rise_thr)

[Back to Top](#top)

</details>

<details>
<summary>Day 3 - Design library cell using Magic Layout and ngspice characterization</summary>
<br>

#### Task 1 - CMOS inverter ngspice simulations

`cmos_inverter.cir` 
```
*** MODEL DESCRIPTIONS ***
*** NETLIST DESCRIPTION ***
M1 out in vdd vdd pmos W=0.375u L=0.25u
M2 out in 0 0 nmos W=0.375u L=0.25u

cload out 0 10f

Vdd vdd 0 2.5
Vin in 0 2.5
*** SIMULATION Commands ***

.op
.dc Vin 0 2.5 0.05
*** include tsmc_025um_model.mod ***
.LIB "tsmc_025um_models.mod" CMOS_MODELS
.end
```

Step 1: For SPICE Simulation steps enter these commands.
```
cd <folder where the .cir file is present>
source CMOS_INVERTER.cir
run
setplot
dc1
display
plot out vs in
```

Take note of the circuit's output; it should exhibit symmetry, meaning that the threshold voltage should align precisely with Vdd/2. If this balance is not achieved, consider adjusting the PMOS transistor width and rerunning the simulation. The switching threshold (Vm), where Vin equals Vout, plays a pivotal role in defining the robustness of a CMOS circuit.

# CMOS Inverter Fabrication Process

## Overview

A CMOS (Complementary Metal-Oxide-Semiconductor) inverter is a fundamental building block in digital integrated circuits. It consists of a p-type metal-oxide-semiconductor (PMOS) transistor and an n-type metal-oxide-semiconductor (NMOS) transistor connected in series. Here's a simplified overview of the fabrication process for a CMOS inverter:

## Fabrication Steps

1) **Substrate Preparation** : Start with a high-purity silicon substrate, typically n-doped.
2) **Oxidation** : Create an insulating silicon dioxide (SiO2) layer on the substrate through oxidation.
3) **Photolithography** : Apply a photoresist material, expose it to UV light through a mask, and develop it to define transistor areas.
4) **Ion Implantation (n-well and p-well)** : Create n-type (NMOS) and p-type (PMOS) regions through selective ion implantation.
5) **Gate Oxide Formation** : Grow or deposit a thin layer of gate oxide (SiO2) to insulate the gate electrode from the silicon channel.
6) **Polysilicon Deposition** : Deposit and pattern polysilicon to create gate electrodes that control current flow.
7) **Doping of Gate Electrodes** : Dope gate electrodes for desired conductivity (boron for PMOS, phosphorus/arsenic for NMOS).
8) **Source and Drain Formation** : Create heavily doped source and drain regions for both PMOS and NMOS transistors.
9) **Metal Layer Deposition** : Deposit and pattern a metal layer (e.g., aluminum or copper) for interconnections.
10) **Passivation Layer** : Deposit a passivation layer (usually silicon dioxide) to protect and insulate underlying layers.
11) **Contact Holes** : Etch contact holes through the passivation layer for metal contacts to transistors.
12) **Final Testing and Packaging** : Test the CMOS inverter to ensure it operates correctly, and then integrate multiple inverters and additional components onto a single chip for electronic device applications.

# Labs

#### Task 1 - git cone vsdstdcelldesign

Step 1: Please execute this command within the `Desktop/work/tools/openlane_working_dir/openlane/` directory.
```
git clone https://github.com/nickson-jose/vsdstdcelldesign.git
```

Step 2: To complete the task, please copy the `sky130A.tech` which is present in this `Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic` 
directory into this `Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign` directory by using the command given below.
```
cp sky130A.tech /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
```

![1](https://github.com/Pavan2280/pes_pd/assets/131603225/afabc5ff-0818-4616-aec6-c7434a6ea062)

![2](https://github.com/Pavan2280/pes_pd/assets/131603225/9258aad7-5cd5-45cf-837b-d6ae64fd2930)

#### Task 2 - Creating an Inverter Layout using Magic
Step 1: Open a terminal and run this command
```
cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
magic -T sky130A.tech sky130_inv.mag &
```
After executing the command, you will have two consoles: one is the `layout` console, and the other is the `tkcon` console.

![16_1](https://github.com/Pavan2280/pes_pd/assets/131603225/3c180df5-d7d6-4d7e-bfa9-cce0698bb70b)

To select an area in layout, position the cursor near it, press the `s` key, and then enter the `what` command in the tkcon console to determine which area or widget has been selected.

![18_1](https://github.com/Pavan2280/pes_pd/assets/131603225/a7602338-bebc-4a2d-a7a7-92946b233874)

#### Task 3 - DRC Check 

To check for DRC Errors, select a region (left click for starting point, right click at end point) and see the DRC column at the top that shows how many DRC errors are present.The Details of DRC Errors will be printed on the console.

![19](https://github.com/Pavan2280/pes_pd/assets/131603225/dc8a1696-299c-4798-9b63-09b9ef08015b)

#### Task 4 - Extracting PEX to SPICE with MAGIC
Step 1: Enter these commands in the tkcon console.
```
pwd
extract all
ext2spice cthresh 0 rthresh 0
ext2spice
```
![19(1)](https://github.com/Pavan2280/pes_pd/assets/131603225/e134e634-50df-4f18-8f1f-3121298a14cd)

Step 2: To view `sky130_inv.spice` file enter this command
```
vim sky130_inv.spice
```

![21](https://github.com/Pavan2280/pes_pd/assets/131603225/2581d55a-4795-4f2b-9d29-33af0f7481c9)

# Grid size

![22](https://github.com/Pavan2280/pes_pd/assets/131603225/5b45b753-317a-452b-83e6-b530cb86cc50)

![23](https://github.com/Pavan2280/pes_pd/assets/131603225/f3359e9a-2efd-4c34-b6be-5943ab658c39)

# Modified Spice netlist

#### Task 5 - Make changes to the `sky130_inv.spice`

![final_vim_22](https://github.com/Pavan2280/pes_pd/assets/131603225/c527fcb6-2ad7-464b-b169-f9f0069401d1)

#### Task 6 - Run modified spice netlist
Step 1: Use this command to run the modified spice netlist
```
ngspice sky130_inv.spice
```
![ngspice](https://github.com/Pavan2280/pes_pd/assets/131603225/1d37848c-f3b5-43da-9410-b18cf466311e)

Step 2: Use this command to run the plot.
```
plot y vs time a
```
![plot](https://github.com/Pavan2280/pes_pd/assets/131603225/db091887-53eb-4460-ba23-eb873177f80f)

![plot_1](https://github.com/Pavan2280/pes_pd/assets/131603225/d69ef1d7-a8fd-4257-9ab0-0b94a845b97e)

# Results

1) The trise result is calculated by subtracting the x-coordinates from each other.
#### trise = 0.062ns
![trise_diff_x0](https://github.com/Pavan2280/pes_pd/assets/131603225/bc2990cd-f74e-4300-aa84-84d4e1cbd98f)

2) Propagation delay is similarly determined, but it involves adjusting the points based on the definition of propagation delay.
#### tprop = 0.034ns
![t_prop](https://github.com/Pavan2280/pes_pd/assets/131603225/9e396323-c6ec-4e44-9177-fe326b1a8800)

[Back to Top](#top)

</details>

<details>
<summary>Day 4 - Pre-Layout timing analysis and importance of good clock tree</summary>
<br>

## Introduction

Standard cell placement and routing are essential steps in semiconductor chip design. To optimize these processes, it is vital to follow specific guidelines and best practices. This README provides an overview of key considerations related to LEF information and standard cell placement.

## LEF Information

1) **Technology LEF**: This file contains critical information about metal layers, via configurations, and restricted Design Rule Check (DRC) rules. It defines the foundational aspects of the chip's technology.

2) **Cell LEF**: The Cell LEF file provides an abstract representation of standard cells, encapsulating their characteristics. It is essential for accurate placement and routing of standard cells.

3) **Standard Cell Dimensions** - The width of standard cells should be an odd multiple of the track pitch. This ensures proper alignment with horizontal tracks.Similarly, the height of standard cells should be an odd multiple of the vertical track pitch. This alignment is crucial for efficient routing.

4) **PnR Tool Integration** - PnR tools utilize the abstract view information from the Cell LEF to guide the placement and interconnection of standard cells.

5) **Routing Guides** - Routing guides are generated from the PnR flow and are used in conjunction with LEF information to guide standard cell placement and interconnect routing.

6) **Compliance with Track Pitch** - Ensuring that input and output ports lie precisely on the intersections of vertical and horizontal tracks is critical for efficient routing and manufacturability.

## Benefits
  
  - Adhering to these guidelines for LEF information and standard cell placement offers several benefits:
  - Efficient interconnect routing.
  - Reduced Design Rule Check violations.
  - Improved manufacturability.
  - Enhanced chip performance.

# Labs

#### Task 1 - Extraction of LEF
The `track.info` file can be found within the following directory path: `~/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/openlane/sky130fd_sc_hd/tracks.info`

Step 1: Enter this command to view `track.info` file
```
less track.info
```
![d31](https://github.com/Pavan2280/pes_pd/assets/131603225/150d3736-8441-4604-bc32-360e61da0084)

From above image we can say that 1st value indicates the offset and 2nd value indicates the pitch along provided direction.

#### Task 2 - Setting grid values using above file info

Step 1: Enter this command in `tkcon` console.
```
grid 0.46um 0.34um 0.23um 0.17um
```
![d32](https://github.com/Pavan2280/pes_pd/assets/131603225/8130337d-373d-414d-b14f-fd05699e6f3c)

Layout view after setting grid info
![d33](https://github.com/Pavan2280/pes_pd/assets/131603225/db6e28a3-a491-43e1-b9ed-fd4f77140dbc)

From the above pic, its confirmed that the pins A and Y are at the intersection of X and Y tracks. So both conditions (The width of standard cells should be an odd multiple of the track pitch & the height of standard cells should be an odd multiple of the vertical track pitch) are met.

# LEF Generation

#### Task 1 - Layout modification

Step 1: Enter these commands in console
```
save sky130_vsdinv.mag
```
![d34](https://github.com/Pavan2280/pes_pd/assets/131603225/22f00960-8215-458f-b58e-1229ce685588)

Step 2: Open the file and extract LEF by using this command.
```
magic -T sky130A.tech sky130_vsdinv.mag &
```
![d45](https://github.com/Pavan2280/pes_pd/assets/131603225/ee95bb94-4736-487c-b991-df17fe6ae3df)

Now enter this command inside `tkcon` console.
```
lef write
```
![image](https://github.com/Pavan2280/pes_pd/assets/131603225/98435750-d31d-4b78-b6b4-21715b2e9aa0)

#### Task 2 - Plug the generated lef file into PICORV32a

Step 1: We can view out lef file by using this command.
```
vim sky130_vsdinv.lef
```
![image](https://github.com/Pavan2280/pes_pd/assets/131603225/fbc52f21-2370-4a01-898e-e80cbedde2e3)

Step 2: Next, please copy the `sky130_vsdinv.lef` which is present in this `Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign` in this
directory into this `Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src` directory by using the command given below.
```
cp sky130_vsdinv.lef /home/vsduser/Desktop/work/tools/openlane_working_dir/designs/picorv32a/src/
```

![image](https://github.com/Pavan2280/pes_pd/assets/131603225/6db8ea1d-619a-4d5b-8ad9-a7298d03463a)

![image](https://github.com/Pavan2280/pes_pd/assets/131603225/43428728-977d-456e-8748-7f9879dcb4ae)

Step 3: Now we need to copy the `sky130_fd_sc_hd__*` which is present in this `Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign/libs` in this
directory into this `Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src` directory by using the command given below.
```
cp sky130_fd_sc_hd__* /home/vsduser/Desktop/work/tools/openlane_working_dir/designs/picorv32a/src/
```

![image](https://github.com/Pavan2280/pes_pd/assets/131603225/d91dd912-4d18-4cad-9ce6-e56e8470017c)

![image](https://github.com/Pavan2280/pes_pd/assets/131603225/310e2651-49df-4024-907a-fde826ad22d1)

Step 4: Modify the `config.tcl` file to specify the usage of these libraries and the LEF file.

![image](https://github.com/Pavan2280/pes_pd/assets/131603225/d412e53e-bd62-4ca9-af23-02fccd22a748)

Step 5: Enter these commands to invoke openlane.
```
cd Desktop/work/tools/openlane_working_dir/openlane/
docker
./flow.tcl -interactive
```

Step 6: Make sure the lef file is added and enter these set of commands given below.
#### Note - "Our synthesis, conducted on a perticular day and time, will serve as our unique timestamp, differing for each run so replace "unique_timestamp" with your actual unique timestamp.
```
package require openlane 0.9
prep -design picorv32a -tag unique_timestamp -overwrite
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
run_synthesis
```

![image](https://github.com/Pavan2280/pes_pd/assets/131603225/4e69f5d0-9581-4742-8313-2f470173727c)

![image](https://github.com/Pavan2280/pes_pd/assets/131603225/e7374ed4-c713-4a59-bda1-9aa91a2efe36)

![image](https://github.com/Pavan2280/pes_pd/assets/131603225/9cc2f7aa-e5c1-4381-97ac-e5e3cc282290)


#### Managing slack in Very Large Scale Integration (VLSI) design, particularly in the context of Static Timing Analysis (STA). Let me provide some additional information and clarification on the points you mentioned:

1) Obtaining System Specifications: In the architecture design phase of VLSI, engineers gather system specifications that include various parameters, one of which is the required frequency of operation. This frequency is crucial for determining the overall performance of the integrated circuit.

2) Static Timing Analysis (STA): STA is a critical step in VLSI design to ensure that the designed circuit meets its timing requirements. It involves analyzing the timing behavior of the circuit to ensure that signals meet setup and hold time requirements.

3) Setup Timing: When referring to "pre clock tree synthesis STA analysis" and setup timing, you're concerned with ensuring that signals reach their destination registers reliably before the clock edge (setup time) to avoid setup violations.

4) Worst Negative Slack (WNS) and Total Negative Slack (TNS): WNS represents the worst-case delay violation in the design, while TNS is the sum of all negative slack values across the design. These metrics help identify critical paths and areas where timing violations are occurring.

5) Fixing Slack Violations: To address timing violations, designers often use STA analysis tools like OpenSTA, which is integrated into the OpenLANE tool. These tools help identify the specific violations and allow for debugging and optimization to meet timing constraints.

#### Two Steps for Correct Operation of Tools:

1) Design Configuration Files (.conf): These files contain tool-specific configuration settings for the design. They specify how the tools should analyze and optimize the design.
2) Design Synopsys Design Constraint (.sdc) Files: SDC files provide industry-standard timing constraints for the design. They specify the timing requirements for various elements of the design, such as setup and hold times, clock definitions, and input/output delays.

By providing these configuration files and constraints to tools, you ensure that the tools operate correctly and optimize the design based on the specified requirements.
In summary, managing slack and ensuring proper timing constraints are essential steps in VLSI design to guarantee that the integrated circuit operates correctly and meets its performance specifications. The use of STA tools and well-defined configuration files and constraints plays a crucial role in achieving this goal.

#### Task 3 - We need to run `run_synthesis` again 
Step 1: Enable STNTH_SIZING and set SYNTH_STRATEGY "DELAY 1," carefully monitor the synthesis results for improvements in critical path delay. Adjust these settings iteratively as needed to meet your design's performance goals.

![image](https://github.com/Pavan2280/pes_pd/assets/131603225/6229fb07-ff85-4a76-990b-cac88deee4d5)

![image](https://github.com/Pavan2280/pes_pd/assets/131603225/73b0866d-835f-4296-8435-1192979847e7)

Despite a significant reduction in slack, the timing requirements have not yet been met. This issue could be related to the constraints defined in the "my_base.sdc" file, which is specified in the "pre_sta.conf" configuration file. To address this, consider revising the constraints within "my_base.sdc" and then rerun the STA analysis using the command "sta pre_sta.conf" for further optimization.

![image](https://github.com/Pavan2280/pes_pd/assets/131603225/de3a3a53-eb66-4d9f-8f62-9ca666aed0be)

High fanout can lead to increased delay in digital circuits. To address this, you can enhance synthesis results by adjusting the SYNTH_MAX_FANOUT variable and then rerunning the synthesis process to optimize the fanout and reduce delay.

Step 2: Enable cell buffering & performing manual cell replacement on our WNS path with the OpenSTA tool

To improve timing on the worst negative slack (WNS) path, enable cell buffering to enhance signal propagation. Additionally, identify the primary net responsible for driving multiple outputs and consider replacing the driving cell with a larger version of the same cell type for potential performance gains.

![image](https://github.com/Pavan2280/pes_pd/assets/131603225/fe3333cd-f309-4b89-97e9-53d4c362294e)

Step 3: Optimize the fanout value with OpenLANE tool

Since we successfully synthesized the core using our VSDINV cell, it should be reflected in the layout after the `run_placement` stage, which follows the `run_floorplan stage`.

![image](https://github.com/Pavan2280/pes_pd/assets/131603225/3114bc3e-ae62-49ed-92df-011e81706ce0)

#### Task 4 - Clock Tree Synthesis

After addressing slack violations using the "pre_sta.conf" configuration, generate a netlist with the corrected design using "write_verilog." Subsequently, replace the original OpenLANE-generated "picorv32a.synthesis.v" file with this modified netlist to ensure the design incorporates the necessary fixes.

In the OpenLANE flow, proceed with the "run_floorplan," "run_placement," and "run_cts" stages to further refine the design and ensure that the corrections made to the netlist are incorporated into the physical layout.

#### Task 5 - Post CTS- STA Analysis

Step 1: Within OpenROAD, perform timing analysis by generating a `.db` database file.
1) Launch OpenRoad.
2) Load the LEF file from the "tmp" folder in your OpenLANE runs.
3) Load the DEF file from the CTS results.
4) Create and save the .db database file.
5) Load the generated .db file.
6) Read the CTS-generated Verilog file.
7) Import both the minimum and maximum liberty files.
8) Define clock domains.
9) Generate timing reports to analyze the design further.

![image](https://github.com/Pavan2280/pes_pd/assets/131603225/c9d2a76b-1eb6-48e1-be6d-92b1ce69049c)

![image](https://github.com/Pavan2280/pes_pd/assets/131603225/2cfc4f79-dd5e-4eea-84df-67d82965ce62)

![image](https://github.com/Pavan2280/pes_pd/assets/131603225/cc27da29-c4ca-47e2-9e2a-3fd8442452be)

The timing results are unlikely to meet our expectations due to the utilization of min and max library files, which OpenRoad does not currently support for multi-corner optimization. To address this, we will solely employ the typical corner library for optimization purposes.

![image](https://github.com/Pavan2280/pes_pd/assets/131603225/e680e9d3-8938-47d4-80ae-49de5c3a77a3)

![image](https://github.com/Pavan2280/pes_pd/assets/131603225/0a62727d-13ff-409f-beb7-f63d37d891ce)

![image](https://github.com/Pavan2280/pes_pd/assets/131603225/80155e7c-a853-451f-980c-053bec327491)

![new_!2](https://github.com/Pavan2280/pes_pd/assets/131603225/347a81d5-80cd-4641-81a4-1ea984866f55)

[Back to Top](#top)
</details>

<details>
<summary>Day 5 - Final steps for RTL2GDSII</summary>
<br>

# Power Distribution Network

After generating the clock tree network and verifying post-routing STA checks, we're ready to generate the power distribution network (PDN) in OpenLANE. The PDN feature within OpenLANE will create:

1) A power ring that spans the entire core.
2) A power halo, which is local to any preplaced cells.
3) Power straps, facilitating power distribution to the center of the chip.
4) Power rails dedicated to the standard cells.

![image](https://github.com/Pavan2280/pes_pd/assets/131603225/3248d882-e74a-42de-b81a-08148757b896)

# Global and Detailed Routing

OpenLANE employs TritonRoute as the routing engine for physical design implementation, involving two key stages:

1) Global Routing: This phase generates routing guides for interconnects, defining the layers and locations on the chip for each net.
2) Detailed Routing: Metal traces are incrementally placed following the routing guides to physically implement the interconnects.

In case of persistent Design Rule Check (DRC) errors after routing, users have two options:

1) Re-run routing with higher Quality of Results (QoR) settings.
2) Manually address and correct specific DRC errors mentioned in the TritonRoute-generated "tritonRoute.drc" file.

# SPEF Extraction

After completing routing, interconnect parasitics need to be extracted for sign-off post-route Static Timing Analysis (STA). These parasitics are typically extracted into a Standard Parasitic Exchange Format (SPEF) file. It's important to note that, as of now, OpenLANE does not include an integrated SPEF extractor for this purpose.

#### Step 1: SPEF Extraction can be done by using these commands.
```
cd ~/Desktop/work/tools/SPEFEXTRACTOR
python3 main.py <path to merged.lef in tmp> <path to def in routing>
```
The SPEF file will be generated in the same location as the DEF file.

[Back to Top](#top)
</details>
