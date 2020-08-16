# Visual Studio Code (VSC)

`{'mod':'speak'}` In this tutorial, you configure Visual Studio Code to use the GCC C++ compiler (g++) and GDB debugger from mingw-w64 to create programs that run on Windows.

After configuring VS Code, you will compile and debug a simple Hello World program in VS Code. This tutorial does not teach you about GCC, GDB, Mingw-w64, or the C++ language.

If you have any problems, feel free to file an issue for this tutorial in the VS Code documentation repository.

## Prerequisites

`{'mod':'speak'}` To successfully complete this tutorial, you must do the following steps:

1. Install Mingw64 and add the path of the bin folder to the Windows PATH environment variable (Which we done if the previous section)
2. Install Visual Studio Code.
3. Install the C/C++ extension for VS Code.
   You can install the C/C++ extension by searching for 'c++' in the Extensions view (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>X</kbd>).
   ![C++ Extension]($/_res/vsc/cpp-extension.png)

> `{'mod':'tag','type':'remember'}` `{'mod':'speak'}` Installation of extensions require internet connection. In this case, the c++ extension may take 15 to 20 mins to install depending on the speed of your internet connection. It is advised to use Digicel or Telikom ISP services if the campus Wifi is too slow. Please note that connection to the extension server may drop for low data rates due to time-out settings of the external server.

# Create a C/C++ Project folder

`{'mod':'speak'}` A Project in VSC is just a folder containing a set of files and subfolders. To begin, let's start by creating an empty folder: `helloworld` in your desktop and open it via the VSC main menu `File > Open Folder ...`

> `{'mod':'tag','type':'remember'}` `{'mod':'speak'}` VSC is just an I.D.E. (Integrated Development Environment). It is a tool that only calls other data processing applications (e.g., GCC: the C compiler) to process data files (e.g., inputting C source codes to GCC and GCC will output Windows executables or apps files). VSC by itself can't generate the machine code for the hosting O.S. nor the MCU: Arduino. However, it provides a flexible set of configuration rules to construct our data processing pipeline so that the development of the software components is more efficient.
> 
> `{'mod':'tag','type':'warning'}` `{'mod':'speak'}` VSC only processes files that "reside" in the currently-opened project folder. Hence you can't open a c-source file directly and expect the tool to run it. In this section we shall look into ways of how to edit VSC configuration files to form the data pipeline of converting a set of c source files into a windows executable.

## Add a **source code file**

 `{'mod':'speak'}` Once the folder is opened, in the **File Explorer** title bar, select the `New File` button and name the file `main.c`.

![C++ Extension]($/_res/vsc/new-file-button.png)

## Add **hello world** source code

 `{'mod':'speak'}` Now paste in this source code:

```{'mod':'code','lang':'c'}
#include <stdio.h>
int main() {
   // printf() displays the string inside quotation
   printf("Hello, World!");
   return 0;
}
```
 `{'mod':'speak'}` Now press <kbd>Ctrl</kbd>+<kbd>S</kbd> to save the file. Notice how the file you just added appears in the `File Explorer` view press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>E</kbd> in the side bar of VS Code:

![C++ Extension]($/_res/vsc/add-a-src-file.png)

## Add a **Makefile** file

 `{'mod':'speak'}` Compiling the source code files can be tiring, especially when your application maybe built from multiple sources, which requires you to type-out many lines compiling command every time you need to compile. Makefiles are the solution to simplify this task.

Makefiles are special format files that help build and manage the projects automatically. Details on more depth usage will be covered in the next section. For now, add another new file and name if `makefile`. Once done your project folder should look like this:

![add-makefile]($/_res/vsc/add-makefile.png)


 `{'mod':'speak'}` Then open it and enter the following code:

 ```{'mod':'code','lang':'makefile','highlight':'2'}
app: main.c
	gcc -g -o app.exe main.c
```

> `{'mod':'tag','type':'warning'}` `{'mod':'speak'}` The indentation of line 2 MUST BE a single <kbd>Tab</kbd> character. If errors occures then it is most likely caused by the inappropriate use of space-based indentations.

 `{'mod':'speak'}` For the time being, the meaning of these two lines of `makefile` statements shall be understood as follows:

