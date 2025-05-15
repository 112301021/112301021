- 👋 Hi, I’m @Ajaykumar
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Ajaykumar/Ajaykumaris a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import os
import time
import sys
import pygame
from pygame.locals import *

def terminate():
    pygame.quit()
    sys.exit()

def display_board(board):
    pygame.draw.rect(screen, BLACK, (0, 0, WIDTH, HEIGHT))
    for x in range(BOARD_SIZE):
        for y in range(BOARD_SIZE):
            rect = pygame.Rect(x * SQUARE_SIZE, y * SQUARE_SIZE, SQUARE_SIZE, SQUARE_SIZE)
            pygame.draw.rect(screen, board[x][y], rect, 1)
    pygame.display.flip()

def create_board():
    board = []
    for x in range(BOARD_SIZE):
        row = []
        for y in range(BOARD_SIZE):
            if (x + y) % 2 == 0:
                row.append(WHITE)
            else:
                row.append(BLACK)
        board.append(row)
    return board

def handle_click(board, x, y):
    # implement logic to handle a click at coordinates (x, y)
    pass

def play_game():
    pygame.init()
    screen = pygame.display.set_mode((WIDTH, HEIGHT))
    pygame.display.set_caption('Chess')
    clock = pygame.time.Clock()

    board = create_board()

    running = True
    while running:
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                running = False
            elif event.type == pygame.MOUSEBUTTONDOWN:
                x, y = pygame.mouse.get_pos()
                handle_click(board, x, y)

        display_board(board)
        clock.tick(60)

    terminate()

play_game()
