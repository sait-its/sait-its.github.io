### Introduction to Linux Shell

- A Linux shell is a program that provides a command-line interface (CLI) for users to interact with the operating system.
- It acts as an intermediary between the user and the system's kernel, allowing users to enter commands, run programs, manage files, and automate tasks through scripts.

---

### Introduction to Linux Shell

- When you type a command into a shell, the shell interprets your input and passes it to the operating system to execute.
- After the command runs, the shell displays the output or any resulting messages.
- This process forms a loop: the shell reads your command, executes it, prints the output, and waits for the next command.

---

### Introduction to Linux Shell

- It is both an interactive command language and a scripting language, meaning you can use it for one-off commands or to write scripts that automate complex tasks.
- Users typically access the shell through a terminal emulator, which is a program that opens a window for shell interaction.

---

### Common Shells in Linux

- **Bourne Shell (sh)**: The first UNIX shell. 
- **GNU Bourne-Again shell (bash)**: Most common; flexible, widely supported, scripting-friendly.
- **C Shell (csh)**: C-like syntax, command history, scripting support.
- **tcsh**: C shell with programmable command-line completion, command-line editing, and a few other features. Unlike the other common shells, functions **CANNOT** be defined in a tcsh script and the user must use aliases instead (as in csh). It is the native root shell for some BSD-based systems.

---

### Common Shells in Linux

- **Korn Shell (ksh)**: A superset of the Bourne shell. It allows in-built support for arithmetic operations while offering interactive features which are similar to the C shell.
- **Z Shell (zsh)**: Modern, feature-rich, with advanced completion and customization. It's the default shell for macOS.
- **Friendly Interactive Shell (fish)**: a [Unix-like shell](https://en.wikipedia.org/wiki/Unix_shell) with a focus on interactivity and usability. Fish is designed to be feature-rich by default, rather than highly configurable, and does **NOT** adhere to [POSIX](https://en.wikipedia.org/wiki/POSIX) shell standards by design.

---

### Creating a Script File

- When creating a shell script file, you should specify the shell you are using in the first line of the file.
- In a normal shell script line, the pound sign (`#`) is used as a comment line. A comment line in a shell script isn't processed by the shell.
- A **shebang** in a shell script is the character sequence `#!` at the very start of the file, immediately followed by the absolute path to the interpreter that should execute the script (for example, `#!/bin/bash` or `#!/usr/bin/env bash`).

---

### Shebang in Linux Shell Scripting

- If the shebang is missing, the OS may not know which interpreter to use, and the script may fail to run unless you explicitly invoke the interpreter (e.g., `bash myscript.sh`).
- The shebang ensures your script runs with the intended interpreter, which is essential because different shells have different features and syntax.
- It makes scripts portable and executable as standalone programs, without requiring the user to manually specify the interpreter each time.

---

### Executing a Shell Script

```bash
#!/usr/bin/bash
echo "Hello World"
```

- Create a file `hello-world.sh` that prints "Hello World" to the stdout.
- You can use `bash hello-world.sh` to execute it.
- Or modify the file permissions and allow execution of the script by `chmod u+x hello-world.sh`. Use `ls -l` to verify the permissions of the file. Use `./hello-world.sh` to run it.

---

### Displaying Messages

- The `echo` command can display a simple text string following the command. By default you don't need to use quotes if there are quotes within the string.
- The `echo` command uses either double or single quotes to delineate text strings. If you use them within your string, you need to use one type of quote within the text and the other type to delineate the string.

```bash
echo This will work without quotes
echo We'll learn shell scripting today
echo "This is a test to see if you're paying attention"
echo 'The instructor says "scripting is easy".'
```

---

### Environment Variables

- Variables allow you to temporarily store information within the shell script for use with other commands in the script.
- The shell maintains **environment variables** that track specific system information, such as the name of the system, the name of the user logged into the system, the user's system ID (called UID), the default home directory of the user, and the search path used by the shell to find programs.

```bash
echo $PATH
echo $HOME $USER $UID $SHELL $HOSTNAME
```

---

### User Variables

- User variables can be any text string of up to 20 letters, digits, or underscore characters. User variables are **case sensitive**, so *`Var1`* is different from *`var1`*.
- Values are assigned to user variables using an equal sign. No spaces can appear between the variable, the equal sign, and the value.
- To get the value of the variable, add dollar sign `$` before the variable.

```bash
#!/bin/bash
greeting=Hello
name=World
echo $greeting $name
```

---

### User Variables

- The shell script stores all variable values as text strings; it's up to the individual commands in the shell to determine the data type used for the variable value.
- Variables defined within the shell script maintain their values throughout the life of the shell script but are deleted when the shell script completes.

---

### Command Substitution

- One of the most useful features of shell scripts is the ability to extract information from the output of a command and assign it to a variable. Once you assign the output to a variable, you can use that value anywhere in your script. This comes in handy when you're processing data in your scripts.
- There are two ways to assign the output of a command to a variable:
  - The backtick character `
  - The `$()` format

---

### Command Substitution

```bash
#!/bin/bash
# copy the /usr/bin directory listing to a log file
# The today variable is assigned the output of a formatted date 
# command. The +%y%m%d format instructs the date command to 
# display the date as a two-digit year, month, and day.
today=$(date +%y%m%d)
ls /usr/bin -al> log.$today
```

- This is a popular example of how command substitution is employed to capture the current date and use it to create a unique filename in a script.

---

### Performing Math

- It's a bit awkward to manipulate numbers in shell script. You can use `$((OPERATION))`, `$[OPERATION]` or `expr` to perform mathematical operations in your shell scripts.

```bash
echo $((1+5))   # 6
echo $((1 + 5)) # 6
echo $[1+5]     # 6
echo $[1 + 5]   # 6
expr 1+5        # 1+5
# Add spaces around operators
expr 1 + 5      # 6
expr 5 * 2      # syntax error
# Many of the expr command operators have other meanings in the 
# shell (such as the asterisk). Use the escape (the backslash)
# to identify any characters that may be misinterpreted.
expr 5 \* 2     # 10
```

---

### `if-then` Statement

- In other programming languages, the object after the `if` statement is an equation that is evaluated for a `TRUE` or `FALSE` value. The Bash shell `if` statement runs the command defined on the `if` line. If the exit status of the command is 0, the commands listed under the `then` section are executed.
- The `if-then` statement has the following format:

```bash
if command
then
    commands
fi
```

---

### `if-then` Statement

```bash
#!/bin/bash
# testing the if statement
if pwd
then
     echo "It worked"
fi
# Because IamNotaCommand is an incorrect command, it produces an 
# exit status that's non-zero. Thus, the Bash shell skips the echo
# statement in the then section.
if IamNotaCommand
then
     echo "It worked"
fi
echo "We are outside the if statement"
```

---

### `if-then-else` Statement

- When the command in the `if` statement line returns a non-zero exit status code, the Bash shell executes the commands in the `else` section.
- The `if-then-else` statement provides another group of commands in the statement:

```bash
if command
then
   commands
else
   commands
fi
```

---

### The `test` Command

- The `test` command provides a way to test different conditions in an `if-then` statement. If the condition listed in the `test` command evaluates to `TRUE` , the `test` command exits with a zero exit status code.
- This makes the `if-then` statement behave in much the same way that `if-then` statements work in other programming languages. If the condition is false, the `test` command exits with a non-zero exit status code, which causes the `if-then` statement to exit.

---

### The `test` Command

- The variable `my_variable` contains content (`Full`), so when the `test` command checks the condition, the exit status returns a zero. This triggers the statements in the `then` code block.

```bash
#!/bin/bash
# testing if a variable has content
my_variable="Full"
if test $my_variable
then
     echo "The my_variable variable has content and returns a True."
     echo "The my_variable variable content is: $my_variable"
else
     echo "The my_variable variable doesn't have content,"
     echo "and returns a False."
fi
```

---

#### Alternative Way of Testing a Condition

- The square brackets `[ condition ]` define the test condition. Be careful: you *must* have **a space after the first bracket and a space before the last bracket**, or you'll get an error message.
- The `test` command and test conditions can evaluate three classes of conditions:
  - Numeric comparisons
  - String comparisons
  - File comparisons

---

#### Alternative Way of Testing a Condition

- **For test conditions, the only numbers the Bash shell can handle are integers.** Although you can use floating-point values for commands, such as `echo` , they will not work properly in test conditions.

```bash
#!/bin/bash
# Using numeric test evaluations
value1=10; value2=11
if [ $value1 -gt 5 ]
then
     echo "The test value $value1 is greater than 5."
fi
if [ $value1 -eq $value2 ]
then
     echo "The values are equal."
else
     echo "The values are different."
fi
```

---

### String Equality

- The equal and not equal conditions are fairly self-explanatory with strings. It's pretty easy to know whether two string values are the same or not.

```bash
#!/bin/bash
# Using string test evaluations
testuser=mario
if [ $testuser = mario ]
then
     echo "The testuser variable contains: mario"
else
     echo "The testuser variable contains: $testuser"
fi
```

---

### String Order

- You need to properly escape the greater-than symbol using the backslash (`\`) to test string order.

```bash
#!/bin/bash
# Properly using string comparisons
string1=soccer
string2=zorbfootball
if [ $string1 \> $string2 ]
then
     echo "$string1 is greater than $string2"
else
     echo "$string1 is less than $string2"
fi
```

---

### File Comparisons

- File comparisons allow you to test the status of files and directories on the Linux filesystem.
  - `-d` *`file`*: Checks if *`file`* exists and is a directory.
  - `-e` *`file`*: Checks if *`file`* exists.
  - `-f` *`file`*: Checks if *`file`* exists and is a file.
  - `-r` *`file`*: Checks if *`file`* exists and is readable.
  - `-s` *`file`*: Checks if *`file`* exists and is not empty.
  - `-w` *`file`*: Checks if *`file`* exists and is writable.
  - `-x` *`file`*: Checks if *`file`* exists and is executable.
  - `-O`, `-G`, *`file1`* `-nt` *`file2`*, *`file1`* `-ot` *`file2`*

---

### Checking Directories

- The `-d` test checks to see if a specified directory exists on the system. This is usually a good thing to do if you're trying to write a file to a directory or before you try to change to a directory location.

```bash
#!/bin/bash
# Look before you leap
jump_directory=/home/student
if [ -d $jump_directory ]
then
     echo "The $jump_directory directory exists."
     cd $jump_directory
     ls
else
     echo "The $jump_directory directory does NOT exist."
fi
```

---

### `for` Statement

- Iterating through a series of commands is a common programming practice.
- The Bash shell provides the `for` command to allow you to create a loop that iterates through a series of values.
- Each iteration performs a defined set of commands using one of the values in the series.

```bash
for var in list
do
    commands
done
```

---

### `for` Statement

- The most basic use of the `for` command is to iterate through a list of values defined within the `for` command itself.

```bash
#!/bin/bash
# basic for command
for test in BC AB SK MB ON QC
do
    echo The next province is $test
done
echo "The last province we visited was $test"
```

---

### `while` Loop

- While loops check for a condition and loop until the condition remains `true`. We need to provide a counter statement that increments the counter to control loop execution.

```bash
#!/bin/bash
i=1
while [[ $i -le 10 ]] ; do
    echo "$i"
    (( i += 1 ))
done
```

---

### Key Takeaways

- A shell is a command-line interface for interacting with the OS.
- Start scripts with a shebang to set the interpreter.
- Use `chmod u+x` to make scripts executable.
- Assign variables with no spaces (`var="value"`) and access with `$var`.
- Capture command output into a variable using `output=$(command)`.
- Use the echo command to display messages and variable values.

---

### Key Takeaways

- Perform math operations using the `$((expression))` syntax.
- if statements check for a command's successful (zero) exit status.
- Use `[ condition ]` with spaces for numeric, string, or file tests.
- Check file status with operators like `-f` (file) or `-d` (directory).
- Use for loops to iterate over a list of items.
- while loops repeat actions as long as a condition is true.

---

### Sources:

- https://www.freecodecamp.org/news/shell-scripting-crash-course-how-to-write-bash-scripts-in-linux/
- https://www.freecodecamp.org/news/bash-scripting-tutorial-linux-shell-script-and-command-line-for-beginners/
- https://www.shellscript.sh/
- https://medium.com/@gudisagebi1/conditions-in-bash-scripting-if-statements-94e883a8d493