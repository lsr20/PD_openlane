# Advance Physical Design Using OpenLANE/Sky130
This project is done in the course "Advanced Physical Design using OpenLANE/Sky130" by VLSI System Design Corporation. In this project a complete RTL to GDSII flow for PicoRV32a SoC is executed with Openlane using Skywater130nm PDK. Custom designed standard cells with Sky130 PDK are also used in the flow. Timing Optimisations are carried out. Slack violations are removed. DRC is verified.

# OpenLANE design stages
* Synthesis
  - yosys - Performs RTL synthesis
  -   abc - Performs technology mapping
  -  OpenSTA - Performs static timing analysis on the resulting netlist to generate timing reports
* Floorplan and PDN
  - init_fp - Defines the core area for the macro as well as the rows (used for placement) and the tracks (used for routing)
  - ioplacer - Places the macro input and output ports
  -  pdn - Generates the power distribution network
  -  tapcell - Inserts welltap and decap cells in the floorplan
* Placement
  -  RePLace - Performs global placement
  -  Resizer - Performs optional optimizations on the design
  -  OpenDP - Perfroms detailed placement to legalize the globally placed components
* CTS
  -  TritonCTS - Synthesizes the clock distribution network (the clock tree)
* Routing
  -   FastRoute - Performs global routing to generate a guide file for the detailed router
  -   CU-GR - Another option for performing global routing.
  -  TritonRoute - Performs detailed routing
  -   SPEF-Extractor - Performs SPEF extraction
* GDSII Generation
  -   Magic - Streams out the final GDSII layout file from the routed def
  -   Klayout - Streams out the final GDSII layout file from the routed def as a back-up
  * Checks
  -   Magic - Performs DRC Checks & Antenna Checks
  -   Klayout - Performs DRC Checks
  -   Netgen - Performs LVS Checks
  -  CVC - Performs Circuit Validity Checks



