#include <Servo.h>

// Define pins
int potPin = A0;          // Pin for the potentiometer
int servoPin = 9;         // Pin for the servo motor
int buttonPin = 2;        // Pin for the button
int ledPin = 13;          // Pin for the LED

// Variables
Servo myServo;
bool powerMode = true;    // True = system active (LED off), False = emergency mode (LED on)

void setup() {
  myServo.attach(servoPin);       // Connect the servo to its pin
  pinMode(buttonPin, INPUT_PULLUP); // Button setup with a pull-up resistor
  pinMode(ledPin, OUTPUT);        // Set the LED pin as an output
  Serial.begin(9600);             // Start serial communication for debugging
  digitalWrite(ledPin, LOW);      // Start with LED off (system is active)
}

void loop() {
  // Check if the button is pressed
  if (digitalRead(buttonPin) == LOW) {
    powerMode = !powerMode;       // Switch between active and emergency modes
    if (powerMode) {
  digitalWrite(ledPin, LOW);  // Turn off the LED
} else {
  digitalWrite(ledPin, HIGH); // Turn on the LED
}
; // LED on = emergency mode, LED off = active mode
    delay(200);                   // Wait to avoid multiple toggles (debounce)
  }

  if (powerMode) {
    // System is active: Read the potentiometer and move the servo
    int potValue = analogRead(potPin);           // Get the potentiometer value
    int servoAngle = map(potValue, 0, 1023, 0, 180); // Convert value to an angle (0-180)
    myServo.write(servoAngle);                  // Move the servo to the calculated angle
    Serial.println(servoAngle);                 // Print the angle for debugging
  } else {
    // Emergency mode: Stop everything
    Serial.println("Emergency mode: System is off.");
  }

  delay(10); // Small delay for smooth operation
}
