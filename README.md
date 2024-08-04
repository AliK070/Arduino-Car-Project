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
To put everything togheter in the main loop, I assign the yAxis and xAxis to analog read from the xAxis in and yAxis and setup if statments to direct the motors. 

```C
  if (yAxis < 470) //Move backwards
  {
    MotorSpeed = map(yAxis, 470, 0, 0, 255);
    analogWrite(LED_IN, MotorSpeed);
    backward();
    printData(1);
  }


  else if (yAxis > 550) //Move forward
  {
    MotorSpeed = map(yAxis, 550, 1023, 0, 255);
    forward();
    printData(2);
  
  }

  else if (xAxis < 470) //Move left
  { 
    MotorSpeed = map(xAxis, 470, 0, 0, 255);
    left(); 
    printData(3);
  }

  else if (xAxis > 550) //Move right
  {
    MotorSpeed = map(xAxis, 550, 1023, 0, 255);
    right();
    printData(4);
  }
    else {
    analogWrite(LED_IN, 0);
    MotorSpeed = 0;
    stop(); 
  }
  analogWrite(pwmM, MotorSpeed);
}
```
