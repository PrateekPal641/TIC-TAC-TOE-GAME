# TIC-TAC-TOE-GAME
def display_board(board):
    print(board[1]+'  |  '+board[2]+'  |  '+board[3])
    print('-------------')
    print(board[4]+'  |  '+board[5]+'  |  '+board[6])
    print('-------------')
    print(board[7]+'  |  '+board[8]+'  |  '+board[9])
    
 def place_marker(board,marker,position):
     board[position] = marker
 
 def player_input():
     marker = ''
     while not(marker == 'X' or marker == 'O'):
        marker = input("Choose a Marker(X/O): ").upper()
        
     if marker == 'X':
        return ('X','O')
     else:
        return ('O','X')  
        
 def win_check(board,mark):
     return((board[1]==board[2]==board[3]==mark)or(board[4]==board[5]==board[6]==mark)or(board[7]==board[8]==board[9]==mark)or
     (board[1]==board[4]==board[7]==mark)or(board[2]==board[5]==board[8]==mark)or(board[3]==board[6]==board[9]==mark)or
     (board[1]==board[5]==board[9]==mark)or(board[3]==board[5]==board[7]==mark))
    
 import random

def choose_first():
    flip = random.randint(0,1)
    if flip == 0:
        return 'PLAYER 1'
    else:
        return 'PLAYER 2'
def space_check(board,position):
    return board[position]==' '
    
def full_board_check(board):
    for i in range(1,9):
        if space_check(board,i) :
            return False
    return True  
    
def player_choice(board):
    position = 0
    while position not in[1,2,3,4,5,6,7,8,9] or not  space_check(board,position):
        position = int(input('choose a position(1-9): '))
        return position

def replay():
    input('PLAY AGAIN? yes or no').upper()
    return choice=='YES'

print('WELCOME TO TIC TAC TOE!')
while True:
    the_board = [' ']*10
    (Player1_marker,Player2_marker) = player_input()
    turn = choose_first()
    print(turn + 'will go first')
    play_game = input('READY TO PLAY(Y/N)?').upper()
    if play_game == 'Y':
        game_on = True
    else:
        game_on = False
    while game_on:
        if turn == 'PLAYER 1':
            display_board(the_board)
            position = player_choice(the_board)
            place_marker(the_board,Player1_marker,position)
            if win_check(the_board,Player1_marker):
                display_board(the_board)
                print('PLAYER 1 HAS WON :) !!')
                game_on = False
            else:    
                if full_board_check(the_board):
                    display_board(the_board)
                    print('TIE :( ')
                    game_on = False
                else:
                    turn = 'Player 2'
            
        else:
            display_board(the_board)
            position = player_choice(the_board)
            place_marker(the_board,Player2_marker,position)
            if win_check(the_board,Player2_marker):
                display_board(the_board)
                print('PLAYER 2 HAS WON :) !!')
                game_on = False
            else:    
                if full_board_check(the_board):
                    display_board(the_board)
                    print('TIE :( ')
                    game_on = False
                    break
                else:
                    turn = 'PLAYER 1'
                    
                    
    
