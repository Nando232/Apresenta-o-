# Apresenta-o-# Jogo da Velha em Python

def print_board(board):
    print(' ' + board[0] + ' | ' + board[1] + ' | ' + board[2])
    print('---|---|---')
    print(' ' + board[3] + ' | ' + board[4] + ' | ' + board[5])
    print('---|---|---')
    print(' ' + board[6] + ' | ' + board[7] + ' | ' + board[8])

def check_winner(board, player):
    win_conditions = [
        [0, 1, 2], [3, 4, 5], [6, 7, 8], # Linhas
        [0, 3, 6], [1, 4, 7], [2, 5, 8], # Colunas
        [0, 4, 8], [2, 4, 6]              # Diagonais
    ]
    for condition in win_conditions:
        if all(board[i] == player for i in condition):
            return True
    return False

def is_full(board):
    return all(space != ' ' for space in board)

def main():
    board = [' '] * 9
    current_player = 'X'
    while True:
        print_board(board)
        move = int(input(f'Jogador {current_player}, escolha uma posição (0-8): '))
        if board[move] == ' ':
            board[move] = current_player
            if check_winner(board, current_player):
                print_board(board)
                print(f'Jogador {current_player} venceu!')
                break
            if is_full(board):
                print_board(board)
                print('Empate!')
                break
            current_player = 'O' if current_player == 'X' else 'X'
        else:
            print('Posição já ocupada! Tente novamente.')

if __name__ == "__main__":
    main()
