# Bash Docs

### Reading User Input
To read input from a user, use the `read` command. There are two ways to utilize read:
<br/>

#### First Approach
Print a message to the screen then run read.
```sh
echo -n "What is your name? "
read VAR
echo "Hi, $VAR!"

# Result
# > What is your name? Brandon
# > Your Answer: Hi, Brandon!
```
*note: the `-n` flag prevents echo from creating a new line after printing the message. if you would like to print your message and have users answer on a new line, simply remove the flag*
<br/>

#### Second Apporach
use `read` with the prompt `-p` flag to print a message to the screen.
```sh
read -p "What is your name? " VAR
echo "Hi, $VAR!"

# Result
# > What is your name? Brandon
# > Your Answer: Hi, Brandon!
```
<br/>

If for whatever reason we don't want to supply our own variable, bash captures the latest read value in the built in `$REPLY` variable.
```sh
read -p "What is your name? "
echo "Hi, $REPLY!"

# Result
# > What is your name? Brandon
# > Your Answer: Hi, Brandon!
```
<br/>

#### Read Flags
| Flag | Description |
| -- | -- |
| `-n` | will only accept number of characters of input following flag. |
| `-p` | echo the following prompt before reading input. |
| `-r` | read the string literally, e.g. to ommit a backslash "\\" character. |
| `-s` | do not echo input, e.g. user inputting a password. |

<br/>

Example: let's say we created a piece of software that requires a user to input a 5 digit numeric pin code.
```sh
read -p "Enter your pin: " -s -n 5 PIN
printf "\n$PIN\n"

# Result
# Enter your pin:
# 12345
```
We used `-p` to set a prompt, `-s` to suppress the input, `-n` to limit the number of inputted characters and finally using `PIN` as our variable to capture eveyrthing.

---
<br/>

### String Formatting
Using the `printf` command, we can insert a variable into a string and then format.  

```sh
declare -r VAR="Hi!"
printf "%s\n" $VAR

# Result
# > Hi!
```

#### Format Specifiers
| Specifier | Description |
| -- | -- |
| `%b` | String: Interprets escaped "\\n" characters. |
| `%d` | Integer Specifier: Show integral values. |
| `%f` | Floating Point Number: Used for output of floating point values |
| `%s` | String: Ignores escaped "\\n" characters and reads them as part of the string. |
| `%x` | Hexadecimal: Used for output of lowercase hexadecimal values for integers and for padding the output|
