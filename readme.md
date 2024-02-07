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
