# LED Light On/Off based on a Photoresistor

### Running the Program
The program is compatible with an Arduino Uno board which was set up using a SparkFun Inventor's Kit. Following the instructions, the basic board set up should look like this: 

![Arduino Board](images-and-videos/board-template.jpg)

Arduino and USB drivers will need to be installed for the code to work. Go to www.arduino.cc/downloads to download Arduino and www.sparkfun.com/ch340 to download drivers. Pnce Arduino is installed you will need to select the correct board, in this case: Arduino Uno, and the correct port. Next, connect your board to the computer using an USB cable.

To run the code click on the upload button on the top left corner (second to left) on the arduino interface.

![Upload Button](images-and-videos/upload-button.png)

### The Code
The program is designed to have the LED turn on or off based on the light the photoresistor receives. If the photoresistor receives a lot of light (ie. room is bright), it will turn the LED off. If the photoresistor does not receive any light (ie. room is dark), it will turn the LED on.

The program first sets the photoresistor and the threshold variables:
```C
int photoresistor = 0;              //this variable will hold a value based on the brightness of the ambient light
int threshold = 750;                //if the photoresistor reading is below this value the the light will turn on
```

Then the program runs on a constant loop using an if/else to set the photoresistor variable and then check it's relation to the threshold.
```C
void loop()
{
  //read the brightness of the ambient light
  photoresistor = analogRead(A0);   //set photoresistor to a number between 0 and 1023 based on how bright the ambient light is
  Serial.println(photoresistor);    //print the value of photoresistor in the serial monitor on the computer

  //if the photoresistor value is below the threshold turn the light on, otherwise turn it off
  if (photoresistor < threshold) {
    digitalWrite(13, HIGH);         // Turn on the LED
  } else {
    digitalWrite(13, LOW);          // Turn off the LED
  }

  delay(100);                       //short delay to make the printout easier to read
}

```

Here is what it looks like:
![Photoresistor Basic]()

### Challenges
1. Response Pattern: create a blink pattern that tiggers when light is below the threshold (ie. it's dark) or when a hand is waved over the sensor.
```C
if (photoresistor < threshold) {
  // creates a blink pattern
  digitalWrite(13, HIGH);         // Turn on the LED
  delay(100);
  digitalWrite(13, LOW);         // Turn off the LED
  delay(100);
}
```
![Photoresistor Pattern]()

2. Replace 10K resistor with an LED
![Photoresistor Light Resistor]()
