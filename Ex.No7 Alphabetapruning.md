# Ex.No: 7   Implementation of Alpha Beta Pruning 
### DATE:                                                                            
### REGISTER NUMBER : 
### AIM: 
Write a Alpha beta pruning algorithm to find the optimal value of MAX Player from the given graph.
### Steps:
1. Start the program
2. Initially  assign MAX and MIN value as 1000 and -1000.
3.  Define the minimax function  using alpha beta pruning
4.  If maximum depth is reached then return the score value of leaf node. [depth taken as 3]
5.  In Max player turn, assign the alpha value by finding the maximum value by calling the minmax function recursively.
6.  In Min player turn, assign beta value by finding the minimum value by calling the minmax function recursively.
7.  Specify the score value of leaf nodes and Call the minimax function.
8.  Print the best value of Max player.
9.  Stop the program. 

### Program:

```
INF = float('inf')

def alpha_beta_pruning(depth, node_index, maximizing_player, values, alpha, beta, max_depth):
    if depth == max_depth:
        return values[node_index]

    if maximizing_player:
        max_eval = -INF
        left_child = node_index * 2
        right_child = node_index * 2 + 1
        if left_child < len(values):
            eval = alpha_beta_pruning(depth + 1, left_child, False, values, alpha, beta, max_depth)
            max_eval = max(max_eval, eval)
            alpha = max(alpha, eval)
        if right_child < len(values):
            eval = alpha_beta_pruning(depth + 1, right_child, False, values, alpha, beta, max_depth)
            max_eval = max(max_eval, eval)
            alpha = max(alpha, eval)
        return max_eval
    
    else:
        min_eval = INF
        left_child = node_index * 2
        right_child = node_index * 2 + 1
        if left_child < len(values):
            eval = alpha_beta_pruning(depth + 1, left_child, True, values, alpha, beta, max_depth)
            min_eval = min(min_eval, eval)
            beta = min(beta, eval)
        if right_child < len(values):
            eval = alpha_beta_pruning(depth + 1, right_child, True, values, alpha, beta, max_depth)
            min_eval = min(min_eval, eval)
            beta = min(beta, eval)
        return min_eval

# New list of values
values = [4, 7, 1, 8, 5, 6, 9, 3]
max_depth = 3

print("The optimal value is : ", end="")
print(alpha_beta_pruning(0, 0, True, values, -INF, INF, max_depth))

```









### Output:

![7)](https://github.com/user-attachments/assets/f9ee91e5-4e25-4404-b29e-82460b34e0ca)


### Result:
Thus the best score of max player was found using Alpha Beta Pruning.
