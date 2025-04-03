## CURRENT MIRROR WITH ACTIVE LOAD CIRCUITS 

### AIM 

To design and analyze the given current mirror circuit with the following specifications:

Voltage Gain (Av) > -10 V/V

Supply Voltage (Vdd) = 1.8V

Power Consumption (P) <= 1mW

Design for 1:1 & 1:2 current ratios, with three cases for channel length (L):

L = 180 nm ; L = 500 nm ; L = 1 μm, maintain same W/L ratios.

### COMPONENTS NEEDED 
Identical PMOSET and NMOSFETs,Current source, Resistor Rss and DC voltage sources.

### THEORY 
A current mirror circuit is used to generate a stable and precise current that remains independent of voltage variations, making it an essential component in analog circuits, especially for biasing amplifiers in integrated circuits (ICs). It ensures uniform current distribution across multiple circuit branches, improving performance and consistency. In such circuits, a MOSFET is used as a load because, when operated in saturation, it behaves as a high-impedance current source, minimizing variations due to voltage fluctuations and providing better stability. Additionally, a current source is preferred over a voltage source as it ensures a constant current supply regardless of changes in voltage, leading to improved gain stability and predictable circuit behavior. This makes current mirrors highly reliable for applications requiring precise current replication.

### PROCEDURE  
1. Create a folder named LTSpice in your PC/Laptop and save all the ltspice files in this folder.
2. Download the TSMC library datasheet from a reliable online source and place it in the directory where LTSpice is installed.
3. Open a new schematic in LTSpice and name it "CurrentMirrorCkt". Construct the required circuit and rename the MOSFETs as CMOSN (for nmos) and 
   CMOSP (for pmos). For the CMOSN transistor, set the channel length to 180nm and the channel width to 3.5 um.
4. Under the "Simulate" option select "Configure Analysis", then choose the appropriate analysis mode (DC, AC, or Transient analysis) based on the circuit 
   requirements. Configure the necessary parameters and run the simulation to observe the circuit's behavior.
5. DC Analysis - Apply the DC voltage of Vdd = 1.8V and Vgs = 0.8V , Go to the Simulate tab and choose Configure Analysis. Select DC Analysis and press OK to 
   apply the .op command. Then choose Run in the tab to see the DC operating point, including Vout and Id.
6. AC Analysis - Go to Spice Directive and set the library file path. In the Simulate tab, choose Configure Analysis option, then AC Analysis. Set the sweep to 
   Decade, points to 10, and frequency from 1 Hz to 1000 GHz, then choose OK. Finally, choose Run to analyze gain and frequency response.     
7. Transiet Analysis - In the Voltage Source settings, go to the Advanced menu and set a sine wave input with Vg = 0.95V, an amplitude of 50mV, and a frequency of 1kHz.In the Simulate tab choose Configure Analysis select Transient Analysis set the stop time to 5m and choose OK (.tran 5m). Finally choose Run to observe the circuit’s response to a time-varying signal.

### CALCULATIONS 

It = Iref + Ix 

Ix- Current flowing through MOSFET 01 ;  Iref- Value of current source.

It = P/Vdd -> 0.001/1.8 = 0.556mA 

For 1:1 ratio 

Iref = Ix 
Iref = Ix = 0.27mA 

For 1:2 ratio 
Ix = 2*Iref 
Iref = It / 3 -> 0.185mA 
Ix = 0.371mA 
### CIRCUIT DIAGRAM 

   <img src= "https://github.com/user-attachments/assets/22f627de-96a4-4ac4-8124-3803d831cefe" width = "600" height = "500">

### L = 180nm [ 1:1 ratio ]

### DC ANALYSIS

Go to the Simulate tab and choose Configure Analysis. Select DC Analysis and press OK to apply the .op command. Then choose Run in the tab to see the DC operating poin. By varying the W and L values in the circuit, we can obtain the required operating point for the MOSFET. In this circuit, I have chosen W = 10 um & L = 180 nm for identical PMOSFETs and L= 180 nm & W = 3.5 um for active load NMOSFET.
  
   <img src= "https://github.com/user-attachments/assets/890d6b95-95da-4c48-8377-7b2233d399a6" width = "600" height = "450">


                              Id1 = Id2 => 0.276985 mA , Vout = 0.785124 V 
                              

### TRANSIENT ANALYSIS 

In the Simulate tab choose Configure Analysis select Transient Analysis set the stop time to 5m and choose OK (.tran 5m). Finally choose Run to observe the circuit’s response to a time-varying signal.

   <img src= "https://github.com/user-attachments/assets/55ffdd55-8a86-4620-b450-445cca6082f9" width = "800" height = "450">

 There is a 180 degree phase shift between input and output signal as expected. 

 
                              Voltage Gain = Vop-p/Vip-p ; (941.17mV - 632.42mV )/20mV ; 15.4375 V/V 
                              Voltage Gain in dB = 20*log[15.4375] -> 23.772 dB 

### AC ANALYSIS

<img src= "https://github.com/user-attachments/assets/0b0dd4b8-158f-4dfc-80c9-e09707b9b9bb" width = "800" height = "450">



                              Mid band Gain in dB = 23.951 ; Gain = 15.76  V/V

### L = 180nm [ 1:2 ratio ]

### DC ANALYSIS

<img src= "https://github.com/user-attachments/assets/9065ddec-6722-453d-995c-1f9be6380539" width = "600" height = "450">

                              Id1 = 0.367736 mA , Vout = 1.03578 V ; Expected Id value -> 0.371mA 

### TRANSIENT ANALYSIS 

<img src= "https://github.com/user-attachments/assets/83c4db59-8675-42a1-893b-ad073aa48d2e" width = "800" height = "450">

                              Voltage Gain = Vop-p/Vip-p ; (1.1794 V - 888.13 mV )/20mV ; 14.1905 V/V 
                              Voltage Gain in dB = 20*log[14.1905] -> 23.04 dB 
### AC ANALYSIS

<img src= "https://github.com/user-attachments/assets/b2302ff3-0720-4a39-a76d-78c629bfbf4c" width = "800" height = "450">



                              Mid band Gain in dB = 23.20955 ; Gain = 14.47  V/V
                              