|                 Command | Meaning                                                                                                                                                                                                                             |
| ----------------------: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|           `app: main.c` | `{'mod':'speak'}` Declares a task named `app` such that it depends on any updates to file `main.c` of the folder where the current `makefile` lives.                                                                                |
| `gcc -o app.exe main.c` | `{'mod':'speak'}` Calls `gcc` and output (via the option `-o`) the executable `app.exe` from the source code stored in `main.c`. The `-g` is to instruct the compiler to embedded debug information so that breakspoint can be used |

## Build helloworld.c

 `{'mod':'speak'}` Next, you'll create a `tasks.json` file to tell VS Code how to build (compile) the program. This task will invoke the `makefile` interpreter from which it shall create an executable file `app.exe` based on the source codes in `main.c`.

`{'mod':'speak'}` From the main menu, choose **Terminal** > **Configure Tasks**. In the dropdown, which will display a tasks dropdown listing various predefined build tasks for C++ compilers. Since we are using `makefile` to build our `app` choose `create task.json from template` > `Others...`. Once completed you should find a new  `.vscode` folder created with a `tasks.json` file living inside. The content of `tasks.json` should look like the following:

```{'mod':'code','lang':'javascript','highlight':'7,8,9'}
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "label": "echo",
            "type": "shell",
            "command": "echo Hello"
        }
    ]
}
```
`{'mod':'speak'}` The meaning of each of the highlighed lines is as follows:

| Line # | Meaning                                                                                                                                  |
| :----: | :--------------------------------------------------------------------------------------------------------------------------------------- |
|   7    | `{'mod':'speak'}` The `label` field defined the name of the task called `echo`.                                                          |
|   8    | `{'mod':'speak'}` The `type` field defined the nature of the task, in which case it is one that sends a command to the `shell` terminal. |
|   9    | `{'mod':'speak'}` The `command` field defines the shell command to be sent the terminal for execution                                    |

### What is a terminal?

`{'mod':'speak'}` Terminals, also known as **command lines** or **consoles**, allow us to accomplish and automate tasks on a computer without the use of a graphical user interface. Using a terminal allows us to send simple text commands to our computer to do things like navigate through a directory or copy a file, and form the basis for many more complex automations and programming skills. You can open a terminal in VSC by selecting from the main menu **Terminal** > **New Terminal**. Below shows how a terminal would appear in VSC:

`{'mod':'img','url':'$/_res/vsc/terminal-view.png'}`

`{'mod':'tag','type':'task'}` `{'mod':'speak'}` Now try out the terminal by pasting following commands
1. `{'mod':'speak'}` The `echo Hello` command and what it does.
2. `{'mod':'speak'}` Now run the `mingw32-make` command and then the file `app.exe` should appear. `app.exe` is the app file generated by the gcc compiler, you can run it by entering `app.exe` in the terminal. The traces of texts produce in the terminal should look something like this:

``` {'mod':'code','lang':'bash', 'highlight':'2,5'}
C:\projects\c++\HelloWorld>mingw32-make
gcc -g -o app.exe main.c

C:\projects\c++\HelloWorld>app.exe
Hello, World!

C:\projects\c++\HelloWorld>
```
Note that:
-  `{'mod':'speak'}` **line 2** is the output generated by the `makefile` interpreter. Which passes the gcc command for creating the `app.exe` executable from `main.c`
-  `{'mod':'speak'}` **line 5** is the output generated by the `app.exe` executable.

### Complete the compilation pipeline
`{'mod':'speak'}` Lets return to the content of `tasks.json` file and update it with some of our modifications:
- `{'mod':'speak'}` Firstly, change the `label` value to something more meaningful such as `build app`
- `{'mod':'speak'}` Next, change the `command` value to `mingw32-make`, which in invoke the makefile interpreter.

