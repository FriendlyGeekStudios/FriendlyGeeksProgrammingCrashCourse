# Numerical Systems in CS

# Binary
Binary, like decimal, is a number counting system. The decimal system is a base-10 counting system while binary is only a base-2 system.

That is to say in decimal, we use the numbers 0-9, whereas in binary, we only use 0 and 1.
When counting in the decimal system, you iterate through each number in the sequence 0-9. 

Once you run out, you increment the next place value and repeat the process.

Remember that every number is preceded by an infinite number of zeros. That is to say, 8 is the same as 08, 008, or 00000008

The same process applies in binary:

00 = 0

01 = 1 # No more numbers to iterate through since 0 and 1 are the only options! 

10 = 2

11 = 3

100 = 4 # added a new place value!


Each place value in a binary number is known as a `bit`, so when we say we have an 8 bit number that can be any number in the range `00000000-11111111` which corresponds to the decimal values `0-255`. 

8 bits is known as a `byte`.

Binary is often represented with a `b` at the end of the number: `1010101b`. Decimal is either not annotated or is annotated with a `d`.

### Converting To and From Binary
converting a decimal number to binary is easier than it sounds. Since each place value in a binary number is a power of two, we can layout binary numbers like so:

| Description | `2^3` | `2^2` | `2^1` | `2^0` |
| - | - | - | - | - |
| Binary number:      | 0 | 0 | 0 | 0 |
| Decimal equivalent: | 8 | 4 | 2 | 1 |

with greater place values and powers of two extending infinitely to the left.
If we want to translate any decimal value into binary, Follow this simple approach:
1. Find the nearest power of 2 that is *less* than your original number, lets call this `n`
2. Turn on the bit in the `n-th` place value
3. Subtract `2^n` from your original number
4. Repeat this process with the reduced number until you have a remainder of 0

So, lets step through converting the decimal number `11` into binary.

First, we find the nearest power of 2 that is smaller than `11`. In this case `2^3 == 8`, so `n = 3`

Second, we turn on the bit in the place value of `2^n =>2^3`:
| Description | `2^3` | `2^2` | `2^1` | `2^0` |
| - | - | - | - | - |
| Binary number:      | 1 | 0 | 0 | 0 |
| Decimal equivalent: | 8 | 4 | 2 | 1 |

Third, we subtract: `11 - 2^3 => 11 - 8 => 3`

Repeat now with `3`: `n = 1 (because: 2^1 == 2)`

Turn on the `1`'s place value:
| Description | `2^3` | `2^2` | `2^1` | `2^0` |
| - | - | - | - | - |
| Binary number:      | 1 | 0 | 1 | 0 |
| Decimal equivalent: | 8 | 4 | 2 | 1 |
Subtract: `3 - 2^1 => 3 - 2 = 1`

Repeat last time for `1`: `n = 0 (because: 2^0 == 1)`

Turn on the 0 place value:
| Description | `2^3` | `2^2` | `2^1` | `2^0` |
| - | - | - | - | - |
| Binary number:      | 1 | 0 | 1 | 1 |
| Decimal equivalent: | 8 | 4 | 2 | 1 |
Subtract: `1 = 2^0 => 1 - 1 = 0`

Since we now have a remainder of 0, there's nothing left to do and we have our final binary number: `11` in decimal is `1011` in binary.

This same process works for all binary numbers, but gets a little trickier with larger numbers.


To convert binary into decimal, summarize the place value powers that are currently "on". So to convert `1011b` back to binary: `2^3 + 2^1 + 2^0 = 11`

# Hexadecimal
Hexadecimal, unlike binary and decimal, is a base-16 counting system. Its only fundamental use is to simplify bigger numbers in computer memory for human processing. You might notice that 16 is a power of 2 here, and that's not a coincidence!

Since hexadecimal uses more numerals than are inherintly available in the decimal system, we had to come up with a solution: letters!

That's right, we now count from `0-9` and then `A-F`. `A` is equal to `10`, `B = 11`, `C = 12`, `D = 13`, `E = 14,` and `F = 15`.
This is handy to know, but not strictly required. Its useful when working with low-level systems since you can represent much larger numbers in many fewer characters, which was *really* important in the olden days of having extremely limited memory.

Hex is usually represented as: `0xNN` or `NNh` where `NN` is any random number

To convert numbers to hex, you can use the same method as the binary, but instead you want to look for the nearest power of 16 that is less than your original number.

You can divide the number by 16, and take the remainder and repeat the process until you have a number less than 16 remaining.
Converting `200d` into hex can be done as: `200/16` = `12` with a remainder of `8`. Remember that `12 = C` and since `8 < 16`, we know our number is: `0xC8`

You can convert hex back to decimal by multiplying each number by 16 raised to its place value and summing them all together. For `0xC8`: `C*(16^1) + 8*(16^0) = 200`

## Excercises 
1. Convert the decimal value 68 into binary.
2. Convert 00110101 into decimal.
3. How many bits are in a 4-byte number?
4. Convert `FFh` to Decimal.
5. Convert `0xFF01` to binary.
6. Convert `1011b` into hex.
7. What's the maximum number (in decimal) you can store in 16 bits?
8. What's the maximum number (in decimal) you can store in 32 bits?
9. What about in 31 bits?