board = [
    [" ", " ", " "],
    [" ", " ", " "],
    [" ", " ", " "]
]

def print_board():
    for row in board:
        print("|" + "|".join(row) + "|")

def make_move(player):
    x = int(input("Jogador %s, escolha a linha: " % player))
    y = int(input("Jogador %s, escolha a coluna: " % player))
    if board[x][y] != " ":
        print("Posição já ocupada!")
        return make_move(player)
    else:
        board[x][y] = player

def has_winner():
    for row in board:
        if row[0] == row[1] == row[2] and row[0] != " ":
            return row[0]
    for col in range(3):
        if board[0][col] == board[1][col] == board[2][col] and board[0][col] != " ":
            return board[0][col]
    if board[0][0] == board[1][1] == board[2][2] and board[0][0] != " ":
        return board[0][0]
    if board[0][2] == board[1][1] == board[2][0] and board[0][2] != " ":
        return board[0][2]
    if not any(" " in row for row in board):
        return "Empate"
    return None

print_board()
while not has_winner():
    make_move("X")
    print_board()
    if has_winner():
        break
    make_move("O")
    print_board()

winner = has_winner()
if winner == "Empate":
    print("O jogo terminou em empate!")
else:
    print("O jogador %s venceu!" % winner)
