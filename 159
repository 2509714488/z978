import pygame, sys
from pygame.locals import *

pygame.init()
fpsClock = pygame.time.Clock()

WINDOW = pygame.display.set_mode((400, 300))
pygame.display.set_caption('贪吃蛇')

BLACK = pygame.Color(0, 0, 0)
WHITE = pygame.Color(255, 255, 255)
RED = pygame.Color(255, 0, 0)

snake_position = [100, 50]
snake_body = [[100, 50], [90, 50], [80, 50]]

food_position = [300, 150]
food_spawn = True

direction = 'RIGHT'
change_to = direction

def game_over():
    pygame.quit()
    sys.exit()

while True:
    for event in pygame.event.get():
        if event.type == QUIT:
            game_over()
        elif event.type == KEYDOWN:
            if event.key == K_RIGHT or event.key == ord('d'):
                change_to = 'RIGHT'
            if event.key == K_LEFT or event.key == ord('a'):
                change_to = 'LEFT'
            if event.key == K_UP or event.key == ord('w'):
                change_to = 'UP'
            if event.key == K_DOWN or event.key == ord('s'):
                change_to = 'DOWN'
            if event.key == K_ESCAPE:
                pygame.event.post(pygame.event.Event(QUIT))

    if change_to == 'RIGHT' and not direction == 'LEFT':
        direction = 'RIGHT'
    if change_to == 'LEFT' and not direction == 'RIGHT':
        direction = 'LEFT'
    if change_to == 'UP' and not direction == 'DOWN':
        direction = 'UP'
    if change_to == 'DOWN' and not direction == 'UP':
        direction = 'DOWN'

    if direction == 'RIGHT':
        snake_position[0] += 10
    if direction == 'LEFT':
        snake_position[0] -= 10
    if direction == 'UP':
        snake_position[1] -= 10
    if direction == 'DOWN':
        snake_position[1] += 10

    snake_body.insert(0, list(snake_position))
    if snake_position[0] == food_position[0] and snake_position[1] == food_position[1]:
        food_spawn = False
    else:
        snake_body.pop()

    if not food_spawn:
        food_position = [pygame.randint(0, 39) * 10, pygame.randint(0, 29) * 10]
    food_spawn = True
    WINDOW.fill(BLACK)
    for pos in snake_body:
        pygame.draw.rect(WINDOW, RED, pygame.Rect(
            pos[0], pos[1], 10, 10))
    pygame.draw.rect(WINDOW, WHITE, pygame.Rect(
        food_position[0], food_position[1], 10, 10))
    if snake_position[0] >= 400 or snake_position[0] < 0:
        game_over()
    if snake_position[1] >= 300 or snake_position[1] < 0:
        game_over()
    for block in snake_body[1:]:
        if snake_position[0] == block[0] and snake_position[1] == block[1]:
            game_over()
    pygame.display.update()
    fpsClock.tick(12)
