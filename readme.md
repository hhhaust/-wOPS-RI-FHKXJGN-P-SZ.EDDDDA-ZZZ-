Using an ESP8266 development board with labeled pins such as D0, D1, ..., D8, AO (analog), G (Ground), 3.3V, Tx and Rx (serial communication), 5V, and RST (reset): 
When interfacing with an external LED, you can choose one of the digital pins (D0-D8) for output. Note that the actual GPIO number might not directly match the D number printed on the board. For example, D1 usually corresponds to GPIO5 on many ESP8266 boards like the NodeMCU.

### Materials Needed
- External LED
- Resistor (220Ω to 1kΩ)
- Jumper wires

### Circuit Setup
- **LED Anode (longer leg)** to a **Digital Pin** (e.g., D1)
- **LED Cathode (shorter leg)** to one end of the **Resistor**
- The other end of the **Resistor** to **Ground (G)**

### Code Example
If you choose D1 (which might correspond to GPIO5, but you should verify based on your specific board), the code would look like this:

```cpp
#define LED_PIN 5 // For D1 on many ESP8266 boards; adjust as needed

void setup() {
  pinMode(LED_PIN, OUTPUT); // Set the LED pin as an output
}

void loop() {
  digitalWrite(LED_PIN, HIGH); // Turn the LED on
  delay(1000);                 // Wait for one second
  digitalWrite(LED_PIN, LOW);  // Turn the LED off
  delay(1000);                 // Wait for one second
}
```
For the board type in the Arduino IDE 2.2.1, select "Generic ESP8266 Module"

### Steps
1. Assemble your circuit according to the setup above.
2. Copy the provided code into a new sketch in the Arduino IDE.
3. Adjust the `LED_PIN` definition if you're using a different pin (verify the GPIO number for your chosen pin).
4. Select the correct board and port under **Tools** in the Arduino IDE.
5. Upload the sketch to your ESP8266 board.

After uploading, the external LED should blink on and off every second. Adjust the `delay()` function in the code to change the blink speed.

Relay Module
For controlling the relay, only connect the "S" pin to the GPIO 5 (D1)


---


To connect an MPU-6050 sensor to an ESP32 or ESP8266 board and retrieve sensor data, follow these steps. This guide provides a basic idea; adjust it based on your specific requirements.

### Circuit Diagram:

1. **MPU-6050 Pins:**
   - VCC to 3.3V on ESP
   - GND to GND
   - SCL to SCL (GPIO 22 on ESP32, GPIO 5 on ESP8266)
   - SDA to SDA (GPIO 21 on ESP32, GPIO 4 on ESP8266)
   - INT (optional) to any digital pin if you want to use the interrupt feature

2. **ESP32/ESP8266 Pins:** Connect as per the above.

### Script Idea:

1. **Libraries Needed:**
   - For ESP8266/ESP32: `Wire.h` for I2C communication, and an MPU6050 library (like `I2Cdev` and `MPU6050` libraries).

2. **Initialization:**
   - Initialize I2C and the MPU-6050 sensor.

3. **Reading Data:**
   - Read accelerometer and gyroscope values.

4. **Output:**
   - Print values to the Serial Monitor or use them in your application.

### Example Code:

```cpp
#include <Wire.h>
#include <MPU6050.h>

MPU6050 mpu;

void setup() {
  Serial.begin(115200);
  Wire.begin(); // Initialize I2C
  mpu.initialize(); // Initialize MPU-6050
  if (!mpu.testConnection()) {
    Serial.println("MPU6050 connection failed");
    return;
  }
  Serial.println("MPU6050 connection successful");
}

void loop() {
  // Read sensor values
  int16_t ax, ay, az;
  int16_t gx, gy, gz;
  mpu.getMotion6(&ax, &ay, &az, &gx, &gy, &gz);
  
  // Print values
  Serial.print("a/g:\t");
  Serial.print(ax); Serial.print("\t");
  Serial.print(ay); Serial.print("\t");
  Serial.print(az); Serial.print("\t");
  Serial.print(gx); Serial.print("\t");
  Serial.print(gy); Serial.print("\t");
  Serial.println(gz);
  
  delay(500); // Delay for readability
}
```

### Notes:
- Ensure your MPU-6050 and ESP board are powered correctly, and the I2C addresses match.
- The `delay` in the loop is for readability; adjust it based on your needs.
- If using interrupts, additional setup and an interrupt handler function are needed.
- Libraries might require installation via your Arduino IDE's Library Manager.

---

On the ESP8266, the GPIO numbers don't always match the D# labels on some development boards, like the NodeMCU or Wemos D1 Mini. Here's how GPIO 4 and GPIO 5 correspond to the D# labels on these common boards:

- **GPIO 4** is usually labeled as **D2**.
- **GPIO 5** is usually labeled as **D1**.

So, for your MPU-6050 connection:
- Connect SDA to **D2** (GPIO 4).
- Connect SCL to **D1** (GPIO 5).

These mappings can vary slightly depending on the specific ESP8266 board you're using, so it's always a good idea to consult the pinout diagram for your specific model.
