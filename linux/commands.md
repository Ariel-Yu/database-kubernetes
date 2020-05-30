- [Strings](https://github.com/Ariel-Yu/knowledge-bases/blob/master/linux/commands.md#strings)
- [Files](https://github.com/Ariel-Yu/knowledge-bases/blob/master/linux/commands.md#files)
- [Directories](https://github.com/Ariel-Yu/knowledge-bases/blob/master/linux/commands.md#directories)
- [System porcesses](https://github.com/Ariel-Yu/knowledge-bases/blob/master/linux/commands.md#system-processes)
- [IP addresses](https://github.com/Ariel-Yu/knowledge-bases/blob/master/linux/commands.md#ip-addresses)
- [Networking](https://github.com/Ariel-Yu/knowledge-bases/blob/master/linux/commands.md#networking)

### Strings

> `echo string_you_want_to_encode | base64`
- Encode string in base64

### Files

> `find / -name <file_name>`
- Find <file_name> from root

> `chmod <+|-><r|w|x> <file_name>`
- Change <file_name> permission
  - **+**: grant permission
  - **-**: disable permission
  - r: read access
  - w: write access
  - x: executable access

> `content | tee <file_name>`
- Output content to <file_name>

> `echo <some_content> > <file_name>`
- Create <file_name> with <some_content>

> `echo <some_content> >> <file_name>`
- Append <some_content> in <file_name>

> `cat|tail|less|more <file_name>`
- view <file_name>

### Directories

> `mkdir -p <existed_directories/parent_directory/child_directory>`

### System processes

> `ps aux`
- ps: processes status from /proc file
- a = show processes for all users
- u = display the process's user/owner
- x = also show processes not attached to a terminal

> `grep Cap /proc/<PID>/status`
- See the [linux capabilities](https://github.com/torvalds/linux/blob/master/include/uapi/linux/capability.h) of the process with <PID>

> `capsh --decode=<capabilities>`
- Decode the linux capabilities

### IP addresses

> `curl ifconfig.me`
- Get the public IP address of the local machine

> `ip a`
- Get the IP addresses of the local machine 
- Linux

### Networking

> `nc` <IP> <port> (Netcat)
- v: verbose mode
- z: scan for listening daemons, without actually sending any data to them
- w <number>: specifies a timeout <number> for connection that can not be established
