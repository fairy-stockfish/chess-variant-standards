
# FEN

## Standard fields

### 1. Piece placement
* Pieces after a shogi style promotion are **prefixed** by a `+`.
* Promoted pawns are **suffixed** by `~` if the promotion status is relevant for the game, e.g., for crazyhouse since promoted pawns demote on capture when going to the opponent's hand. In games where promoted pawns are commonly differentiated for displaying purposes, like makruk, this information can optionally be provided.
* In games with 10 or more ranks, the spaces between pieces on the board in an FEN can reach double digit numbers. In this case the FEN still contains the space as this double digit number, e.g., `rnabqkbcnr/pppppppppp/10/10/10/10/PPPPPPPPPP/RNABQKBCNR w KQkq - 0 1`.
* Pieces in hand are specified after the board pieces surrounded by square brackets `[]`, e.g., `rnbqkb1r/ppp2ppp/5p2/3p4/8/8/PPPP1PPP/RNBQKBNR[Np] w KQkq - 0 4`. It is common to list the hand pieces in inverse order of value, but the order is not defined per specification. The notation for pieces in hand applies to S-Chess style gating pieces as well.
  * Note that a common exception to this standard is that lichess uses a `/` instead of square brackets to separate the hand pieces from the board pieces, e.g., `rnbqkb1r/ppp2ppp/5p2/3p4/8/8/PPPP1PPP/RNBQKBNR/Np w KQkq - 0 4`. It is recommended to support this non-standard notation as input, but it is discouraged to follow this when outputting FENs.

### 2. Color
The color field is denoted as `w` or `b` as for standard chess FENs.

### 3. Castling
In chess variants the FEN castling field retains its original role, but might be extendend with additional information.
* For S-Chess style gating rights, the castling field contains the letter of each first rank square where gating is still possible. Redundancies with castling fields are removed, since castling always indicates an unmoved king and rook. E.g., the S-Chess starting position is `rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR[HEhe] w KQBCDFGkqbcdfg - 0 1`.
  * Note that in the case of 960 variants with gating the situation can arise that gating on the rook square is still allowed, but castling no longer is due to a king move. In this case an `A` castling right in contrast to normal Chess960 doesn't refer to a castling right but only to gating, and only if, e.g., `AE` is present it means that both the rook and king are unmoved, so castling is possible as well. Therefore castling is encoded as the combination of a king and rook gating right.
* Special extra moves that are lost once a piece moves for the first time like in Ouk Chatrang can also be encoded in the castling field with the letter of the file of the respective piece. 

### 4. En passant
The en passant field can naturally be generalized by using the respective crossed square of any pawn double step, irrespective of its rank. Note that in the CECP/xboard protocol, for FENs of variants with 10 ranks the en passant square uses a zero-based rank counting, just like the moves. For berolina pawns the en passant field contains both the crossed square and the target square of the berolina double step, e.g., `e3d4`, in order to disambiguate between two pawns that might both have crossed the same square via a double step, e.g., moves f2-d4 and d2-f4 for the e3 square.

For variants with endgame counting rules and where there is no en passant, such as Makruk, the en passant field is instead used in order to specify the counting limit in ply, e.g., `128` for 64 moves. In case no counting rule is active the field is `0` or `-`.

### 4.5. Check count (optional)
Usually after the en passant field follows the halfmove clock. However, for variants with check counting, such as 3check, the check counts are an additional field inbetween. This does not apply for variants where the first check wins, since the counts are the same for all non-final positions. In order to be able to represent arbitrary check counting variants, the check counting field specifies the number of remaining checks for the winning condition, separated by a `+`, e.g., `rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR w KQkq - 3+3 0 1` for the 3check starting position.

Note that lichess uses a different format incompatible with this standard. Instead of adding the remaining checks, it specifies the count of given checks for each side after a `+`. E.g., the 3check starting position looks like `rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR w KQkq - 0 1 +0+0`. Therefore it is recommended to support this non-standard notation as input, but it is discouraged to follow this when outputting FENs.

### 5. Halfmove clock
For variants with endgame counting rules, such as Makruk, the halfmove clock is used to specify the current count in ply. In case no counting rule is active the field specifies the usual halfmove clock as for all other variants.

### 6. Fullmove clock
The fullmove clock is the same as for standard chess FENs.
