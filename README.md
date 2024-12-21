# Pokerface

**Version:** v2024.06.10  
**Authors:** Derek Tang, Peter Nguyen, Mharlo Borromeo, Jack Lu, Calvin Nguyen, and Mervin Nguyen\
**Last Modified:** June 10, 2024\
© 2004 - 2024 PretendGINEERS. All Rights Reserved.

---

## General Instructions

- Please follow the instructions stated in the `INSTALL` file for detailed instructions on how to install (downloading `.tar` files, unpack/extract using `gtar`) and run the program.
- To run the program, navigate to the `bin/` directory and run the main executables on different servers/accounts.
- To start, connect the client to the server's port, then connect the server to the port the client is connected to.

**Example:**
- Step #1: Run `./pokerserver [port number]` on an SSH client, taking care to use ports 10080-10089.
- Step #2: On a different instance of an SSH client or in a separate SSH client, run `./pokerclient [hostname] [port number]` to connect to the running server, taking care to use ports 10080-10089.
- After executing `./pokerclient`, use the ASCII interface to send messages to the server.

---

## V1.0 Version Notes

- In the GUI, the player actions are represented by integers:
    - `0`: No Action  
    - `1`: Folded  
    - `2`: Called  
    - `3`: Raised  
    - `4`: All In
- The game logic, client/server, and GUI teams completed their portions of the code, but we were unable to join them together in this version. To test each portion separately, please run all unit tests individually in the `bin/` directory.
- The GUI works separately with updates based on an agreed-upon string format and outputs a string based on user inputs.

---

## BONUS POINTS: Bonus points will be awarded in the following categories:

- **+5 points:** Better-than-basic login options  
    - Username and password are entered in the GUI  
    - Password is hidden after keys are entered  
    - Dropdown menu for seat selection
- **+10 points:** Better-than-basic graphics and style  
    - Mimicked a poker table for the game  
    - Professional-looking backgrounds, cards, and dealer chip
- **+5 points:** Scoreboard at the end of the game  
    - Points for each player are displayed throughout the game
- **+10 points:** Other fun options  
    - The background images aren’t created using GTK Widgets but are directly changed by changing the style of a GTK EventBox

---

## String Format between Server/Client

### Client to Server:
Notation:  
`Username: username; Password: password; Seat: (1-4); Fold: (boolean); Call: (boolean); Raise: (int); All In: (boolean);`

**Example:**  
`Username: Test; Password: Test; Seat: 1; Fold: 0; Call: 0; Raise: 100; All In: 0`

### Server to Client:
Note:
- `0`: No Action  
- `1`: Fold  
- `2`: Call  
- `3`: Raise  
- `4`: All In

Notation:\
`Dealer Cards: card1, card2, card3, card4, card5;`  
`Player#1: Name, (int) Points, (int) Current_Bet, (boolean) Is In Game, (int) Action, (boolean) Turn, (boolean) Dealer Chip, card1, card2; ... (for the other players)`  
`Side Pot: (int) total side pot`  
`Dealer: Message from dealer/server;`

**Example:**  
`Dealer Cards: king_of_diamonds, ace_of_spades, back_of_card, back_of_card, back_of_card; Player#1: Alex, 800, 200, 1, 1, 0, 1, back_of_card, back_of_card; Player#2: Bob, 1000, 0, 0, 0, 0, 0, back_of_card, back_of_card; Player#3: Max, 1000, 0, 0, 0, 0, 0, back_of_card, back_of_card; Player#4: Cry, 900, 100, 1, 2, 1, 0, back_of_card, back_of_card; Side Pot: 300; Dealer: Here comes the turn!;`

---

## README For USERS

[For more details, see `Poker_UserManual.pdf` located in the `doc/` directory]

### Poker_Beta.tar.gz Contents:

- **bin/**: Directory containing all the executables  
    - `pokerserver`: Main poker executable for the server  
    - `pokerclient`: Main poker executable for the client  
- **doc/**: Directory with the user documentation  
    - `Poker_UserManual.pdf`: Detailed user manual for the user  
- `INSTALL`: Installation directions  
- `COPYRIGHT`: Licensing by PretendGINEERS Studios & PretendGINEERS Software Inc.  
- `README`: README for Pokerface

---

## README FOR PROGRAMMERS

[For more details, see `Poker_SoftwareSpec.pdf` located in the `doc/` directory]

### Top-Level Make Commands:

- `make all`: Create the main executables and place them in the `bin/` directory
- `make test`: Create the test executables and place them in the `bin/` directory
- `make test-gui`: Create the unit test for the GUI and run it (Requires XMing)
- `make test-gamelogic`: Test game logic
- `make test-comm`: Test communication
- `make test-client`: Test the client
- `make test-server`: Test the server
- `make clean`: Clean up excess files
- `make tar`: Generate the `.tar.gz` files for the user/programmer

### Poker_Beta_src.tar.gz Contents:

- **bin/**: Directory containing all the executables  
    - `pokerserver`: Main poker executable for the server  
    - `pokerclient`: Main poker executable for the client  
- **doc/**: Directory with the user and software documentation  
    - `Poker_SoftwareSpec.pdf`: Detailed software specifications for the programmer  
    - `Poker_UserManual.pdf`: Detailed user manual for the user  
- **src/**: Directory containing all the C files and Makefile  
    - `gui_images/`: Directory with images needed by the GUI  
    - `client.c`: Functions for the client  
    - `client.h`: Header file for `client.c`  
    - `constants.h`: File with all the macros  
    - `gamelogic.c`: Functions for the game logic  
    - `gamelogic.h`: Header file for `gamelogic.c`  
    - `gui.c`: Functions for the GUI  
    - `gui.h`: Header file for `gui.c`  
    - `Makefile`: Makefile to create the executables  
    - `pokerclient.c`: Main executable for the client  
    - `pokerserver.c`: Main executable for the server  
    - `server.c`: Functions for the server  
    - `server.h`: Header file for `server.c`  
    - `structures.h`: File with structure definitions  
    - `unit_test_client.c`: Unit test for the client  
    - `unit_test_gamelogic.c`: Unit test for game logic  
    - `unit_test_gui.c`: Unit test for the GUI  
    - `unit_test_server.c`: Unit test for the server  
- `INSTALL.TXT`: Installation directions  
- `LICENSE.TXT`: Licensing by PretendGINEERS Studios & PretendGINEERS Software Inc.  
- `Makefile`: Top-level Makefile  
- `README`: README for Pokerface