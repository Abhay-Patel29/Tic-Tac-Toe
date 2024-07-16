# intern1
#python code of tic tac toe
def print_board(board):
    for row in board:
        print(" | ".join(row))
        print("-"*5)

def check_win(board, player):
    #check rows
    for row in board:
        if all(s == player for s in row):
            return True
    #checck columns
    for col in range(3):
        if all(row[col] == player for row in board):
            return True
        if all(board[i][2 - i] == player for i  in range(3)):
            return True
        return False

def check_draw(board):
    return all(all(cell != " " for cell in row)for row in board)

def tic_tac_toe():
    board = [[" " for _ in range(3)]for _ in range(3)]
    current_player = "X"
    while True:
        print_board(board)
        #get player input
        try:
            row=int(input(f"Player {current_player}, enter the row(0,1,2): "))
            col=int(input(f"Player {current_player}, enter the column(0,1,2): "))
        except valueError:
            print("Invalid input, Please enter number between o and 2:")
            continue
        if board[row][col] !=" ":
            print("Cell already taken, Try again")
            continue
        #update board
        board[row][col] = current_player
        #check for win or draw
        if check_win(board,current_player):
            print_board(board)
            print(f"Player {current_player} wins!")
            break
        elif check_draw(board):
            print_board(board)
            print("It's a draw!")
            break
        #switch player
        current_player = "0" if current_player == "X" else "X"
if __name__ == "__main__":
    tic_tac_toe()
