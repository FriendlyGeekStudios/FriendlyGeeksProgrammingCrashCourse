## Exercises:
1. Create an array of size `10` that is initialized to all `0`'s. Using a for loop, fill the array with the numbers 1-10. Lastly, print each number in the array in ascending order.
```C
#include <stdio.h>

int main(){
    int arr[10] = {0};
    for(int i = 0; i < 10; i++){
        arr[i] = i+1;
        printf("%d ", arr[i]);
    }

    printf("\n");
}
```
2. Create a function that takes in a number and prints "even" if the number is even, otherwise print "false". (Hint: what binary operator might be useful for this???);
```C
#include <stdio.h>

void isEven(int input){
    if(input % 2 == 0){
        printf("even\n");
    } else {
        printf("odd\n");
    }
    
}

int main(){
    isEven(2);
    isEven(3);
    isEven(400);
    isEven(401);
}
```
3. Using a for loop, can you print the alphabet? Lowercase characters only!
```C
#include <stdio.h>

int main(){
    for(char i = 'a'; i < 'z'+1; i++){
        printf("%c", i);
    }
    printf("\n");
}
```
4. Write a function that will take an integer as an argument, and, using a `switch` statement, print the day of the week depending on the number
  * The input number should be between 0 and 7 where 0 represents Sunday and 7 represents Saturday.
  * What happens if the number is greater than 7 or less than 0? Can we constrain it somehow?
```C
#include <stdio.h>

void printDayOfWeek(int dayNumber){
    switch(dayNumber % 7){ // Constrain the day number to be within the expected range, no matter what!
    case 0:
        printf("Sunday\n");
        break;
    case 1:
        printf("Monday\n");
        break;
    case 2:
        printf("Tuesday\n");
        break;
    case 3:
        printf("Wednesday\n");
        break;
    case 4:
        printf("Thursday\n");
        break;
    case 5:
        printf("Friday\n");
        break;
    case 6:
        printf("Saturday\n");
        break;
    default:
        // Should be impossible to get here!
        break;
    }
}

int main(){
    printDayOfWeek(0);
    printDayOfWeek(2455);
    printDayOfWeek(3);
}
```
5. Write a function that will take a `char` as an argument, and return `1` if the `char` is a vowel and 0 otherwise. Can you do this with a `switch` statement?
```C
#include <stdio.h>

int isVowel(char c){
    switch(c){
        case 'a':
        case 'e':
        case 'i':
        case 'o':
        case 'u':
            return 1;
        default:
            return 0;
    }
}

int main(){
    isVowel('a'); // 1!
    isVowel('b'); // 0!
}
```
6. Create an array containing the `char`acters in your name and print them out using a `for` loop.
```C
#include <stdio.h>

int main(){
    char myName[] = {'e','v','a','n'};
    for(int i = 0; i < 4; i++){
        printf("%d", myName[i]);
    }

    printf("\n");
}
```