`{'mod':'speak'}` The following snippet should reflect all the changes made (Don't forget to save the changes):

```{'mod':'code','lang':'javascript','highlight':'7,9'}
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "label": "build app",
            "type": "shell",
            "command": "mingw32-make"
        }
    ]
}
```

## Running main.c from VSC

`{'mod':'speak'}` A debugger or debugging tool is a computer program used to test and debug other programs (the "target" program). The main use of a debugger is to run the target program under controlled conditions that permit the programmer to track its operations in progress and monitor changes in computer resources (most often memory areas used by the target program or the computer's operating system) that may indicate malfunctioning code. The GCC tool chain provide the GDB debugger for such purpose. To debug or run our prototype application `app.exe` within VSC, you'll create a `launch.json` file to configure VS Code to launch the GDB debugger when you press <kbd>F5</kbd> to debug the program. From the main menu, choose **Run > Add Configuration...** and then choose C++ (GDB/LLDB).

`{'mod':'speak'}` VS Code creates a `launch.json` file and opens it in the editor:

```{'mod':'code','lang':'javascript','highlight':'11,18,19-25'}
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "(gdb) Launch",
            "type": "cppdbg",
            "request": "launch",
            "program": "enter program name, for example ${workspaceFolder}/a.exe",
            "args": [],
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}",
            "environment": [],
            "externalConsole": false,
            "MIMode": "gdb",
            "miDebuggerPath": "/path/to/gdb",
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ]
        }
    ]
}
```

`{'mod':'speak'}` The lines highlighted have the following meanings

|  Line   | Meaning                                                                                                                                                 |
| :-----: | :------------------------------------------------------------------------------------------------------------------------------------------------------ |
|   11    | `{'mod':'speak'}` The `program` field refers the executable the debugger to latch onto. In this case we will set it to `${workspaceFolder}/app.exe`     |
|   18    | `{'mod':'speak'}` The `miDebuggerPath` field refers to the location of the debugger app: `gdb.exe`, which is located in `C:\msys64\mingw64\bin\gdb.exe` |
| 19 - 25 | `{'mod':'speak'}` replace it with `"preLaunchTask": "build app"` task which calls the `"build app"` that was defined in `task.json`                     |

`{'mod':'speak'}` The final changes to the `launch.json` file should look like this:


```{'mod':'code','lang':'javascript','highlight':'11,18,19'}
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "(gdb) Launch",
            "type": "cppdbg",
            "request": "launch",
            "program": "${workspaceFolder}/app.exe",
            "args": [],
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}",
            "environment": [],
            "externalConsole": false,
            "MIMode": "gdb",
            "miDebuggerPath": "C:/msys64/mingw64/bin/gdb.exe",
            "preLaunchTask": "build app"
        }
    ]
}
```

`{'mod':'speak'}` Now we have a very basic, vannila version of the software build pipeline is ready to run. try it out by
modifying the `main.c` with the following snippet of code and press `F5` to run:

```{'mod':'code','lang':'c'}
#include <stdio.h>

int main()
{
    // printf() displays the string inside quotation
    printf("Hello, World!\n");
    printf("This is my c first program\n");
    printf("For EE344!!\n");
    return 0;
}
```
`{'mod':'speak'}` Once the app finishes you should see the following text being printed into the terminal view:

```{'mod':'code','lang':'bash'}
Hello, World!
This is my c first program
For EE344!!
```

### Using GDB

`{'mod':'speak'}` GDB provides source-code debugging functionality through breakpoints, step-throughs, variable inspection and evaluation of simple expressions. We will learn more on how to use these functions as we proceed with the labs and exercises through-out the course.

`{'mod':'speak'}` For now, open `main.c` and mark a simple breakpoint by moving your mouse towards the left margine of the line-number column as show here:

`{'mod':'img','url':'$/_res/vsc/set-breakpoint.png'}`

`{'mod':'speak'}` Then press <kbd>F5</kbd> to run it. In these situation you'll find that the program **pauses** at the breakpoint:

`{'mod':'img','url':'$/_res/vsc/pause-at-breakpoint.png'}`

`{'mod':'speak'}` At the top-right section of VSC, you'll find a list of buttons like this:

`{'mod':'img','url':'$/_res/vsc/debug-buttons.png'}`

`{'mod':'speak'}` The function of each button is listed in the following table:

| Button # | Functions                                                                                                     |
| :------: | :------------------------------------------------------------------------------------------------------------ |
|    1     | `{'mod':'speak'}` The "Continue" button will unpause the program until it hits another break point            |
|    2     | `{'mod':'speak'}` The "Step into" button will execute the body of a function, called by the current statement |
|    3     | `{'mod':'speak'}` The "Restart" button simply restart the execution of the program                            |
|    4     | `{'mod':'speak'}` The "Step Over" button will unpause the program until the next line or statement            |
|    5     | `{'mod':'speak'}` The "Step out" button unpause the program until the calling function completes              |
|    6     | `{'mod':'speak'}` The "Stop" button simply kills the execution of the program                                 |

`{'mod':'speak'}` For now, you can use button 4 to step through the statements and see what happens in the terminal.

Finally you may remove a breakpoint simply by clicking on an existing one.
