프로세싱
import processing.serial.*;
Serial p;
void setup(){
  size(400, 400);
 p = new Serial(this, "COM4", 9600);
}
void draw(){
 if(p.available()>0){
   String m = p.readStringUntil('\n');
   if(m != null){
    print(m);
    if( float(m) > 28) background(255, 0, 0);
    else background(0, 255, 0);
    textSize(128);
    text(m, 20, 250);
   }
 }
}
아두이노
void setup() {
  pinMode(13, OUTPUT);
  Serial.begin(9600);
}
void loop() {
  int a = analogRead(A0);
  Serial.println( a );
  if(a > 140) digitalWrite(13, HIGH);
  else        digitalWrite(13, LOW);
  delay(500);
}
