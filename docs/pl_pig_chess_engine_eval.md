# PL_PIG_CHESS_ENGINE_EVAL Package

## Method Signatures and Code Behavior

### `pdN` Function

```plsql
FUNCTION pdN(
    brik_n SIMPLE_INTEGER,
    felt SIMPLE_INTEGER
) RETURN SIMPLE_INTEGER;
```

**Behavior:**
- Returns the index of a piece in the `pd` array based on its numeric representation and the felt (board position).

### `pdX` Function

```plsql
FUNCTION pdX(
    brik CHAR,
    felt SIMPLE_INTEGER
) RETURN SIMPLE_INTEGER;
```

**Behavior:**
- Returns the index of a piece in the `pd` array based on its character representation and the felt.

### `Initialize` Procedure

```plsql
PROCEDURE Initialize;
```

**Behavior:**
- Performs allocation and initializations, called on startup.

### `PreProcess` Procedure

```plsql
PROCEDURE PreProcess;
```

**Behavior:**
- Sets the `pd` array to default positional values, called once for each engine call.

### `PreProcessor` Procedure

```plsql
PROCEDURE PreProcessor(
    stilling STILLINGTYPE
);
```

**Behavior:**
- Adjusts the `pd` array and game states according to the actual position, called once for each engine call.

### `Eval` Function

```plsql
FUNCTION Eval(
    stilling STILLINGTYPE,
    Activity SIMPLE_INTEGER,
    Black BOOLEAN,
    alpha SIMPLE_INTEGER,
    beta SIMPLE_INTEGER
) RETURN SIMPLE_INTEGER;
```

**Behavior:**
- Evaluates the actual position using the `pd` array and position data.
- Called thousands of times for each engine call.