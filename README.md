# Chess Piece Classification with CNN

## The data

The images come from a classic book on chess published in the early 20th century, Chess Fundamentals, José Raúl Capablanca (1921).

There are two types of data.

1. *Image files*. These are `jpg` images of chessboard diagrams. The images have all be pre-processed to be exactly 400 by 400 pixels, i.e., each square is 50 by 50 pixels.
2. *Label files*. There are two label files: `boards.train.json` which provides labels for the training data, and `boards.dev.json` which provides labels for the test data. They are stored in JSON format and contain a list of dictionaries. Each dictionary represents one board and has the structure shown below,

```json
 {
    "image": "capablanca/078.jpg",
    "fen": "2R5/p4p1k/5p1p/6r1/5K2/4P2P/Pr4P1/7R",
    "board": [
      "..R.....",
      "p....p.k",
      ".....p.p",
      "......r.",
      ".....K..",
      "....P..P",
      "Pr....P.",
      ".......R"
    ]
  },
```

In the dictionary, the fields have the following meaning:

- `image` field is the name of the board image.
- `fen` is a representation of the board in FEN notation. This field is not used.
- `board` is a string representation of the board.

The string representation is interpreted as follows. A list of 8 strings provides the state of each board row. Each string is a sequence of 8 characters, one per each square in the row. The `.` represents an empty square. Uppercase letters represent white pieces, and lowercase letters are black pieces. The letters have the following meaning: k = king, q = queen, r = rook, n = knight, b = bishop and p = pawn.

There is also a dataset in which the images have been corrupted, i.e., by the addition of artificial noise.