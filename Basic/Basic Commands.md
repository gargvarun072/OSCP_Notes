Basic Commands

# Basic Commands

1.  Print total lines in a file - `wc –l *`
2.  Print only 8 or more length strings - `strings -n 8 filename`
3.  Enumerate the filesystem to see if this group has any special access - `find / -type f -group {bugtracker} 2>/dev/null`
4. Crack the zip file password - `fcrackzip -u -D -p <worlist> <zipfile>`