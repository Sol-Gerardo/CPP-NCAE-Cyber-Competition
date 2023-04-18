- Spaces are columns in awk
- ![[Screenshot 2023-04-16 at 10.06.53 AM.png]]

- **'{print $0}'** will print everything 
- We could also use **'{print}'** to print everything 

- awk -F ":" '{print $1}' /etc/passwd
	- -F is our field separator 
	- colon is used to separate our fields 
	- $1 is the first column
	- /etc/passwd is the file we are obtaining our data from
	- This will print every user on our system

- Printing multiple columns:
	- awk -F ":" '{print $1 $6 $7}' /etc/passwd

- To separate the columns
	- awk -F ":" '{print $1 " " $6 " " $7}' /etc/passwd
- Alternatively:
	- awk -F ":" '{print $1 "\t" $6 "\t" $7}' /etc/passwd

- awk 'BEGIN{FS=":"; OFS="-"} {print $1, $6,$7}' /etc/passwd
	- Print field separator that is a dash
	- Print first, sixth, and seventh columns 

- awk -F "/" '/^\// {print $NF}' /etc/shells 
	- We use escape character / 
	- ^ Means beginning with a slash
	- \/ escapes the slash 
	- $NF means last field in the record

- awk -F "/" '/^\// {print $NF}' /etc/shells | uniq
	- We can also use this to remove repeated outputs 
- Alternatively:
	- awk -F "/" '/^\// {print $NF}' /etc/shells | uniq
		- To sort the output

- df | awk '/\/dev\/sda/ {print $1}'
	- Print first field with /dev/sda
- ![[Screenshot 2023-04-16 at 1.04.42 PM.png]]
- Add the results:
	- ![[Screenshot 2023-04-16 at 1.05.25 PM.png]]

- We are asking for the length greater than 7 within the respective files 
	- ![[Screenshot 2023-04-16 at 1.06.13 PM.png]]

- Note: awk is also a scripting language 

- If the last field equals \\bin\\fish print $0
	- ![[Screenshot 2023-04-16 at 1.09.34 PM.png]]

- Loop
	- ![[Screenshot 2023-04-16 at 1.11.39 PM.png]]

- The first column needs to match the search patter 
	- The beginning of the line needs to be a b or a c
	- Print every line that matches this criteria
	- ![[Screenshot 2023-04-16 at 1.14.40 PM.png]]

- Print starting at substring 4 until the end of the line 
	- ![[Screenshot 2023-04-16 at 1.16.15 PM.png]]

- Match every line that has the letter o and following it with the following string 
- RSTART is the index location where the letter o appeared on the line
	- ![[Screenshot 2023-04-16 at 1.18.30 PM.png]]

- NR is the number of records that equals the length of 7 from line 7 to line 11 then print the number of records starting from first line 
- ![[Screenshot 2023-04-16 at 1.21.37 PM.png]]

- Number of lines within the file
	- ![[Screenshot 2023-04-16 at 1.22.45 PM.png]]

- 