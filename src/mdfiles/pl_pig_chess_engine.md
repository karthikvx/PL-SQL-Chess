# PL_PIG_CHESS_ENGINE Package

## Method Signatures and Code Behavior

### `STILLING_TO_EPD` Function

```plsql
FUNCTION STILLING_TO_EPD(
    stilling PL_PIG_CHESS_ENGINE_EVAL.STILLINGTYPE,
    operationlist VARCHAR2 DEFAULT NULL
) RETURN VARCHAR2;
```

**Behavior:**
- Converts a position from internal array format to a string in EPD format.
- Allows for the addition of EPD operations, such as 'bm Nf3; id "test1";'.

### `FEN_EPD_TO_STR` Function

```plsql
FUNCTION FEN_EPD_TO_STR(
    FEN_EPD VARCHAR2
) RETURN VARCHAR2;
```

**Behavior:**
- Converts a position in FEN or EPD format to POSITIONSTR format.

### `still` Procedure

```plsql
PROCEDURE still(
    stilling in out PL_PIG_CHESS_ENGINE_EVAL.STILLINGTYPE,
    p_st char DEFAULT ''
);
```

**Behavior:**
- Sets up a position from a string in POSITIONSTR format.
- Converts to internal format if standard FEN or EPD format is detected.
- Accepts English format and translates it to the internal format.

### `DoMoveOk` Function

```plsql
FUNCTION DoMoveOk(
    stilling in out PL_PIG_CHESS_ENGINE_EVAL.STILLINGTYPE,
    fra SIMPLE_INTEGER,
    til SIMPLE_INTEGER,
    MoveTyp in out MOVETYPE
) RETURN BOOLEAN;
```

**Behavior:**
- Checks if a move is legal and generates black/white moves.
- Returns `TRUE` if the move is legal, `FALSE` otherwise.

### `DoMoveC` Procedure

```plsql
PROCEDURE DoMoveC(
    stilling in out PL_PIG_CHESS_ENGINE_EVAL.STILLINGTYPE,
    fra SIMPLE_INTEGER,
    til SIMPLE_INTEGER
);
```

**Behavior:**
- Performs a move without requiring move type information.
- Faster than `DoMoveOk` and used when the move is already validated.

### `DoMove` Procedure

```plsql
PROCEDURE DoMove(
    stilling in out PL_PIG_CHESS_ENGINE_EVAL.STILLINGTYPE,
    fra SIMPLE_INTEGER,
    til SIMPLE_INTEGER,
    MoveTyp MOVETYPE
);
```

**Behavior:**
- Performs a move with move type information.
- Validates the move before execution.

### `GetNext` Procedure

```plsql
PROCEDURE GetNext(
    stilling in out PL_PIG_CHESS_ENGINE_EVAL.STILLINGTYPE,
    fra in out SIMPLE_INTEGER,
    til in out SIMPLE_INTEGER,
    retning in out SIMPLE_INTEGER,
    MoveTyp in out MOVETYPE
);
```

**Behavior:**
- Finds the next legal move in the position.
- Updates the `fra` and `til` parameters to the next move.

### `Mirror` Procedure

```plsql
PROCEDURE Mirror(
    stilling in out PL_PIG_CHESS_ENGINE_EVAL.STILLINGTYPE
);
```

**Behavior:**
- Mirrors a position, swapping the board layout and colors.

### `FindTrk` Procedure

```plsql
PROCEDURE FindTrk(
    stilling in out PL_PIG_CHESS_ENGINE_EVAL.STILLINGTYPE,
    dybde SIMPLE_INTEGER,
    ekstra SIMPLE_INTEGER,
    Traek in out TRKDATA
);
```

**Behavior:**
- Finds a move at a specific depth in the search tree.
- Updates the `Traek` parameter with the move data.

### `GetMove` Procedure

```plsql
PROCEDURE GetMove(
    stilling in out PL_PIG_CHESS_ENGINE_EVAL.STILLINGTYPE,
    t in out TRKDATA,
    MoveNr SIMPLE_INTEGER,
    Quick BOOLEAN
);
```

**Behavior:**
- Makes a move based on a move number.
- If `Quick` is `TRUE`, it drops the check for checks.

### `GetMoveNr` Procedure

```plsql
PROCEDURE GetMoveNr(
    stilling in out PL_PIG_CHESS_ENGINE_EVAL.STILLINGTYPE,
    p_fra SIMPLE_INTEGER,
    p_til SIMPLE_INTEGER,
    MoveNr in out SIMPLE_INTEGER,
    Quick BOOLEAN
);
```

**Behavior:**
- Gets a move number based on a move.
- If `Quick` is `TRUE`, it drops the check for checks.

### `Initialize` Procedure

```plsql
PROCEDURE Initialize;
```

**Behavior:**
- Initializes the chess engine, likely setting up initial variables and data structures.