# Sewage Monitoring System

This project is designed to monitor the flow rate and volume of sewage using a flow sensor, and display the data on an LCD. It also includes a **buzzer** to alert when the sewage level exceeds a certain threshold. The system uses an **interrupt-driven flow sensor** to measure the flow rate and calculate the sewage volume over time.

### Features:
- **Flow sensor** to measure the flow rate in liters per minute (L/min).
- **LCD display** to show the flow rate and total volume of sewage.
- **Buzzer** to alert when the sensor detects a flow or when conditions are met.
- Real-time monitoring with data displayed every second.

### Components Used:
- **Flow Sensor**: Measures the flow rate of sewage.
- **Buzzer**: Alerts when flow conditions are met.
- **LCD Display (20x4)**: Shows flow rate and volume.
- **Arduino Board** (e.g., Arduino Uno).

### Circuit Connections:
1. **Flow Sensor** connected to pin **2** (input with interrupt).
2. **Buzzer** connected to pin **7**.
3. **Analog Input Pin** connected to the analog sensor to measure sewage content.
4. **LCD** connected via I2C (using pins **SDA** and **SCL**).

### Code Overview:
- **Flow Measurement**: The flow sensor sends pulses, which are counted by an interrupt function. The number of pulses is used to calculate the flow rate (in liters per minute).
- **LCD Display**: The flow rate and total volume of sewage are displayed on a 20x4 LCD screen. The flow rate is updated every second.
- **Buzzer Alert**: The buzzer will sound for 5 seconds if the flow sensor reads a specific value.
- **Sewage Volume Calculation**: The code calculates the total volume of sewage by accumulating the flow rate over time.

### Setup Instructions:
1. **Hardware Setup**: 
   - Connect the flow sensor to pin 2 and the buzzer to pin 7 of the Arduino.
   - Connect the LCD via I2C to the SDA and SCL pins of the Arduino.
   - Use the analog pin A0 for the sewage content sensor.
   
2. **Install Arduino IDE**: 
   - Download and install the **Arduino IDE** if you haven't already.
   
3. **Upload Code**: 
   - Open the Arduino IDE, paste the provided code, and upload it to the Arduino.

4. **Monitor System**: 
   - Open the Serial Monitor to observe the real-time flow rate and sewage volume.
   - The LCD will display the flow rate in liters per minute (L/M) and the total volume (in liters).
   - The buzzer will sound briefly if flow is detected.

### Code Functionality:
- **Flow Measurement**: 
   - The flow sensor generates pulses, and the interrupt function (`flow()`) counts these pulses. The flow rate is calculated using the formula:
     \[
     \text{Flow Rate} = \frac{\text{Flow Frequency}}{7.5}
     \]
     This gives the flow rate in liters per minute (L/min).

- **LCD Display**:
   - The LCD shows the **flow rate** and **total volume**. Every second, the system updates the display with the new values.
   - The flow rate is calculated in liters per second and displayed in L/min and the accumulated volume in liters.

- **Buzzer**: 
   - If the sewage content sensor reads a certain value (greater than 512), the **buzzer** is activated for 5 seconds.
   
- **Flow Calculation Reset**:
   - After every second, the flow rate is reset to allow accurate measurements of subsequent flow.

### Flow Sensor Logic:
- The **interrupt** function increases the flow frequency every time a pulse is detected from the flow sensor.
- The flow rate is calculated based on these pulses and displayed on the LCD.
- Every minute, the flow rate is used to calculate the total sewage volume.

### Notes:
- **Sensor Calibration**: The flow sensor might need calibration for different flow rates, depending on the specific sensor used.
- **LCD Display**: The system uses a **20x4 LCD** to display real-time data. Ensure your LCD is connected correctly via the I2C interface.
- **Threshold Value**: The sensor threshold for triggering the buzzer is currently set at 512. Adjust this value according to your sensor's specifications or system requirements.

### Example Output:
- **Serial Monitor**:
- Sensor = 200 Rate: 5 L/M Vol: 12 L
  
- **LCD**:
- Line 1: Rate: **5 L/M**
- Line 2: Vol: **12 L**

### License:
This project is open-source and available under the [MIT License](LICENSE).
