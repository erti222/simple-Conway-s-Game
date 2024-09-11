import pygame
import random

# Set up the constants
WIDTH = 1800
HEIGHT = 1000
ROWS = 100
COLS = 175
BLOCK_SIZE = 10


# Set up the colors
WHITE = (255, 255, 255)
BLACK = (0, 0, 0)

# Set up pygame
pygame.init()
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Game of Life")

# Function to draw a block
def draw_block(x, y, color):
    pygame.draw.rect(screen, color, (x, y, BLOCK_SIZE, BLOCK_SIZE))

# Function to draw the grid
def draw_grid(grid):
    screen.fill(BLACK)
    for r in range(ROWS):
        for c in range(COLS):
            if grid[r][c]:
                draw_block(c * BLOCK_SIZE, r * BLOCK_SIZE, WHITE)
    pygame.display.flip()

# Function to generate a random grid
def generate_grid(rows, cols):
    return [[random.choice([0, 1]) for _ in range(cols)] for _ in range(rows)]

# Function to count the live neighbors
def count_live_neighbors(grid, r, c):
    live_neighbors = 0
    for i in range(max(0, r-1), min(len(grid), r+2)):
        for j in range(max(0, c-1), min(len(grid[0]), c+2)):
            if (i, j) != (r, c) and grid[i][j] == 1:
                live_neighbors += 1
    return live_neighbors

# Function to run the game of life
def game_of_life(grid):
    result = [[0 for _ in range(len(grid[0]))] for _ in range(len(grid))]
    for r in range(len(grid)):
        for c in range(len(grid[0])):
            live_neighbors = count_live_neighbors(grid, r, c)
            if grid[r][c] == 1 and live_neighbors in [2, 3]:
                result[r][c] = 1
            elif grid[r][c] == 0 and live_neighbors == 3:
                result[r][c] = 1
    return result

# Function to run the main loop
def main():
    grid = generate_grid(ROWS, COLS)
    while True:
        draw_grid(grid)
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                pygame.quit()
                return
        grid = game_of_life(grid)

if __name__ == "__main__":
    main()

