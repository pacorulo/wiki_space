**$0** The variable $0 contains the script name itself.

Command-line arguments range from $1 to $9. These variables correspond to the arguments with which a script was invoked. Here n is a positive decimal number corresponding to the position of an argument (the first argument is $1, the second argument is $2, and so on).

The **$#** variable contains the total number of parameters entered on the command line. The value of this variable is always an integer.

**$*** This special variable contains all the command-line arguments that have been passed to a script, listed as a single word. If a script receives two arguments, $* is equivalent to $1 $2.

The **$@** special variable is similar to $* in that it contains all the values specified as command-line arguments. However, $@ lists each argument as a separate word, whereas $* does not distinguish between ordinary spaces separating values and those within quotation marks. If a script receives two arguments, $@ is equivalent to $1 $2.

**$?** The exit status of the last command executed.

**$!** The process number of the last background command

**$$** Echo PID of current Shell

