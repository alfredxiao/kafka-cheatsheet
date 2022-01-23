# Default to current directory
- `find -name afile`

# Find by name
- `find ~ -name '*bash*'`
- `find . -name '*.txt'`

# Case insensitive
- `find . -iname abc.txt`
- there is no `-i` option

# NOT
- `find . ! -name "*abc*"`

# OR
- `find . \( -name '*.c' -o -name '*.go' \)` finds both C files and Go files

# Find within multiple paths
- `find ./dir1 ./dir2 -name "*abc*"`

# Find path
- `find . -path "./sr*sc"` will match `./src/misc`

# Otherwise mode
- `find . -name '*abc*' -o -print` prints files named not matcing `*abc*`
  - `-o` means OR/Otherwise
  - `-o -print` means for entries (that NOT matching `*abc*`), print it out
- `find . -name '*abc*' -print -o -print`
  - Prints found entries, for Otherwise (not matching) entries, print too

# Prune
- Basically means for a found entry, if it is a directory, don't look into this directory
- `find . -name temp -prune` finds things named 'temp' but not looking into directories named 'temp'
- `find . -name "temp" -prune -o -perm 644 -print`
  - finds files as per permission bits matching excluding 'temp' folder
- `find . -name "temp" -prune -o -name "*.c" -print`
  - finds all C files except those in temp folder

# Limit depth of sub-directories
- `find . -maxdepth 2 -name "*.txt"`

# Find by file type
- `find . -type d -name 'mydir*'`
- types
  - `d` directory
  - `f` regular file
  - `b` block file
  - `c` character file
  - `p` named pipe
  - `l` symbolic link
  - `s` socket
- specify multiple types
  - `find . -type d,f -name 'myfile*'`

# Find by permission bits
- `find . -perm 644`
- `find . -perm 4744` finds files SUID is on, also permission bits are `744`
- `find . -perm /4000` finds files SUID is on, ignoring permission bits
- `find / -perm /6000 -type f` finds files with both SUID and SGID on

# find by user/owner
- `find . -user user1`
- `find . -nouser` finds files do not being to an account

# find by group id
- `find / -gid 1003`
- `find / -gid 1003 2>/dev/null`

# find empty files/dirs
- `find . -empty`

# modified minutes ago
- `find . -mmin -60` # files modified less than 60 minutes ago
- `find . -mmin 60`  # files modified exactly 60 minutes ago
- `find . -mmin +60` # files modified more than 60 minutes ago
## same for `-amin` for accessed minutes ago
## same for `-cmin` for changed minutes ago

# find by days ago
* period calculation: n hours ago -> n/24 = p (dropping fractional part)
  * e.g. 10/24 => 0, 40/24 => 1, 50/24 => 2
* `find /tmp -mtime 0`   # files modified where p==1
* `find /tmp -mtime +0`  # files modified where p>0
* `find /tmp -mtime 1`   # files modified where p==1
* `find /tmp -mtime +1`  # files modified where p>1
* `find /tmp -mtime -1`  # files modified where p<1
## same for `-atime` and `-ctime`

# find by size
- `find . -size 1024c` size is 1024 bytes
- `find . -size +1024` sizer is > 1024 bytes
- `find . -size -1024` sizer is < 1024 bytes
- `find . -size +100k` size is > 100*1024 bytes
- `find . -size +1M` size is > 1024*1024 bytes

# find by newer than another file
- `find . -newer /etc/passwd`

# actions
- `find . -name '*.txt' -delete` delete found files
- `find . -name '*.txt' -print` print file name (actually is the default action)
- `find . -name '*.txt' -exec rm {} \;` pass to a command

# find by inode number
- `find / -inum 278772`
