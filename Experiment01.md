# CS Amplifier 
## Aim : 
1. To Perform DC Analysis, AC Analysis and Transient analysis on CS Amplifier circuit to obtain various circuit parameters like DC operating point, Gain, Bandwidth and Power using LTSpice Simuator.
2. To Perform DC Analysis, AC Analysis and Transient analysis on CS Amplifier circuit with resistor replaced my PMOS and additional voltage source to obtain various circuit parameters like DC operating point, Gain, Bandwidth and Power using LTSpice Simuator.
## Components Required : 
Mosfet(nmos4 & pmos4), Voltage Supply(1.8V & 0.6V), Resistors(1Kohms) and Connecting Wires. 
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
5. DC Analysis - Apply the DC voltage of Vdd = 1.8V and Vgs = 0.6V , Go to the Simulate tab and choose Configure Analysis. Select DC Analysis and press OK to apply 
   the .op command. Then choose Run in the tab to see the DC operating point, including Vout and Id.
6. AC Analysis - Go to Spice Directive and set the library file path. In the Simulate tab, choose Configure Analysis option, then AC Analysis. Set the sweep to 
   Decade, points to 20, and frequency from 0.1 Hz to 1 THz, then choose OK. Finally, choose Run to analyze gain and frequency response.     


7. Transiet Analysis - In the Voltage Source settings, go to the Advanced menu and set a sine wave input with Vgs = 0.6V, an amplitude of 50mV, and a frequency of 1kHz.In the Simulate tab choose Configure Analysis select Transient Analysis set the stop time to 5m and choose OK (.tran 5m). Finally choose Run to observe the circuit’s response to a time-varying signal.

## Circuit 01 :
  <img src= "https://github.com/user-attachments/assets/e5df7d35-3d60-44e4-b528-7da9bfd39b71" width = "1100" height = "500">

## Results :

1. DC Analysis (DC Sweep) 
 
  <img src= "https://github.com/user-attachments/assets/e19f1e87-5857-470b-b141-74436ad35724" width = "1100" height = "500">

       Id = 27.727uA ; Vout = 1.77227V; length of channel L = 180nm; width of channel W = 1.08um ; DC Operating point (1.7727V, 27.727uA)

2. AC Analysis
 
  <img src= "https://github.com/user-attachments/assets/76fec5ea-0c13-4b3d-86cf-c70c06d85c41" width = "1100" height = "300">


  <img src= "https://github.com/user-attachments/assets/c84bd1cc-6c26-46ea-83be-4c5b0f44cf20" width = "1100" height = "300">
 
  Formula to Find gain Av = -gm*Rd 
  
                                                    Gain = -0.316*0.001*1000 ;   Gain = -0.316
                                                    

4. Transient Analysis
 
  <img src= "https://github.com/user-attachments/assets/e8523fe3-4e26-4a37-8b9f-30c2faf6dbaf" width = "1100" height = "300">
  There is a 180 degree phase shift between input and output signal as expected

5. Inference

The drain current increases with MOSFET width and decreases with length. For amplification, the MOSFET must operate in the saturation region, ensuring a stable Q-point and linear gain. The amplifier produces a 180° phase shift to the amplified output signal. Transient analysis helps in understanding time-domain response, while AC analysis aids in frequency response and impedance matching. These factors are crucial for designing efficient amplifiers.

## Circuit 02 : 
A MOSFET in a diode-connected configuration stays in saturation mode and primarily functions as a current source with a stable output. In certain conditions, it can also provide amplification. To study its behavior, DC, AC, and transient analyses are commonly used. The drain current is determined by the equation

                                        Id = 1/2*Kn*Vov^2 ; Kn = W/L*unCox ; Vov = Vgs - Vt  
#### Instead of Resistor of 1K ohm PMOS is used with Gate voltage = [1.8-0.3906 = 1.4094 V] ; Input Gate voltage to NMOS = 0.9V ; VTHO for PMOS = 0.3906

   <img src= "https://github.com/user-attachments/assets/bfbdb18a-e1ca-4265-955a-a94761e942e5" width = "1100" height = "500">




1. DC Analysis (DC Sweep) 

<img src= "https://github.com/user-attachments/assets/666c5457-3cfe-4e4a-80ea-61b1538fd395" width = "1100" height = "500">

       Id = 27.586 uA ;  Vout = 0.0352 V ; length of channel L = 1200 nm; width of channel W = 0.09 um For PMOS ; DC Operating point (0.0352,27.586 )





3. AC Analysis

  <img src= "https://github.com/user-attachments/assets/31b9edbd-7896-4a74-83f4-3043356d738f" width = "1100" height = "300">




4. Transient Analysis


  <img src= "https://github.com/user-attachments/assets/56212689-5e27-46f6-8b38-e5b743e9938a" width = "1100" height = "300">


                                        Gain = Voutp-p / Vinp-p ; Gain = 8.8mV/100mV ; Gain = -0.088



5. Inference

The common-source amplifier with an active load operates effectively as a CMOS inverter. DC analysis verified proper biasing, while AC analysis highlighted its frequency response. Transient analysis confirmed that the circuit amplifies signals with minimal distortion. The results indicate that this design is efficient and provides good gain. This makes it a strong candidate for amplification applications. Additionally, its simplicity and ease of integration make it useful in various circuits.
NMOS : W = 1.08um ; L = 180nm , PMOS : W = 0.09um ; L = 1200nm

Gain for ciruit 01 = -0.316

Gain for circuit 02 = -0.088

power for circuit 01 ; P=V*I= 1.8 * 27.727u == 49.908 uW.

power for circuit 02 ; P=V*I= 1.8 * 27.586u ==  49.6548 uW.

Vb : -1.4094V

Vgs : 0.9V

Vdd : 1.8V

Rd : 1K ohms 

   
