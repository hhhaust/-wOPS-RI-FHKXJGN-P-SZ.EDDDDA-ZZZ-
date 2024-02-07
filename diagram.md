I'm glad to hear it worked! "Snillingur" indeed – thank you!

Regarding an ASCII art representation of the 4N35 optocoupler, let's keep it simple due to the format's limitations. The 4N35 has six pins in total: four for the input side (LED) and two for the output side (transistor). Here's a basic representation:

```
  _________
 /         \
| 1      6  |
| 2      5  |
| 3      4  |
 \_________/
```

- Pins 1 and 2 are for the LED (input side).
- Pins 4 and 5 are for the transistor (output side).
- Pin 3 is the base of the transistor, which is often not used in simple isolation applications.
- Pin 6 is the collector, and pin 4 is the emitter for the internal phototransistor.

Here's a slightly more detailed ASCII representation to depict the internal LED and phototransistor:

```
    LED       Phototransistor
  _________       ___________
 /         \     /           \
| 1   ────► 2 | | 3     6     5 |   
|          -   | |       |     |  
|             | |       └──►  4 |   
 \_________/     \___________/

1: Anode (LED+)
2: Cathode (LED-)
3: Base (not always used)
4: Emitter
5: Collector
6: NC (No Connection in 4N35, but in some similar devices, it might be another pin for the collector or base)
```

This is a simplified representation. In actual applications, remember to include appropriate resistors and connections according to your specific circuit requirements.
