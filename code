import pygame
import random

# Initialize Pygame
pygame.init()

# Set up the game window
screen_width = 600
screen_height = 600
screen = pygame.display.set_mode((screen_width, screen_height))
pygame.display.set_caption("Snake Game")

# Define the colors
black = (0, 0, 0)
white = (255, 255, 255)
red = (255, 0, 0)

# Define the Snake class
class Snake:
    def __init__(self):
        self.size = 1
        self.elements = [[100, 100]]
        self.radius = 10
        self.direction = "right"
    
    def draw(self):
        for element in self.elements:
            pygame.draw.circle(screen, white, element, self.radius)

    def move(self):
        if self.direction == "right":
            head = [self.elements[0][0] + 20, self.elements[0][1]]
        elif self.direction == "left":
            head = [self.elements[0][0] - 20, self.elements[0][1]]
        elif self.direction == "up":
            head = [self.elements[0][0], self.elements[0][1] - 20]
        elif self.direction == "down":
            head = [self.elements[0][0], self.elements[0][1] + 20]

        self.elements.insert(0, head)
        if len(self.elements) > self.size:
            self.elements.pop()

    def eat(self):
        self.size += 1

# Define the Food class
class Food:
    def __init__(self):
        self.position = [random.randrange(1, screen_width/20) * 20,
                          random.randrange(1, screen_height/20) * 20]
        self.radius = 10

    def draw(self):
        pygame.draw.circle(screen, red, self.position, self.radius)

# Define the main function
def main():
    snake = Snake()
    food = Food()

    running = True
    clock = pygame.time.Clock()

    while running:
        # Event handling
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                running = False
            if event.type == pygame.KEYDOWN:
                if event.key == pygame.K_RIGHT:
                    snake.direction = "right"
                elif event.key == pygame.K_LEFT:
                    snake.direction = "left"
                elif event.key == pygame.K_UP:
                    snake.direction = "up"
                elif event.key == pygame.K_DOWN:
                    snake.direction = "down"

        # Game logic
        snake.move()
        if snake.elements[0] == food.position:
            snake.eat()
            food = Food()

        # Drawing
        screen.fill(black)
        snake.draw()
        food.draw()
        pygame.display.update()

        # FPS control
        clock.tick(10)

    pygame.quit()
    quit()

# Run the main function
if __name__ == "__main__":
    main()
