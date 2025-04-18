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
   Decade, points to 10, and frequency from 1 Hz to 1000 GHz, then choose OK. Finally, choose Run to analyze gain and frequency response.     
7. Transiet Analysis - In the Voltage Source settings, go to the Advanced menu and set a sine wave input with Vg = 0.95V, an amplitude of 50mV, and a frequency of 1kHz.In the Simulate tab choose Configure Analysis select Transient Analysis set the stop time to 5m and choose OK (.tran 5m). Finally choose Run to observe the circuit’s response to a time-varying signal.

##### MOSFET DIFFERENTIAL PAIR AMPLIFIER CIRCUIT DIAGRAM 
   <img src= "https://github.com/user-attachments/assets/2fe91466-6337-4ecd-b508-a1f53d9e014c" width = "300" height = "200">

##### CALCULATIONS 
<img src= "https://github.com/user-attachments/assets/43f3587c-e1ac-458c-b01d-159e27bbed18" width = "700" height = "600">


### CIRCUIT 01 
   <img src= "https://github.com/user-attachments/assets/cb563cc9-5bec-4f87-b549-3c7307f3e497" width = "600" height = "500">
  
   <img src= "https://github.com/user-attachments/assets/80b29cff-b01b-4e9f-a75d-1f3f541104cb" width = "600" height = "500">


### DC ANALYSIS
Go to the Simulate tab and choose Configure Analysis. Select DC Analysis and press OK to apply the .op command. Then choose Run in the tab to see the DC operating poin. By varying the W and L values in the circuit, we can obtain the required operating point for the MOSFET. In this circuit, I have chosen W = 120.29 µm and L = 200 nm.
  
   <img src= "https://github.com/user-attachments/assets/59dc9f46-e61b-45f8-a455-cafd7a1808a7" width = "600" height = "450">
                                  
                              Id1 = Id2 => 0.6109mA , Vocm1 = Vocm2 -> 1.1001V 
                              Operating point of NMOSFETS = (1.1001 V, 0.6109mA)

Maximum and Minimum Common mode input voltage ( Common mode input range )
1. Vicm(max)
 
   from the circuit

   Vd = Vdd - IdRd 

   at the mosfet's triode saturation boundary

   Vds = Vgs - Vt

   Vg = Vd + Vt

   Vicm(max) = Vt + Vdd - IdRd

   Vicm(max) = 0.3226 + 1.8 + 0.611*1.1456

   Vicm(max) = 1.4222
   
3. Vicm(min)

   Vicm(min) = Vgs + Vp 

   Vicm(min) = 0.95

### TRANSIENT ANALYSIS 
In the Simulate tab choose Configure Analysis select Transient Analysis set the stop time to 5m and choose OK (.tran 5m). Finally choose Run to observe the circuit’s response to a time-varying signal.

   <img src= "https://github.com/user-attachments/assets/210ba4d4-fe14-414b-930c-2a0cf1bf8262" width = "600" height = "450">
 
 There is a 180 degree phase shift between input and output signal as expected. 
 
                              Voltage Gain = Vop-p/Vip-p ; (1.1717-1.0284 )/0.1 ; 1.433V/V 
                              Voltage Gain in dB = 20*log[1.433] -> 3.12 dB; Common mode gain
### AC ANALYSIS
In the Simulate tab, choose Configure Analysis option, then AC Analysis. Set the sweep to Decade, points to 20, and frequency from 1 Hz to 1000 GHz, then choose OK. Finally, choose Run to analyze gain and frequency response.
<img src= "https://github.com/user-attachments/assets/745189a7-cf42-405e-ada4-aa33c44a60ba" width = "600" height = "450">
<img src= "https://github.com/user-attachments/assets/47a6b3c4-ef1e-4fb1-866f-34ddaec132a9" width = "600" height = "450">


                              Vid = Vg1 - Vg2 ; 2V
                              differential gain = (Vd1 - Vd2)/ Vid ; (9.817 + 9.817)/2 -> 9.817 V/V 

### CIRCUIT 02  [RESISTOR REPLACED WITH CURRENT SOURCE]
   <img src= "https://github.com/user-attachments/assets/cf1916f6-ecae-4554-8bed-6fa69dc296f7" width = "600" height = "500">

