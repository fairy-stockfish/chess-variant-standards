# Chess variant standards

This is an overview of standards used for chess variants. Most standards are taken over from chess with minor extensions and modifications, but the differences often are not documented, so this page tries to fill this gap.

## PGN
The [Portable Game Notation](https://en.wikipedia.org/wiki/Portable_Game_Notation) is a standard for recording chess games, see its [specification](https://ia802908.us.archive.org/26/items/pgn-standard-1994-03-12/PGN_standard_1994-03-12.txt). For chess variants it can be naturally extended by generalizing the move and position notation, i.e., SAN and FEN. The main addition is the `Variant` header tag containing the capitalized variant name in order to specify the variant the game record is using.

See the [PGN subpage](/pgn.md) for details.
## FEN
The [Forsyth-Edwards Notation]() for standard chess is specified in the [PGN standard](https://ia802908.us.archive.org/26/items/pgn-standard-1994-03-12/PGN_standard_1994-03-12.txt). For chess variants FEN can be naturally extended by allowing arbitrary piece characters and board sizes. For specific rule modifications some extensions and modifications are required, such as for chess counting, S-Chess gating, counting rules, and the like.

See the [FEN subpage](/fen.md) for details.
## SFEN
The specification of the [Shogi Forsyth-Edwards Notation](https://en.wikipedia.org/wiki/Shogi_notation#SFEN) is part of the [USI protocol specification](http://hgm.nubati.net/usi.html).
## EPD
https://ia802908.us.archive.org/26/items/pgn-standard-1994-03-12/PGN_standard_1994-03-12.txt
## SAN
https://ia802908.us.archive.org/26/items/pgn-standard-1994-03-12/PGN_standard_1994-03-12.txt
## UCI
https://www.shredderchess.com/chess-features/uci-universal-chess-interface.html
http://wbec-ridderkerk.nl/html/UCIProtocol.html
## USI
The Universal Shogi Protocol is defined in the [USI protocol specification](http://hgm.nubati.net/usi.html).
## UCCI
## UCI-cyclone
## CECP
https://www.gnu.org/software/xboard/engine-intf.html
http://hgm.nubati.net/CECP.html
http://hgm.nubati.net/newspecs.html
## coordinate notation
https://www.shredderchess.com/chess-features/uci-universal-chess-interface.html
http://wbec-ridderkerk.nl/html/UCIProtocol.html

