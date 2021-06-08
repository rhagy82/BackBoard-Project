# BackBoard-Project

### Goals For Project
We want to build a fully functioning backboard with a ultrasonic sensor that counts made baskets. We also want to be able to understand code and how to use an ultrasonic sensor.


### Major Obstacles 
We are really struggling to find out how to successfully make our code and create our rim and backboard in onshape.

### What we accomplished
We where able to almost finsh are cad and have found a code online that should work for our project

### Spring Break Before check
The project is going fine but we are not on time the major obstacle is the fact that we don't have a backboard.
When I return from spring break in person the first thing I am going to do is make a backboard.

When I Return from spring break in person the first thing im going to do is, work on CAD
### On time or Not?
We are on time to finish we might even be able to finish early

### Milestones
We printed our ultrasonic sensor holder and we are ready to finish our backboard.


### Parts used
we 3d printed our holder but we also use an arduino and an ultrasonic sensor and a mini hoop




### Link For onshape Document
(https://cvilleschools.onshape.com/documents/370ec0ce98278459c33782b4/w/71aaa089db0a2a1361a07167/e/d96bccb9132f9ffcce7fcd90)

### Psuedo Code
```
#include <Adafruit_LEDBackpack.h>
#include <Wire.h> // Enable this line if using Arduino Uno, Mega, etc.
#include <Adafruit_GFX.h>
#include "Adafruit_LEDBackpack.h"

Adafruit_7segment matrix = Adafruit_7segment();


int led = 8;

int counter = 0;
#define echoPin 2 // attach pin D2 Arduino to pin Echo of HC-SR04
#define trigPin 3 //attach pin D3 Arduino to pin Trig of HC-SR04

// defines variables
long duration; // variable for the duration of sound wave travel
int distance; // variable for the distance measurement
int oldDistance;//variable for the distance from the last loop


void setup() {
  pinMode(trigPin, OUTPUT); // Sets the trigPin as an OUTPUT
  pinMode(echoPin, INPUT); // Sets the echoPin as an INPUT
  Serial.begin(9600); // // Serial Communication is starting with 9600 of baudrate speed
  Serial.println("Ultrasonic Sensor HC-SR04 Test"); // print some text in Serial Monitor
  Serial.println("with Arduino UNO R3");
  pinMode(led, OUTPUT);
  Serial.println(counter);

#ifndef __AVR_ATtiny85__
  Serial.println("7 Segment Backpack Test");
#endif
  matrix.begin(0x70);
}


void loop() {
  delay(100);

  // Clears the trigPin condition
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  // Sets the trigPin HIGH (ACTIVE) for 10 microseconds
  digitalWrite(trigPin, HIGH);
  delay(10);
  digitalWrite(trigPin, LOW);
  // Reads the echoPin, returns the sound wave travel time in microseconds
  duration = pulseIn(echoPin, HIGH);
  // Calculating the distance
  distance = duration * 0.034 / 2; // Speed of sound wave divided by 2 (go and back)
  // Displays the distance on the Serial Monitor

  Serial.print("Distance: ");
  Serial.print(distance);


  if (distance != 0 && distance < 100) {
    if (distance < 20 && oldDistance >= 20) {
      digitalWrite(led, HIGH);
      counter++;
    }
    if (distance > 20) {
      digitalWrite(led, LOW);

    }
    matrix.println(counter);
    matrix.writeDisplay();

    oldDistance = distance;

  }
  Serial.println(" cm");
  Serial.println(counter);



}

})
```
### Wiring for Basketball Backboard
<img src="Wiring for Basketball Backboard.PNG">
### Image

<img src="Backboard Screenshot">


### Cad for Assembly
We are starting our assembly for are backboard that we are using to hold the arduino and count the made baskets.

<img src="Backboard.png">
