# Nasym Worklog

- [Nasym Worklog](#nasym-worklog)
- [2025-02-07 - Testing Triboelectric Pressure Sensor](#2025-02-07---testing-triboelectric-pressure-sensor)

# 2025-02-07 - Testing Triboelectric Pressure Sensor 

Professor Hernandez showed us how to measure the voltage of the pressure sensor. We tested out a couple different sensors to find the voltage range upon loading. We were unable to measure the full range as the sensor exceeded the &pm;10V range of the system, resulting in clipping. 

However, we were able to make two meaningful observations:

First, the sensor has a "break-in" period. If the user uses the sensor after it sits idle for ~30 seconds, the readings increase over the next few steps. Hopefully, in the future we can use a PCB to lower the range. Then after further testing we can determine whether there is usable data to distinguish load amount. Then, ideally we adjust for this "break-in" error using software.

Second, we observed a significant amount of noise. We observed a response when the wires were bumped and there was no loading. This means we will need to package the sensor and wiring so it is protected from external noise.


