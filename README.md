import pygame
import sys

# Initialize Pygame
pygame.init()

# Set up some constants
SCREEN_WIDTH = 640
SCREEN_HEIGHT = 480
FPS = 60

# Set up some variables
mario_x = 100
mario_y = 100
mario_speed = 5
mario_jumping = False
mario_gravity = 1

# Create the game screen
screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))

# Set up the game clock
clock = pygame.time.Clock()

# Game loop
while True:
    # Handle events
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()
        elif event.type == pygame.KEYDOWN:
            if event.key == pygame.K_SPACE:
                mario_jumping = True

    # Move Mario
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT]:
        mario_x -= mario_speed
    if keys[pygame.K_RIGHT]:
        mario_x += mario_speed

    # Apply gravity
    if not mario_jumping:
        mario_y += mario_gravity

    # Jumping logic
    if mario_jumping:
        mario_y -= mario_speed
        if mario_y < 0:
            mario_y = 0
            mario_jumping = False

    # Draw everything
