
# Summary

`{'mod':'speak'}` Makefiles are a simple way to organize code compilation. This tutorial the basic concept on how to use the tool to assist the running of lab practices and project setup for assignments.

# Makefile Syntax

`{'mod':'speak'}` A Makefile consists of a set of rules. A rule generally looks like this:

```{'mod':'code','lang':'makefile'}
targets : prerequisities
   command1
   command2
   ...
   commandN
```
- `{'mod':'speak'}` The `targets` are file names, seperated by spaces. Typically, there is only one per rule.
- `{'mod':'speak'}` The `commands` are a series of steps typically used to make the targets. These need to start with a **tab character**, NOT **spaces**.
- `{'mod':'speak'}` The `prerequisites` are also file names, seperated by spaces. These files need to exist before the commands for the target are run.

# Window file-paths syntax

`{'mod':'speak'}` Window file-paths are based on the standard DOS path can consist of three components:

- `{'mod':'speak'}` A volume or drive letter followed by the volume separator (:).
- `{'mod':'speak'}` A directory name. The directory separator character (`"\"`) separates subdirectories within the nested directory hierarchy.
- `{'mod':'speak'}` An optional filename. The directory separator character separates the file path and the filename.

`{'mod':'speak'}` If all three components are present, the path is absolute. If no volume or drive letter is specified and the directory name begins with the directory separator character, the path is relative from the root of the current drive. Otherwise, the path is relative to the current directory. The following table shows some possible directory and file paths.

| Path example                                     | Interpretation                                                                                    |
| :----------------------------------------------- | :------------------------------------------------------------------------------------------------ |
| C:\Documents\Newsletters\Summer2018.pdf          | `{'mod':'speak'}` An absolute file path from the root of drive C:                                 |
| \Program Files\Custom Utilities\StringFinder.exe | `{'mod':'speak'}` An absolute path from the root of the current drive.                            |
| 2018\January.xlsx                                | `{'mod':'speak'}` A relative path to a file in a subdirectory of the current directory.           |
| ..\Publications\TravelBrochure.pdf               | `{'mod':'speak'}` A relative path to file in a directory that is a peer of the current directory. |
| C:\Projects\apilibrary\apilibrary.sln            | `{'mod':'speak'}` An absolute path to a file from the root of drive C:                            |
| C:Projects\apilibrary\apilibrary.sln             | `{'mod':'speak'}` A relative path from the current directory of the C: drive.                     |



# Version 1: A Simple Example

`{'mod':'speak'}` Let's start off, within the same project folder of the previous chapter, by:
1. `{'mod':'speak'}` Creating two new files: "hellofunc.c" and "hellomake.h", and populate them with the following content.
   
    hellofunc.c:
    ```{'mod':'code','lang':'c'}
    #include <stdio.h>
    #include <hellomake.h>

    void myPrintHelloMake(void) {
        printf("Hello makefiles!\n");
        return;
    }
    ```
    hellofunc.h:
    ```{'mod':'code','lang':'c'}
    void myPrintHelloMake(void);
    ```
2. `{'mod':'speak'}` Replace the source code in `main.c` with the following:
   ```{'mod':'code','lang':'c'}
    #include <hellomake.h>
    int main()
    {
        // call a function in another file
        myPrintHelloMake();

        return (0);
    }
    ```
4. `{'mod':'speak'}` At this point, your project directory should look like this:
   
   `{'mod':'img','url':'$/_res/makefile/project-file-list.png'}`

3. `{'mod':'speak'}` Now, open `makefile` and make the following changes

    ```{'mod':'code','lang':'makefile'}
    app: main.c hellofunc.c
	    gcc -g -o app.exe main.c hellofunc.c -I.
    ```
    `{'mod':'speak'}` Notice that we added `hellofunc.c` to the dependency list? The reason for doing
    this is to ensure the commands of the `app` task is executed when any of the files
    (in this case `main.c hellofunc.c`) are updated.

    `{'mod':'speak'}` Also, notice the `gcc ...` command has changed to include `hellofunc.c` and `-I.`. The
    reason for doing this is because:
    1. `{'mod':'speak'}` function `myPrintHelloMake()` called by the `int main()` function is implemented in a
    different file: `hellofunc.c`
    2. `{'mod':'speak'}` `-I.` (dash-I-dot) specify an additional path where the include files are located. In this
    case the "dot" meaning the current folder.

4. `{'mod':'speak'}` Press <kbd>F5</kbd> to run the code.


> `{'mod':'tag','type':'remember'}` `{'mod':'speak'}` One very important thing to note is that there is a <kbd>tab</kbd> before the `gcc` command in the `makefile`. There must be a <kbd>tab</kbd> at the **beginning of any command**, and `make` will not be happy if it's not there.

# Version 2: Make constants

`{'mod':'speak'}` In order to be a bit more efficient, let's replace the 'makefile' content with the following:

```{'mod':'code','lang':'makefile','highlight':'1-2,5'}
CC=gcc
CFLAGS=-I.

app: main.o hellofunc.o
	$(CC) -g -o app.exe main.o hellofunc.o
```

`{'mod':'speak'}` So now we've defined some constants `CC` and `CFLAGS`. It turns out these are special constants that communicate to `make`: how we want to compile the files `hellomake.c` and `hellofunc.c`. In particular, the macro `CC` is the C compiler to use, and `CFLAGS` is the list of flags to pass to the compilation command. By putting the object files `hellomake.o` and `hellofunc.o` in the dependency list and in the rule, `make` knows it must first compile the `.c` versions **individually**, and then build the executable `app.exe`.

# Version 3: Pattern matching

`{'mod':'speak'}` Using this form of `makefile` is sufficient for most small scale projects. However, there is one thing missing: dependency on the include files. If you were to make a change to `hellomake.h`, for example, make would not recompile the .c files, even though they needed to be. In order to fix this, we need to tell make that all `.c` files depend on certain `.h` files. We can do this by writing a simple rule and adding it to the `makefile`.

```{'mod':'code','lang':'makefile','highlight':'3,5-6'}
CC=gcc
CFLAGS=-I.
DEPS = hellomake.h

%.o: %.c $(DEPS)
	$(CC) -c -o $@ $< $(CFLAGS)

app: main.o hellofunc.o
	$(CC) -g -o app.exe main.o hellofunc.o
```

`{'mod':'speak'}` This addition first creates the macro `DEPS`, which is the set of `.h` files on which the `.c` files depend. Then we define a rule that applies to all files ending in the `.o` suffix. The rule says that the `.o` file depends upon the `.c` version of the file and the `.h` files included in the `DEPS` macro. The rule then says that to generate the `.o` file, make needs to compile the `.c` file using the compiler defined in the `CC` macro. The `-c` flag says to generate the object file, the `-o` `$@` says to put the output of the compilation in the file named on the left side of the `:`, the `$<` is the first item in the dependencies list, and the `CFLAGS` macro is defined as above.

`{'mod':'speak'}` You can add multiple rules to a makefile; you can even create rules that call other rules. For more information on makefiles and the make function, check out the [GNU Make Manual](http://www.gnu.org/software/make/manual/make.html), which will tell you more than you ever wanted to know (really).
