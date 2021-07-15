# 3-phase-fault-detection-sysytm
3 phase use line to line line to ground code
//YWROBOT
//Compatible with the Arduino IDE 1.0
//Library version:1.1
#include <Wire.h> 
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27,A4,A5);  // set the LCD address to 0x27 for a 16 chars and 2 line display
int button = 2;
int button1 = 3;
int button2 = 4;
int relay = 9;
int relay1 = 10 ;
int relay2 = 11;

void setup()
{Serial.begin(9600);
  lcd.init();                      // initialize the lcd 
  lcd.init();
  // Print a message to the LCD.
  lcd.backlight();

  lcd.setCursor(2,0);
  lcd.print("ITM ALIGARH");
  delay(1500);
  lcd.clear();
  lcd.setCursor(1,0);
  lcd.print("EE DEPARTMENT");
  delay(2000);
  lcd.clear();
  lcd.setCursor(4,0);
  lcd.print("NO FAULT");

  
  pinMode(button,INPUT_PULLUP);
 pinMode(button1,INPUT_PULLUP);
 pinMode(button2,INPUT_PULLUP);
 pinMode( relay , OUTPUT);
 pinMode( relay1 , OUTPUT);
 pinMode( relay2 , OUTPUT);
 
}


void loop()
{ if(digitalRead(button) == LOW  ){
   digitalWrite(relay,LOW);
        lcd.clear();
  lcd.setCursor(3,0);
  lcd.print(" Y = 2km ");
  
  Serial.println("Y = 2km");
   digitalWrite(relay, LOW); 
        delay (100);
        digitalWrite(relay, HIGH);
        delay (100);
        digitalWrite(relay, LOW);
  
}
  else if (digitalRead(button1) == LOW){
     digitalWrite(relay1,LOW);
          lcd.clear();
      lcd.setCursor(7,0);
  lcd.print("R = 11km");
       
  Serial.println("R = 8km");
  digitalWrite(relay1, LOW); 
        delay (100);
        digitalWrite(relay1, HIGH);
        delay (100);
        digitalWrite(relay1, LOW);
 
  
  }
  else if (digitalRead(button2) == LOW) {
    digitalWrite(relay2,LOW);
         lcd.clear();
    lcd.setCursor(5,0);
    lcd.print("B= 4km");
         
    
    Serial.println("B = 4km");
  digitalWrite(relay2, LOW); 
        delay (100);
        digitalWrite(relay2, HIGH);
        delay (100);
        digitalWrite(relay2, LOW);
    
  }
  else{
   
    lcd.setCursor(3,0);
     lcd.print(" NO FAULT ..");

     
     
}
}

           
