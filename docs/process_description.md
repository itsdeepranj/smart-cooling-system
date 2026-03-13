# Process_Description

## Initialize Controllers

### Purpose 

Start the main the controller and other controllers connected by communication line.
Also main controller will check E-stop status before moving to next step

### Input 

1. Pwr Signal input to the main controller
2. Pwr signla input to Power Inverter and DC-DC converter controllers
3. Read the Data from sensors ( Temperature, Coolant Level, Filter status)

### Processing 

1. Process the E-stop status , if e-stop pressed , it will trigeer the Battery cut off contactor coil
2. Establish the communication between the controllers
3. Initialize the MCU peripheral
4. Initialize the ADC channel
5. Initialize the display


### Output

1. Operate the E-stop contactors

## Validate Sensor Inputs

In this process the main controller read the data from peripheral and validate the sensor data with the given refrance value.

### Sensor Input

1. Read data from temperature sensors 
2. Read data from Level sensor 
3. Read data from filter 

### Process Output 

1. Validate the sensor inputs
2. Triger the fault state if sensor input is faulty

### Compute Cooling Demand

Determine the required cooling capacity based on the thermal state of the inverter and DC-DC converter.

### Inputs

* Inverter Temperature
* DC-DC Converter Temperature
* Coolant Temperature

### Cooling Demand Processing Steps

1. Compare Coolant , inverter and DC-DC converter temperature with warning threshold (75°C).
2. Compare Coolant,  inverter and DC-DC converter temperature with critical threshold (85°C).
3. Determine cooling demand level.
4. Calculate pump speed percentage.
5. Calculate fan speed percentage.

### Cooling Outputs

* Pump Speed Command
* Fan Speed Command

### Pump Control

Control coolant pump speed to regulate coolant circulation.

### Pump Control Inputs

* Cooling Demand Level
* Fault Status

### Processing Steps

1. If system state is RUN, calculate pump speed.
2. If cooling demand is low, set pump speed to minimum.
3. If cooling demand is high, increase pump speed.
4. If system enters fault state, stop the pump.

### Pump Control Outputs

* Pump Speed CAN Singal to Pump Controller

### Fan Control

Regulate cooling fan speed to improve heat dissipation through the radiator.

#### Fan Inputs

* Coolant Temperature
* Cooling Demand

### Fan Processing Steps

1. Monitor coolant temperature.
2. If coolant temperature exceeds threshold, start fan.
3. Adjust fan speed proportionally to temperature.
4. Stop fan if cooling demand is low.

### Fan Outputs

* Fan Speed PWM Signal ( PI Conrroller)

## System fault 

system will identify the fault and hold the operation partially or fully depends on the type of fault

### System Fault Input

1. Medium Level (20-50%) / Low Level of coolant in the tank ( <20%>).
2. Critical High temperate of coolant, Inverter and DC- DC converter( >85°C).
3. Filter clogged ( either of any filter clogged).
4. Sensors wires short or cut ( Short circuit or open circuit faut).
5. Pump Malfunction. 
6. Fan stopped.

### System Fault Outputs

1. For moderate fault system will work 
2. For critical fault system will stop