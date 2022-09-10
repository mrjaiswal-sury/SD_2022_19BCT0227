# Chess_Console for Software Developer Task


I have made this game which runs on a console, i.e., that means no GUI is available to the user. All the input is taken from the keyboard, and for that, it uses the Coordinate Notation.
Co-ordinate Notion is used to find the co-ordinates or the reflection of a point in C++

The white pieces are represented by capital letters and the black pieces are represented in lowercase letters. They are all represented by the first letter of their names, the only exception being the Knight, which is represented by an N, leaving the K for the king

Pawn
Rook
Knight
Bishop
Queen
King

I have used ASCII characters 0xDB and 0xFF to draw white and black cells, respectively

First, I decided how big I want the squares do be, After looking through some samples i decided the height of one square should equal to three characters (For better GUI experience)
Now, I faced a problem here as the mentioned characters (0xDB and 0xFF) are not squared; they are actually rectangular with one side being twice as big as the other. This means that, in order to form a square, we have to use six characters in a row.

The code consists of three .cpp files:

main.cpp: Entry-point of the application. Prompts the user for an action (new game, move, undo, save, load, quit) and, depending on the action to be performed, prompts for more information and call the functions from the other files.
chess.cpp: consists of two classes. The first one is named Chess and contains enums, structs and simple functions to describe chess pieces, colors and the board. The second one is called Game, it inherits from Chess. It stores all the information that a single game has, like the position of every piece in the board, list of moves made, list of pieces captured. It also contained functions to determine if the king is in check, if castling is allowed, if a square is occupied, everything that is necessary to verify if a move is valid or not.
user_interface.cpp: Basically consists of functions printing information to the console, like printing the board, last moves, menu, messages for the user, etc.

For storing moves i used some of the containers provided by C++ to store the game information. But first, I created a simple structure that stores one white and one black move. Each move is a tring that contains the position of the piece to be moved, followed by a dash, and the destination square. For the captured pieces, these are stored in vectors:

#Starting a New Game
Start the app and press N, followed by ENTER, to start a new game. The board is shown and it's WHITE turn.

#Make a Move
Type M to make a move.

You will be prompted to choose a piece to be moved. Do it by entering two characters (uppercase or lowercase will give the same results) describing first the column, then the row where the piece you want to be moved currently is. For example, the white pawn in front of the king is the E2 square.

Next, you'll be prompted for the destination square. One of the most common moves is moving the pawn from E2 to E4.

You will be warned if the move is invalid.
#The conditions for move to be invalid are -

Input command on a character that does not exist
Character going out of grid bounds.
Invalid move presented for a given character.
Targeting a friendly character, i.e a character from our own team.

#Undo a Move
Simply type U followed by ENTER to undo the last move. It is possible to undo only the very last move.

#Checkmate
After every move, we must check if a checkmate has taken place. These are the steps to be followed:

Is the king in check? If not, no need to check any further.the code stops
Can the king move to another square? If the king can move to another square and not be under attack anymore, than it's not checkmate.
Can the attacker be taken or another piece get in the way? If the attacker can be taken, then it's not a checkmate. If it can't, there's still the possibility for another piece to get in the middle of the way between the attacker and the king.
If the answers to questions two and three are NO, then it's a checkmate and the game is over!

#Saving the game 
Save a game is useful if you want to finish it later, but also it is an incredibly useful debugging tool. When the user types 'S' on the menu to save the game, he's prompted for a name. The application will create (or override) a file called 'name_entered.dat' on the same directory as the executable. You can open the file with notepad++ and have a look

#Time and date were included for debugging purposes.

Thank you


