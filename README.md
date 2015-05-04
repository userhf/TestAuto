# TestAuto
#include <Servo.h>

  Servo left;
  Servo right;

void setup() { 
  left.attach(13);
  right.attach(14);
  left.write(90);
  right.write(90);
  
  delay(3000);
}

void loop() {
  left.write(120);
  right.write(120);
  delay(1000);
  left.write(60);
  right.write(60);
  delay(1000);
}
