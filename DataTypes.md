# Data Types

At the most fundamental level, computers only see and interpret 1's and 0's, and there is no distinction between the different types of data the computer will process. In order to make computers useful to humans, we've abstracted the process of producing the binary code into more natural, human-esque languages: Programming languages. One of the things that is really important for us humans, is to know what kind of data is being operated on. Here, we introduce Data Types. Data types are a classification mechanism that dictate how we interact with certain variables and data. We'll be exploring primitive data types such as integral numbers, decimal numbers, basic characters, and even our first collection type. We'll also cover complex data types at a high level, but an in-depth discussion will be reserved for the Object Oriented Programming topic.

Its important to note that various programming languages themselves will have different primitive types with the inclusion or exclusion of types entirely. For example, JavaScript, the popular website development language, does not have a concept of an integer type, it uses `number` instead which encapsulates whole numbers as well as fractions in a single data type. Lower level langauges, like our reliable C language, make an important distinction between these types of numbers to remove the ambiguity in calculations. Addtionally, some languages forgo a type system entirely. Python automatically determines what type a piece of data is based on the context of the code.

## Integers
Integers refer to whole numbers and are mostly commonly types as `int`. In older computers, we often worked with extremely limited memory space which made it really important to conserve space where possible. One of the ways of doing that was to limit the amount of space that a number could occupy. We did this with specifically sized `int` data types. For example, `int32_t` consumes 32 bits while `int16_t` and `int8_t` consume 16 and 8 bits respectively. Modern computers have significantly more memory and developers can often get away with defaulting to just `int`. Developers should only use size-specific variants of `int` when there is a direct need, such as working with embedded systems and hardware. Here are a few examples of integral types in C. You'll notice that we use `uint32_t` instead of `int32_t` here which will be discussed in the next section. You might see data types like `short`, `long`, or even `long long`; these are all numeric types that describe differently sized integers. `short` is the same as `int8_t`, while `long` usually refers to a 64-bit number.
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
Doubles and Floats are how we store and show non-whole decimal numbers. There are a lot little details on how these numbers are stored in memory and how mathematical operations are done on them, but we can limit our study here to knowing that `double`s and `float`s use more memory and are slower to conduct operations on than whole numbers. You can review the detailed specification of most floating point numbers using the [IEEE 754-2019 standard](https://ieeexplore.ieee.org/document/8766229).

You might be asking yourself, "What's the difference between a double and a float?"

Well, the answer is simple: a `double` consumes twice the memory that a `float` does! This inherently means that a double can be much larger than a `float`, and as an added benefit, `double`s can also be more precise. Generally, when working in mathematically complex programs, we'll tend toward using `double` as the de facto data type because of the increased size and precision, but this isn't always the case. In game programming, its quite common to use floats because they are faster to compute with and the precision is usually less important.

```C
float nonWholeNumber = 1.22222;
double wayMorePrecision = 3.00000000001;
```
## Chars

`char` is a special data type that you will typically only interact with in systems level programming languages such as C and C++. A `char` is just a single character. That's it. In C/C++, `char` is represented by its corresponding `int`eger value. In particular, `char` is ALWAYS the smallest type of `int` available, commonly `short` or `uint8_t`. `char` just being a wrapper around the smallest `int` type does have some interesting implications. It means that we can use `char` to do some interesting and unique things like math with characters or printing string characters with plain numbers. Check out the code snippet below to see some interesting ways that `char` can be used. The [ASCII Table](https://www.asciitable.com) is a key resource in knowing what numbers in hex and decimal (and even octal!) map to which common character.

```C
int main()
{
    int hexValueForThe_A_Character = 0x61;
    int integerValueForThe_A_Character = 97;
    char charValueFor_A_Character = 'a'; // Notice that `char` is wrapped in single "'"'s

    printf("Print 'a' using a hex number: %c (0x%x)\n", hexValueForThe_A_Character, hexValueForThe_A_Character);
    // Prints: Print 'a' using a hex number: a (0x61)
    printf("Print 'a' using an integer: %c (%d)\n", integerValueForThe_A_Character, integerValueForThe_A_Character);
    // Prints: Print 'a' using an integer: a (97)
    printf("Print 'a' using a char: %c\n", charValueFor_A_Character);
    // Prints: Print 'a' using a char: a

    // Time to do some... weirder things...
    char nine = '9'; // This refers to the character value 9, not the numeric value 9! the character value of 9 is actually 57 in decimal!
    printf("'9' + '9' = %c\n", nine + nine);

    // Here we can print it directly as acharacter
    printf("nine = %c\n", nine);
    // and here, we can print it as a numeric integer! (but you have to subtract 48 first!)
    int n = nine - 48;
    printf("nine = %d\n", n);

    return 0;
}
```

`char` can be a tricky data type because it can be used in a lot of different ways, but at its core, just remember that it is a number!

## Arrays
The last data type we'll talk about in this section are arrays. Arrays are contiguous sections in memory that store multiple values of the same type. We will be using these A LOT because they are super important!

In C, the size of an array cannot change. Once an array is created, you cannot change how big it is, but you can change the data stored in the array. If we don't necessarily know how big an array is going to be, we have to come up with a different solution; which we will talk about in a later section. There are two ways to create an array: with an initializer list or with a size and a default value:
```C
int arr1[] = {1,2,3,4,5}; // This will create an array of size 5 with the numbers 1-5 stored in it
int arr2[5] = {0}; // This will create an array of size 5 with 5 zeroes in it
```

Notice, that in the above example, we specified a size in the second array, but in the first, we just provided 5 unique values.

When we talk about arrays, we will often talk about indexes and what it means to zero-indexed. The index is the offset of a data member from the beginning of the array. Zero-indexed means that when counting our data members, we start with 0! That means that the first element in our list is identified with index 0. If we want to access an element in an array, we do the following:
```C
int arr[] = {1,2,3,4,5};
arr[0]; // Get the zero-th (first!) element of the array
```

This does mean that if we want to access the last element in an array, then the index we need to access is the **size of the array - 1**

It's important to note that, in C, the array size must be fixed. See the below example for a bit more detail on how to interact with arrays. Review the ![Introduction To Programming](./IntroductionToProgramming.md) Guide for an explanation of the `for` loops.

```C
int main()
{
    int arr[] = {1,2,3,4,5};
    int arr2[5] = {0};
    int arr3[]; // Illegal! This won't compile

    for(int i = 0; i < 5; i++){
        printf("%d ", arr[i]);
    }
    printf("\n");
    for(int i = 0; i < 5; i++){
        printf("%d ", arr2[i]);
    }
    printf("\n");

    return 0;
}
```

# Exercises:
There are none! You'll apply these concepts in the ![Introduction To Programming](./IntroductionToProgramming.md) section.