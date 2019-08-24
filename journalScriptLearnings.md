# Journal Script Learnings

## Variables

### Declaring A Variable

Varibles are declared using `=` as an assignment operator, with no spaces.

```
myVar1=Hello
myVar2=200
myVar3='My variable contents'
myVar4="My variable contents again"

echo $myVar1
$ Hello
echo $myVar2
$ 200
echo $myVar3
$ My variable contents
echo $myVar4
$ My variable contents again
```

- If the variable is one word, you do not need ""
- If the variable is more than one word, you need "" or ''
- '' treats the variable contents as literal
- "" allows variable substitution
- The variable is accessed using a $ character immediately followed by its name.

### Concatenating Variables

Type the variable names in order.

```
var1="This is a "
var2="sentence."
var3=$var1$var2
echo var3

*Output*

This is a sentence.
```
### Variable Substitution

A variable name can be added to a string in an echo statement to enable display of the variable contents. This has to be used with "" characters.

```
# using the variables above...
echo "The contents of \$myVar1 is: $myVar1"

*Output*

The contents of $myVar1 is Hello
```

- $myVar1 has its contents substituted in the string output by echo
- note the use of backslash to escape $

### Command Substitution

Stores the output of a command/s in a variable. Uses the form `$(command)`.


```
workingDir=$(pwd)
echo "The current directory is: $workingDir"

*Output*

The current directory is: /home/steve/Scripts

	or

echo "The current directory is: $(pwd)"
```

References:

1. [Command Substitution](http://mywiki.wooledge.org/CommandSubstitution)  
2. [What is the benefit of using $() instead of backticks in shell scripts? (Stack Overflow)](https://stackoverflow.com/questions/9449778/what-is-the-benefit-of-using-instead-of-backticks-in-shell-scripts<Paste>)


## Dates


```
$ date
Fri Jul  5 13:07:15 UTC 2019
```

To use a timezone with `date`, use:

```
$ TZ='Australia/Melbourne' date
Fri Jul  5 23:07:15 AEST 2019
```

To format a date, use `+` followed by the formatting codes. For example, the format for my journal entry is:

```
TZ='Australia/Melbourne' date +%Y-%m-%d\ %H%M\ %A
	or
TZ='Australia/Melbourne' date +"%Y-%m-%d %H%M %A"

*Output*

2019-07-05 2324 Friday
```

Note the escaping of spaces in formatting. Without this, the command fails. Alternately, enclose the formatting string (after `+`) in quotes.

Common date formatting strings are:

- %Y	4 digit year (2019)
- %y	2 digit year (19)
- %m	2 digit month (01-12)
- %d	2 digit day (01-31)
- %H	2 digit hour (00-23)
- %M	2 digit minute (00-59)
- %A	Long day name (Monday)
- %a	Short day name (Mon)
- %B	Long month name (January)
- %b	Short month name (Jan)
- %u	Day of week (0-7)
- %U	Week of year (00-53)
- %j	Day of year (001-366)
- %T	Time as hh:mm:ss (24 hr format)
- %F	Date as yyyy-mm-dd (2019-07-05)
- %Z	Timezone abbreviation (AEST)

For a complete list of formatting strings, see [How To Format Date For Display or Use In a Shell Script (NixCraft)](https://www.cyberciti.biz/faq/linux-unix-formatting-dates-for-display/), [Bash Shell Scripting - Bash Date](https://www.tutorialkart.com/bash-shell-scripting/bash-date-format-options-examples/) Or `man date`.

To use this in a script, use the following form:

```
dateString="`TZ='Australia/Melbourne' date +%F\ %T`"
	(using legacy Bourne shell backticks)
*or*

dateString=$(TZ='Australia/Melbourne' date +%F $T)
	(using command substitution)
```