### DC ANALYSIS
W & L is not altered.
  
   <img src= "https://github.com/user-attachments/assets/4ec265ac-157f-4b21-836a-f9a11d58a775" width = "600" height = "450">
                              
                              Id1 = Id2 -> 0.61092mA , Vocm1 = Vocm2 -> 1.10009V 
                              Operating point of NMOSFETS = (1.10009 V, 0.61092mA)
   
### TRANSIENT ANALYSIS 
   <img src= "https://github.com/user-attachments/assets/bdbe1ff2-bcd3-4be0-a780-835b991f9948" width = "600" height = "450">

                              Voltage Gain = Vop-p/Vip-p ; (1.5369-0.0066328)/0.1 ; 8.7362 V/V 
                              Voltage Gain in dB = 20*log[8.7362] -> 18.823 dB

### AC ANALYSIS
<img src= "https://github.com/user-attachments/assets/c7b566b4-82cd-4a3a-b2e7-0239015329b0" width = "600" height = "450">
                              
                              Gain in dB = 19.86 ; Gain = 9.874 V/V

### CIRCUIT 03 [CURRENT SOURCE REPLACED WITH NMOSFET]
   <img src= "https://github.com/user-attachments/assets/f90d863f-777e-4f75-b00a-cb8682be7d19" width = "600" height = "500">


W.K.T

Vds = Vgs - Vt ( Vds = Vp -> 0.4V )

0.4 + 0.36624 = Vg ( since source is grounded )

Vbias -> Vg = 0.76624V ( Bias voltage at the gate for 3rd n type mosfet)

### DC ANALYSIS 
The width and length of the differential pair MOSFETs remain unchanged, while the third MOSFET has a width of 21.69um and a length of 180nm.
 
   <img src= "https://github.com/user-attachments/assets/b0a39c18-aae7-4ff4-9255-fb6e0c5c138e" width = "600" height = "450">
                          
                              Id1 = Id2 => 0.61049mA , Vocm1 = Vocm2 -> 1.10058V 
   
                            Operating point of NMOSFETS = (1.10058 V, 0.61049mA)

1. Vicm(max)

   from the circuit

   Vd = Vdd - IdRd 

   at the mosfet's triode saturation boundary

   Vds = Vgs - Vt

   Vg = Vd + Vt

   Vicm(max) = Vt + Vdd - IdRd

   
3. Vicm(min)

   Vicm(min) = Vgs + Vbias - Vt 

   
### TRANSIENT ANALYSIS 

   <img src= "https://github.com/user-attachments/assets/97925994-02d3-42dd-a5f2-25d30fc25df4" width = "600" height = "450">
                
                              Voltage Gain = Vop-p/Vip-p ; (1.53566-0.006606)/0.1 ; 15.29054 V/V 
                              Voltage Gain in dB = 20*log[15.29054] ->  23.69 dB
### AC ANALYSIS

<img src= "https://github.com/user-attachments/assets/cfe08f55-bf04-4840-865d-11553cebf1a1" width = "600" height = "450">

                              Gain in dB = 19.844 ; Gain = 9.822 V/V

### INFERENCE 
In this experiment, we explored the working principles of a differential amplifier along with its various configurations.
We implemented three distinct configurations—resistor, current source, and NMOS—each operating differently, leading to variations in voltage gain and MOSFET stability

Operating point of Circuit 01 = (1.1001 V, 0.6109mA)

Operating point of Circuit 02 = (1.10009 V, 0.61092mA) 

Operating point of Circuit 03 = (1.10058 V, 0.61049mA)

Gain of circuit 01 =  9.817 V/V 

Gain of circuit 02 = 9.874 V/V

Gain of circuit 03 = 9.822 V/V

The output common-mode voltage (Vocm) remains around 1.1V, aligning well with the design specification.
The bias current (≈ 0.61mA) is stable across all configurations, indicating that the circuit is properly biased.
The resistor load (Circuit 01) provides a gain of 9.817 V/V, influenced by The current source load (Circuit 02) achieves a slightly higher gain of 9.874 V/V, as an ideal current source has a high output impedance, maximizing gain.The NMOS load (Circuit 03) shows a gain of 9.822 V/V, close to the resistor load, due to the active load’s finite output impedance.
This experiment successfully demonstrates how different load configurations impact differential amplifier performance.
