
# [Day 1]
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

![1-17](https://github.com/lsr20/PD_openlane/assets/141831819/d5922286-bf15-438e-be69-3bebab1f851c)


## Run Synthesis
* command : run_synthesis
  

![1-19](https://github.com/lsr20/PD_openlane/assets/141831819/163558db-f245-4b4a-a256-31468d626850)

## Analyze the Synthesis report
* Flop ratio
  *  No of D flops =
  *  No of cells
 
  ![1-20](https://github.com/lsr20/PD_openlane/assets/141831819/422139fa-dd7d-4175-96f5-0e42de687724)
![1-21](https://github.com/lsr20/PD_openlane/assets/141831819/67b394d7-b538-4a8c-94cb-2babd01e3853)
* new floder
  ![1-21](https://github.com/lsr20/PD_openlane/assets/141831819/e95adab4-4d29-471a-a66c-8dd2c9d98497)
![1-22](https://github.com/lsr20/PD_openlane/assets/141831819/971dc3de-9425-49d7-a0fd-f245f161ce0e)
![1-23](https://github.com/lsr20/PD_openlane/assets/141831819/52c14ede-22db-4034-adfa-66f230ccf3e6)
