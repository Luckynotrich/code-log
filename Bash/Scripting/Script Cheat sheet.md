

# Better  [Bash scripting cheatsheet](https://devhints.io/bash)

### Introduction

This is a quick reference to getting started with Bash scripting.

-   [Learn bash in y minutes](https://learnxinyminutes.com/docs/bash/) _(learnxinyminutes.com)_
-   [Bash Guide](http://mywiki.wooledge.org/BashGuide) _(mywiki.wooledge.org)_
-   [Bash Hackers Wiki](https://web.archive.org/web/20230406205817/https://wiki.bash-hackers.org/) _(wiki.bash-hackers.org)_

### Example

```bash
#!/usr/bin/env bash name="John" echo "Hello $name!"
```

### Variables

```bash
name="John" echo $name # see below echo "$name" echo "${name}!"
```

Generally quote your variables unless they contain wildcards to expand or command fragments.

```bash
wildcard="*.txt" options="iv" cp -$options $wildcard /tmp
```

### String quotes

```bash
name="John" echo "Hi $name" #=> Hi John echo 'Hi $name' #=> Hi $name
```

### Shell execution

```bash
echo "I'm in $(pwd)" echo "I'm in `pwd`" # obsolescent # Same
```

See [Command substitution](https://web.archive.org/web/20230326081741/https://wiki.bash-hackers.org/syntax/expansion/cmdsubst)

### Conditional execution

```bash
git commit && git push git commit || echo "Commit failed"
```

### Functions

```bash
get_name() { echo "John" } echo "You are $(get_name)"
```

See: [Functions](https://devhints.io/bash#functions)

### Conditionals

```bash
if [[ -z "$string" ]]; then echo "String is empty" elif [[ -n "$string" ]]; then echo "String is not empty" fi
```

See: [Conditionals](https://devhints.io/bash#conditionals)

### Strict mode

```bash
set -euo pipefail IFS=$'\n\t'
```

See: [Unofficial bash strict mode](http://redsymbol.net/articles/unofficial-bash-strict-mode/)

### Brace expansion

```bash
echo {A,B}.js
```

<table><tbody><tr><td><code>{A,B}</code></td><td>Same as <code>A B</code></td></tr><tr><td><code>{A,B}.js</code></td><td>Same as <code>A.js B.js</code></td></tr><tr><td><code>{1..5}</code></td><td>Same as <code>1 2 3 4 5</code></td></tr><tr><td><code>{{1..3},{7..9}}</code></td><td>Same as <code>1 2 3 7 8 9</code></td></tr></tbody></table>

See: [Brace expansion](https://web.archive.org/web/20230207192110/https://wiki.bash-hackers.org/syntax/expansion/brace)

## Parameter expansions

### Basics

```bash
name="John" echo "${name}" echo "${name/J/j}" #=> "john" (substitution) echo "${name:0:2}" #=> "Jo" (slicing) echo "${name::2}" #=> "Jo" (slicing) echo "${name::-1}" #=> "Joh" (slicing) echo "${name:(-1)}" #=> "n" (slicing from right) echo "${name:(-2):1}" #=> "h" (slicing from right) echo "${food:-Cake}" #=> $food or "Cake"
```

```bash
length=2 echo "${name:0:length}" #=> "Jo"
```

See: [Parameter expansion](https://web.archive.org/web/20230408142504/https://wiki.bash-hackers.org/syntax/pe)

```bash
str="/path/to/foo.cpp" echo "${str%.cpp}" # /path/to/foo echo "${str%.cpp}.o" # /path/to/foo.o echo "${str%/*}" # /path/to echo "${str##*.}" # cpp (extension) echo "${str##*/}" # foo.cpp (basepath) echo "${str#*/}" # path/to/foo.cpp echo "${str##*/}" # foo.cpp echo "${str/foo/bar}" # /path/to/bar.cpp
```

```bash
str="Hello world" echo "${str:6:5}" # "world" echo "${str: -5:5}" # "world"
```

```bash
src="/path/to/foo.cpp" base=${src##*/} #=> "foo.cpp" (basepath) dir=${src%$base} #=> "/path/to/" (dirpath)
```

### Prefix name expansion

```bash
prefix_a=one prefix_b=two echo ${!prefix_*} # all variables names starting with `prefix_` prefix_a prefix_b
```

### Indirection

```bash
name=joe pointer=name echo ${!pointer} joe
```

### Substitution

<table><tbody><tr><td><code>${foo%suffix}</code></td><td>Remove suffix</td></tr><tr><td><code>${foo#prefix}</code></td><td>Remove prefix</td></tr></tbody><tbody><tr><td><code>${foo%%suffix}</code></td><td>Remove long suffix</td></tr><tr><td><code>${foo/%suffix}</code></td><td>Remove long suffix</td></tr><tr><td><code>${foo##prefix}</code></td><td>Remove long prefix</td></tr><tr><td><code>${foo/#prefix}</code></td><td>Remove long prefix</td></tr></tbody><tbody><tr><td><code>${foo/from/to}</code></td><td>Replace first match</td></tr><tr><td><code>${foo//from/to}</code></td><td>Replace all</td></tr></tbody><tbody><tr><td><code>${foo/%from/to}</code></td><td>Replace suffix</td></tr><tr><td><code>${foo/#from/to}</code></td><td>Replace prefix</td></tr></tbody></table>

```bash
# Single line comment
```

```bash
: ' This is a multi line comment '
```

### Substrings

<table><tbody><tr><td><code>${foo:0:3}</code></td><td>Substring <em>(position, length)</em></td></tr><tr><td><code>${foo:(-3):3}</code></td><td>Substring from the right</td></tr></tbody></table>

### Length

### Manipulation

```bash
str="HELLO WORLD!" echo "${str,}" #=> "hELLO WORLD!" (lowercase 1st letter) echo "${str,,}" #=> "hello world!" (all lowercase) str="hello world!" echo "${str^}" #=> "Hello world!" (uppercase 1st letter) echo "${str^^}" #=> "HELLO WORLD!" (all uppercase)
```

### Default values

<table><tbody><tr><td><code>${foo:-val}</code></td><td><code>$foo</code>, or <code>val</code> if unset (or null)</td></tr><tr><td><code>${foo:=val}</code></td><td>Set <code>$foo</code> to <code>val</code> if unset (or null)</td></tr><tr><td><code>${foo:+val}</code></td><td><code>val</code> if <code>$foo</code> is set (and not null)</td></tr><tr><td><code>${foo:?message}</code></td><td>Show error message and exit if <code>$foo</code> is unset (or null)</td></tr></tbody></table>

Omitting the `:` removes the (non)nullity checks, e.g. `${foo-val}` expands to `val` if unset otherwise `$foo`.

## Loops

### Basic for loop

```bash
for i in /etc/rc.*; do echo "$i" done
```

### C-like for loop

```bash
for ((i = 0 ; i < 100 ; i++)); do echo "$i" done
```

### Ranges

```bash
for i in {1..5}; do echo "Welcome $i" done
```

#### With step size

```bash
for i in {5..50..5}; do echo "Welcome $i" done
```

### Reading lines

```bash
while read -r line; do echo "$line" done <file.txt
```

### Forever

## Functions

### Defining functions

```bash
myfunc() { echo "hello $1" }
```

```bash
# Same as above (alternate syntax) function myfunc { echo "hello $1" }
```

```bash
myfunc "John"
```

### Returning values

```bash
myfunc() { local myresult='some value' echo "$myresult" }
```

```bash
result=$(myfunc)
```

### Raising errors

```bash
myfunc() { return 1 }
```

```bash
if myfunc; then echo "success" else echo "failure" fi
```

### Arguments

<table><tbody><tr><td><code>$#</code></td><td>Number of arguments</td></tr><tr><td><code>$*</code></td><td>All positional arguments (as a single word)</td></tr><tr><td><code>$@</code></td><td>All positional arguments (as separate strings)</td></tr><tr><td><code>$1</code></td><td>First argument</td></tr><tr><td><code>$_</code></td><td>Last argument of the previous command</td></tr></tbody></table>

**Note**: `$@` and `$*` must be quoted in order to perform as described. Otherwise, they do exactly the same thing (arguments as separate strings).

See [Special parameters](https://web.archive.org/web/20230318164746/https://wiki.bash-hackers.org/syntax/shellvars#special_parameters_and_shell_variables).

## Conditionals

### Conditions

Note that `[[` is actually a command/program that returns either `0` (true) or `1` (false). Any program that obeys the same logic (like all base utils, such as `grep(1)` or `ping(1)`) can be used as condition, see examples.

<table><tbody><tr><td><code>[[ -z STRING ]]</code></td><td>Empty string</td></tr><tr><td><code>[[ -n STRING ]]</code></td><td>Not empty string</td></tr><tr><td><code>[[ STRING == STRING ]]</code></td><td>Equal</td></tr><tr><td><code>[[ STRING != STRING ]]</code></td><td>Not Equal</td></tr></tbody><tbody><tr><td><code>[[ NUM -eq NUM ]]</code></td><td>Equal</td></tr><tr><td><code>[[ NUM -ne NUM ]]</code></td><td>Not equal</td></tr><tr><td><code>[[ NUM -lt NUM ]]</code></td><td>Less than</td></tr><tr><td><code>[[ NUM -le NUM ]]</code></td><td>Less than or equal</td></tr><tr><td><code>[[ NUM -gt NUM ]]</code></td><td>Greater than</td></tr><tr><td><code>[[ NUM -ge NUM ]]</code></td><td>Greater than or equal</td></tr></tbody><tbody><tr><td><code>[[ STRING =~ STRING ]]</code></td><td>Regexp</td></tr></tbody><tbody><tr><td><code>(( NUM &lt; NUM ))</code></td><td>Numeric conditions</td></tr></tbody></table>

#### More conditions

<table><tbody><tr><td><code>[[ -o noclobber ]]</code></td><td>If OPTIONNAME is enabled</td></tr></tbody><tbody><tr><td><code>[[ ! EXPR ]]</code></td><td>Not</td></tr><tr><td><code>[[ X &amp;&amp; Y ]]</code></td><td>And</td></tr><tr><td><code>[[ X || Y ]]</code></td><td>Or</td></tr></tbody></table>

### File conditions

<table><tbody><tr><td><code>[[ -e FILE ]]</code></td><td>Exists</td></tr><tr><td><code>[[ -r FILE ]]</code></td><td>Readable</td></tr><tr><td><code>[[ -h FILE ]]</code></td><td>Symlink</td></tr><tr><td><code>[[ -d FILE ]]</code></td><td>Directory</td></tr><tr><td><code>[[ -w FILE ]]</code></td><td>Writable</td></tr><tr><td><code>[[ -s FILE ]]</code></td><td>Size is &gt; 0 bytes</td></tr><tr><td><code>[[ -f FILE ]]</code></td><td>File</td></tr><tr><td><code>[[ -x FILE ]]</code></td><td>Executable</td></tr></tbody><tbody><tr><td><code>[[ FILE1 -nt FILE2 ]]</code></td><td>1 is more recent than 2</td></tr><tr><td><code>[[ FILE1 -ot FILE2 ]]</code></td><td>2 is more recent than 1</td></tr><tr><td><code>[[ FILE1 -ef FILE2 ]]</code></td><td>Same files</td></tr></tbody></table>

### Example

```bash
# String if [[ -z "$string" ]]; then echo "String is empty" elif [[ -n "$string" ]]; then echo "String is not empty" else echo "This never happens" fi
```

```bash
# Combinations if [[ X && Y ]]; then ... fi
```

```bash
# Equal if [[ "$A" == "$B" ]]
```

```bash
# Regex if [[ "A" =~ . ]]
```

```bash
if (( $a < $b )); then echo "$a is smaller than $b" fi
```

```bash
if [[ -e "file.txt" ]]; then echo "file exists" fi
```

## Arrays

### Defining arrays

```bash
Fruits=('Apple' 'Banana' 'Orange')
```

```bash
Fruits[0]="Apple" Fruits[1]="Banana" Fruits[2]="Orange"
```

### Working with arrays

```bash
echo "${Fruits[0]}" # Element #0 echo "${Fruits[-1]}" # Last element echo "${Fruits[@]}" # All elements, space-separated echo "${#Fruits[@]}" # Number of elements echo "${#Fruits}" # String length of the 1st element echo "${#Fruits[3]}" # String length of the Nth element echo "${Fruits[@]:3:2}" # Range (from position 3, length 2) echo "${!Fruits[@]}" # Keys of all elements, space-separated
```

### Operations

```bash
Fruits=("${Fruits[@]}" "Watermelon") # Push Fruits+=('Watermelon') # Also Push Fruits=( "${Fruits[@]/Ap*/}" ) # Remove by regex match unset Fruits[2] # Remove one item Fruits=("${Fruits[@]}") # Duplicate Fruits=("${Fruits[@]}" "${Veggies[@]}") # Concatenate lines=(`cat "logfile"`) # Read from file
```

### Iteration

```bash
for i in "${arrayName[@]}"; do echo "$i" done
```

## Dictionaries

### Defining

```bash
declare -A sounds
```

```bash
sounds[dog]="bark" sounds[cow]="moo" sounds[bird]="tweet" sounds[wolf]="howl"
```

Declares `sound` as a Dictionary object (aka associative array).

### Working with dictionaries

```bash
echo "${sounds[dog]}" # Dog's sound echo "${sounds[@]}" # All values echo "${!sounds[@]}" # All keys echo "${#sounds[@]}" # Number of elements unset sounds[dog] # Delete dog
```

### Iteration

#### Iterate over values

```bash
for val in "${sounds[@]}"; do echo "$val" done
```

#### Iterate over keys

```bash
for key in "${!sounds[@]}"; do echo "$key" done
```

## Options

### Options

```bash
set -o noclobber # Avoid overlay files (echo "hi" > foo) set -o errexit # Used to exit upon error, avoiding cascading errors set -o pipefail # Unveils hidden failures set -o nounset # Exposes unset variables
```

### Glob options

```bash
shopt -s nullglob # Non-matching globs are removed ('*.foo' => '') shopt -s failglob # Non-matching globs throw errors shopt -s nocaseglob # Case insensitive globs shopt -s dotglob # Wildcards match dotfiles ("*.sh" => ".foo.sh") shopt -s globstar # Allow ** for recursive matches ('lib/**/*.rb' => 'lib/a/b/c.rb')
```

Set `GLOBIGNORE` as a colon-separated list of patterns to be removed from glob matches.

## History

### Commands

<table><tbody><tr><td><code>history</code></td><td>Show history</td></tr><tr><td><code>shopt -s histverify</code></td><td>Don’t execute expanded result immediately</td></tr></tbody></table>

### Expansions

<table><tbody><tr><td><code>!$</code></td><td>Expand last parameter of most recent command</td></tr><tr><td><code>!*</code></td><td>Expand all parameters of most recent command</td></tr><tr><td><code>!-n</code></td><td>Expand <code>n</code>th most recent command</td></tr><tr><td><code>!n</code></td><td>Expand <code>n</code>th command in history</td></tr><tr><td><code>!&lt;command&gt;</code></td><td>Expand most recent invocation of command <code>&lt;command&gt;</code></td></tr></tbody></table>

### Operations

<table><tbody><tr><td><code>!!</code></td><td>Execute last command again</td></tr><tr><td><code>!!:s/&lt;FROM&gt;/&lt;TO&gt;/</code></td><td>Replace first occurrence of <code>&lt;FROM&gt;</code> to <code>&lt;TO&gt;</code> in most recent command</td></tr><tr><td><code>!!:gs/&lt;FROM&gt;/&lt;TO&gt;/</code></td><td>Replace all occurrences of <code>&lt;FROM&gt;</code> to <code>&lt;TO&gt;</code> in most recent command</td></tr><tr><td><code>!$:t</code></td><td>Expand only basename from last parameter of most recent command</td></tr><tr><td><code>!$:h</code></td><td>Expand only directory from last parameter of most recent command</td></tr></tbody></table>

`!!` and `!$` can be replaced with any valid expansion.

### Slices

<table><tbody><tr><td><code>!!:n</code></td><td>Expand only <code>n</code>th token from most recent command (command is <code>0</code>; first argument is <code>1</code>)</td></tr><tr><td><code>!^</code></td><td>Expand first argument from most recent command</td></tr><tr><td><code>!$</code></td><td>Expand last token from most recent command</td></tr><tr><td><code>!!:n-m</code></td><td>Expand range of tokens from most recent command</td></tr><tr><td><code>!!:n-$</code></td><td>Expand <code>n</code>th token to last from most recent command</td></tr></tbody></table>

`!!` can be replaced with any valid expansion i.e. `!cat`, `!-2`, `!42`, etc.

## Miscellaneous

### Numeric calculations

```bash
$((a + 200)) # Add 200 to $a
```

```bash
$(($RANDOM%200)) # Random number 0..199
```

```bash
declare -i count # Declare as type integer count+=1 # Increment
```

### Subshells

```bash
(cd somedir; echo "I'm now in $PWD") pwd # still in first directory
```

### Redirection

```bash
python hello.py > output.txt # stdout to (file) python hello.py >> output.txt # stdout to (file), append python hello.py 2> error.log # stderr to (file) python hello.py 2>&1 # stderr to stdout python hello.py 2>/dev/null # stderr to (null) python hello.py >output.txt 2>&1 # stdout and stderr to (file), equivalent to &> python hello.py &>/dev/null # stdout and stderr to (null) echo "$0: warning: too many users" >&2 # print diagnostic message to stderr
```

```bash
python hello.py < foo.txt # feed foo.txt to stdin for python diff <(ls -r) <(ls) # Compare two stdout without files
```

### Inspecting commands

```bash
command -V cd #=> "cd is a function/alias/whatever"
```

### Trap errors

```bash
trap 'echo Error at about $LINENO' ERR
```

or

```bash
traperr() { echo "ERROR: ${BASH_SOURCE[1]} at about ${BASH_LINENO[0]}" } set -o errtrace trap traperr ERR
```

### Case/switch

```bash
case "$1" in start | up) vagrant up ;; *) echo "Usage: $0 {start|stop|ssh}" ;; esac
```

### Source relative

```bash
source "${0%/*}/../share/foo.sh"
```

### printf

```bash
printf "Hello %s, I'm %s" Sven Olga #=> "Hello Sven, I'm Olga printf "1 + 1 = %d" 2 #=> "1 + 1 = 2" printf "This is how you print a float: %f" 2 #=> "This is how you print a float: 2.000000" printf '%s\n' '#!/bin/bash' 'echo hello' >file # format string is applied to each group of arguments printf '%i+%i=%i\n' 1 2 3 4 5 9
```

### Transform strings

<table><tbody><tr><td><code>-c</code></td><td>Operations apply to characters not in the given set</td></tr><tr><td><code>-d</code></td><td>Delete characters</td></tr><tr><td><code>-s</code></td><td>Replaces repeated characters with single occurrence</td></tr><tr><td><code>-t</code></td><td>Truncates</td></tr><tr><td><code>[:upper:]</code></td><td>All upper case letters</td></tr><tr><td><code>[:lower:]</code></td><td>All lower case letters</td></tr><tr><td><code>[:digit:]</code></td><td>All digits</td></tr><tr><td><code>[:space:]</code></td><td>All whitespace</td></tr><tr><td><code>[:alpha:]</code></td><td>All letters</td></tr><tr><td><code>[:alnum:]</code></td><td>All letters and digits</td></tr></tbody></table>

#### Example

```bash
echo "Welcome To Devhints" | tr '[:lower:]' '[:upper:]' WELCOME TO DEVHINTS
```

### Directory of script

### Getting options

```bash
while [[ "$1" =~ ^- && ! "$1" == "--" ]]; do case $1 in -V | --version ) echo "$version" exit ;; -s | --string ) shift; string=$1 ;; -f | --flag ) flag=1 ;; esac; shift; done if [[ "$1" == '--' ]]; then shift; fi
```

### Heredoc

```sh
cat <<END hello world END
```

### Reading input

```bash
echo -n "Proceed? [y/n]: " read -r ans echo "$ans"
```

The `-r` option disables a peculiar legacy behavior with backslashes.

```bash
read -n 1 ans # Just one character
```

### Special variables

<table><tbody><tr><td><code>$?</code></td><td>Exit status of last task</td></tr><tr><td><code>$!</code></td><td>PID of last background task</td></tr><tr><td><code>$$</code></td><td>PID of shell</td></tr><tr><td><code>$0</code></td><td>Filename of the shell script</td></tr><tr><td><code>$_</code></td><td>Last argument of the previous command</td></tr><tr><td><code>${PIPESTATUS[n]}</code></td><td>return value of piped commands (array)</td></tr></tbody></table>

See [Special parameters](https://web.archive.org/web/20230318164746/https://wiki.bash-hackers.org/syntax/shellvars#special_parameters_and_shell_variables).

### Go to previous directory

```bash
pwd # /home/user/foo cd bar/ pwd # /home/user/foo/bar cd - pwd # /home/user/foo
```

### Check for command’s result

```bash
if ping -c 1 google.com; then echo "It appears you have a working internet connection" fi
```

### Grep check

```bash
if grep -q 'foo' ~/.bash_history; then echo "You appear to have typed 'foo' in the past" fi
```

## Also see

-   [Bash-hackers wiki](https://web.archive.org/web/20230406205817/https://wiki.bash-hackers.org/) _(bash-hackers.org)_
-   [Shell vars](https://web.archive.org/web/20230318164746/https://wiki.bash-hackers.org/syntax/shellvars) _(bash-hackers.org)_
-   [Learn bash in y minutes](https://learnxinyminutes.com/docs/bash/) _(learnxinyminutes.com)_
-   [Bash Guide](http://mywiki.wooledge.org/BashGuide) _(mywiki.wooledge.org)_
-   [ShellCheck](https://www.shellcheck.net/) _(shellcheck.net)_