# Data Types

At the most fundamental level, computers only see and interpret 1's and 0's, and there is no distinction between the different types of data the computer will process. In order to make computers useful to humans, we've abstracted the process of producing the binary code into more natural, human-esque languages: Programming languages. One of the things that is really important for us humans, is to know what kind of data is being operated on. Here, we introduce Data Types. Data types are a classification mechanism that dictate how we interact with certain variables and data. We'll be exploring primitive data types such as integral numbers, decimal numbers, basic characters, and even our first collection type. We'll also cover complex data types at a high level, but an in-depth discussion will be reserved for the Object Oriented Programming topic.

Its important to note that various programming languages themselves will have different primitive types with the inclusion or exclusion of types entirely. For example, JavaScript, the popular website development language, does not have a concept of an integer type, it uses `number` instead which encapsulates whole numbers as well as fractions in a single data type. Lower level langauges, like our reliable C language, make an important distinction between these types of numbers to remove the ambiguity in calculations. Addtionally, some languages forgo a type system entirely. Python automatically determines what type a piece of data is based on the context of the code.

## Integers
Integers refer to whole numbers and are mostly commonly types as `int`. In older computers, we often worked with extremely limited memory space which made it really important to conserve space where possible. One of the ways of doing that was to limit the amount of space that a number could occupy. We did this with specifically sized `int` data types. For example, `int32_t` consumes 32 bits while `int16_t` and `int8_t` consume 16 and 8 bits respectively. Modern computers have significantly more memory and developers can often get away with defaulting to just `int`. Developers should only use size-specific variants of `int` when there is a direct need, such as working with embedded systems and hardware. Here are a few examples of integral types in C. You'll notice that we use `uint32_t` instead of `int32_t` here which will be discussed in the next section.
```C
int defaultIntType = 100000; // The size if `int` often defaults to the max register size on the computer. For modern computers, this is at least 32-bits but is commonly 64-bits now
uint32_t max32BitValueIs = 4294967295;
uint16_t max16BitValueIs = 65535;
uint8_t max8BitValueIs = 255;
```

### Signed vs Unsigned
Our current understanding of binary only allows us to represent positive numbers. If we want to represent negative numbers, we have to make a small sacrifice. We can dedicate 1 bit in our number to containing a positive or negative sign. This introduces the concept of signed integers versus unsigned integers. Signed integers include a bit indicating whether the number is positive or negative and is the default behavior when utilizing an `int` type. If we want to explicilty indicate that the number will always be positive, we have to use the `unsigned` keyword or a more precise data type directly:
```C
int iAmASignedInteger = -1000;
unsigned int iAmAnUnsignedInteger = 4000; // This number CANNOT be negative
int32_t anotherSignedInteger = 239898; // I can still be positive!
uint32_t anotherUnsignedInteger = 123123; // I Also cannot be negative!
```

When we use signed numbers, we lose one of the bits that allows us to store numbers. Unfortunately, this means that we cannot store numbers that are quite as large as an unsigned number. An `unsigned` 8-bit integer can store numbers in the range from [0,255], but a `signed` 8-bit integer, can only store numbers in the range of [-128,127].

## Doubles and Floats
## Chars
## Arrays