![0-1](https://github.com/lsr20/PD_openlane/assets/141831819/8b7b9b54-8519-447d-abc4-a06ad7535b0a)


* Synthesis: RTL Converted to gate level netlist using standard cell libraries (SCL)
* Floor & Power Planning: Planning of silicon area to ensure robust power distribution
* Placement: Placing cells on floorplan rows aligned with sites
* Global Placement: for optimal position of cells
* Detailed Placement: for legal positions
* Routing: Valid patterns for wires
* Signoff: Physical (DRC, LVS) and Timing verifications (STA)




![0-2](https://github.com/lsr20/PD_openlane/assets/141831819/769941fc-a6ad-44c3-bc57-4f4582746e58)


# Day 1
## Some Basic to Linux Command
* ls -ltr  <br> 
* pwd 
* command_name --help   <br> 
* clear  <br> 

 
## OpenLANE Files
In open lane working directory there are three dir PDK a

* skywater-pdk: contains PDK files provided by foundry
* open_pdks: contains scripts to setup pdks for opensource tools
* sky130A: contains sky130 pdk files
![1-1](https://github.com/lsr20/PD_openlane/assets/141831819/0a08f27b-e938-4fcf-b9fc-2887644e6eea)
![1-2](https://github.com/lsr20/PD_openlane/assets/141831819/5eb4c2c1-a168-40c2-bc3a-0ce4eaa6bb2d)

![1-3](https://github.com/lsr20/PD_openlane/assets/141831819/5103a78e-7445-46ed-b62f-b7276af0205a)
![1-4](https://github.com/lsr20/PD_openlane/assets/141831819/71ae125c-86f3-4c55-9362-6015ed1f9040)
![1-5](https://github.com/lsr20/PD_openlane/assets/141831819/36f16e6c-4543-456a-b8c3-ed0bb1ed33e9)
![1-6](https://github.com/lsr20/PD_openlane/assets/141831819/59f14ddd-0639-4abb-acc3-2def7cf51150)

![1-7](https://github.com/lsr20/PD_openlane/assets/141831819/5d0b0f8f-94cf-476e-9f42-376f2a16dad5)

##  invoking open lane 
Go to the openlane directory then floow the command as shown :
* docker
* ./flow.tcl -interactive



![1-8](https://github.com/lsr20/PD_openlane/assets/141831819/27de25b3-573d-4771-987f-1cc310770d57)


  ## Imprt package
* package reuire openlane

![1-9](https://github.com/lsr20/PD_openlane/assets/141831819/7253e318-ca2b-41c7-926d-337e4b4847a5)

## Design floder



![1-10](https://github.com/lsr20/PD_openlane/assets/141831819/b931cec0-e002-4e2e-bd9b-278c0f29de99)
![1-11](https://github.com/lsr20/PD_openlane/assets/141831819/aaca1bcc-10c5-470a-8
![1-12](https://github.com/lsr20/PD_openlane/assets/141831819/e11e167f-4913-440c-be1a-d8fb7787ab9b)
c3c-a80ffa13cdb5)


![1-13](https://github.com/lsr20/PD_openlane/assets/141831819/f618aa46-88b8-4ac8-a21f-47ed1a0b19fc)
## Design Setup
* command : prep design picorv32a




![1-15](https://github.com/lsr20/PD_openlane/assets/141831819/0183f037-2c1e-445d-83b8-6e2f8c28e860)




![1-16_merge lef created in runs](https://github.com/lsr20/PD_openlane/assets/141831819/50738df0-7c94-4a40-bf56-ba9bd9d23b77)
Review of files & Synthesis step
* A "runs" folder is generated within the picorv32a folder.
* The merged file is created during the merging operation in the pircorv32a design preparation (it merges lef and techlef files)
* Next, we run the synthesis of picorv32a design in the openlane interactive terminal:
![1-17](https://github.com/lsr20/PD_openlane/assets/141831819/d5922286-bf15-438e-be69-3bebab1f851c)


## Run Synthesis
* command : run_synthesis
  

![1-19](https://github.com/lsr20/PD_openlane/assets/141831819/163558db-f245-4b4a-a256-31468d626850)

## Analyze the Synthesis report
* Flop ratio
  *  No of D flops =. 1613
  *  No of cells =14876
 * Flop ratio = 1613/14876 = 0.1084 = 10.84%
  ![1-20](https://github.com/lsr20/PD_openlane/assets/141831819/422139fa-dd7d-4175-96f5-0e42de687724)
![1-21](https://github.com/lsr20/PD_openlane/assets/141831819/67b394d7-b538-4a8c-94cb-2babd01e3853)
* new floder
  ![1-21](https://github.com/lsr20/PD_openlane/assets/141831819/e95adab4-4d29-471a-a66c-8dd2c9d98497)
![1-22](https://github.com/lsr20/PD_openlane/assets/141831819/971dc3de-9425-49d7-a0fd-f245f161ce0e)
![1-23](https://github.com/lsr20/PD_openlane/assets/141831819/52c14ede-22db-4034-adfa-66f230ccf3e6)





# DAY 2 Floor Plan and Introduction to library cells
## 1. Define width and height of cells 
*  Utlisation factor = Area occupied by Netlist/ Total area of the core 
* Aspect Ratio = Height / ratio
## 2. Define location of pre placed cells
Arragnement of IP'S in a chip is called as $Floorplanning$. These IP's/blocks have user defined locations , and hence are placed in a chip before automated placement and routing and are called as pre placed cells. Automated place and routing tools places the remaining logical cells in the design onto chip.
## 3. Decoupling Capacitor
Pre-placed cells must then be surrounded with decoupling capacitors (decaps). The resistances and capacitances associated with long wire lengths can cause the power supply voltage to drop significantly before reaching the logic circuits. This can lead to the signal value entering into the undefined region, outside the noise margin range. Decaps are huge capacitors charged to power supply voltage and placed close the logic circuit. Their role is to decouple the circuit from power supply by supplying the necessary amount of current to the circuit. They pervent crosstalk and enable local communication.
## 4.Power Planning
Each block on the chip, however, cannot have its own decap unlike the pre-placed macros. Therefore, a good power planning ensures that each block has its own VDD and VSS pads connected to the horizontal and vertical power and GND lines which form a power mesh.
## 5.Pin placement
The netlist defines connectivity between logic gates. The place between the core and die is utilised for placing pins. The connectivity information coded in either VHDL or Verilog is used to determine the position of I/O pads of various pins. Then, logical placement blocking of pre-placed macros is performed so as to differentiate that area from that of the pin area.

## Floorplanning with OpenLANE
To run floorplan in OpenLANE command :
* run_floorplan



* DEF lines showing the area of the die used


![2-2](https://github.com/lsr20/PD_openlane/assets/141831819/ede43543-f15f-4243-a0fa-46eccb1de762)

* floor plan 

* command - magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read merged_unpadded.lef def picorv32a.floorplan.def &




![2-3](https://github.com/lsr20/PD_openlane/assets/141831819/f8f1eb37-3903-4eb3-ab85-315445ea1933)

#Placement
The next step in the Digital ASIC design flow after floorplanning is placement. The synthesized netlist has been mapped to standard cells and floorplanning phase has determined the standard cells rows, enabling placement. OpenLANE does placement in two stages:

*Global Placement - Optimized but not legal placement. Optimization works to reduce wirelength by reducing half parameter wirelength
*Detailed Placement - Legalizes placement of cells into standard cell rows while adhering to global placement

command : run_placement

* All the standard cells which are at the lower left corner during floorplan are now placed in Placement of standard cells happens in respectice rows.
  
![2-4](https://github.com/lsr20/PD_openlane/assets/141831819/8d889808-2d70-4f27-b58d-8d8788f778ca)

* Floorplan ensures - Decap, boundary of stnd. cells , tap cells, io cells are correctly placed
* Placement ensures that Standard cells are correclty placed .
*  generally Power plan happens during Placement but in Openlane we do it post placemnt , post CTS just before routed .


# Day 3
## Design Library cell
OpenLANE has the benefit of allowing changes to internal switches of the ASIC design flow on the fly. This allows users to experiment with floorplanning and placement without having to reinvoke the tool.

## Spice Simulations
* To simulate standard cells spice deck wrappers will need to be created around our model files.
SPICE deck will comprise of:

- Model include statements
- Component connectivity, including substrate taps
- Output load capacitance
- Component values
- Node names
- Simulation commands

To plot the output waveform of the spice deck we will use ngspice. The steps to run the simulation on ngpice are as follows:

- Source the .cir spice deck file
- Run the spice file by: run
- Run: setplot → allows you to view any plots possible from the simulations specified in the spice deck
- Select the simulation desired by entering the simulation name in the terminal
- Run: display to see nodes available for plotting
- Run: plot  vs  to obtain output waveform


OpenLANE allows users to make changes to environment variables on the fly. For instance, if we wish to change the pin placement from equidistant to some other style of placement we may do the following in the openLANE flow:

* set ::env(FP_IO_MODE) 2
![3-1](https://github.com/lsr20/PD_openlane/assets/141831819/655ade82-a2f6-44c8-bb77-838e940acf23)



# Inverter Standard cell Layout and SPICE extraction
The Magic layout of a CMOS inverter will be used so as to intergate the inverter with the picorv32a design. To do this, inverter magic file is sourced from vsdstdcelldesign by cloning it within the openlane_working_dir/openlane directory as follows:

* command : git clone https://github.com/nickson-jose/vsdstdcelldesign
This creates a vsdstdcelldesign named folder in the openlane directory.

To invoke magic to view the sky130_inv.mag file, the sky130A.tech file must be included in the command along with its path. To ease up the complexity of this command, the tech file can be copied from the magic folder to the vsdstdcelldesign folder.

The sky130_inv.mag file can then be invoked in Magic very easily:
* command :magic -T sky130A.tech sky_inv.mag
![3-2](https://github.com/lsr20/PD_openlane/assets/141831819/62f98488-04bc-4a09-9875-6f0977e4059f)


  # Extract the layout netlist of Inverter for ngspice simulation
  
* use command " extract all " in the tckon window and you will see new file is created in directory with extension .ext

![3-3](https://github.com/lsr20/PD_openlane/assets/141831819/39586e66-6bb8-43a1-adc1-8b7d339215f9)



# Day 4

![4-1](https://github.com/lsr20/PD_openlane/assets/141831819/08b75eda-e967-49c1-a119-b94d11fd3692)

![4-2](https://github.com/lsr20/PD_openlane/assets/141831819/15e3b37c-b845-4bc0-86a6-b12054f4a37a)
![4-3](https://github.com/lsr20/PD_openlane/assets/141831819/b9421648-ee46-47a6-a5bf-b2e98dfaca9b)
![4-4_lef](https://github.com/lsr20/PD_openlane/assets/141831819/20e20321-ba39-4f09-bb1b-b969cf4f3bef)
![4-5](https://github.com/lsr20/PD_openlane/assets/141831819/a58ecec3-d9eb-4577-bc48-d073fec2bf90)

# Integrating custom cell in OpenLANE


In order to include the new standard cell in the synthesis, copy the sky130_vsdinv.lef file to the designs/picorv32a/src directory
Since abc maps the standard cell to a library abc there must be a library that defines the CMOS inverter. The sky130_fd_sc_hd_typical.lib file from vsdstdcelldesign/libs directory needs to be copied to the designs/picorv32a/src directory 


In order to integrate the standard cell in the OpenLANE flow, invoke openLANE as usual and carry out following procedure:
 Commands :
* prep -design picorv32a -tag 13-08_09-13 -overwrite
*  set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
* add_lefs -src $lefs
* run_synthesis
* run_floorplan
  ![4-6](https://github.com/lsr20/PD_openlane/assets/141831819/c806d4b8-ab3d-4297-a7b2-7287de17121d)
  * command- magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read merged_unpadded.lef def picorv32a.placement.def &
![4-7](https://github.com/lsr20/PD_openlane/assets/141831819/212ce494-d5f9-4eb2-af48-0953634b8259)

# Day 5
* Clock Tree Synthesis
The purpose of building a clock tree is enable the clock input to reach every element and to ensure a zero clock skew. H-tree is a common methodology followed in CTS. Before attempting a CTS run in TritonCTS tool, if the slack was attempted to be reduced in previous run, the netlist may have gotten modified by cell replacement techniques. Therefore, the verilog file needs to be modified using the write_verilog command. Then, the synthesis, floorplan and placement is run again. To run CTS use the below command:

command : run_cts
The CTS run adds clock buffers in therefore buffer delays come into picture and our analysis from here on deals with real clocks. Setup and hold time slacks may now be analysed in the post-CTS STA anlysis in OpenROAD within the openLANE flow:

* openroad
* write_db pico_cts.db
* read_db pico_cts.db
* read_verilog /openLANE_flow/designs/picorv32a/runs/03-07_11-25/results/synthesis/picorv32a.synthesis_cts.v
* read_liberty $::env(LIB_SYNTH_COMPLETE)
* link_design picorv32a
* read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc
* set_propagated_clock (all_clocks)
* report_checks -path_delay min_max -format full_clock_expanded -digits 4



# Final steps in RTL2GDS
* Power Distribution Network generation
Unlike the general ASIC flow, Power Distribution Network generation is not a part of floorplan run in OpenLANE. PDN must be generated after CTS and post-CTS STA analyses:

* command : gen_pdn
