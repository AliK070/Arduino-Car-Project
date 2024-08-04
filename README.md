# Arduino-Car-Project
Here is the code for my arduino car project, there are two folders the processed and the raw folders. The raw folders include the circuit diagram file and the .ino file, while the processed folder contains a viewable, sharable, and readable docuemnt of the code and a .png version of the circuit diagram. 

## Preface
I have tried my best to organize the code through comments and regions for better accessbility. I would also like to mention that this specifc project was made on the Arduino Uno R4 WiFi, that is why you'll see the Arduino_LED_Matrix header file and its functions. To make it compatible with the R3, remove that code. This project was made on two TB6612FNG H-bridges, one joystick for the control, and four hobby motors, refer to my blog about the TB6612FNG H-Bridge at https://alik070.github.io/Alis-Portfolio/pages/blogs/TB6612FNG.html 

## Talking a bit about the code
Getting into the finer details, after defining all my pins I set up six total functions: 
```C
FORWARD(); //-> Sets the motors to go in a forwards direction
BACKWARD(); //-> Sets the motors to go in a backward direction
LEFT(); //-> Sets the motors to go left while spinning the right motors in the opposite direction for a smooth turn
RIGHT(); //->  Sets the motors to go right while spinning the left motors in the opposite direction for a smooth turn
STOP(); //-> Full stop for all motors.
PRINTDATA(); //-> Prints valuable data like the yAxis, xAxis, direction, and updates the LED Matrix on the R4.
```
