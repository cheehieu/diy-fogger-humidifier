# diy-fogger-humidifier

![assembled_full_view](https://user-images.githubusercontent.com/1174029/75936687-7ca3fe80-5e48-11ea-8f94-96d295f9af78.jpg)

I needed a humidifer to maintain the humidity inside my indoor walk-in greenhouse. It was primarily being used as a mushroom fruiting chamber, which required a high relative humidity of over 85%. I found some cheap bedroom humidifer options on Amazon, but they were a bit limited with their tank capacities. Most of the affordable options ranged from 2-6 liters. Since my grow needed such a high humidity, the humidifier would need to be left on for long periods of time and require frequent water tank refills.

So I opted to build my own fogger humidifier. Key areas of focus for this build were a larger tank capacity (18 liters), affordabilty (~$50), and humidifing performance sufficient to maintaining a good distribution of moisture content inside the greenhouse. For reference, this is the [indoor greenhouse](https://smile.amazon.com/gp/product/B00U9RGVWK/) I used.


## Parts List
- [5 Gal Bucket](https://www.lowes.com/pd/United-Solutions-5-Gallon-General-Bucket/1000462835) - $4
- [Bucket Lid](https://www.lowes.com/pd/Encore-Plastics-12-in-Blue-Plastic-Bucket-Lid/3029999) - $2
- [Ultrasonic Fogger](https://smile.amazon.com/gp/product/B00PAK245E/) - $10
- [Fogger Float](https://www.ebay.com/itm/Spare-FLOAT-BUOY-for-1-3-5-9-12-head-disc-ultrasonic-MIST-MAKER-fogger/222170140688) - $10
- [Extension Tubes](https://smile.amazon.com/gp/product/B07VCLR6SZ/) - $13
- [Waterproof Fan](https://smile.amazon.com/gp/product/B07NZS7BN7/) - $10

TOTAL COST: $49


## Build Instructions
This is a pretty simple build. The basic tools that you'll need are a small Phillips-head screwdriver, sharp knife, and packing tape.

1. Cut holes.
![lid_top_view](https://user-images.githubusercontent.com/1174029/76055065-34640980-5f38-11ea-9119-c768bdb1d2ab.jpg)
2. Mount fan.

3. Thread cables. Test electronics.
![thread_cables](https://user-images.githubusercontent.com/1174029/76055067-34fca000-5f38-11ea-9247-3cd65d7d158a.jpg)
4. Close bucket lid.

5. Tape and mount extension tubes.
![mount_extension](https://user-images.githubusercontent.com/1174029/76055078-3928bd80-5f38-11ea-9a4a-4c7d550892d6.jpg)
![mount_tubes](https://user-images.githubusercontent.com/1174029/76055076-38902700-5f38-11ea-8154-6f1a1b2d65f6.jpg)

6. Power on.


## Operation
- Smart Plug
- Humidity Sensor

## Demo
[video, gif]

## Automation
Arduino-controlled mini water pump.
```
/*
  Mini Water Pump Control
  Use a switch and relay to control a mini water pump's ON/OFF state.
  https://smile.amazon.com/gp/product/B07TLRYGT1/
  Connect relay to 5V (VCC, COM) and GND
*/

const int RELAY_PIN = 13;  // (also the LED_BUILTIN pin)
const int SWITCH_PIN = 2;
int switch_state = 0;

void setup() {
  pinMode(RELAY_PIN, OUTPUT);
  pinMode(SWITCH_PIN, INPUT_PULLUP);
}

void loop() {
  // Read the switch state
  switch_state = digitalRead(SWITCH_PIN);

  // Control active-low relay based on switch input
  if (switch_state == HIGH) {
    digitalWrite(RELAY_PIN, LOW); // pump ON
  } else {
    digitalWrite(RELAY_PIN, HIGH);  // pump OFF
  }
}
```
