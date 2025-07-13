# SPEECH-RECOGNITION-SYSTEM

*COMPANY*: CODTECH IT SOLUTIONS

*NAME*: SEEPANA MURALIKRISHNA

*INTERN ID*: CT08DF1739

*DOMAIN*: EMBEDDED SYSTEMS

*DURATION*: 8 WEEKS

*MENTOR*: NEELA SANTOSH

# 🗣️ Task 4: Speech Recognition System (Simulated via Serial Monitor)

## 📘 Objective

The objective of this project is to build a **Speech Recognition System** using **Arduino Uno**, where command-based inputs simulate voice commands to control two devices (represented by LEDs). Since Arduino alone cannot perform voice recognition, this project simulates the functionality by accepting pre-defined text commands via the **Serial Monitor**. This simulates what would happen if an external speech recognition module or voice-controlled app sent commands to the Arduino via serial communication.

The core concept is to demonstrate how an embedded system can act on spoken commands such as **“light on”** or **“fan off”**—except here, those commands are typed manually into the serial monitor. The Arduino reads the commands, compares them with known phrases, and performs the corresponding action by turning devices ON or OFF. This introduces the learner to basic **string processing**, **digital output control**, and **embedded C programming**.


## 💻 Software Used

* **Tinkercad Circuits** – An online simulation tool from Autodesk that supports Arduino Uno and allows simulation of real-time serial input and output using the Serial Monitor.
* **Arduino IDE (C/C++ syntax)** – The code for this project is written in Arduino-style C, including functions like `Serial.readStringUntil()`, `digitalWrite()`, and standard setup-loop structure.
* **Serial Monitor** – Used to manually type text-based commands to simulate speech recognition input.

## 🧰 Components Used

| Component                | Quantity  |
| ------------------------ | --------- |
| Arduino Uno              | 1         |
| LED (for output devices) | 2         |
| 220Ω Resistors           | 2         |
| Breadboard (optional)    | 1         |
| Jumper Wires             | As needed |

> Note: No voice modules or microphones are used. The **Serial Monitor** simulates command input.


## 🔌 Circuit Connections

The project uses two LEDs to represent controllable devices (e.g., “light” and “fan”).

| LED Label | Arduino Pin | Resistor | Connection Description                 |
| --------- | ----------- | -------- | -------------------------------------- |
| Light LED | D2          | 220Ω     | Anode → D2, Cathode → GND via resistor |
| Fan LED   | D3          | 220Ω     | Anode → D3, Cathode → GND via resistor |

This simple wiring ensures that each LED can be individually controlled via digital signals from the Arduino.


## 🧠 Working Principle

The idea is to **simulate a speech-controlled environment** by using typed commands in the Serial Monitor. When the user types a command like `"light on"` or `"fan off"` and presses Enter, the Arduino reads the full string and compares it with predefined valid phrases using string comparison (`==`). If the input matches a known command, the corresponding output pin is set HIGH or LOW, turning the LED ON or OFF.

This system mimics how an actual voice recognition module might work—where commands recognized from speech are converted into serial text and sent to Arduino.

The LED connected to D2 represents a **light**, while the LED on D3 represents a **fan**. Both can be turned ON or OFF by sending simple lowercase commands like:

* `"light on"` → Turn ON Light LED
* `"light off"` → Turn OFF Light LED
* `"fan on"` → Turn ON Fan LED
* `"fan off"` → Turn OFF Fan LED

If any unrecognized command is entered, the Arduino responds with `"Unknown command"` on the Serial Monitor.


## 💻 Arduino Code

```c
String command;

void setup() {
  Serial.begin(9600);
  pinMode(2, OUTPUT);  // Light LED
  pinMode(3, OUTPUT);  // Fan LED
  Serial.println("Speech Command System Ready");
}

void loop() {
  if (Serial.available()) {
    command = Serial.readStringUntil('\n');
    command.trim(); // Remove whitespace

    if (command == "light on") {
      digitalWrite(2, HIGH);
      Serial.println("Light turned ON");
    }
    else if (command == "light off") {
      digitalWrite(2, LOW);
      Serial.println("Light turned OFF");
    }
    else if (command == "fan on") {
      digitalWrite(3, HIGH);
      Serial.println("Fan turned ON");
    }
    else if (command == "fan off") {
      digitalWrite(3, LOW);
      Serial.println("Fan turned OFF");
    }
    else {
      Serial.println("Unknown command");
    }
  }
}
```


## ▶️ Steps to Simulate in Tinkercad

1. Open [https://www.tinkercad.com/](https://www.tinkercad.com/)
2. Go to **Circuits** → **Create New Circuit**
3. Add:

   * 1 × Arduino Uno
   * 2 × LEDs (label one as “Light”, one as “Fan”)
   * 2 × 220Ω resistors
   * Breadboard (optional)
4. Wire:

   * LED1 (Light): Anode → D2, Cathode → GND via 220Ω resistor
   * LED2 (Fan): Anode → D3, Cathode → GND via 220Ω resistor
5. Open **Code Editor**, switch to **Text** mode
6. Paste the Arduino code above
7. Click **Start Simulation**
8. Open the **Serial Monitor**
9. Type the following commands one by one and hit Enter:

   * `"light on"` → turns on the light LED
   * `"light off"` → turns it off
   * `"fan on"` → turns on the fan LED
   * `"fan off"` → turns it off


## 🧪 Simulation Output

Once the simulation starts, the Serial Monitor shows “Speech Command System Ready”. You can then type commands like `"light on"` to turn on the Light LED, and `"fan off"` to turn off the Fan LED. The system processes the commands in real-time and prints confirmation messages like `"Light turned ON"` or `"Unknown command"`.

This simulates how a speech recognition-enabled Arduino would respond to vocal instructions, making it ideal for concept-level demonstrations.

## Output

<img width="1910" height="1082" alt="Image" src="https://github.com/user-attachments/assets/005d8f90-1905-4d2c-9f9a-6aa83a467f34" />

## 🎯 Final Notes

Although real speech recognition is not implemented due to Tinkercad limitations, this project successfully simulates its behavior. It shows how serial input can be processed as string commands to control outputs. The project uses only LEDs and resistors to represent devices, making it beginner-friendly and fully functional in an online simulation. The code is written in Arduino C using Serial communication, string handling, and digital output control. This system can easily be extended to support more commands or actual speech modules in future hardware implementations.
