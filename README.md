void setup() {
  Serial.begin(9600);
  pinMode(10, OUTPUT);
  pinMode(11, OUTPUT);
  
  pinMode(12, OUTPUT);
  pinMode(9, OUTPUT);

  pinMode(13, OUTPUT);
  pinMode(8, OUTPUT);

  countdown();
  
  int ctr = 0;
  while (ctr < 6){
    if(ctr%2 == 1){
      digitalWrite(10, HIGH);
    }
    if(ctr%2 == 0){
      digitalWrite(10, LOW);
    }
    ctr++;
    delay(1000);
  }
  digitalWrite(10, HIGH);
  
  lforward();
  rforward();
}
int ctr = 0;
void loop(){
  int far = 0;
  int last = 0;
    
  far = howFar();
  
  if (last != 0){
    if ((last-far) > 5){
      far = last;
    }
  }
  
  if (far == 0){
    ctr++;
    Serial.println(ctr);
    
    last = 0;
  }
  else{
    Serial.println(far);
  }
  
  if (far > 5){
    lforward();
    rforward();
    
    digitalWrite(10, HIGH);
    
    last = far;
  }
  
  if (far <= 5){
    digitalWrite(10, LOW);
    
    lstop();
    rstop();
        
    delay(1000);
    
    lback();
    rback();

    delay(1000);
    
    lstop();
    rstop();
    
    int ctr = 0;
    int record = 0;
    int otherrecord = 0;
    
    while (ctr <= 16){
      int far = look();
      
      Serial.print(far);
      
      Serial.print("                         ");
      
      if (far >= record){
        record = far;
        otherrecord = ctr;
      }
      
      Serial.println(otherrecord);
      
      ctr++;
      
      last = 0;
    }
    
    lback();
    rforward();
    
    delay((16-otherrecord)*200);
    
    lforward();
    rforward();
}
}

void lback(){
  digitalWrite(12, HIGH);
  digitalWrite(9, LOW);
  analogWrite(3, 123);
}

void rback(){
  digitalWrite(13, HIGH);
  digitalWrite(8, LOW);
  analogWrite(11, 123);
}

void lforward(){
  digitalWrite(12, LOW);
  digitalWrite(9, LOW);
  analogWrite(3, 123);
}

void rforward(){
  digitalWrite(13, LOW);
  digitalWrite(8, LOW);
  analogWrite(11, 123);
}

void lstop(){
  digitalWrite(9, HIGH);
}

void rstop(){
  digitalWrite(8, HIGH);
}

void countdown(){
  int notes[] = {659, 587, 659, 440, 698, 659, 698, 659, 587};
  int durations[] = {8, 8, 4, 1, 8, 8, 4, 4, 2};
  for(int note = 0; note < 10; note++){
    tone(11, notes[note], (1000/ durations[note]);
  }
  notone(11);
}

int look(){
  lstop();
  rstop();
  
  delay(500);
  
  int far;
  
  lforward();
  rback();
  
  digitalWrite(10, HIGH);
  
  delay(200);
  
  far = howFar();
  
  digitalWrite(10, LOW);

  if(far == 0){
    far = 300;
  }

  if(far > 300){
    far = 300;
  }
  
  return far;
}

int howFar(){
  int trigpin = 5;
  int echopin = 4;
    
  pinMode(trigpin, OUTPUT);
  pinMode(echopin, INPUT);
  
  int cm = 0;
  int duration = 0;
  
  digitalWrite(trigpin, LOW);
  delayMicroseconds(2);
  
  digitalWrite(trigpin, HIGH);
  delayMicroseconds(10);
  
  digitalWrite(trigpin, LOW);
  duration = pulseIn(echopin, HIGH);
  
  cm = duration / 58.2;
  
  if(cm == 0){
    cm = 300;
  }

  if(cm > 300){
    cm = 300;
  }
  
  return cm;
}
