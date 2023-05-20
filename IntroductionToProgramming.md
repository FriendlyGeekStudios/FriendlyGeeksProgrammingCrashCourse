# Introductory Programming in C

The C language has been around since the late 60's although it saw the most development in 1972 and wasn't widely adopted until the late 80's. C is a rather minimal programming language in that it does not include a lot of useful, quality of life features provided by more modern languages. Aside from a few core data types and control flow structures, the C language provides practically nothing else, which makes it an excellent language for learning fundamental concepts as well has how some low-level innards of a program work and operate. We'll be exploring these fundamentals and then building on them to understand how more modern languages work for the convenience of the developer.

### Environment Setup
Let’s start by first creating an environment conducive to programming. I strongly encourage using [Windows Subsystem for Linux](https://learn.microsoft.com/en-us/windows/wsl/install) which you can install following this guide. You should also, if you don’t have it installed already, get [Visual Studio Code](https://code.visualstudio.com/) (Not Visual Studio!). Once you have both installed, open VS Code, and select File > Open Folder
[](images/introduction_to_c_open_folder.PNG)
From there, I recommend creating a new folder for these exercises and storing the files there. Once you’ve opened your folder, you should have an empty explorer pane:
[](images/introduction_to_c_empty_explorer.PNG)
You can right click anywhere in there and create a new file. We’re going to call this first one hello_word.c and then inside the file, we’re going to add the following code:
[](images/introduction_to_c_hello_world.PNG)
In order to compile and run this program, we’re going to need a terminal available to us. At the top of you VS Code window, select Terminal > New Terminal:
[](images/introduction_to_c_new_terminal.PNG)
That should open a new window at the bottom of your screen that looks something like so:
[](images/introduction_to_c_empty_terminal.PNG)
From here, select the down arrow next to the + icon and select your WSL option. Mine is Ubuntu WSL, hopefully yours is similar:
[](images/introduction_to_c_wsl_select.PNG)
This should result in a new prompt that looks like:
[](images/introduction_to_c_wsl_terminal.PNG)
At this point, we can compile our application and run it with the following commands:
[](images/introduction_to_c_code_execution.PNG)

### Why we did all of that
Now, you may be wondering what the purpose of all of this “hello, world” stuff is. The simple answer is that it is a basic litmus test to ensure that you have all of the resources you need to build and run programs using the C Language. Anytime you set up a project, it should start with a “Hello, world” test because it shows that your system is minimally configured to work with your selected technology stack. This does, of course, get more complicated with bigger projects and build systems, but all of those advanced tools are just wrappers around these simple concepts.

### Breaking down the code
Let’s take a look at the source code and discuss what’s happening on each line
[](images/introduction_to_c_code_annotated.PNG)
1. This `#include` statement is called a preprocessor macro which we can discuss more in depth later. What it essentially does is copy all of the contents of the “stdio.h” file into this source file. We do this so that we have access to the functions within that file.
2. This is the function declaration. A function is a series of statements (i.e. lines of code) that are grouped together and executed sequentially to perform a set of operations. We’ll discuss functions in more detail later and explain what the `int` `main` and `()` components all mean individually. For now, we’ll call this the main function
3. This section contains the body of the function that we declared in line 3. The body is just the grouping of statements belonging to the main function.
4. Here, we call the `printf` function with the argument “Hello, world!\n”. Normally, we wouldn’t have access to the `printf` function, but if you recall from section 1, we `#include`d the `stdio.h` file which actually contains the definition of this file. This particular function is actually responsible for writing text to the standard output stream of our systems. Typically, this is the monitor or program window that we're looking at.
5. Lastly, we have the statement `return 0;` The keyword `return` tells the program that we are done with this particular function and that we can exit from it. Often, a function will be responsible for returning data to its original calling source which is why we have the 0 tacked on to the end there.

## Variables
## Control Flow
## Organization and Structure
## Exercises: