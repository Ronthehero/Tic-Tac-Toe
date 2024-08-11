import random

def print_board(board):
    for row in board:
        print(" | ".join(row))
        print("-" * (len(row) * 4 - 1))

def check_winner(board, player):
    for row in board:
        if all(cell == player for cell in row):
            return True

    for col in range(len(board[0])):
        if all(row[col] == player for row in board):
            return True

    if all(board[i][i] == player for i in range(len(board))) or all(board[i][len(board) - 1 - i] == player for i in range(len(board))):
        return True

    return False

def is_board_full(board):
    return all(cell != " " for row in board for cell in row)

def get_bot_move(board):
    # Simple bot: randomly select an available move
    available_moves = [(row, col) for row in range(len(board)) for col in range(len(board[0])) if board[row][col] == " "]
    return random.choice(available_moves)

def choose_board_size():
    while True:
        print("Choose your board size:")
        print("1. 3x3")
        print("2. 4x4")
        print("3. 5x5")
        choice = input("Enter 1, 2, or 3: ")
        if choice in ["1", "2", "3"]:
            return int(choice) + 2  # Adding 2 to get the size (3, 4, or 5)
        else:
            print("Invalid choice. Please enter 1, 2, or 3.")

def get_player_move(board_size):
    while True:
        try:
            position = int(input(f"Enter a position (1-{board_size ** 2}): "))
            if 1 <= position <= board_size ** 2:
                row = (position - 1) // board_size
                col = (position - 1) % board_size
                return row, col
            else:
                print("Invalid position. Try again.")
        except ValueError:
            print("Invalid input. Enter a number.")

def offline_multiplayer(board_size):
    board = [[" " for _ in range(board_size)] for _ in range(board_size)]
    current_player = "X"

    print(f"Welcome to {board_size}x{board_size} Tic Tac Toe (Offline Multiplayer)!")
    
    while True:
        print_board(board)

        row, col = get_player_move(board_size)

        if board[row][col] != " ":
            print("Invalid move. Position already taken. Try again.")
            continue

        board[row][col] = current_player

        if check_winner(board, current_player):
            print_board(board)
            print(f"Player {current_player} wins!")
            break

        if is_board_full(board):
            print_board(board)
            print("It's a draw!")
            break

        current_player = "X" if current_player == "O" else "O"

def main():
    print("Welcome to Tic Tac Toe!")
    print("Choose your game mode:")
    print("1. Offline Multiplayer")

    choice = input("Enter 1: ")

    if choice == "1":
        board_size = choose_board_size()
        offline_multiplayer(board_size)

    else:
        print("Invalid choice. Please enter 1.")

if __name__ == "__main__":
    main()
