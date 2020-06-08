- [Strings](https://github.com/Ariel-Yu/knowledge-bases/blob/master/linux/commands.md#strings)
- [Files](https://github.com/Ariel-Yu/knowledge-bases/blob/master/linux/commands.md#files)
- [Directories](https://github.com/Ariel-Yu/knowledge-bases/blob/master/linux/commands.md#directories)
- [System porcesses](https://github.com/Ariel-Yu/knowledge-bases/blob/master/linux/commands.md#system-processes)
- [IP addresses](https://github.com/Ariel-Yu/knowledge-bases/blob/master/linux/commands.md#ip-addresses)
- [Networking](https://github.com/Ariel-Yu/knowledge-bases/blob/master/linux/commands.md#networking)
- [Environment variables](https://github.com/Ariel-Yu/knowledge-bases/blob/master/linux/commands.md#environment-variables)

### Strings

> `echo -n string_you_want_to_encode | base64`
- Encode string in base64
- -n avoid newline, should be in front of string_you_want_to_encode

> `echo string_you_want_to_decode | base64 --decode`
- Decode string from base64

> `wc <file_name>`

> `<output> | wc`
- Word count of a file or an output
- \# of lines / word count / charater count / file name
  - -l: # of lines
  - -w: word count
  - -c: count of byte
  - -m: character count
  
> `wc <file_name1> <file_name2>`
- \# of lines / word count / charater count / file name 1
- \# of lines / word count / charater count / file name 2
- \# of lines / word count / charater count / total

### Files

> `find / -name <file_name>`
- Find <file_name> from root

> `grep -Ril <content_to_find> <from_where_to_start>`
- Find <content_to_find> from <from_where_to_start>
- R: Recursively find
- i: Case insensitive
- l: Show names of the files include <content_to_find>

> `chmod <+|-><r|w|x> <file_name>`
- Change <file_name> permission
  - **+**: grant permission
  - **-**: disable permission
  - r: read access
  - w: write access
  - x: executable access

> `content | tee <file_name>`
- Output \<content> to <file_name>

> `echo <content> > <file_name>`
- Create <file_name> with \<content>

> `echo <content> >> <file_name>`
- Append \<content> in <file_name>

> `cat|tail|less|more <file_name>`
- view <file_name>

### Directories

> `mkdir -p <existed_directories/parent_directory/child_directory>`

### System processes

> `ps aux`
- See all the processes on the system using BSD syntax
  - ps: processes status from /proc file
  - a = show processes for all users
  - u = display the process's user/owner
  - x = also show processes not attached to a terminal

> `ps -ef`
- See all the processes on the system using standard syntax

> `grep Cap /proc/<PID>/status`
- See the [linux capabilities](https://github.com/torvalds/linux/blob/master/include/uapi/linux/capability.h) of the process with \<PID>

> `capsh --decode=<capabilities>`
- Decode the linux capabilities

### IP addresses

> `curl ifconfig.me`
- Get the public IP address of the local machine

> `config.me`
- Display network interfaces

> `ip a`
- Display network interfaces
- From [iproute2util](https://www.tecmint.com/ifconfig-vs-ip-command-comparing-network-configuration/) only available for linux kernal OS

### Networking

> `nc <IP> <port>` (Netcat)
- v: verbose mode
- z: scan for listening daemons, without actually sending any data to them
- w <number>: specifies a timeout <number> for connection that can not be established
  
### Environment variables

> `printenv`
- See all the environment variables
