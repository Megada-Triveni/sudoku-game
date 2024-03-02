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
def solve(grid,row,col):
  if col ==9:
    if row== 0:
      return True
    row+=1
    col=0
  if grid[row][col]>0:
    return solve(grid,row,col+1)
  for num in range(1,10):
    if is_valid(grid,row,col,number):
      grid[row][col]=num
      if solve(grid,row,col+1):
        return True
      grid[row][col]=0
  return True
if solve(grid,0,0):
  for i range(9):
    for j range(9):
      print(grid[i][j],end=" ")
else:
  print("No solution")






  
