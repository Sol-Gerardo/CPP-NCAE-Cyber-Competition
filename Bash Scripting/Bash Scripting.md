- We can run bash scripts using:
	- bash shelltest.sh

- Alternatively we can run scripts using:
	- ./shelltest.sh

- Before doing this we must give the script execution permissions:
	- chmod u+x shelltest.sh

- Example:
```bash
#!/bin/bash

FIRST_NAME=Herbert
LAST_NAME=Lindemans
echo Hello $FIRST_NAME $LAST_NAME
```

# Interactive Shell:
```bash
#!/bin/bash

echo What is your first name?
read FIRST_NAME
echo What is your list name?
read LAST_NAME

echo Hello $FIRST_NAME $LAST_NAME
```

# Positional arguments:
- Arguments are at specific positions, commands can take in arguments at a specific position, counting from one (0 reserved for the shell)

- ![[Screenshot 2023-04-15 at 3.43.05 PM.png]]

- Use ./posargu Gerardo Solis 
```bash
#!/bin/bash
echo Hello $1 $2
```

# Piping
- We can send a commands output to other commands 
- ![[Screenshot 2023-04-15 at 3.50.12 PM.png]]

# Output Redirection
- Symbols used
	- > symbol to write to a file 
	- >> to append to a file 
- ![[Screenshot 2023-04-15 at 4.03.05 PM.png]]

- Example use cases:
	- Logging to a log file  (for ex. using timestamps)
	- Dynamically creating (config) files

```bash
cat << EOF
> I will 
> write some
> text here
> EOF
I will 
write some 
text here 
```

- Once the EOF is reached the text entered will be displayed 

``` bash
wc -w <<< "Hello There"
2
```

- The three <<< will display the word count number rather than accepting input

- ![[Screenshot 2023-04-15 at 4.55.17 PM.png]]
- $? will display the exit code of the last executed command 
	- 0 means successful 
	- 1 means unsuccessful 
- The \[ hello = hello \]
	- Is just a comparison statement

- ![[Screenshot 2023-04-15 at 4.57.02 PM.png]]
- We can also use -eq instead of =, but this will fails with strings 

# Case Statements 
- Better than if/elif/else when 
	- Checking for multiple values 
	- Is easier to read 

```bash
#!/bin/bash

case ${1,,} in
        jerry | administrator )
              echo "Hello, you're the boss here!"
              ;;
        help)
              echo "Just enter your username!"
              ;;
        *) # This is the catch all option when no options are give
              echo "Hello there. You're not the boss of me. Enter a valid username!"
esac # exit case statement 

# | acts as a separator for 
# multiple options 
```

# Arrays
- Assigning multiple values to one variable collected in a list known as an array
- MY_FIRST_LIST=(one two three four five)
- echo $MY_FIRST_LIST 
	- displays only first element
- To display all elements 
- echo {$MY_FIRST_LIST[@]}
- Display first element:
	- echo {$MY_FIRST_LIST[0]}

# For Loop
- Counting length of each word in the array
	- for item in ${MY_FIRST_LIST[@]}; do echo -n $item | wc -c; done

# Functions
```bash
#!/bin/bash

showuptime(){
    up=$(uptime -p  |cut -c4-)
    since=$(uptime -s)
    cat <<EOF
-----
This machine has up for  ${up}
It has been running since ${since}
-----
EOF
}
showuptime # This calls the function
```

```bash
#!/bin/bash

showuptime(){
    up=$(uptime -p  |cut -c4-)
    since=$(uptime -s)
    cat <<EOF
-----
This machine has up for  ${up}
It has been running since ${since}
-----
EOF
}
showuptime # This calls the function
```

```bash
#!/bin/bash
up="before"
since="function"
echo $up
echo $since

showuptime(){
    local =$(uptime -p  |cut -c4-)
    local since=$(uptime -s)
    cat <<EOF
-----
This machine has up for  ${up}
It has been running since ${since}
-----
EOF
}
showuptime # This calls the function
echo $up
echo $since
# variables not overwritten
```

```bash
#!/bin/bash
showname(){
    echo hello $1
}
showname jerry
```

# Exit Codes 
```bash
#!/bin/bash
showname(){
    echo hello $1
    if [ ${1,,} = jerry ]; then
        return 0
    else
        return 1
    fi
}
showname $1
if [ $? = 1 ]; then
   echo "Someone unknown called the function!"
```

# AWK
- Used to filter files to get the portion that we want 
- ![[Screenshot 2023-04-16 at 9.14.33 AM.png]]
- ![[Screenshot 2023-04-16 at 9.16.16 AM.png]]
- ![[Screenshot 2023-04-16 at 9.17.59 AM.png]]

# SED
- Before: 
	- ![[Screenshot 2023-04-16 at 9.25.22 AM.png]]
- After, we replaced fly with grasshopper:
	- ![[Screenshot 2023-04-16 at 9.25.57 AM.png]]
- Breakdown: 
	- s for substitute
		- Substitute fly with grasshopper 
	- g to search the file globally for this text and replace every occurrence 

- sed -i.ORIGINAL 's/fly/grasshopper/g' sedtest.txt
	- Creates original file