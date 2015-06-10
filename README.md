void setup() {
  Serial.begin(9600);
  pinMode(10, OUTPUT);
  
  pinMode(12, OUTPUT);
  pinMode(9, OUTPUT);

  pinMode(13, OUTPUT);
  pinMode(8, OUTPUT);
  
  int ctr = 0;
  while (ctr < 10){
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

int look(){
  lstop();
  rstop();
  
  delay(500);
  
  int far;
  int far2;
  int far3;
  lforward();
  rback();
  
  digitalWrite(10, HIGH);
  
  delay(200);
    
  far = howFar();
  far2 = howFar();
  far3 = howFar();
  
  digitalWrite(10, LOW);

  if(far == 0){
    far = 300;
  }

  if(far > 300){
    far = 300;
  }
  if(far2 == 0){
    far2 = 300;
  }

  if(far2 > 300){
    far2 = 300;
  }
  if(far3 == 0){
    far3 = 300;
  }

  if(far3 > 300){
    far3 = 300;
  }
  
  far = ((far + far2 + far3) / 3);
  
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
