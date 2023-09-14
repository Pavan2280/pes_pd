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
![image](https://github.com/Pavan2280/pes_pd/assets/131603225/60b0b776-f6de-47b9-98f8-b749bb3cba04)
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


# Timing threshold definitions

**slew_low_rise_thr**: This threshold is set at 20% above the lowest power supply voltage when the signal is transitioning from low to high (rising).
**slew_high_rise_thr**: This threshold is set at 20% below the highest power supply voltage when the signal is transitioning from low to high (rising).
**slew_low_fall_thr**: This threshold is set at 20% above the lowest power supply voltage when the signal is transitioning from high to low (falling).
**slew_high_fall_thr**: This threshold is set at 20% below the highest power supply voltage when the signal is transitioning from high to low (falling).
**in_rise_thr**: This threshold is placed at the point where the input signal is halfway through its transition from low to high during a rising edge.
**in_fall_thr**: This threshold is placed at the point where the input signal is halfway through its transition from high to low during a falling edge.
**out_rise_thr**: This threshold is positioned at the point where the output signal is halfway through its transition from low to high during a rising edge.
**out_fall_thr**: This threshold is positioned at the point where the output signal is halfway through its transition from high to low during a falling edge.
</details>
