# CMOS-inverter
Static and Dynamic Power Consumption of CMOS inverter
Here, we are using two sources: DC source for performing DC analysis and calculate static power consumption and Pulse source to perform transient analysis and calculate dynamic power consumption. 
1) To analyse static power, first, enable the DC source and assign a variable voltage ‘Vin’ to it. Now sweep the design variable ‘Vin’ from 0 v to 1.8 v. Let the bias voltage ‘vdd’ be 1.8 v. 
<img width="518" height="371" alt="image" src="https://github.com/user-attachments/assets/c19e3b19-1c26-45a9-9b0c-91c80821016b" />

On plotting vin (voltage at input port), vout (voltage at output port) and the current drawn from the bias voltage ’vdd’, we obtain the following waveform.
 <img width="940" height="418" alt="image" src="https://github.com/user-attachments/assets/99bd40bb-f1a4-49c8-995f-523e5578fed2" />

This is the general voltage transfer characteristics of a CMOS inverter. When input voltage: vin = 0 v, output voltage: vout is active high and when vin = 1.8 v, vout is active low. As vin sweeps from 0 to 1.8v, vout switches from high to low. 
The pink curve represents the leakage current or the current that is drawn from the inverter circuit from the bias source. At vin = 0, the NMOS transistor is in OFF state and has a leakage current of 16.942 pA. While at vin = 1.8v, the PMOS transistor is in OFF state and has a leakage current of 54.032 pA.
2) To analyse dynamic power, disable the DC source and enable the pulse source using ‘shift’ + ‘delete’. Let the bias voltage ‘vdd’ be 1.8 v. 
<img width="442" height="415" alt="image" src="https://github.com/user-attachments/assets/8410bd54-8ecc-4fd3-a9d0-ebef5cdd0da3" />

On plotting vin (voltage at input port), vout (voltage at output port), current drawn by the inverter circuit (V1 Minus), current entering  source of PMOS ‘PM0/S’ and current entering drain of NMOS ‘NM0/D’, we get the below waveform:
 <img width="940" height="441" alt="image" src="https://github.com/user-attachments/assets/59acd03c-2233-46c0-8de6-e4a26a002ab8" />

From the waveform, it is clear that during the rising edge of the output, the PMOS draws current from supply and during the falling edge of the output, the NMOS draws current from supply. To calculate dynamic power, take average of the current drawn by the inverter circuit i.e. ‘V1/MINUS’ and multiply it with the supply voltage vdd. On doing this, I got value of dynamic power consumed as 53.28 uW.

3) Power Dissipation of Inverter Circuit
To calculate power dissipation, we need to perform transient analysis. Before running the analysis, remember to save all signals and power signals to output. Once the vin and vout waveforms are obtained, we need to click on ‘Browser’ followed by ‘Open Results’ and open the ‘psf’ file. All the available signals would be displayed in the browser and on clicking the pwr signals of NM0,PM0 we get their waveforms and on sending them to calculator, we can fetch their average values. 
Using this method, we can find the average power dissipated by the overall circuit as well as the individual transistors
 <img width="940" height="441" alt="image" src="https://github.com/user-attachments/assets/0a67ba86-159a-4de4-b394-613d712ff60a" />

Power dissipated by PMOS is: 572.5 nW
Power dissipated by NMOS is: 857 nW
Total power dissipated: 1.429 mW
