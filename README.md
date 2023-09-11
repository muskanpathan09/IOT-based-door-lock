# IOT-based-door-lock
This Arduino code is for controlling a door lock system with a keypad and a servo motor. It allows the user to input a password via a keypad, and if the correct password is entered, the door (represented by the servo motor) is unlocked.

Here's a detailed explanation of the code:

1. **Libraries and Definitions:**
   - The code includes three libraries: `Keypad`, `LiquidCrystal`, and `Servo`, which provide functionality for working with a keypad, an LCD display, and a servo motor, respectively.
   - It defines `Password_Length` as 5, indicating the length of the password.
   - It sets up various variables and arrays for storing and managing data related to the password and keypad input.

2. **Servo and LCD Initialization (`setup` function):**
   - It initializes the servo motor using `myservo.attach(9, 2000, 2400)`, specifying the servo control pin (9) and pulse width range.
   - Initializes the LCD display using `lcd.begin(16, 2)`.
   - Displays a "Protected Door" message on the LCD and then clears it.

3. **Main Loop (`loop` function):**
   - If the `door` variable is `true`, it means the door is open, and the code waits for the '#' key to close the door. When the '#' key is pressed, the door is closed (servo position reset), and the LCD displays "Door is closed" for 3 seconds.

   - If the `door` variable is `false`, it means the door is closed, and the `Open` function is called.

4. **Loading Function (`loading`):**
   - This function is used to display a loading message with dots on the LCD. It's mainly for visual feedback and a delay.

5. **Clear Data Function (`clearData`):**
   - This function is used to clear the `Data` array, which stores the user's input data (key presses).

6. **Servo Control Functions (`ServoClose` and `ServoOpen`):**
   - `ServoClose` closes the door by gradually moving the servo from its current position to 0 degrees.
   - `ServoOpen` opens the door by gradually moving the servo from its current position to 90 degrees.

7. **Open Function:**
   - This function handles the keypad input and password validation.
   - It displays "Enter Password" on the LCD.
   - It listens for key presses using the `customKeypad.getKey()` function and stores the entered characters in the `Data` array.
   - When the password length is reached, it compares the entered password (`Data`) with the master password (`Master`).
   - If the passwords match, it displays "Door is Open" on the LCD, unlocks the door (servo), and sets the `door` variable to `true`. After 5 seconds, it locks the door again, displays a "Time is up!" message, and sets `door` to `false`.
   - If the passwords do not match, it displays "Wrong Password" on the LCD and sets `door` to `false`.

Overall, this code implements a basic door locking system with a keypad and servo motor, providing access control based on a predefined password.
