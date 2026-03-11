# Functional Specification

## Temperature Monitoring

The controller should continuously read temperature data from the inverter and DC-DC controller 
sensors and calculate the colling demand.

## Pump Control

The coolant pump speed should be adjusted according to inverter temperature:

| Temperature Range | Pump Speed |
| --- | --- |
| <40°C | OFF |
| 40-60°C | 30-60% |
| 60-75°C | 60-80% |
| 75-85°C | 80-100% |
| >85°C | 100% + Alarm |
| >90°C | System Shutdown |

## Fan Control

The Fan speed should be adjusted according to coolant temperature: 

IF COOLANT TEMPERATURE >60°C OR INVERTER TEMPERATURE >70°C OR DC-DC CONVERTER > 70°C THEN
    FAN := TRUE;

END_IF;

## Coolant Level

If coolant level falls below the given threshold; the system should be;

| Coolant Level | Pump Status | System Status |
| --- | --- | --- |
| >50% | ON | ON |
| 20-50% | ON | Low Level Warning |
| <20% | OFF | Low Level Fault |

## High and Low Pressure Filter

If both filter clogged, then the system should:

| High Pressure Filter | Low Pressure Filter | Pump Status | System Status |
| --- | --- | --- | --- |
| OK | OK | ON | Normal |
| NOT OK | OK | OFF | High Pressure Filter Fault |
| OK | NOT OK | OFF | Low Pressure Filter Fault |
| NOT OK | NOT OK | OFF | Critical Pressure Filter Fault |

## Alarm / Buzzer

If coolant temperature exceeds 90°C then buzzer should ON

## Display Interface

The display should provide the following information:
• Inverter Temperature
• Dc-DC converter Temperature
• Coolant Level
• Coolant Temperature
• Fan status (Speed %)
• Pump Status (Speed%)
• Filters status (Clogged or Not)
• E-stop Status (Pressed) 

## Watchdog / Controller Safety

The controller shall include a watchdog timer to reset the system in case of firmware malfunction.

## Sensor Plausibility

The system shall detect invalid sensor values.
