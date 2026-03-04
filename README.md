# Design-of-an-Astable-555-Timer-LED-Flasher-and-Modification-of-the-Circuit-to-a-Light-Sensitive-Alarm
This project involves the design and transient analysis of an Astable Multivibrator using the NE555 timer IC. The circuit is designed to generate a continuous square wave pulse to toggle an LED at a specific frequency, simulated using LTspice.

🛠️ Components & Parameters:
The following component values were used to determine the timing and output characteristics:

Timing Resistor (R1): 10K Ohm

Timing Resistor (R2): 100K Ohm

Timing Capacitor (C1): 10 micro Farad

LED Protection Resistor (R3): 330 Ohm

Power Supply (V1): 5V(DC)

🚀 Simulation Procedure : 

1. Schematic entry: The circuit was drafted in LTspice with the NE555 macro.
 
2. Analysis configuration: A Transient Analysis was configured with a Stop Time of 5 seconds to observe multiple oscillation cycles.
  
3. Probing: Current probes were placed on the LED (D1) and the Voltage Source (V1) to analyze input-output state .

 📈 Analysis of Results:

Oscillation: The circuit successfully oscillates with a period of approximately 1.455 seconds per blink.

Output Current: When the output is HIGH, the LED draws approximately 12mA.

Supply Load: The voltage source shows a negative current pulse of -15mA during the "ON" state, accounting for the LED load and IC quiescent current.

Present duty cycle = 52.37 %

We can make the LED blink controllable such that only when the signal comes in the LED blinks by disconnecting the RESET Pin(Pin 4) from VCC rail and connecting it to an external signal.When the signal goes high(5V) the LED goes on and when it is <5V the LED stays off. Thus it can be used as a dummy alarm circuit.

🌙 Smart Feature: Light-Sensitive Activation:

The circuit has been upgraded from a basic flasher to a Light-Sensitive Dummy Alarm. By utilizing a voltage divider connected to the RESET (Pin 4), the system automatically arms itself only when environmental light levels drop.Technical ImplementationVoltage Divider: Composed of a 10k Ohm pull-up resistor (R4) and a Light Dependent Resistor (R5/LDR).

Logic:  Daytime: LDR resistance is low -> Reset pin is LOW -> Timer is disabled.

Nighttime: LDR resistance is high -> Reset pin is HIGH -> Timer begins pulsing.

Simulation Strategy
To verify this behavior, I used a SPICE Parameter Sweep:

.step param Rlight 1k 100k 25k
(Simulations will be generated for five values of R5(from 1K Ohm to 100K Ohm in 25K Ohm increments(including last one 101k ohm))

Depending on light the resistance(R5) changes

This allowed for the simultaneous analysis of five different light conditions, confirming that the LED only draws current approaximately 13mA when the simulated LDR resistance exceeds the trigger threshold.

🔮 Future Implementations:
1. Hardware implementation.
2. Variable Frequency: Replacing R2 with a potentiometer to allow for adjustable blink rates.
3. PWM Control: Modifying the circuit to act as a Pulse Width Modulation (PWM) generator for DC motor speed control.

 ****AUTHOR****
   
Ananyaa Maity

Indian Institute of Engineering Science and Technology(Shibpur)

B'Tech(Electronics and Telecommunication Engineering)

Interests-Analog and Digital Design ,Embedded Systems




