# Boolean Logic

Boolean Algebra is a branch of mathematics that deals solely with logical operations on binary data. It contains a whole vocabulary of complex terms, laws, and theorems, but we're only going to pay attention to the pieces that are most useful in a daily context. Because Boolean Algebra is about binary, we'll use `1` to represent `true` and `0` to represent `false`

## Truth Tables

Truth Tables are a relatively intuitive way to view boolean operations. They're simply a grid showing all of our inputs and all of the possible permutations of values and the output from an operation.

## Standard Operations
The most important operations in boolean algebra are listed here. These are all simple and straightforward.

A note on operator precedence: Parenthesis will always be evaluated first, then the unary operator, NOT, will be evaluated. All other operations are evaluated greedily from left to right with the same precedence.

### AND
Formally known as 'Conjunction', the AND operation only produces a `true` result when all of its inputs are also `true`. We use the symbol `&&` to indicate the AND operation.
| `x` | `y` | `x && y` |
|:-:|:-:|:-:|
| 0 | 0 |  0 |
| 1 | 0 |  0 |
| 0 | 1 |  0 |
| 1 | 1 |  1 |

### OR
Logical Or is known as Disjunction and evaluates to `true` anytime x OR y is `true`. We use the `||` symbol to indicate the OR operation.
| `x` | `y` | `x \|\| y` |
|:-:|:-:|:-:|
| 0 | 0 |  0 |
| 1 | 0 |  1 |
| 0 | 1 |  1 |
| 1 | 1 |  1 |

### NOT
The negation operation, Not, simply inverts any input that it receives. It is the only unary (1 input) operation in boolean algebra. All other operations are binary (2 inputs). The `!` is used to indicate negation and is pronounced "not x"
| `x` | `!x` |
|:-:|:-:|
| 0 |  1 |
| 1 |  0 |
| 0 |  1 |
| 1 |  0 |

### XOR
This last one is a little trickier, XOR is Exclusive OR and it evaluates to `true` when one and only one input in the binary expression is true. The `^` is used to represent XOR. You may notice that this is also a common way to indicate exponents on numbers.

| `x` | `y` | `x ^ y` |
|:-:|:-:|:-:|
| 0 | 0 |  0 |
| 1 | 0 |  1 |
| 0 | 1 |  1 |
| 1 | 1 |  0 |

## Exercises
1. Evaluate this expression: `(0 || 1) && (!(1 && 0)) = ?`
2. Evaluate this expression: `(1 ^ 1) ^ (!1 || 1) = ?`
3. Evaluate this expression: `(!true || false) && (!false && !false) ^ true = ?`