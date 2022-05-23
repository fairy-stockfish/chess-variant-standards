# Chess variant standards

This is an overview of standards used for chess variants. Most standards are taken over from chess with minor extensions and modifications, but the differences often are not documented, so this page tries to fill this gap.

## Game records
### PGN
The [Portable Game Notation](https://en.wikipedia.org/wiki/Portable_Game_Notation) is a standard for recording chess games, see its [specification](https://ia802908.us.archive.org/26/items/pgn-standard-1994-03-12/PGN_standard_1994-03-12.txt). For chess variants it can be naturally extended by generalizing the move and position notation, i.e., SAN and FEN. The main addition is the `Variant` header tag containing the capitalized variant name in order to specify the variant the game record is using.

## Position description
### FEN
The [Forsyth-Edwards Notation]() for standard chess is specified in the [PGN standard](https://ia802908.us.archive.org/26/items/pgn-standard-1994-03-12/PGN_standard_1994-03-12.txt). For chess variants FEN can be naturally extended by allowing arbitrary piece characters and board sizes. For specific rule modifications some extensions and modifications are required, such as for check counting, S-Chess gating, counting rules, and the like.

See the [FEN subpage](/fen.md) for details.
### SFEN
The specification of the [Shogi Forsyth-Edwards Notation](https://en.wikipedia.org/wiki/Shogi_notation#SFEN) is part of the [USI protocol specification](http://hgm.nubati.net/usi.html).
### EPD
The [Extended Position Description](https://www.chessprogramming.org/Extended_Position_Description) for chess variants does not have any variant-specific modifications other than applying all the changes as for FEN. Apart from that the EPD specification defined in the [PGN standard](https://ia802908.us.archive.org/26/items/pgn-standard-1994-03-12/PGN_standard_1994-03-12.txt) for chess applies. It is recommended to add a `variant` operation in order to specify the variant name.

## Move description
### SAN
The [Short/Standard Algebraic Notation](https://www.chessprogramming.org/Algebraic_Chess_Notation#Standard_Algebraic_Notation_.28SAN.29) for standard chess is specified in the [PGN standard](https://ia802908.us.archive.org/26/items/pgn-standard-1994-03-12/PGN_standard_1994-03-12.txt). For chess variants there are several extensions in order to represent special moves, such as piece drops and gating.
### Coordinate notation
The [pure coordinate notation](https://www.chessprogramming.org/Algebraic_Chess_Notation#Pure_coordinate_notation) is specified as part of the [UCI protocol](https://www.shredderchess.com/chess-features/uci-universal-chess-interface.html) (also [here](http://wbec-ridderkerk.nl/html/UCIProtocol.html)). For chess variants it requires extensions in order to describe piece drops, gating, and shogi-style piece promotions.

## Engine protocols
### UCI
The [Universal Chess Interface](https://en.wikipedia.org/wiki/Universal_Chess_Interface) is a chess engine protocol specified [here](https://www.shredderchess.com/chess-features/uci-universal-chess-interface.html) ([older version](http://wbec-ridderkerk.nl/html/UCIProtocol.html)). For chess variants it only requires an additional convention which UCI option to use to set the variant, which is `UCI_Variant`, and it uses the generalized FEN and coordinate notation as described above. The `UCI_Chess960` option for chess variants is used as a general switch to Chess960 style castling rules and notation in both the FEN (`KQkq` -> `AHah`) and coordinate notation (`e1g1` -> `e1h1`).

### USI
The Universal Shogi Protocol is a dialect of the UCI protocol for Shogi defined in the [USI protocol specification](http://hgm.nubati.net/usi.html).
### UCCI
The Universal Chinese Chess Interface is a dialect of the UCI protocol for Xiangqi. It skips the `name` and `value` keywords in the reporting of options and instead requires option names not to contain spaces in order to disambiguate parsing of tokens. It uses a move coordinate notation using ranks 0-9 instead of 1-10.
### UCI-cyclone
The UCI-cyclone protocol is a modification of the UCI protocol for Xiangqi. It uses a move coordinate notation using ranks 0-9 instead of 1-10 and it skips the `position` keyword in commands to set up the board position.
### CECP
There are several specifications of the [Chess Engine Communication Protocol](https://www.chessprogramming.org/Chess_Engine_Communication_Protocol) [here](https://www.gnu.org/software/xboard/engine-intf.html), [here](http://hgm.nubati.net/CECP.html), and [here](http://hgm.nubati.net/newspecs.html). It by the specification already supports chess variants.

