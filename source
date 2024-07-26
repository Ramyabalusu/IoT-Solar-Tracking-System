#include <Servo.h>

// Define LDR pins
#define LDR1 A0
#define LDR2 A1

// Define error threshold
#define ERROR_THRESHOLD 10

// Initial servo position
int initialServoPosition = 90;

// Create a Servo object
Servo servo;

// Define LED pins
int led1 = 4;
int led2 = 2;

void setup() {
  // Attach the servo to PWM pin
  servo.attach(11);
  pinMode(led1, OUTPUT);
  pinMode(led2, OUTPUT);
  
  // Set the initial position of the servo
  servo.write(initialServoPosition);

  delay(1000);
}

void loop() {
  // Read LDR sensor values
  int ldr1 = analogRead(LDR1);
  int ldr2 = analogRead(LDR2);

  // Calculate the difference between LDR values
  int ldrDifference = abs(ldr1 - ldr2);

  // Check if the difference is within the acceptable error range
  if (ldrDifference > ERROR_THRESHOLD) {
    // Adjust servo position based on LDR values
    if (ldr1 > ldr2) {
      initialServoPosition--;
      digitalWrite(led1, HIGH);
      digitalWrite(led2, LOW);
    } else {
      initialServoPosition++;
      digitalWrite(led1, LOW);
      digitalWrite(led2, HIGH);
    }

    // Constrain the servo position to a valid range (0 to 180)
    initialServoPosition = constrain(initialServoPosition, 0, 180);

    // Set the new servo position
    servo.write(initialServoPosition);
    delay(50);
    
    // Reset LED states
    digitalWrite(led1, LOW);
    digitalWrite(led2, LOW);
  }
}
