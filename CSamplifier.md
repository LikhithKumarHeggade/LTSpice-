# CS Amplifier 
## Aim : 
To Perform DC Analysis, AC Analysis and Transient analysis on CS Amplifier circuit to obtain various circuit parameters like DC operating point, Gain, Bandwidth and Power using LTSpice Simuator. 
## Components Required : 
Mosfet(nmos4 & pmos4), Voltage Supply(1.8V & 0.9V), Resistors(1Kohms) and Connecting Wires. 
## Theory : 
MOSFET is a four-terminal device (Drain, Source, Gate, and Body) which can control the flow of current through the applied voltage at the Gate terminal, creating an electric field that regulates the conductivity between the Drain and Source terminals usually the body and source terminals are internally connected. 
In order to function as an Amplifier the MOSFET should operate in saturation region. A Common-Source Amplifier is a voltage amplifier that uses a MOSFET to amplify small AC signals. It is called "Common-Source" because the Source terminal is common to both input and output.MOSFET Operates in Ssturation region when 
                                              
                                   Vds > Vgs - Vt  (for nmos) ; Vsd > |Vsg| - Vt (for pmos)
In the saturation region, a n-type MOSFET functions as a Voltage-Controlled Current Source (VCCS) where the drain current is given by 
                                   
                                            Id = 1/2*kn*Vov^2 ; Vov = Vgs - Vt 
### Different Types of Analysis :
1. DC Analysis - Determines the quiescent operating point (Q-point) of the MOSFET.
2. AC Analysis -  Determines how the amplifier responds to small AC signals.
3. Transient Analysis - Shows how the circuit responds to time-varying inputs, Helps to analyze switching behavior, distortion, and signal delay.
## Procedure : 
1. Create a folder named LTSpice in your PC/Laptop and save all the ltspice files in this folder.
2. Download the TSMC library datasheet from a reliable online source and place it in the directory where LTSpice is installed.
3. Open a new schematic in LTSpice and name it "CS Amplifier". Construct the required circuit and rename the MOSFETs as CMOSN (for nmos) and CMOSP (for pmos). For 
   the CMOSN transistor, set the channel length to 180nm and the channel width to 1um.
4. Under the "Simulate" option select "Configure Analysis", then choose the appropriate analysis mode (DC, AC, or Transient analysis) based on the circuit 
   requirements. Configure the necessary parameters and run the simulation to observe the circuit's behavior.
5. DC Analysis - Apply the DC voltage of Vdd = 1.8V and Vgs = 0.9V , Go to the Simulate tab and choose Configure Analysis. Select DC Analysis and press OK to apply 
   the .op command. Then choose Run in the tab to see the DC operating point, including Vout and Id.
6. AC Analysis - Go to Spice Directive and set the library file path. In the Simulate tab, choose Configure Analysis option, then AC Analysis. Set the sweep to 
   Decade, points to 20, and frequency from 0.1 Hz to 1 THz, then choose OK. Finally, choose Run to analyze gain and frequency response.                            9. Transiet Analysis - In the Voltage Source settings, go to the Advanced menu and set a sine wave input with Vgs = 0.9V, an amplitude of 50mV, and a frequency of 
   1kHz.In the Simulate tab choose Configure Analysis select Transient Analysis set the stop time to 5m and choose OK (.tran 5m). Finally choose Run to observe the 
   circuit’s response to a time-varying signal.

# Circuit 01 
  ![Screenshot 2025-02-17 010113](https://github.com/user-attachments/assets/4c03dc99-a315-44dd-81d2-eeb03ddcf597)

   
