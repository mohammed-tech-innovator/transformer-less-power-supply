#define PWM_PIN 0 // pwm output to mosfet drivers 
#define DRIVER_ENABLE_PIN 1 // enable / disable mosfet driver
#define FEEDBACK A1 // read output voltage
#define FEEDIN A2 // read input voltage
#define VREF 12.2 // refrence to output voltage
#define INPUT_V_DEV_R 101.0 //input voltage divider ratio
#define OUTPUT_V_DEV_R 10.0 //output voltage divider ratio
#define TOLERANCE 0.25 // acceptable tolarence
#define VIN_MAX 400 // maximum input voltage
#define WARRNING_LED 3 // over voltage led 
#define MAIN_LOOP_DELAY 100 // main loop delay in milisecondes
///
/// variables
///
float Vout = 0 ;// output voltage
float Vin = 0 ; // input voltage
unsigned short PWM = 0x00; // pwm value
void setup()
{
  pinMode(WARRNING_LED,OUTPUT);
  digitalWrite(DRIVER_ENABLE_PIN,HIGH);
  delay(100);
}
void loop()
{
  Vout = (5/1023.0)*OUTPUT_V_DEV_R*analogRead(FEEDBACK); 
  Vin = (5.0/1023.0)*INPUT_V_DEV_R*analogRead(FEEDIN); 
  if ( Vin > VIN_MAX ) // over voltage subroutine
  {
    PWM = 0x00;
    digitalWrite(WARRNING_LED,HIGH);
    analogWrite(PWM_PIN , PWM); // shut down
    digitalWrite(DRIVER_ENABLE_PIN,LOW);
    while(Vin > VIN_MAX);
    digitalWrite(DRIVER_ENABLE_PIN,HIGH);
    digitalWrite(WARRNING_LED,LOW);
  }
  if( Vout > VREF + TOLERANCE)
  {
    if (PWM > 0)
    {
      PWM--;
      PWM = constrain(PWM,0,255);
    }
  }
  if( Vout < VREF - TOLERANCE)
  {
    if (PWM < 255)
    {
      PWM++;
      PWM = constrain(PWM,0,255);
    }
  }
  analogWrite(PWM_PIN,PWM);
  delay(MAIN_LOOP_DELAY);
}
