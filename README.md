# Electric Powertrain

## I. Overview
This project focuses on the design of control software for an Electric Powertrain including Contactors Control, Battery Management and Field-Oriented Control. The project also includes modeling of the powertrain for testing of the control algorithms.

## II. Powertrain Modeling
The electric powertrain model can be divided into 3 main parts:
- Contactors & IVTs
- Energy Storage System (Battery)
- Inverter & Motor

### Contactors & IVTs
The contactors connect the battery to the inverter and motor. The ES and CUK IVTs measure the current and voltage at the ES side and inverter/motor side of the contactors respectively.

### Energy Storage System
The energy storage system is modelled with an Equivalent-Circuit Model (ECM) with 2 RC pairs. The State-of-Charge (SoC) is calculated using Coulomb Counting.

### Inverter & Motor
The motor is an Interior Permanent Magnet Synchronous Motor. Blocks from the Simulink Powertrain Blockset are used to model the inverter and motor.

## III. Controller
The powertrain controller can be divided into 4 parts:
- Powertrain State
- Contactors Controller
- Battery Management System
- Field-Oriented Motor Controller

### Powertrain State
The Powertrain State subsystem includes the main powertrain state machine and the logic for state transitions.
The 4 states of the powertrain are:
- Off
- Contactors Close Request
- Contactors Closed
- Torque Control
- Contactors Open Request

### Contactors Controller
The Contactors Controller subsystem handles the logic and sequence for closing and opening contactors. It also controls the precharge and active discharge switches.

### Battery Management System
The Battery Management System (BMS) is reponsible for monitoring and controlling the energy storage system.
Its functionality includes:
- State-of-Charge Estimation
- Current Limits

### Field-Oriented Motor Controller
The Field-Oriented Motor Controller (FOC) is reponsible for executing the torque commands of the motor at the current speed.
Its functionality includes:
- Clarke & Park Forward & Inverse Transformations
- Id & Iq Current Control
- Maximum Torque Per Ampere (MTPA)
- Field Weakening (FW)

## IV. Simulation Models

### Contactors
The **Contactors.slx** model includes contactors and IVTs model as well as the Powertrain State and Contactors controller. It is used to separately test the functionality of closing/opening contactors as well as the state transitions of the powertrain controller.

### Battery Management
The **BatteryManagement.slx** model includes the Battery Management System (BMS) and the Energy Storage System. It is used to separately test the functionality of the BMS.

### Motor Control
The **MotorControl.slx** model includes the Field-Oriented Motor Controller and the inverter and PMSM models. It is used to separately test the FOC functionality.

### Electric Powertrain
The **ElectricPowertrain.slx** model includes the full controller and the full powertrain model. It is used to test all the pieces of the controller and the performance of a full powertrain.