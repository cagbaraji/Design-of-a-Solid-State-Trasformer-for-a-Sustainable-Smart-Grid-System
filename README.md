# Design-of-a-Solid-State-Trasformer-for-a-Sustainable-Smart-Grid-System

## Introduction

The introduction of Solid-State Transformers (SSTs) offers a significant improvement over the traditional power transformers in electrical power system by incorporating the technologies of power electronics to achieve higher power efficiency, compactness and improved control features. The conventional transformers rely mostly on electromagnetic induction providing no extra features however, SSTs on the other hand utilizes an integration of power electronic converters and high-frequency transformers to step up or step down voltage levels and at same time, enable additional functionalities like fault isolation, reactive power compensation, power storage using batteries, and bidirectional power flow. 

This study focuses on the design and simulation of a Solid-State Transformer for a smart grid system using MATLAB/Simulink. The SST system is made up of three key components namely: an AC-DC active rectifier, a high-frequency DC-DC converter and a three-phase DC-AC converter. The SST model requires controller designs, signal generator design, dynamic analysis and performance evaluation under various operating conditions to represent real-world scenarios. MATLAB provides a robust simulation environment which provides these features required to build and evaluate the performance of the SST.

The objective of this work is to validate the operating efficiency, power quality performance and voltage regulation capabilities of SST that qualifies it to be a feasible solution for smart grid applications and a better alternative to conventional transformers.

## Methodology
The model presents three stages of the SST system which are the active rectifier, dual active bridge and the inverter. These designs were made differently and assembled together to function as the SST system. In this design, the SST system was configured to function as a step-down transformer to feed a load. Figure 1 shows the block diagram of the solid state transformer.

