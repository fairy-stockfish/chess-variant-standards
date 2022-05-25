
# FEN

## Standard fields

### 1. Piece placement
* Pieces after a shogi style promotion are **prefixed** by a `+`
* Promoted pawns are **suffixed** by `~` if the promotion status is relevant for the game, e.g., for crazyhouse since promoted pawns demote on capture when going to the opponent's hand. In games where promoted pawns are commonly differentiated for displaying purposes, like makruk, this information can optionally be provided.
* In games with 10 or more ranks, the spaces between pieces on the board in an FEN can reach double digit numbers. In this case the FEN still contains the space as this double digit number, e.g., `rnabqkbcnr/pppppppppp/10/10/10/10/PPPPPPPPPP/RNABQKBCNR w KQkq - 0 1`.
* Pieces in hand are specified after the board pieces surrounded by square brackets `[]`, e.g., `rnbqkb1r/ppp2ppp/5p2/3p4/8/8/PPPP1PPP/RNBQKBNR[Np] w KQkq - 0 4`. It is common to list the hand pieces in inverse order of value, but the order is not defined per specification. The notation for pieces in hand applies to S-Chess style gating pieces as well.
  * Note that a common exception to this standard is that lichess uses a `/` instead of square brackets to separate the hand pieces from the board pieces, e.g., `rnbqkb1r/ppp2ppp/5p2/3p4/8/8/PPPP1PPP/RNBQKBNR/Np w KQkq - 0 4`. Therefore it is recommended to support this non-standard notation as input, but it is discouraged to follow this when outputting FENs.

### 2. Color
The color field is denoted as `w` or `b` as for standard chess FENs.

### 3. Castling
* gating
* extra moves (cambodian)

### 4. En passant
* berolina
* counting limit

### 4.5. Check count (optional)

### 5. Halfmove clock
* counting ply

### 6. Fullmove clock
The fullmove clock is the same as for standard chess FENs.

## Non-standard fields

### 7. Lichess check count (optional)
