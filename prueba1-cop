/* 
 UV SENSOR DFROBOT TOY0044
 
 #Connection:
    VCC-5V
    GND-GND
    OUT-Analog pin 0
*/
*/

// Declaración de pines

int salida1 = 9;     // verde
int salida2 = 10;    // amarillo
int salida3 = 11;    // naranja
int salida4 = 12;    // rojo
int salida5 = 13;    // violeta

int UVOUT = A0; //Salida de Sensor
int REF_3V3 = A1; //3.3V
int tiempo = 30000;

void setup()

{

 Serial.begin(9600);

 pinMode(UVOUT, INPUT);
 pinMode(REF_3V3, INPUT);
 pinMode(salida1, OUTPUT);   // declaramos la variable como salida, OUTPUT
 pinMode(salida2, OUTPUT);   // declaramos la variable como salida, OUTPUT
 pinMode(salida3, OUTPUT);   // declaramos la variable como salida, OUTPUT
 pinMode(salida4, OUTPUT);   // declaramos la variable como salida, OUTPUT
 pinMode(salida5, OUTPUT);   // declaramos la variable como salida, OUTPUT

 digitalWrite(salida1, LOW); // estado inicial del LED apagado
 digitalWrite(salida2, LOW); // estado inicial del LED apagado
 digitalWrite(salida3, LOW); // estado inicial del LED apagado
 digitalWrite(salida4, LOW); // estado inicial del LED apagado
 digitalWrite(salida5, LOW); // estado inicial del LED apagado
 delay(2000);

}


void verde() {
 digitalWrite(salida1, HIGH);
 digitalWrite(salida2, LOW);
 digitalWrite(salida3, LOW);
 digitalWrite(salida4, LOW);
 digitalWrite(salida5, LOW);
}

void amarillo() {
 digitalWrite(salida1, LOW);
 digitalWrite(salida2, HIGH);
 digitalWrite(salida3, LOW);
 digitalWrite(salida4, LOW);
 digitalWrite(salida5, LOW);
}

void naranja() {
 digitalWrite(salida1, LOW);
 digitalWrite(salida2, LOW);
 digitalWrite(salida3, HIGH);
 digitalWrite(salida4, LOW);
 digitalWrite(salida5, LOW);
}

void rojo() {
 digitalWrite(salida1, LOW);
 digitalWrite(salida2, LOW);
 digitalWrite(salida3, LOW);
 digitalWrite(salida4, HIGH);
 digitalWrite(salida5, LOW);
}

void violeta() {
 digitalWrite(salida1, LOW);
 digitalWrite(salida2, LOW);
 digitalWrite(salida3, LOW);
 digitalWrite(salida4, LOW);
 digitalWrite(salida5, HIGH);
}


void loop()

{
  
  int sensorValue;
  sensorValue = analogRead(0);// UV sensors  Analogo 0    
  Serial.println(sensorValue);// Salido en serial  
  delay(200);      

  int uvLevel = averageAnalogRead(UVOUT);
  int refLevel = averageAnalogRead(REF_3V3);

  //Use the 3.3V power pin as a reference to get a very accurate output value from sensor

  float outputVoltage = 3.3 / refLevel * uvLevel;
  float uvIntensity = mapfloat(outputVoltage, 0.99, 2.8, 0.0, 15.0); //Convert the voltage to a UV intensity level

  Serial.print("UV Intensity (W/m^2): ");
  Serial.print(uvIntensity*10);
  Serial.println();

  // Si la lectura del sensor es menor ó igual al valor umbral:

  if (uvIntensity < 2.0){
                        verde();
                        delay(tiempo);
                        }
  	else if (uvIntensity >= 2.0 && uvIntensity < 2.6){
        			   amarillo();
                                   delay(tiempo);   
      				   }
  		else if (uvIntensity >= 2.6 && uvIntensity < 3.2){
       				           naranja();
                                           delay(tiempo);  
				           }
 		       else if (uvIntensity >= 3.2 && uvIntensity < 3.8){
        			                   rojo();
                                                   delay(tiempo);   
						   }
        			else if (uvIntensity >= 3.8){
 							     violeta();
                                                             delay(tiempo);
							     }

}




int averageAnalogRead(int pinToRead)

{

  byte numberOfReadings = 8;
  unsigned int runningValue = 0; 

  for(int x = 0 ; x < numberOfReadings ; x++)
    runningValue += analogRead(pinToRead);
    runningValue /= numberOfReadings;
  return(runningValue);  

}


float mapfloat(float x, float in_min, float in_max, float out_min, float out_max)
{
  return (x - in_min) * (out_max - out_min) / (in_max - in_min) + out_min;
}
