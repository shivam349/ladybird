# Shorthand Assertion Helpers

This document describes the shorthand helper functions provided by Ladybird for common comparison operations and assertions.

## Generic Shorthand Functions

The `AK/GenericShorthands.h` header provides a set of template functions that make it easier to write common comparison operations in a more concise and readable way. These functions are particularly useful when you need to check if a value matches any one of several possible values, or if it satisfies a comparison against multiple values.

### Checking Against One Of Multiple Values

#### `first_is_one_of`
Checks if the first argument is equal to any of the subsequent arguments.

```cpp
#include <AK/GenericShorthands.h>

int value = 5;
if (first_is_one_of(value, 1, 5, 10, 15)) {
    // This will be true since value == 5
}
```

#### `first_is_smaller_than_one_of`
Checks if the first argument is smaller than at least one of the subsequent arguments.

```cpp
int value = 5;
if (first_is_smaller_than_one_of(value, 3, 10, 15)) {
    // This will be true since value < 10 and value < 15
}
```

#### `first_is_smaller_or_equal_than_one_of`
Checks if the first argument is smaller than or equal to at least one of the subsequent arguments.

```cpp
int value = 5;
if (first_is_smaller_or_equal_than_one_of(value, 5, 10)) {
    // This will be true since value <= 5
}
```

#### `first_is_larger_than_one_of`
Checks if the first argument is larger than at least one of the subsequent arguments.

```cpp
int value = 10;
if (first_is_larger_than_one_of(value, 5, 15, 20)) {
    // This will be true since value > 5
}
```

#### `first_is_larger_or_equal_than_one_of`
Checks if the first argument is larger than or equal to at least one of the subsequent arguments.

```cpp
int value = 10;
if (first_is_larger_or_equal_than_one_of(value, 10, 15)) {
    // This will be true since value >= 10
}
```

### Checking Against All Values

#### `first_is_equal_to_all_of`
Checks if the first argument is equal to all of the subsequent arguments.

```cpp
int value = 5;
if (first_is_equal_to_all_of(value, 5, 5, 5)) {
    // This will be true since all values are 5
}
```

#### `first_is_smaller_than_all_of`
Checks if the first argument is smaller than all of the subsequent arguments.

```cpp
int value = 5;
if (first_is_smaller_than_all_of(value, 10, 15, 20)) {
    // This will be true since value < 10, value < 15, and value < 20
}
```

#### `first_is_smaller_or_equal_than_all_of`
Checks if the first argument is smaller than or equal to all of the subsequent arguments.

```cpp
int value = 5;
if (first_is_smaller_or_equal_than_all_of(value, 5, 10, 15)) {
    // This will be true since value <= 5, value <= 10, and value <= 15
}
```

#### `first_is_larger_than_all_of`
Checks if the first argument is larger than all of the subsequent arguments.

```cpp
int value = 20;
if (first_is_larger_than_all_of(value, 5, 10, 15)) {
    // This will be true since value > 5, value > 10, and value > 15
}
```

#### `first_is_larger_or_equal_than_all_of`
Checks if the first argument is larger than or equal to all of the subsequent arguments.

```cpp
int value = 15;
if (first_is_larger_or_equal_than_all_of(value, 5, 10, 15)) {
    // This will be true since value >= 5, value >= 10, and value >= 15
}
```

## Related Assertion Macros

For runtime assertions and verification in your code, see the [`VERIFY` macro documentation](../AK/Assertions.h) in `AK/Assertions.h`. The `VERIFY` macro is used throughout the codebase to assert conditions that must be true at runtime, and will trigger program termination if the condition fails.

Common assertion macros include:
- `VERIFY(condition)` - Verifies that a condition is true, terminates if false
- `ASSERT(condition)` - Debug-only assertion (removed in release builds)
- `VERIFY_NOT_REACHED()` - Marks code paths that should never be reached
- `TODO()` - Marks code that needs to be implemented

See also: [Common Patterns](Patterns.md) for other coding patterns used in Ladybird.
