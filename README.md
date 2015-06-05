void setup() {
  pinMode(12, OUTPUT);
  pinMode(9, OUTPUT);
  pinMode(13, OUPUT);
  pinMode(8, OUTPUT);
  pinMode(10, OUTPUT);
  
  delay(1000);
  
  digitalWrite(10, HIGH);
  
  delay(1000);
  void setup() {
  pinMode(12, OUTPUT);
  pinMode(9, OUTPUT);
  pinMode(13, OUTPUT);
  pinMode(8, OUTPUT);

  forward();
}
void forward(){
  digitalWrite(8, LOW);
  digitalWrite(13, HIGH);
  analogWrite(11, 255);
}

void back(){
  digitalWrite(8, LOW);
  digitalWrite(13, HIGH);
  analogWrite(11, 255);
  
  digitalWrite(9, LOW);
  digitalWrite(12, HIGH);
  analogWrite(3, 255);
}

void stp(){
  digitalWrite(8, HIGH);
  
  digitalWrite(9, HIGH);
}

void loop() {
}

  digitalWrite(10, LOW);
  
  delay(1000);
  
  digitalWrite(9, LOW);
  digitalWrite(12, HIGH);
  analogWrite(3, 123);
}

void loop() {
  // put your main code here, to run repeatedly:

}
