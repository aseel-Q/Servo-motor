# Servo-motor
Driving four servo motors using Arduino
https://www.tinkercad.com/things/1kK4RPYarST-servo-sweep?sharecode=undefined
Project Objective:

This project aims to experiment with controlling multiple servo motors simultaneously using an Arduino board. Through this project, I learned how to program four motors to move simultaneously, how to move them in a specific direction, and then how to fix them at a specific angle. The main goal is to build a simple practical understanding that will help me design robots that move in a human-like manner in the future.

What does the project do?

When the project is turned on, the four servo motors begin moving together from 0 degrees to 180 degrees, then back down, repeating this movement for two seconds. After this, all motors stop and lock onto a 90-degree angle. This movement resembles the movement of a robot's joints or limbs, and is a first step toward simulating walking or any other complex movement in robots.
 
The components used are: 

1- Arduino Uno R3
2- breadboard
3- 4 servo motors
4- connecting wires. 
5- If the circuit is implemented in real life without simulation programs, external power must be used (9-volt battery and voltage regulator).

Circuit connection: 

The signal (orange wire) port of the four servos was connected in series with the Arduino ports (D9, D10, D11, D3), then the positive line of the breadboard was connected to the 5V port on the Arduino and the negative line of the breadboard was connected to the GND port on the Arduino, then the Power (Red wire) port of the four servos was connected to the positive line of the breadboard and the GND port was connected to the negative line of the breadboard.

Code: 

#include <Servo.h>

Servo servos[4];
const byte servoPins[4] = {9, 10, 11, 3};

int pos = 0;

void setup() {
  for (byte i = 0; i < 4; i++) {
    servos[i].attach(servoPins[i]);
  }

  unsigned long startTime = millis();

  while (millis() - startTime < 2000) {
    for (pos = 0; pos <= 180; pos++) {
      for (byte i = 0; i < 4; i++) {
        servos[i].write(pos);
      }
      delay(5);
    }
    for (pos = 180; pos >= 0; pos--) {
      for (byte i = 0; i < 4; i++) {
        servos[i].write(pos);
      }
      delay(5);
    }
  }

  for (byte i = 0; i < 4; i++) {
    servos[i].write(90);
  }
}

void loop() {
  // Do nothing
}

How this project relates to humanoid robots:

What I've created in this project is the foundation used by humanoid robots. Any moving robot requires motors to control the joints, allowing them to move at specific times and at specific angles. I've tried this here in a simple way, but the same idea can be developed further, allowing the robot to walk, raise its hand, or balance. This project is a great start and suitable for anyone considering entering the field of robotics or even motion artificial intelligence.

Suggestions for project development:

• I could add more motors, such as 6 or 8, so I could control the arms and legs like a humanoid robot.
• I could install balance or touch sensors so the robot interacts with its environment.
• I could program realistic walking steps, not just back and forth movements.
• I could use Bluetooth or Wi-Fi to control it remotely.
• Most importantly, I could create a robot frame using a 3D printer, install motors, and see more realistic movement.

The end :

Through this project, I learned how to control four servo motors using an Arduino board, creating simple, organized movements that form the basis for leg movement in robots. The experience was very useful, especially in understanding how the motors synchronize with each other and how to stop them at a specific angle. I felt that the project helped me practically understand how motors work in robots, and it opened the door for me to think about larger projects in the future.
