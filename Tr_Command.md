### Tr Command

The ****tr**** command is a UNIX  command-line utility for translating or deleting characters. It supports a range of transformations including uppercase to lowercase, squeezing 
repeating characters, deleting specific characters, and basic find and 
replace.

```css
Syntax
$tr [OPTION] SET1 [SET2]
Where:
-c : complements the set of characters in string.i.e., 
     operations apply to characters not in the given set
-d : delete characters in the first set from the output
-s : replaces repeated characters listed in the set1 with single 
     occurrence
-t : truncates set1 to lenght of set2
```



### Accepted interpreted sequence

```css
\\	Backslash.
\a	An audible bell character.
\b	Backspace.
\f	Form feed.
\n	Newline character.
\r	Return character.
\t	Horizontal tab.
\v	Vertical tab.
CHAR1-CHAR2	All characters from CHAR1 to CHAR2 in an ascending order.
[CHAR*]	Copies CHAR* in SET2 up to the length of SET1.
[CHAR*REPEAT]	Repeats copies of CHAR. Repeats octal if starting with 0.
[:alnum:]	All letters and digits.
[:alpha:]	All letters.
[:blank:]	Horizontal whitespaces.
[:cntrl:]	All control characters.
[:digit:]	All digits.
[:graph:]	Printable characters, excluding space.
[:lower:]	All lowercase characters.
[:print:]	Printable characters, including space.
[:punct:]	All punctuation characters.
[:space:]	Horizontal or vertical whitespace characters.
[:upper:]	All uppercase letters.
[:xdigit:]	Hexadecimal digits.
[=CHAR=]	All characters equivalent to CHAR.
```

### Examples

```css
Convert Lower Case to Upper Case
$cat file | tr [a-z] [A-Z]
or
$cat file | tr [:lower:] [:upper:]
```



```css
White Space to Tab
$cat file | tr [:space:] "\t"
```



```css
Braces to Parenthesis
$cat file | tr "{}" "()"
```



```css
Squeeze a sequence of repetitive characters using "-s"
$tr -s " " <<< "Welcome    To    GeeksforGeeks"


$echo 'TODAYYYY IIIS SOOO COOOLD ~' | tr -s 'A-Z' 'a-z'  
today is so cold ~
```



```css
Delete specified characters using "-d"
$cat file | tr -d W
Deletes W from the file
```



```css
Complement the sets using "-c"
$cat file | tr -cd [:digit:]
Removes all character except digit 
```



```css
Delete Character
$cat file | tr -d '0-9'
Removes all numbers


Delete Spaces
$cat file | tr -d '[:space:]'


To Remove Newline
$cat file | tr -d '\n'


Find and Replace
$cat file | tr '-' '_'


New Line to Single Space
$cat file | tr -s '\n' ' '
```
