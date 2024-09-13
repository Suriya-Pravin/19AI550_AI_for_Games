# Ex.No: 4  Implementation of Snake game using Steering behaviors
### DATE:                                                                            
### REGISTER NUMBER : 212223230223
### AIM: 
To write a python program to simulate the snake game using steering behaviors
### Algorithm:
1. Start the program
2. Import the necessary modules
3. Initiate the pygame engine and window
4. Specify the necessary parameter for background,snake and food
5. Create a function for seeking behavior towards the target
6.  Move the snake towards the target by move function
7.  Increase the size of snake by wrap around function
8.  create a food at location randomly
9.  In main, create a game loop, move the snake towards the food,check the collision and increase the size
10.  Update the display
11.  Stop the program
 ### Program:


```
import pygame
import random

pygame.init()

width, height = 800, 600
screen = pygame.display.set_mode((width, height))
pygame.display.set_caption("Wandering Behavior")


black = (0, 255, 0)
white = (255, 255, 255)

character_size = 20
x = width // 2
y = height // 2
velocity = 2

direction_x = random.choice([-1, 1])
direction_y = random.choice([-1, 1])


change_direction_time = 1000  # in milliseconds
last_change_time = pygame.time.get_ticks()

running = True
while running:
   for event in pygame.event.get():
       if event.type == pygame.QUIT:
           running = False

   current_time = pygame.time.get_ticks()
   if current_time - last_change_time > change_direction_time:
       direction_x = random.choice([-1, 1])
       direction_y = random.choice([-1, 1])
       last_change_time = current_time

   x += direction_x * velocity
   y += direction_y * velocity

   if x < 0 or x > width - character_size:
       direction_x *= -1
   if y < 0 or y > height - character_size:
       direction_y *= -1

   screen.fill(black)

   pygame.draw.rect(screen, white, (x, y, character_size, character_size))

   pygame.display.flip()

   pygame.time.delay(30)

pygame.quit()
```








### Output:

![4)'](https://github.com/user-attachments/assets/ac773a0a-6976-4397-b291-bc40b2f15150)


### Result:
Thus the simple snake game was implemented.
