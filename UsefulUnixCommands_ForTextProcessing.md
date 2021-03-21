# awk

A powerful command that can be used to extract logs between two timestamps

Example:<br>
$ awk -F'[]]|[[]' \ <br>
  '$0 ~ /^\[/ && $2 >= "2014-04-07 23:00" { p=1 }<br>
   $0 ~ /^\[/ && $2 >= "2014-04-08 02:00" { p=0 }<br>
                                        p { print $0 }' log
Where:

-F specifies the characters [ and ] as field separators using a regular expression
$0 references a complete line
$2 references the date field
p is used as boolean variable that guards the actual printing
$0 ~ /regex/ is true if regex matches $0

'>=' is used for lexicographically comparing string (equivalent to e.g. strcmp())

*Variation*<br>
For a timestamp format like YYYY-MM-DD HH24:MI:SS (without [] braces) the command can be modified as below:

$ awk \<br>
  '$0 ~ /^[0-9]{4}-[0-9]{2}-[0-9]{2} [0-2][0-9]:[0-5][0-9]:[0-5][0-9]/<br>
      {<br>
        if ($1" "$2 >= "2014-04-07 23:00")     p=1;<br>
        if ($1" "$2 >= "2014-04-08 02:00:01")  p=0;<br>
      }<br>
    p { print $0 }' log

Source: https://unix.stackexchange.com/questions/123979/how-to-extract-logs-between-two-time-stamps

# grep

A command to search an input stream for specific patterns.

# tail

A command to extract lines from end of the file. A powerful feature of this command is to use the -f option to keep appending the data as new data becomes available in input stream.

# head

Extract n lines from the beginning of the file

# wc

Useful to count the number of matching patters in a grep'd stream.

# cut

Usefule to truncate n characters from beginning/end of a line.




