void setup() {
  pinMode(12, OUTPUT);
  pinMode(9, OUTPUT);
  pinMode(10, OUTPUT);
  
  delay(1000);
  
  digitalWrite(10, HIGH);
  
  delay(1000);
  
  digitalWrite(10, LOW);
  
  delay(1000);
  
  digitalWrite(9, LOW);
  digitalWrite(12, HIGH);
  analogWrite(3, 255);
}

void loop() {
  // put your main code here, to run repeatedly:

}
