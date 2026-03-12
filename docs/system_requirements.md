# System Requirements

## Operating Modes

The system shall operating using a three position key switch.

| Key Position | Mode | Description |
| --- | --- | --- | --- |
| 0 | OFF | System powered down |
| 1 | INIT/IGNITION | Contollers intialized and sensors are monitored |
| 2 | RUN/ACC | Colling system operates normally |

## Thermal Requirements

1. The system should maintain inverter and DC-DC controller temperature below 85°C during 
normal operation.
2. The system should trigger the warning when temperature exceeds 75°C.
3. The system should initiate emergency cooling when temperature exceeds 90°C.

## Monitoring Requirements

1. The system should continuously monitor the inverter and DC-DC converter temperature.
2. The system should monitor the coolant level in the cooling loop.
3. The system should monitor the coolant temperature in the cooling loop.
4. The system shall monitor the status of the high-pressure and low-pressure filters.

## Control Requirements

1. The system should control the pump speed based on the invert and DC-DC converter 
temperature.
2. The system should control the fan speed based on the colling demand.

## Saftey Requirements

1. The system should shut down when coolant level is below the minimum threshold.
2. The system should shut down the inverter or DC-DC controller if colling system failure is 
detected or it exceeds the rated temperature.
3. The system should shut down if press the E-Stop button. 
4. The system should operate the alarm when temperature exceeds 90°C.

## Communication Requirements

1. The system should communicate system status to the main controller.
2. The system should provide the status information to a user display.

## Power Requirements

1. The system should operate from a 24V DC supply.
2. The sensors and controller electronics should operate from 5V and 3.3V regulated supplies.

## Environmental Requirements

1. The system should operate in ambient temperature from -20°C to 60°C.
2. The system should tolerate the vibration typical of mobile machinery.