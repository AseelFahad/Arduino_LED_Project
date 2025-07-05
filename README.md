# 🔘 Arduino Project: 3 LEDs Using 3 Pushbuttons

This project demonstrates how to use an Arduino UNO to control three LEDs using three individual pushbuttons.

---

## 🧰 Components Used

- 1 × Arduino UNO
- 3 × Pushbuttons
- 3 × LEDs (any color)
- 3 × 220Ω resistors (for LEDs)
- 3 × 10kΩ resistors (for pull-down configuration)
- Breadboard
- Jumper wires
- USB cable (for powering and uploading code)

---

## 🖼️ Circuit Diagram

> The circuit is built on Tinkercad and looks like this:

![Copy of  3--leds with 3 buttons A Alrashdi](https://github.com/user-attachments/assets/af788ee3-8232-4532-b3a9-40e560d586f6)

- Buttons are connected to digital pins 7, 8, and 9
- LEDs are connected to digital pins 10, 11, and 12
- Each button has a 10kΩ pull-down resistor
- Each LED has a 220Ω current-limiting resistor


---

## 🚀 How It Works
Pressing Button 1 toggles LED 1.

Pressing Button 2 toggles LED 2.

Pressing Button 3 toggles LED 3.

The debounce delay (200 ms) prevents false triggering due to noisy input.

---

## 🧪 Simulation (Optional)
You can simulate this project using Tinkercad Circuits:

Create a new circuit project.

Add an Arduino UNO, breadboard, buttons, LEDs, and resistors as shown.

Paste the code into the Arduino editor.

Start the simulation and test the buttons.

---

## 💻 Arduino Code

```cpp
const int button1 = 7;
const int button2 = 8;
const int button3 = 9;

const int led1 = 10;
const int led2 = 11;
const int led3 = 12;

int lastButton1 = LOW;
int lastButton2 = LOW;
int lastButton3 = LOW;

bool led1State = false;
bool led2State = false;
bool led3State = false;

void setup() {
  pinMode(button1, INPUT);
  pinMode(button2, INPUT);
  pinMode(button3, INPUT);

  pinMode(led1, OUTPUT);
  pinMode(led2, OUTPUT);
  pinMode(led3, OUTPUT);
}

void loop() {
  int current1 = digitalRead(button1);
  int current2 = digitalRead(button2);
  int current3 = digitalRead(button3);

  if (current1 == HIGH && lastButton1 == LOW) {
    led1State = !led1State;
    digitalWrite(led1, led1State);
    delay(200); // Debounce
  }
  lastButton1 = current1;

  if (current2 == HIGH && lastButton2 == LOW) {
    led2State = !led2State;
    digitalWrite(led2, led2State);
    delay(200);
  }
  lastButton2 = current2;

  if (current3 == HIGH && lastButton3 == LOW) {
    led3State = !led3State;
    digitalWrite(led3, led3State);
    delay(200);
  }
  lastButton3 = current3;
}