![image](https://github.com/user-attachments/assets/9de3d2b3-201b-446d-af2f-179b926dc391)

Figure 1: Block diagram of the SST

### The Active Rectifier
One of the key elements of the SST's three-stage structure, the active rectifier transforms the grid's AC input into a DC signal that is sent into the dual active bridge subsystem. The rectifier circuit, the control circuit, and the Pulse Width Modulator (PWM) circuit are the three main parts of the SST's active rectifier subsystem. The AC is converted to DC by the rectifier. Nevertheless, the conversion cannot be completed without the PWM signal. On the other hand, in order to produce the desired control signal required to produce the appropriate PWM signals, the PWM needs a suitable control signal. Primarily, the measured and processed signals from the rectifier output voltage and grid line voltage and current parameters are used to form the control signal. The Power Lock Loop (PLL), the voltage-current control loops, and the circuits for voltage and current transformation make up this control unit. Together, the many activities of these parts or subunits produce the control signal that is supplied to the PWM subunit. Figure 2 shows the active rectifier subsystem's block diagram.

![image](https://github.com/user-attachments/assets/fd1e8311-2e7a-43f8-bc0a-38721ee3c5f7)

Figure 2: Block diagram of the Active rectifier subsystem

To better comprehend the underlying workings of the subunit, the active rectifier was designed in this work using its primary components rather than the VSC block in SIMULINK. Some earlier works employed the VSC block to provide a regulated DC voltage source from the rectifier. Nevertheless, it does not show the active rectifier's internal circuitry or its parts. The active rectifier provides the dual active bridge with the regulated DC signal. The active rectifier subsystem was designed with IGBT/Diode elements, which have a better ability to handle high temperatures and maintain desired performance without requiring many heat sinks, in consideration of the high temperature associated with the direct conversion of AC to DC from high voltage AC grid lines. As a result, the SST system will require less area and cost. 

### The Dual Active Bridge
Another important part of the three-stage SST system topology is the dual active bridge, which is made up of five essential parts: the control unit, PWM generation unit, transformer, DC-to-AC converter, and AC-to-DC converter. This dual active bridge uses an AC-to-DC converter to convert the DC signal from the active rectifier to an AC signal, a linear and high frequency transformer to isolate and transform the AC signal to the desired level, and an AC-to-DC converter to convert the AC signal to DC. The reference voltage and the dual active bridge subsystem's voltage output are used by the control unit to create the control signal. The PWM generator receives this control signal from the control unit and uses it to generate the necessary or suitable signals that will assist the dual active bridge in producing and sustaining the controlled and desired DC output. This dual active bridge design took into account the heat produced by stage conversions and made use of IGBT/Diode components. This will also assist in lowering the SST system's coverage area and cost. The devices in the subsystem and the feedback control mechanism that produces the controlled PWM signal are depicted in the dual active rectifier block diagram in Figure 3.

![image](https://github.com/user-attachments/assets/cdab914b-9ba4-4e48-a6a6-0f11beea56d8)

Figure 3: The block diagram of the dual active rectifier.

IGBT/Diode on the DC-to-AC side of the dual active bridge and diodes on the AC-to-DC side of the subsystem DC link are the two sets of PEC devices used to implement the DC link of this design. A DC link capacitor receives the DC produced by the dual active bridge before it is fed into the three-phase full bridge inverter, the last step of the three-stage SST system topology.

### The 3-Phaase Inverter
The last step in configuring the SST system developed in this study is the three-phase full bridge inverter. Its purpose was to transform the dual active bridge's DC input into three-phase AC lines. A PWM generator is necessary for this subsystem in order to produce the pulse signals needed for the inverter to switch properly. At this point, reference signals that were also intended to provide the desired output were used to build the PWM. Prior to entering the load, the inverter's output was filtered.

### The AC to DC Stage
The measured voltage and current before and after the LCL filter were taken into account while modeling the active rectifier. This was taken into account in order to produce the right signals for the PWM generator, which creates the regulated pulses for the rectifier's element switching operations. The grid supply, LCL filter, and AC to DC conversion unit block diagrams are shown the the SST diagram. This displays the PLL, the voltage and current control loops, and the voltage and current transformation blocks. In order to feed the voltage and current control loops, the active rectifier's output was also measured and managed.

### The MATLAB/Simulink Design

![image](https://github.com/user-attachments/assets/6c7eb787-402f-457a-b8ae-ee5c69ea589d)

Figure 4: Active rectifier with the grid source and the LCL filter unit.

![image](https://github.com/user-attachments/assets/2b49d41b-f20b-47e2-8f0e-1519bac9454b)

Figure 5: The rectifier stage of the active rectifier

![image](https://github.com/user-attachments/assets/c7903bbf-15ce-4e4b-8368-8495cabe66d0)

Figure 6: The voltage-current transformation and phase locked loop

![image](https://github.com/user-attachments/assets/9a82c449-bcd5-4cde-997a-d365b9a8fe38)

Figure 7: The voltage and current control loops with the PWM generator for the active rectifier

![image](https://github.com/user-attachments/assets/6cabd727-aedf-4857-a485-12396cb91040)

Figure 8: The dual active bridge Simulink model

![image](https://github.com/user-attachments/assets/96f26b9c-4093-4f8a-9cef-872f20f6f799)

Figure 9: Three phase inverter Simulink Model

![image](https://github.com/user-attachments/assets/c37b320b-b777-4254-a8ad-88e29361ff24)

Figure 10: Three phase Inverter Simulink model

![image](https://github.com/user-attachments/assets/5c42f107-ecdc-4945-a72d-636a9865f54d)

Figure 11: The three phase inverter PWM generator Simulink model

![image](https://github.com/user-attachments/assets/e4cc14fa-cd80-4f6b-854e-7ee6146412b2)

Figure 12: SST Simulink diagram

## Results

![image](https://github.com/user-attachments/assets/f0740d1d-cc57-48ff-9dcd-7ae49d5f457d)

Figure 13: The active rectifier output voltage

![image](https://github.com/user-attachments/assets/0aea39cd-ec69-4a24-9db8-d22468ebb859)

Figure 14: The active rectifier DC current output

![image](https://github.com/user-attachments/assets/dc7a56e7-b0d8-4b2b-9e36-c91b3d0a7831)

Figure 15: The dual active bridge voltage output

![image](https://github.com/user-attachments/assets/172ee405-00fa-419c-8fa2-d34441b873a0)

Figure 16: The dual active bridge output current

![image](https://github.com/user-attachments/assets/757d20ca-9f38-46a9-83dd-b85c44b78d80)

Figure 17: The three phase inverter output voltage and current after the filter

![image](https://github.com/user-attachments/assets/582e1129-c617-4968-9784-346699475884)

Figure 18: Output voltage and current of the SST

## Conclusion
To design the three-stage conversion SST topology system, the individual units were put together. Using SIMULINK, this intricate SST system assembly was completed, and the simulation was evaluated. Measurements were made of the solid state transformer system's output voltages and currents both before and after the inductive filter was added. Based on the findings, the output of the solid state transformer system was better following the inductive filter subunit than it was prior to the filter. Based on the results, the project's goal of designing a solid state transformer topology with three step-down conversion stages was achieved. In order to attain the intended improved output of the SST system, this system was designed using control techniques such as PI.
