# STM32F103-ICE-Hockey-game
This updated C code appears to be a main program file targeting a microcontroller, likely an STM32 microcontroller. The code is intended to interface with a 16x2 character LCD using the HD44780 driver library and to control a simple game or application involving movement of characters on the LCD screen.

Let's go through the key components of the code:
The hockey game is a simple two-player game that simulates air hockey, a popular arcade game. In this version of the game, two paddles represent the players, and a ball moves between them on a 16x2 character LCD screen.
![download (1)](https://github.com/ivias2000/STM32F103-ICE-Hockey-game/assets/125237611/73a38643-1010-4144-ba65-7b4503435d5f)

Here's a step-by-step explanation of the key components of the code:

Initialization:
The code starts by initializing the microcontroller's peripherals, such as GPIOs, and the 16x2 character LCD using the "HD44780LIB.h" library. It also defines some variables used throughout the program.

Printing and Moving Paddles:![20220816_161020](https://github.com/ivias2000/STM32F103-ICE-Hockey-game/assets/125237611/53050015-5767-4a75-ab2e-b582b3f3737d)

The printlcd function is used to print characters representing paddles on the LCD at specific positions (x_left, x_rast, y_left, y_rast). The paddles are represented by "]" (right paddle) and "[" (left paddle) symbols.

The paddles can move up and down on the LCD based on button inputs from the user. The buttons are connected to GPIO pins and are monitored in the infinite loop.
When a button is pressed, the corresponding paddle's current position is erased from the LCD by printing a space character (" ") at its previous position.
Then, the paddles' positions (x_left, y_left, x_rast, y_rast) are updated according to the button press, and the paddles are printed at their new positions.
Moving Ball:
The ball in the game is represented by an asterisk symbol ("*"), which is printed on the LCD at the position specified by x_setare and y_setare. The x_setare and y_setare variables control the position of the ball on the LCD screen.

The ball's movement direction is determined by the dx (delta-x) and dy (delta-y) variables.
The ball bounces off the top and bottom edges of the LCD screen by reversing the sign of dy when it reaches the top or bottom.
Game Scoring:
The game tracks the score of the two players, "LEFT" and "RIGHT". If the ball reaches the left or right edge of the LCD screen, the corresponding player wins a point.

When the ball reaches the left edge, the game checks if the ball's vertical position (y_setare) matches the vertical position of the left paddle (y_left).
If it does, the right player ("RIGHT") wins the round, and the score is updated. The LCD displays "RIGHT WIN!" along with the updated score.
A similar process is followed for the right edge and the left player ("LEFT").
Continuous Gameplay:
The game continuously runs in an infinite loop. After a player wins a round, the paddles and the ball's positions are reset to their starting positions, and the game continues.

Button Inputs and Delay:
The code includes delays (HAL_Delay) to provide a simple debouncing mechanism for the button inputs. This helps prevent rapid and unintended multiple inputs from being registered.

LCD Refresh Rate:
The refresh rate of the LCD screen is controlled by the delays in the infinite loop. Adjusting these delays can modify the game's speed and difficulty.

It's important to note that this code is a basic implementation of the game, and there are many ways to enhance and optimize it. For example, more sophisticated collision detection, paddle movement, and scoring algorithms could be implemented to make the game more engaging. Additionally, a more advanced LCD driver library could provide smoother graphics and more display options.

Overall, this code provides a simple and fun example of how to use an LCD and GPIOs to create a two-player game on a microcontroller platform.


https://github.com/ivias2000/STM32F103-ICE-Hockey-game/assets/125237611/415ebf8a-34e2-4b08-a3b8-fb98b23daeab

