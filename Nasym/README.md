# Nasym Worklog

- [Nasym Worklog](#nasym-worklog)
- [2025-02-07 - Testing Triboelectric Pressure Sensor](#2025-02-07---testing-triboelectric-pressure-sensor)
- [2025-02-22 - Further Testing of Pressure Sensor and Voltage Divider](#2025-02-22---further-testing-of-pressure-sensor-and-voltage-divider)
- [2025-04-10 - Testing Bluetooth Latency](#2025-04-10---testing-bluetooth-latency)

# 2025-02-07 - Testing Triboelectric Pressure Sensor 

Professor Hernandez showed us how to measure the voltage of the pressure sensor. We tested out a couple different sensors to find the voltage range upon loading. We were unable to measure the full range as the sensor exceeded the &pm;10V range of the system, resulting in clipping. 

However, we were able to make two meaningful observations:

First, the sensor has a "break-in" period. If the user uses the sensor after it sits idle for ~30 seconds, the readings increase over the next few steps. Hopefully, in the future we can use a PCB to lower the range. Then after further testing we can determine whether there is usable data to distinguish load amount. Then, ideally we adjust for this "break-in" error using software.

Second, we observed a significant amount of noise. We observed a response when the wires were bumped and there was no loading. This means we will need to package the sensor and wiring so it is protected from external noise.


# 2025-02-22 - Further Testing of Pressure Sensor and Voltage Divider

The aim of this meeting was to determine the max voltage and normal voltage range of the pressure sensor. This would allow us to create a voltage divider for the ADC to recieve voltage within its input range. 

The first setup was simply an oscilliscope hooked directly to the sensor. The sensor was placed on the ground so we could step on it. Under heavy load, the sensor reached a max voltage of 70 V. Under normal load it usually stayed around 10-20 V. 

Next, we tested our voltage divider. We measured the voltage at the sensor with one channel of the oscilliscope and used another channel to measure the divided voltage. With this setup, we could never get both channels to read simaltaneously: only one would work at a time. However, just by observing the voltage after the divider, it seemed to be about the same as without, so we hypothesized that it did not work correctly. We then tested using two different oscilliscopes and replacing the sensor with a wave function generator. The voltage was divided correctly in this setup. Due to these results, we determined that the sensor needs one voltage divider for each terminal because it works on differential. 


# 2025-04-10 - Testing Bluetooth Latency 

Each ESP32 is structured as a BLE server. A laptop running a web app is the BLE client. To start collecting data, both servers are sent a start command from the client. The original hope was that the time at which the BLE servers recieve the signals is approximately the same (<12ms as described in high-level requirements). To test the latency, I conected a button to both the ESP32's. Each ESP32 starts a timer when the start command is sent and sends the time at which the button is clicked. Across about 30 tests, the latency was observed to be 6-30ms. This means we will need to create a synchronization feature.

To do this, we will attach a wire to each ESP32 that is connected to a IO pin and ground. There will be a button on one of the ESP32's that when pressed, connects the ground and IO pin. The web app will tell the user to connect the ESP32's together using the wires mentioned and click the button. Once the button is clicked, the ESP32's will start the timer. This will ensure that they are synchronized almost exactly.