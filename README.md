# sudoku-game
from dokusan import generators
import numpy as np
arr=np.array(list(str(generators.random_sudoku(avg_rank=150))))
grid=arr.reshape(9,9)
print(grid)
def is_valid(grid,row,col,number):
  for x in range(9):
    if grid[row][x]==number:
      return False
  for x in range(9):
    if grid[x][col]==number:
      return False
  corner_row= row -row % 3
  corner_col=  col-col % 3
  for x in range(3):
    for y in range(3):  
      if grid[corner_row + x][corner_col + y] ==number:
        return False
  return True







  
