# Miguel Pescador-Servin

# Servo and LED Control with Emergency Mode

This code controls a servo motor and an LED, with a button used to toggle between normal operation and emergency mode.

Components and Pins

- Potentiometer: Reads an analog value to control the servo motor angle.  
    
- Servo Motor: Moves to a specific angle based on the potentiometer's input.  
    
- Button: Toggles the system between active mode (normal operation) and emergency mode (safety mode).  
    
- LED: Indicates the current mode (OFF \= active, ON \= emergency).

How It Works

1. Setup Phase:  
     
   - The servo is connected and initialized on **servoPin**.  
       
   - The button is configured with an internal pull-up resistor.  
       
   - The LED is set as an output and starts OFF (indicating the system is active).

   

2. Loop Phase:  
     
   - Button Press: Checks if the button is pressed. When pressed, the system toggles between:  
       
     - Active Mode: The servo motor moves based on the potentiometer's value.  
         
     - Emergency Mode: The servo motor is locked at a neutral angle and the LED turns ON.

   

3. LED Control:  
     
   - The LED reflects the current system state using a if-else operator:

```c
if (powerMode) {
digitalWrite(ledPin, LOW);  
} else {
 digitalWrite(ledPin, HIGH); 
} - LOW turns the LED OFF (system active).
```

```c
 - HIGH turns the LED ON (emergency mode).
```

4. Servo Control:  
     
   - In active mode, the potentiometer's analog input is mapped to an angle (0-180°), and the servo is moved accordingly.

   

5. Serial Monitor:  
     
   - Prints the servo angle or a message indicating emergency mode for debugging.

Key Features

- Emergency Mode: Ensures the system halts operations and visually indicates the state via the LED.  
    
- Debounce: A short delay prevents multiple toggles from a single button press.

