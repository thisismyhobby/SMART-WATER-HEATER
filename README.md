

 How the Code Works

This project uses an ESP32 microcontroller to control a heating system based on real-time temperature readings and a manual switch input. The goal is to automate the heating process while maintaining safety through state-based logic and visual/audio indicators.

 Hardware Behavior Overview

* Temperature Sensor: A DS18B20 waterproof sensor reads the temperature via the OneWire protocol.
* Toggle Switch: When turned ON (HIGH), the system begins monitoring and controlling the heater based on temperature thresholds.
* Relay & Blue LED: The relay module powers the heating coil. A **blue LED** connected in parallel provides a visual indication of the relay’s state and helps confirm relay functionality.
* Indicator LED: Shows when the system is actively heating or stabilizing.
* Buzzer:

  * Sounds once when the switch transitions from OFF to ON to indicate entry into the heating sequence.
  * Also sounds continuously during an overheat condition.
* Serial Monitor : Outputs the current temperature and system state.

State-Based Logic

The system transitions through the following states:

1. IDLE

   * Switch OFF: System idle, no sensor reading taken.
   * Switch ON but temp below threshold: Sensor begins reading, but no heating yet.

2. HEATING

   * Begins when switch is ON and temperature is between defined thresholds.
   * Relay and LED turn ON to power the heater.

3. STABILIZING

   * As temperature nears the target.
   * Note: The stabilizing threshold is equal to the target threshold.

4. TARGET REACHED

   * Heater and LED turn OFF to prevent overshooting.

5. OVERHEAT

   * If temperature exceeds a defined limit, heater and LED are turned OFF, and buzzer sounds continuously for alert.



This system ensures manual control (via switch), automatic regulation (via sensor thresholds), and fail-safe behavior (via buzzer alerts and visual indicators).




