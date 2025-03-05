## MOSFET DIFFERENTIAL PAIR AMPLIFIER CIRCUITS 
### AIM 
To design and analyze MOSFET differential amplifier for the following specification P <= 2.2mW, Vdd = 1.8V, Vicm = 0.95V, Vocm = 1.1V and Vp = 0.4V
To perform DC, AC, Transient and Frequency Response Analysis and extract parameters like Gain, quiescent point (Q point), maximum and minimum input and output 
voltage swing. 
### COMPONENTS NEEDED 
Identical PMOSET and NMOSFETs, Identical Resistors Rd, Resistor Rss and DC voltage sources 
### THEORY 
- MOS differential pair is the fourth fundamental amplifier topology.
- It is less sensitive to noise and interference compared to single transistor amplifier, it is well suited for DC coupled multistage designs.
- It rejects common mode input signals and amplifies only the differential signals, These citcuits are used in Operational Amplifiers & Mixed-Signal Circuits.
- The circuit consists of two MOSFETs with their sources connected together and biased by a current source (or a resistor in simpler designs) or Mosfet as load 
  instead of resistor/current source
- A current source at the source terminal provides a constant tail current which splits between the two transistors based on the differential input voltage. This 
  improves symmetry and gain stability
### KEY PARAMETERS 
- Input Common-Mode Range : The voltage range over which the differential pair amplifier circuit functions properly.
- Differential Gain : Determines the amplification of the differential signal.
- Input & Output Swing: Maximum and minimum voltages the amplifier can handle without distortion.
- Common-Mode Rejection Ratio (CMRR): A high CMRR ensures better noise rejection.

### PROCEDURE  
1. Create a folder named LTSpice in your PC/Laptop and save all the ltspice files in this folder.
2. Download the TSMC library datasheet from a reliable online source and place it in the directory where LTSpice is installed.
3. Open a new schematic in LTSpice and name it "MOS Differential Amplifier Ckt". Construct the required circuit and rename the MOSFETs as CMOSN (for nmos) and 
   CMOSP (for pmos). For the CMOSN transistor, set the channel length to 200nm and the channel width to 120.29um , give the values for resistors Rd1, Rd2 and Rss 
   based on calculated value
4. Under the "Simulate" option select "Configure Analysis", then choose the appropriate analysis mode (DC, AC, or Transient analysis) based on the circuit 
   requirements. Configure the necessary parameters and run the simulation to observe the circuit's behavior.
5. DC Analysis - Apply the DC voltage of Vdd = 1.8V and Vgs = 0.95V , Go to the Simulate tab and choose Configure Analysis. Select DC Analysis and press OK to 
   apply the .op command. Then choose Run in the tab to see the DC operating point, including Vout and Id.
6. AC Analysis - Go to Spice Directive and set the library file path. In the Simulate tab, choose Configure Analysis option, then AC Analysis. Set the sweep to 
   Decade, points to 20, and frequency from 0.1 Hz to 1 THz, then choose OK. Finally, choose Run to analyze gain and frequency response.     
7. Transiet Analysis - In the Voltage Source settings, go to the Advanced menu and set a sine wave input with Vg = 0.95V, an amplitude of 50mV, and a frequency of 1kHz.In the Simulate tab choose Configure Analysis select Transient Analysis set the stop time to 5m and choose OK (.tran 5m). Finally choose Run to observe the circuit’s response to a time-varying signal.

##### MOSFET DIFFERENTIAL PAIR AMPLIFIER CIRCUIT DIAGRAM 
   <img src= "https://github.com/user-attachments/assets/2fe91466-6337-4ecd-b508-a1f53d9e014c" width = "300" height = "200">

##### CALCULATIONS 
<img src= "" width = "400" height = "250">

### CIRCUIT 01 
   <img src= "https://github.com/user-attachments/assets/cb563cc9-5bec-4f87-b549-3c7307f3e497" width = "600" height = "500">


### DC ANALYSIS
Go to the Simulate tab and choose Configure Analysis. Select DC Analysis and press OK to apply the .op command. Then choose Run in the tab to see the DC operating poin. By varying the W and L values in the circuit, we can obtain the required operating point for the MOSFET. In this circuit, I have chosen W = 120.29 µm and L = 200 nm.
  
   <img src= "https://github.com/user-attachments/assets/59dc9f46-e61b-45f8-a455-cafd7a1808a7" width = "600" height = "450">
                                  
                              Id1 = Id2 => 6.109mA , Vocm1 = Vocm2 => 1.1001V 
                              Operating point of NMOSFETS = (1.1001 V, 6.109mA)
### TRANSIENT ANALYSIS 
In the Simulate tab choose Configure Analysis select Transient Analysis set the stop time to 5m and choose OK (.tran 5m). Finally choose Run to observe the circuit’s response to a time-varying signal.

   <img src= "https://github.com/user-attachments/assets/210ba4d4-fe14-414b-930c-2a0cf1bf8262" width = "600" height = "450">
 
 There is a 180 degree phase shift between input and output signal as expected. 
 
                              Voltage Gain = Vop-p/Vip-p ; (1.1717-1.0284 )/0.1 ; 1.433V/V 
                              Voltage Gain in dB = 20*log[1.433] => 3.12 dB
### AC ANALYSIS
In the Simulate tab, choose Configure Analysis option, then AC Analysis. Set the sweep to Decade, points to 20, and frequency from 0.1 Hz to 1 THz, then choose OK. Finally, choose Run to analyze gain and frequency response.
<img src= "https://github.com/user-attachments/assets/745189a7-cf42-405e-ada4-aa33c44a60ba" width = "600" height = "450">


